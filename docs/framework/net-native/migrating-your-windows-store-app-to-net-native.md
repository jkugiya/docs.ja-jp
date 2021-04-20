---
description: '詳細情報: Windows ストア アプリを .NET Native に移行する'
title: Windows ストア アプリの .NET Native への移行
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
ms.openlocfilehash: 7a9e8f7108ca21dbbae7ca0097b15af078c8c6bb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100464678"
---
# <a name="migrate-your-windows-store-app-to-net-native"></a>Windows ストア アプリを .NET Native に移行する

.NET Native では、Windows ストアまたは開発者のコンピューターでアプリの静的なコンパイルが行われます。 これは、デバイス上で Just-In-Time (JIT) コンパイラまたは [ネイティブ イメージ ジェネレーター (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) によって Windows ストア アプリに対して実行される動的なコンパイルとは異なります。 違いはありますが、.NET Native では、[Windows ストア アプリ用 .NET](/previous-versions/windows/apps/br230302(v=vs.140)) との互換性を保持しようとしています。 ほとんどの場合、Windows ストア アプリ用 .NET で機能するものは .NET Native でも機能します。  ただし、動作に違いがある場合もあります。 このドキュメントでは、次の領域における、標準の Windows ストア アプリ用 .NET と .NET Native との違いについて説明します。

- [全般的なランタイムの違い](#Runtime)

- [動的プログラミングの違い](#Dynamic)

- [リフレクションに関するその他の違い](#Reflection)

- [サポートされていないシナリオと API](#Unsupported)

- [Visual Studio の違い](#VS)

<a name="Runtime"></a>

## <a name="general-runtime-differences"></a>全般的なランタイムの違い

- アプリが共通言語ランタイム (CLR) で実行されているときに JIT コンパイラによってスローされる <xref:System.TypeLoadException> などの例外は、通常、.NET Native によって処理されるときにはコンパイル時エラーになります。

- アプリの UI スレッドから <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> メソッドを呼び出さないでください。 これにより .NET Native でデッドロックが発生する可能性があります。

- 静的クラス コンストラクターの呼び出し順序に依存しないでください。 .NET Native では、呼び出し順序が標準ランタイムでの順序と異なります (標準ランタイムを使用する場合であっても、静的クラス コンストラクターの実行順序に依存しないでください)。

- スレッドでの呼び出しを行わない無限ループ (たとえば、 `while(true);`) によって、アプリが停止する可能性があります。 同様に、長時間または無限の待機によってもアプリが停止する可能性があります。

- .NET Native では、特定の汎用初期化サイクルで例外がスローされません。 たとえば、次のコードは標準 CLR では <xref:System.TypeLoadException> 例外をスローします。 .NET Native ではそうではありません。

  [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]

- 場合によっては、.NET Native では、.NET Framework クラス ライブラリのさまざまな実装が用意されます。 メソッドから返されるオブジェクトは、常に、返される型のメンバーを実装します。 ただし、その補助的な実装が異なるため、その他の .NET Framework プラットフォームの場合と同じ型セットへのオブジェクトのキャストを行うことができない場合があります。 たとえば、 <xref:System.Collections.Generic.IEnumerable%601> や <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> などのメソッドにより返される <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> インターフェイス オブジェクトを `T[]`にキャストできない場合があります。

- WinInet キャッシュは、Windows ストア アプリ用 .NET では既定で有効になっていませんが、.NET Native では有効になっています。 これによりパフォーマンスが向上しますが、作業セットへの影響があります。 開発者のアクションは必要ありません。

<a name="Dynamic"></a>

## <a name="dynamic-programming-differences"></a>動的プログラミングの違い

.NET Native では、パフォーマンスを最大化するために、.NET Framework からコードを静的にリンクして、コードをアプリにローカルなものにします。 ただし、バイナリ サイズは小さいままである必要があるため、.NET Framework 全体を取り入れることはできません。 .NET Native コンパイラは、未使用のコードへの参照を削除する依存関係レジューサを使用して、この制限を解決します。 ただし、.NET Native では、型情報をコンパイル時に静的に推論できず、代わりに実行時に動的に取得される場合、一部の型情報やコードが維持または生成されないことがあります。

.NET Native では、リフレクションと動的プログラミングが可能です。 ただし、すべての型をリフレクション対象としてマークできるわけではありません。そうすると、生成されるコード サイズが大きくなりすぎるため (特に、.NET Framework での パブリック API へのリフレクションがサポートされているため) です。 .NET Native コンパイラは、どの型でリフレクションをサポートする必要があるかを適切に判断し、それらの型についてのみメタデータを維持し、コードを生成します。

たとえば、データ バインディングは、プロパティ名を関数にマップするためにアプリを必要とします。 Windows ストア アプリ用 .NET では、共通言語ランタイムが自動的にリフレクションを使用して、マネージド型および公開されているネイティブ型にこの機能を提供します。 .NET Native では、データのバインド先の型のメタデータが、コンパイラによって自動的にインクルードされます。

.NET Native コンパイラでは、ヒントやディレクティブなしで機能する <xref:System.Collections.Generic.List%601> や <xref:System.Collections.Generic.Dictionary%602> などの一般的に使用されるジェネリック型も処理できます。 [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) キーワードも、一定の制限の下でサポートされます。

> [!NOTE]
> アプリを .NET Native に移植するときには、すべての動的コード パスを十分にテストする必要があります。

ほとんどの開発者にとっては .NET Native の既定の構成で十分ですが、開発者によっては、ランタイム ディレクティブ (.rd.xml) ファイルを使用した構成の微調整が必要となる場合もあります。 さらに、場合によっては、.NET Native コンパイラが、どのメタデータがリフレクション用に使用できる必要があるかを判断できず、特に次のような場合に、ヒントを利用することがあります。

- <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> や <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> などの一部の構造体は、静的に決定できません。

- コンパイラでインスタンス化を決定できないため、リフレクション対象のジェネリック型をランタイム ディレクティブで指定する必要があります。 これは、すべてのコードを含める必要があるだけではなく、ジェネリック型へのリフレクションによって無限サイクルが生じる可能性があるためです (たとえば、ジェネリック型でジェネリック メソッドが呼び出された場合)。

> [!NOTE]
> ランタイム ディレクティブは、ランタイム ディレクティブ (.rd.xml) ファイルで定義されます。 このファイルの使用方法に関する全般的な情報は、「[Getting Started with .NET Native](getting-started-with-net-native.md)」(.NET ネイティブの概要) をご覧ください。 ランタイム ディレクティブについては、「 [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md)」をご覧ください。

.NET Native には、既定セット以外のどの型でリフレクションをサポートするかを開発者が決定するときに役立つプロファイル ツールも含まれています。

<a name="Reflection"></a>

## <a name="other-reflection-related-differences"></a>リフレクションに関するその他の違い

Windows ストア アプリ用 .NET と .NET Native の間には、その動作にリフレクション関連のその他の個別の違いが多数あります。

.NET Native では:

- .NET Framework クラス ライブラリでの型とメンバーに対するプライベート リフレクションはサポートされません。 ただし、独自のプライベート型とメンバー、およびサードパーティ ライブラリの型とメンバーに対するリフレクションは行うことができます。

- <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> プロパティは、戻り値を表す `false` オブジェクトに対し、正しく <xref:System.Reflection.ParameterInfo> を返します。 Windows ストア アプリ用 .NET の場合、これは `true`を返します。 これに対する中間言語 (IL) による直接的なサポートはなく、解釈は言語に任されます。

- <xref:System.RuntimeFieldHandle> 構造体と <xref:System.RuntimeMethodHandle> 構造体のパブリック メンバーはサポートされません。 これらの型は、LINQ、式ツリー、および静的な配列の初期化でのみサポートされます。

- <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> と <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> の基底クラスには隠ぺいされたメンバーが含まれるため、明示的なオーバーライドなしでオーバーライドできます。 これは、その他の [RuntimeReflectionExtensions.GetRuntime*](xref:System.Reflection.RuntimeReflectionExtensions) メソッドの場合も同様です。

- 特定の組み合わせ (たとえば、`byref` オブジェクトの配列) を作成しようとしたときに、<xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> と <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> が失敗することはありません。

- リフレクションを使用して、ポインター パラメーターを持つメンバーを呼び出すことはできません。

- リフレクションを使用して、ポインター フィールドを取得または設定することはできません。

- 引数カウントが間違っていて、いずれかの引数の型が正しくない場合、.NET Native では <xref:System.Reflection.TargetParameterCountException> ではなく <xref:System.ArgumentException> がスローされます。

- 通常、例外のバイナリ シリアル化はサポートされません。 そのため、シリアル化不可能なオブジェクトを <xref:System.Exception.Data%2A?displayProperty=nameWithType> ディクショナリに追加できます。

<a name="Unsupported"></a>

## <a name="unsupported-scenarios-and-apis"></a>サポートされていないシナリオと API

次のセクションに、全般的な開発、相互運用、および HTTPClient や Windows Communication Foundation (WCF) などの技術でサポートされないシナリオと API を示します。

- [一般的な開発](#General)

- [HttpClient](#HttpClient)

- [相互運用](#Interop)

- [サポートされていない API](#APIs)

<a name="General"></a>

### <a name="general-development-differences"></a>全般的な開発の違い

**値型**

- 値型の <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> メソッドと <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> メソッドをオーバーライドする場合は、基底クラスの実装を呼び出さないでください。 Windows ストア アプリ用 .NET では、これらのメソッドはリフレクションに依存します。 コンパイル時、.NET Native では、ランタイム リフレクションに依存しない実装が生成されます。 つまり、これら 2 つのメソッドをオーバーライドしなければ、.NET Native によるコンパイル時に実装が生成されるため、これらは期待どおりに動作します。 ただし、基底クラスの実装を呼び出さずにこれらのメソッドをオーバーライドすると、例外が発生します。

- 1 メガバイトより大きい値型はサポートされません。

- .NET Native では、値型でパラメーターなしのコンストラクターを使用することはできません (C# と Visual Basic では、値型でのパラメーターなしのコンストラクターは禁止されています。 ただし、IL ではこれらを作成できます)。

**配列**

- ゼロ以外の下限を持つ配列はサポートされません。 通常、これらの配列は <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> オーバーロードを呼び出すことで作成されます。

- 多次元配列の動的作成はサポートされません。 そのような配列は通常、 <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> パラメーターを含む `lengths` メソッドのオーバーロードを呼び出すか、 <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> メソッドを呼び出すことで作成されます。

- 4 つ以上の次元を持つ多次元配列 (つまり、 <xref:System.Array.Rank%2A?displayProperty=nameWithType> プロパティ値が 4 以上のもの) はサポートされません。 代わりに [ジャグ配列](../../csharp/programming-guide/arrays/jagged-arrays.md) (配列の配列) を使用してください。 たとえば、 `array[x,y,z]` は無効ですが、 `array[x][y][z]` は有効です。

- 多次元配列の共変性はサポートされず、実行時に <xref:System.InvalidCastException> 例外を発生させます。

**ジェネリック**

- ジェネリック型の無限展開はコンパイル エラーになります。 たとえば、このコードはコンパイルに失敗します。

  [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]

**ポインター**

- ポインターの配列はサポートされていません。

- リフレクションを使用して、ポインター フィールドを取得または設定することはできません。

**シリアル化**

<xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> 属性はサポートされていません。 代わりに <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> 属性を使用してください。

**リソース**

<xref:System.Diagnostics.Tracing.EventSource> クラスでのローカライズされたリソースの使用はサポートされません。 <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> プロパティはローカライズされたリソースを定義しません。

**デリゲート**

`Delegate.BeginInvoke` と `Delegate.EndInvoke` はサポートされません。

**その他の API**

- <xref:System.Runtime.InteropServices.GuidAttribute> 属性が型に適用されない場合、[TypeInfo.GUID](xref:System.Type.GUID) プロパティは <xref:System.PlatformNotSupportedException> 例外をスローします。 GUID は主に COM サポートで使用されます。

- .NET Native では、<xref:System.DateTime.Parse%2A?displayProperty=nameWithType> メソッドで、短い日付を含む文字列が正しく解析されます。 ただし、日付と時刻の解析の特定の変更との互換性は維持されません。

- .NET Native では、<xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` は適切に丸められます。 CLR の一部のバージョンでは、結果の文字列が丸められるのではなく、切り捨てられます。

<a name="HttpClient"></a>

### <a name="httpclient-differences"></a>HttpClient の違い

.NET Native では、<xref:System.Net.Http.HttpClientHandler> クラスは、標準の Windows ストア アプリ用 .NET で使用される <xref:System.Net.WebRequest> クラスと <xref:System.Net.WebResponse> クラスの代わりに、(<xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> クラスを通して) WinINet を内部使用します。  WinINet では、 <xref:System.Net.Http.HttpClientHandler> クラスでサポートされる構成オプションがすべてサポートされるわけではありません。  その結果、次のような影響が出ています。

- <xref:System.Net.Http.HttpClientHandler> の機能プロパティの一部は、.NET Native では `false` を返しますが、標準の Windows ストア アプリ用 .NET では `true` を返します。

- 構成プロパティ `get` アクセサーの一部は、.NET Native では常に固定値を返しますが、これは Windows ストア アプリ用 .NET の既定の構成値とは異なっています。

次のサブセクションで、その他の動作の違いについて説明します。

**Proxy**

<xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> クラスで、要求ごとのプロキシの構成とオーバーライドはサポートされません。  つまり、.NET Native では、すべての要求でシステム構成のプロキシ サーバーが使用されるか、プロキシ サーバーは使用されません (<xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> プロパティの値によって決まります)。  Windows ストア アプリ用 .NET では、プロキシ サーバーは <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> プロパティにより定義されます。  .NET Native では、<xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> を `null` 以外の値に設定すると、<xref:System.PlatformNotSupportedException> 例外がスローされます。  <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> プロパティは、.NET Native では `false` を返しますが、標準の Windows ストア アプリ用 .NET Framework では `true` を返します。

**自動リダイレクト**

<xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> クラスでは、自動リダイレクトの最大数の構成が許可されません。  標準の Windows ストア アプリ用 .NET での <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> プロパティの値は既定で 50 で、変更できません。 .NET Native では、このプロパティの値は 10 であり、変更しようとすると <xref:System.PlatformNotSupportedException> 例外がスローされます。  <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> プロパティは、.NET Native では `false` を返し、Windows ストア アプリ用 .NET では `true` を返します。

**自動展開**

Windows ストア アプリ用 .NET では、 <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> プロパティを <xref:System.Net.DecompressionMethods.Deflate>、 <xref:System.Net.DecompressionMethods.GZip>、 <xref:System.Net.DecompressionMethods.Deflate> と <xref:System.Net.DecompressionMethods.GZip>の両方、または <xref:System.Net.DecompressionMethods.None>に設定できます。  .NET Native では、<xref:System.Net.DecompressionMethods.Deflate> と <xref:System.Net.DecompressionMethods.GZip> の両方に設定するか <xref:System.Net.DecompressionMethods.None> のみがサポートされます。  <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> プロパティを <xref:System.Net.DecompressionMethods.Deflate> のみまたは <xref:System.Net.DecompressionMethods.GZip> のみに設定しようとすると、 <xref:System.Net.DecompressionMethods.Deflate> と <xref:System.Net.DecompressionMethods.GZip>の両方に自動的に設定されます。

**Cookie**

クッキーの処理は、 <xref:System.Net.Http.HttpClient> と WinINet により同時に行われます。  <xref:System.Net.CookieContainer> のクッキーは、WinINet クッキー キャッシュのクッキーと組み合わされます。  <xref:System.Net.CookieContainer> のクッキーを削除すると <xref:System.Net.Http.HttpClient> からクッキーが送信されませんが、クッキーが既に WinINet に示されており、ユーザーによって削除されない場合、WinINet がクッキーを送信します。  <xref:System.Net.Http.HttpClient>、 <xref:System.Net.Http.HttpClientHandler>、または <xref:System.Net.CookieContainer> API を使用して、プログラムにより WinINet からクッキーを削除することはできません。  <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> プロパティを `false` に設定しても、 <xref:System.Net.Http.HttpClient> からクッキーが送信されなくなるのみで、WinINet の要求にはまだそのクッキーが含まれている可能性があります。

**資格情報**

Windows ストア アプリ用 .NET では、 <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> プロパティと <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> プロパティは独立して動作します。  また、 <xref:System.Net.Http.HttpClientHandler.Credentials%2A> プロパティは <xref:System.Net.ICredentials> インターフェイスを実装するオブジェクトをすべて受け入れます。  .NET Native では、<xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> プロパティを `true` に設定すると、<xref:System.Net.Http.HttpClientHandler.Credentials%2A> プロパティが `null` になります。  さらに、 <xref:System.Net.Http.HttpClientHandler.Credentials%2A> プロパティは、 `null`、 <xref:System.Net.CredentialCache.DefaultCredentials%2A>、または <xref:System.Net.NetworkCredential>型のオブジェクトにしか設定できません。  その他の <xref:System.Net.ICredentials> オブジェクト (最も一般的なものは <xref:System.Net.CredentialCache>) を <xref:System.Net.Http.HttpClientHandler.Credentials%2A> プロパティに割り当てると、 <xref:System.PlatformNotSupportedException>がスローされます。

**その他のサポートされていない機能または構成できない機能**

.NET Native では:

- <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> プロパティの値は常に <xref:System.Net.Http.ClientCertificateOption.Automatic>です。  Windows ストア アプリ用 .NET での既定値は <xref:System.Net.Http.ClientCertificateOption.Manual>です。

- <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> プロパティは構成できません。

- <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> プロパティは常に `true`です。  Windows ストア アプリ用 .NET での既定値は `false`です。

- 応答の `SetCookie2` ヘッダーは廃止されたものとして無視されます。

<a name="Interop"></a>

### <a name="interop-differences"></a>相互運用の違い

 **非推奨の API**

 マネージド コードで相互運用性のために使用される頻度が低い API のいくつかが、非推奨にされました。 .NET Native でこれらの API を使用すると、<xref:System.NotImplementedException> または <xref:System.PlatformNotSupportedException> 例外がスローされるか、コンパイラ エラーになる場合があります。 Windows ストア アプリ用 .NET では、これらの API は廃止としてマークされていますが、これらの API を呼び出すとコンパイラ エラーではなくコンパイラの警告が生成されます。

 非推奨の `VARIANT` マーシャリング用 API には、以下が含まれます。

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>

 <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> はサポートされていますが、一部のシナリオ ([IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) や `byref` バリアントと共に使用された場合など) では例外がスローされます。

 非推奨の [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) サポート用 API には、以下が含まれます。

- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>

非推奨のクラシック COM イベント用 API には、以下が含まれます。

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>

非推奨の <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> インターフェイスの API (.NET Native では非サポート) には、以下が含まれます。

- <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (すべてのメンバー)
- <xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (すべてのメンバー)
- <xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (すべてのメンバー)
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>

その他のサポートされない相互運用機能には、以下が含まれます。

- <xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (すべてのメンバー)
- <xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (すべてのメンバー)
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>

 ほとんど使用されないマーシャリング API:

- <xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29?displayProperty=fullName>

 **プラットフォーム呼び出しと COM 相互運用の互換性**

 ほとんどのプラットフォーム呼び出しと COM 相互運用シナリオは、.NET Native でもサポートされます。 特に、Windows ランタイム (WinRT) API とのすべての相互運用性と Windows ランタイムで必要なすべてのマーシャリングがサポートされます。 これには、次のものに対するマーシャリング サポートが含まれます。

- 配列 ( <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>を含む)

- `BStr`

- デリゲート

- 文字列 (Unicode、ANSI、および HSTRING)

- 構造体 (`byref` と `byval`)

- Unions

- Win32 ハンドル

- すべての WinRT 構造体

- マーシャリング バリアント型の部分的なサポート。 サポート対象は次のとおりです。

  - <xref:System.Boolean>

  - <xref:System.Byte>

  - <xref:System.Decimal>

  - <xref:System.Double>

  - <xref:System.Int16>

  - <xref:System.Int32>

  - <xref:System.Int64>

  - <xref:System.SByte>

  - <xref:System.Single>

  - <xref:System.UInt16>

  - <xref:System.UInt32>

  - <xref:System.UInt64>

  - `BStr`

  - [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)

ただし、.NET Native では、以下はサポートされません。

- クラシック COM イベントの使用

- マネージド型での <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> インターフェイスの実装

- [属性を使用したマネージド型での](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) IDispatch <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> インターフェイスの実装。 ただし、`IDispatch` を通して COM オブジェクトを呼び出すことはできず、マネージド オブジェクトで `IDispatch` を実装できません。

リフレクションを使用したプラットフォーム呼び出しメソッドの呼び出しはサポートされません。 この制限を回避するには、別のメソッドでメソッド呼び出しをラップし、リフレクションを使用してラッパーを代わりに呼び出します。

<a name="APIs"></a>

### <a name="other-differences-from-net-apis-for-windows-store-apps"></a>その他の Windows ストア アプリ用 .NET API との違い

このセクションには、.NET Native でサポートされないその他の API を示します。 サポートされない API で最も多いのは、Windows Communication Foundation (WCF) API です。

**DataAnnotations (System.ComponentModel.DataAnnotations)**

.NET Native では、<xref:System.ComponentModel.DataAnnotations> 名前空間と <xref:System.ComponentModel.DataAnnotations.Schema> 名前空間内の型はサポートされません。 これらには、Windows 8 向け Windows ストア アプリ用 .NET に存在する次の型が含まれます。

- <xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>
- <xref:System.ComponentModel.DataAnnotations.EditableAttribute>
- <xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>
- <xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>

 **Visual Basic**

Visual Basic は、現在 .NET Native ではサポートされません。 <xref:Microsoft.VisualBasic> 名前空間と <xref:Microsoft.VisualBasic.CompilerServices> 名前空間内の次の型は、.NET Native では使用できません。

- <xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>

**リフレクション コンテキスト (System.Reflection.Context 名前空間)**

<xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> クラスは .NET Native ではサポートされません。

**RTC (System.Net.Http.Rtc)**

`System.Net.Http.RtcRequestFactory` クラスは .NET Native ではサポートされません。

**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**

[System.ServiceModel.* 名前空間](xref:System.ServiceModel)内の型は、.NET Native ではサポートされません。 これらには、次の型が含まれます。

- <xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>
- <xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>
- <xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>
- <xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>
- <xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>

### <a name="differences-in-serializers"></a>シリアライザーの違い

<xref:System.Runtime.Serialization.DataContractSerializer>、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>、および <xref:System.Xml.Serialization.XmlSerializer> クラスによるシリアル化と逆シリアル化に関する違いを次に示します。

- .NET Native では、<xref:System.Runtime.Serialization.DataContractSerializer> と <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> は、型がルート シリアル化型ではない基底クラス メンバーを持つ派生クラスのシリアル化または逆シリアル化に失敗します。 たとえば、次のコードでは、 `Y` をシリアル化または逆シリアル化しようとするとエラーになります。

  [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]

  基底クラスのメンバーはシリアル化時にスキャンされないため、 `InnerType` 型はシリアライザーに認識されていません。

- <xref:System.Runtime.Serialization.DataContractSerializer> と <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> は、 <xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装するクラスまたは構造体のシリアル化に失敗します。 たとえば、次の型ではシリアル化と逆シリアル化が失敗します。

- <xref:System.Xml.Serialization.XmlSerializer> は、シリアル化するオブジェクトの正確な型を認識していないため、次のオブジェクト値をシリアル化できません。

- <xref:System.Xml.Serialization.XmlSerializer> は、シリアル化されるオブジェクトの型が <xref:System.Xml.XmlQualifiedName>の場合、シリアル化と逆シリアル化に失敗します。

- すべてのシリアライザー (<xref:System.Runtime.Serialization.DataContractSerializer>、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>、および <xref:System.Xml.Serialization.XmlSerializer>) は、 <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> 型または <xref:System.Xml.Linq.XElement>を含む型のシリアル化コードを生成できません。 代わりに、ビルド時エラーが表示されます。

- 次のシリアル化型のコンストラクターが、期待どおりに動作する保証はありません。

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29>

- <xref:System.Xml.Serialization.XmlSerializer> は、次のいずれかの属性が設定されているメソッドを持つ型のコードを生成できません。

  - <xref:System.Runtime.Serialization.OnSerializingAttribute>

  - <xref:System.Runtime.Serialization.OnSerializedAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializingAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializedAttribute>

- <xref:System.Xml.Serialization.XmlSerializer> は、 <xref:System.Xml.Serialization.IXmlSerializable> カスタム シリアル化インターフェイスを受け入れません。 このインターフェイスを実装するクラスがある場合、 <xref:System.Xml.Serialization.XmlSerializer> は型を Plain Old CLR Object (POCO) 型であると見なし、そのパブリック プロパティのみをシリアル化します。

- プレーンな <xref:System.Exception> オブジェクトのシリアル化は、<xref:System.Runtime.Serialization.DataContractSerializer> と <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> では正しく行われません。

<a name="VS"></a>

## <a name="visual-studio-differences"></a>Visual Studio の違い

**例外とデバッグ**

デバッガーで .NET Native を使用してコンパイルされたアプリを実行する場合、次の例外の種類について初回例外が有効になります。

- <xref:System.MemberAccessException>

- <xref:System.TypeAccessException>

**アプリのビルド**

Visual Studio で既定で使用される x86 ビルド ツールを使用します。 C:\Program Files (x86)\MSBuild\12.0\bin\amd64 にある AMD64 MSBuild ツールは、ビルドの問題が発生する可能性があるため、使用しないことをお勧めします。

**プロファイラー**

- Visual Studio CPU プロファイラーと XAML メモリ プロファイラーでは、マイ コードのみは正しく表示されません。

- XAML メモリ プロファイラーでは、マネージド ヒープ データが正しく表示されません。

- CPU プロファイラーでは、モジュールが正しく識別されず、プレフィックス付きの関数名が表示されます。

**単体テスト ライブラリ プロジェクト**

Windows ストア アプリ用単体テスト ライブラリ プロジェクトで .NET Native を有効にすることはサポートされていません。有効にすると、プロジェクトはビルドに失敗します。

## <a name="see-also"></a>関連項目

- [はじめに](getting-started-with-net-native.md)
- [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](runtime-directives-rd-xml-configuration-file-reference.md)
- [Windows ストア アプリ用 .NET の概要](/previous-versions/windows/apps/br230302(v=vs.140))
- [Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート](../cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
