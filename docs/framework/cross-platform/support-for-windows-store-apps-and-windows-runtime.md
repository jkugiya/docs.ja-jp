---
description: '詳細情報: Microsoft Store アプリおよび Windows ランタイムのための .NET Framework サポート'
title: Microsoft Store アプリおよび Windows ランタイムのための .NET Framework サポート
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Store apps, .NET Framework support for
- Windows Runtime, .NET Framework support for
- .NET for Windows Store apps
- .NET Framework, and Windows Store apps
- .NET Framework, and Windows Runtime
ms.assetid: 6fa7d044-ae12-4c54-b8ee-50915607a565
ms.openlocfilehash: 851deb30420eb19c4fe2037bebe2cf8f84743c49
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "102402290"
---
# <a name="net-framework-support-for-microsoft-store-apps-and-windows-runtime"></a>Microsoft Store アプリおよび Windows ランタイムのための .NET Framework サポート

.NET Framework 4.5 では、Windows ランタイムを使用した多数のソフトウェア開発シナリオがサポートされています。 これらのシナリオは次の 3 つのカテゴリに分類されます。

- [C# または Visual Basic を使った Windows Store アプリのためのロードマップ](/previous-versions/windows/apps/br229583(v=win.10))に関する記事、「[操作方法 (XAML)](/previous-versions/windows/apps/br229566(v=win.10))」、および「[Windows Store アプリ用 .NET の概要](/previous-versions/windows/apps/br230302(v=vs.140))」で説明されているような、XAML コントロールを使用した Windows 8.x Store アプリの開発。

- .NET Framework で作成する Windows 8.x Store アプリで使用するクラス ライブラリの開発。

- .WinMD ファイルにパッケージ化され、Windows ランタイムをサポートするすべてのプログラミング言語で使用できる、Windows ランタイム コンポーネントの開発。 たとえば、[C# および Visual Basic での Windows ランタイム コンポーネントの作成](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)に関する記事を参照してください。

この記事では、3 つのカテゴリすべてに対して .NET Framework が提供するサポートの概略と、Windows ランタイム コンポーネント用のシナリオについて説明します。 最初のセクションでは、.NET Framework と Windows ランタイムの関係についての基本情報と、ヘルプ システムや IDE で見られる可能性がある特異な状況について説明します。 [2 番目のセクション](#WindowsRuntimeComponents)では、Windows ランタイム コンポーネント開発のシナリオについて説明します。

## <a name="the-basics"></a>基本操作

.NET Framework では、Windows 8.x Store アプリ用 .NET を提供すること、および Windows ランタイム自体をサポートすることによって、前述の 3 つの開発シナリオがサポートされています。

- [.NET Framework 名前空間と Windows ランタイム名前空間](/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces)によって、.NET Framework クラス ライブラリの合理化されたビューが提供されます。これには Windows 8.x Store アプリと Windows ランタイム コンポーネントの作成に使用できる型とメンバーのみが含まれます。

  - Visual Studio (Visual Studio 2012 以降) を使用して Windows 8.x Store アプリまたは Windows ランタイム コンポーネントを開発する場合、一連の参照アセンブリによって、関連する型とメンバーのみが表示されます。

  - この合理化された API セットは、.NET Framework 内で重複している機能や、Windows ランタイム機能と重複している機能を削除することによって、さらに簡素化されます。 たとえば、これにはジェネリック バージョンのコレクション型のみが含まれ、XML ドキュメント オブジェクト モデルは削除されて代わりに Windows ランタイム XML API セットが使用されます。

  - オペレーティング システムの API をラップするだけの機能も削除されます。Windows ランタイムはマネージド コードから簡単に呼び出すことができるためです。

  Windows 8.x Store アプリ用 .NET の詳細については、「[Windows Store アプリ用 .NET の概要](/previous-versions/windows/apps/br230302(v=vs.140))」を参照してください。 API 選択プロセスについては、.NET ブログのエントリ「[Metro スタイル アプリの .NET](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/)」を参照してください。

- [Windows ランタイム](/uwp/api/)によって、Windows 8.x Store アプリをビルドするためのユーザー インターフェイス要素が提供されます。また、オペレーティング システム機能にアクセスすることもできます。 .NET Framework と同様、Windows ランタイムには、C# や Visual Basic のコンパイラが .NET Framework クラス ライブラリを使用するのと同じ方法で Windows ランタイムを使用できるようにするためのメタデータが含まれています。 .NET Framework では、いくつかの相違点が隠されることによって Windows ランタイムが使いやすくなります。

  - .NET Framework と Windows ランタイム間のプログラミング パターン (イベント ハンドラーを追加および削除するパターンなど) におけるいくつかの相違点が隠されます。 ユーザーは .NET Framework のパターンを使用するとよいだけです。

  - よく使用される型 (たとえばプリミティブ型やコレクション) の違いの一部が非表示になります。 この記事で後述する「[IDE で表示される相違点](#DifferencesVisibleInIDE)」で説明しているように、.NET Framework の型を使用するだけで済みます。

ほとんどの場合、Windows ランタイムの .NET Framework サポートは透過的です。 次のセクションでは、マネージド コードと Windows ランタイムとの明確な相違点についていくつか説明します。

<a name="AboutReferenceDocumentation"></a>

### <a name="the-net-framework-and-the-windows-runtime-reference-documentation"></a>.NET Framework と Windows ランタイムのリファレンス ドキュメント

Windows ランタイムと .NET Framework のドキュメント セットは別々になっています。 型またはメンバーに関するヘルプを表示するために F1 キーを押すと、該当するセットのリファレンス ドキュメントが表示されます。 ただし、[Windows ランタイム リファレンス](/uwp/api/)を参照すると、次のような、一見不可解な例を見つけることがあります。

- <xref:Windows.Foundation.Collections.IIterable%601> インターフェイスなどのトピックには、Visual Basic または C# 用の宣言構文がありません。 代わりに、構文セクションの上に注意 (このケースでは ".NET: このインターフェイスは System.Collections.Generic.IEnumerable\<T> として表示されます。") が表示されます。 これは、.NET Framework と Windows ランタイムによって、同様の機能が異なるインターフェイスで用意されているためです。 さらに、`IIterable` では列挙子を返すのに `First` メソッドではなく <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> メソッドを使用するという、動作の違いもあります。 .NET Framework では、一般的なタスクを実行する別の方法をユーザーが学習する必要はなく、使い慣れた型を使用できるようにマネージド コードを表示することで Windows ランタイムがサポートされます。 IDE では `IIterable` インターフェイスが表示されないため、Windows ランタイムのリファレンス ドキュメントでこれを目にするのは、そのドキュメントを直接参照する場合のみです。

- <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)> のドキュメントでは、パラメーターの型が言語ごとに異なって表示されるという、密接に関連する問題が説明されています。 C# と Visual Basic の場合、パラメーターの型は <xref:System.String?displayProperty=nameWithType> と <xref:System.Uri?displayProperty=nameWithType> です。 これもやはり、.NET Framework で独自の `String` 型と `Uri` 型が使われるためであり、このようなよく使用される型について、.NET Framework ユーザーが処理を実行する別の方法を学習しても意味はありません。 IDE では、これに対応する Windows ランタイムの型が .NET Framework によって隠されます。

- <xref:Windows.UI.Xaml.GridLength> 構造体などのいくつかのケースでは、.NET Framework によって、同じ名前でより多くの機能を備えた型が提供されます。 たとえば、一連のコンストラクターとプロパティのトピックは `GridLength` に関連付けられますが、メンバーがマネージド コードでのみ使用可能であるために、Visual Basic と C# に関してのみ構文ブロックの機能を備えています。 Windows ランタイムでは、構造体にはフィールドがあるだけです。 Windows ランタイムの構造体には、同等の機能を提供するヘルパー クラス <xref:Windows.UI.Xaml.GridLengthHelper> が必要です。 このヘルパー クラスは、マネージド コードを記述している間は IDE に表示されません。

- IDE では、Windows ランタイムの型は <xref:System.Object?displayProperty=nameWithType> から派生するように表示されます。 この型のメンバーは、<xref:System.Object> などの <xref:System.Object.ToString%2A?displayProperty=nameWithType> から継承されるように表示されます。 これらのメンバーは、型が実際に <xref:System.Object> から継承されたように動作し、Windows ランタイムの型は <xref:System.Object> にキャスト可能です。 この機能は、.NET Framework が Windows ランタイム用に用意しているサポートの一部です。 ただし、Windows ランタイムのリファレンス ドキュメントで型を表示しても、このようなメンバーは表示されません。 これらの見かけ上の継承されたメンバーに関するドキュメントは、<xref:System.Object?displayProperty=nameWithType> のリファレンス ドキュメントに含まれています。

<a name="DifferencesVisibleInIDE"></a>

### <a name="differences-that-are-visible-in-the-ide"></a>IDE で表示される相違点

より高度なプログラミング シナリオ (例: C# で記述された Windows ランタイム コンポーネントを使い、JavaScript を使用して Windows 用にビルドされた Windows 8.x Store アプリのアプリケーション ロジックを提供する) では、ドキュメントと同様 IDE でもこのような相違点が表示されます。 コンポーネントから JavaScript に `IDictionary<int, string>` が返され、それを JavaScript デバッガーで調べた場合、JavaScript によって Windows ランタイムの型が使用されるため、`IMap<int, string>` のメソッドが表示されます。 よく使用されるコレクション型のうち、この 2 言語で表示が異なる型の一部を次の表に示します。

|Windows ランタイム型|対応する .NET Framework の型|
|--------------------------------------------------------------|---------------------------------------|
|`IIterable<T>`|`IEnumerable<T>`|
|`IIterator<T>`|`IEnumerator<T>`|
|`IVector<T>`|`IList<T>`|
|`IVectorView<T>`|`IReadOnlyList<T>`|
|`IMap<K, V>`|`IDictionary<TKey, TValue>`|
|`IMapView<K, V>`|`IReadOnlyDictionary<TKey, TValue>`|
|`IBindableIterable`|`IEnumerable`|
|`IBindableVector`|`IList`|
|`Windows.UI.Xaml.Data.INotifyPropertyChanged`|`System.ComponentModel.INotifyPropertyChanged`|
|`Windows.UI.Xaml.Data.PropertyChangedEventHandler`|`System.ComponentModel.PropertyChangedEventHandler`|
|`Windows.UI.Xaml.Data.PropertyChangedEventArgs`|`System.ComponentModel.PropertyChangedEventArgs`|

Windows ランタイムでは、`IMap<K, V>` と `IMapView<K, V>` は `IKeyValuePair` を使用して反復処理されます。 これらをマネージド コードに渡すと、`IDictionary<TKey, TValue>` および `IReadOnlyDictionary<TKey, TValue>` として表示されるため、これを列挙するには必然的に `System.Collections.Generic.KeyValuePair<TKey, TValue>` を使用します。

インターフェイスがマネージド コード内に表示される方法によって、これらのインターフェイスを実装する型の表示方法が決まります。 たとえば、`PropertySet` クラスは `IMap<K, V>` を実装しますが、これはマネージド コードでは `IDictionary<TKey, TValue>` として表示されます。 `PropertySet` では、`IMap<K, V>` ではなく `IDictionary<TKey, TValue>` が実装されたように見えるため、マネージド コードでは .NET Framework ディクショナリの `Add` メソッドのように動作する `Add` メソッドがあるように表示されます。 `Insert` メソッドがないように見えます。

.NET Framework を使用して Windows ランタイム コンポーネントを作成する方法の詳細について、および JavaScript でそのようなコンポーネントを使用する方法のチュートリアルについては、[C# および Visual Basic での Windows ランタイム コンポーネントの作成](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)に関する記事を参照してください。

### <a name="primitive-types"></a>プリミティブ型

マネージド コードで Windows ランタイムのナチュラルな使用を有効にすると、Windows ランタイムのプリミティブ型ではなく .NET Framework のプリミティブ型がコードに表示されます。 .NET Framework では、`Int32` 構造体などのプリミティブ型には、`Int32.TryParse` メソッドなどの便利なプロパティとメソッドが多くあります。 一方、Windows ランタイムのプリミティブ型と構造体にはフィールドしかありません。 マネージド コードでプリミティブを使用すると、.NET Framework の型のように表示され、通常どおりに .NET Framework 型のプロパティとメソッドを使用できます。 要約すると、次のようになります。

- Windows ランタイムのプリミティブ `Int32`、`Int64`、`Single`、`Double`、`Boolean`、`String` (Unicode 文字の変更できないコレクション)、`Enum`、`UInt32`、`UInt64`、および `Guid` では、`System` 名前空間内の同じ名前の型を使用します。

- `UInt8` では `System.Byte` を使用します。

- `Char16` では `System.Char` を使用します。

- `IInspectable` インターフェイスでは、`System.Object` を使用します。

- `HRESULT` では、`System.Int32` のメンバーを 1 つ含む構造体を使用します。

インターフェイス型の場合と同様、この表示の証拠が表示されるのは、.NET Framework プロジェクトが、JavaScript を使用してビルドされた Windows 8.x Store アプリで使用される Windows ランタイム コンポーネントである場合に限られます。

.NET Framework に相当するものとしてマネージド コードに表示される、よく使用されるその他の基本的な Windows ランタイムの型としては、マネージド コードで <xref:System.DateTimeOffset?displayProperty=nameWithType> 構造体として表示される `Windows.Foundation.DateTime` 構造体や、<xref:System.TimeSpan?displayProperty=nameWithType> 構造体として表示される `Windows.Foundation.TimeSpan` 構造体があります。

### <a name="other-differences"></a>その他の相違点

いくつかのケースでは、Windows ランタイムの型ではなく .NET Framework の型がコードに表示されるため、ユーザー側のアクションが必要になる場合があります。 たとえば、<xref:Windows.Foundation.Uri?displayProperty=nameWithType> クラスは、.NET Framework コードで <xref:System.Uri?displayProperty=nameWithType> として表示されます。 <xref:System.Uri?displayProperty=nameWithType> では相対 URI を使用できますが、<xref:Windows.Foundation.Uri?displayProperty=nameWithType> では絶対 URI が必須です。 したがって、Windows ランタイム メソッドに URI を渡すときには、絶対 URI にする必要があります。 「[Windows ランタイムへの URI の引き渡し](passing-a-uri-to-the-windows-runtime.md)」をご覧ください。

<a name="WindowsRuntimeComponents"></a>

## <a name="scenarios-for-developing-windows-runtime-components"></a>Windows ランタイム コンポーネントの開発シナリオ

Windows ランタイムのマネージド コンポーネントでサポートされるシナリオは、次の原則に依存します。

- .NET Framework を使用してビルドされる Windows ランタイム コンポーネントとその他の Windows ランタイム ライブラリの間に、明確な違いはありません。 たとえば、マネージド コードを使用して Windows ランタイムのネイティブ コンポーネントを再実装する場合、この 2 つのコンポーネントは外部から見て区別が付きません。 コンポーネントがマネージド コードで記述されているという事実は、そのコード自体がマネージド コードであったとしても、そのコンポーネントを使用するコードには表示されません。 ただし内部的には、そのコンポーネントは真のマネージド コードであり、共通言語ランタイム (CLR) 上で実行されます。

- コンポーネントには、アプリケーション ロジック、Windows 8.x Store UI コントロール、またはその両方を実装する型を含めることができます。

  > [!NOTE]
  > アプリケーション ロジックから UI 要素を分離することをお勧めします。 また、JavaScript と HTML を使用して Windows 用にビルドされた Windows 8.x Store アプリでは、Windows 8.x Store UI コントロールを使用できません。

- コンポーネントは、Windows 8.x Store アプリ用 Visual Studio ソリューション内のプロジェクトの場合もあれば、複数のソリューションに追加できる再利用可能なコンポーネントの場合もあります。

  > [!NOTE]
  > コンポーネントが C# または Visual Basic でのみ使用される場合は、それを Windows ランタイム コンポーネントにする理由はありません。 代わりにそれを通常の .NET Framework クラス ライブラリにすると、そのパブリック API サーフェイスを Windows ランタイムの型に制限する必要はありません。

- 異なるバージョンで追加された型 (および型のメンバー) を識別するために Windows ランタイムの <xref:Windows.Foundation.Metadata.VersionAttribute> 属性を使用することにより、再利用可能なコンポーネントの各バージョンをリリースできます。

- コンポーネントの型は Windows ランタイムの型から派生できます。 コントロールは、<xref:Windows.UI.Xaml.Controls.Primitives> 名前空間内のプリミティブ コントロール型から派生することも、より完成度の高いコントロール (<xref:Windows.UI.Xaml.Controls.Button> など) から派生することもできます。

  > [!IMPORTANT]
  > Windows 8 および .NET Framework 4.5 以降では、マネージド Windows ランタイム コンポーネント内のすべてのパブリック型がシールドされている必要があります。 別の Windows ランタイム コンポーネント内の型を、それらから派生させることはできません。 コンポーネントでポリモーフィックな動作を提供するには、インターフェイスを作成し、そのインターフェイスをポリモーフィックな型に実装します。

- コンポーネント内のパブリック型で指定されるすべてのパラメーターと戻り値の型は、Windows ランタイムの型 (コンポーネントで定義する Windows ランタイムの型を含む) である必要があります。

次のセクションでは、一般的なシナリオの例を示します。

### <a name="application-logic-for-a-windows-8x-store-app-with-javascript"></a>JavaScript を使用した Windows 8.x Store アプリ用のアプリケーション ロジック

JavaScript を使用して Windows 用の Windows 8.x Store アプリを開発する場合、アプリケーション ロジックの一部がマネージド コードでより適切に機能したり、開発が容易であったりすることがあります。 JavaScript では .NET Framework クラス ライブラリを直接使用できませんが、クラス ライブラリを .WinMD ファイルにすることができます。 このシナリオでは、Windows ランタイム コンポーネントはアプリに不可欠な部分であるため、バージョン属性を提供する意味がありません。

### <a name="reusable-windows-8x-store-ui-controls"></a>再利用可能な Windows 8.x Store UI コントロール

関連する UI コントロールのセットを再利用可能な Windows ランタイム コンポーネントにパッケージ化できます。 コンポーネントは、単独で商品化することも、作成するアプリの要素として使用することもできます。 このシナリオでは、Windows ランタイム の <xref:Windows.Foundation.Metadata.VersionAttribute> 属性を使用して互換性を高めることに意味があります。

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>既存の .NET Framework アプリからの再利用可能なアプリケーション ロジック

既存のデスクトップ アプリからマネージド コードをスタンドアロンの Windows ランタイム コンポーネントとしてパッケージ化できます。 これによって、C# または Visual Basic を使用してビルドされる Windows 8.x Store アプリに加えて、C++ または JavaScript を使用してビルドされる Windows 8.x Store アプリでも、コンポーネントを使用できるようになります。 コードに再利用シナリオが複数ある場合、バージョン管理はオプションです。

## <a name="related-topics"></a>関連トピック

|Title|説明|
|-----------|-----------------|
|[Windows ストア アプリ用 .NET の概要](/previous-versions/windows/apps/br230302(v=vs.140))|Windows 8.x Store アプリと Windows ランタイム コンポーネントの作成に使用できる .NET Framework の型およびメンバーについて説明します (Windows デベロッパー センター内)。|
|[C# または Visual Basic を使った Windows ストア アプリのためのロードマップ](/previous-versions/windows/apps/br229583(v=win.10))|C# または Visual Basic を使用して Windows 8.x Store アプリの開発を開始するときに役立つ主要リソース (各種クイック スタート トピック、ガイドライン、ベスト プラクティスなど) が用意されています (Windows デベロッパー センター内)。|
|[操作方法 (XAML)](/previous-versions/windows/apps/br229566(v=win.10))|C# または Visual Basic を使用して Windows 8.x Store アプリの開発を開始するときに役立つ主要リソース (各種クイック スタート トピック、ガイドライン、ベスト プラクティスなど) が用意されています (Windows デベロッパー センター内)。|
|[C# および Visual Basic での Windows ランタイム コンポーネントの作成](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|.NET Framework を使用して Windows ランタイム コンポーネントを作成する方法、JavaScript を使用して Windows 用にビルドされた Windows 8.x Store アプリの一部としてそのコンポーネントを使用する方法、Visual Studio との組み合わせをデバッグする方法について説明します (Windows デベロッパー センター内)。|
|[Windows ランタイム リファレンス](/uwp/api/)|Windows ランタイムのリファレンス ドキュメント (Windows デベロッパー センター内)。|
|[Windows ランタイムへの URI の引き渡し](passing-a-uri-to-the-windows-runtime.md)|マネージド コードから Windows ランタイムに URI を渡すときに発生する可能性がある問題と、その回避方法について説明します。|
