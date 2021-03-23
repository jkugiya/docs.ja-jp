---
title: トリミングのオプション
description: 自己完結型アプリのトリミングを制御する方法について説明します。
author: sbomer
ms.author: svbomer
ms.date: 08/25/2020
ms.openlocfilehash: 93fee991cf218a52ad1d9a2597b1c9b2d442110a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874252"
---
# <a name="trimming-options"></a>トリミングのオプション

[トリミングされた自己完結型の展開](trim-self-contained.md)の動作は、MSBuild の次のプロパティと項目によって影響を受けます。 一部のオプションで示されている `ILLink` は、トリミングが実装されている、基になるツールの名前です。 基になるツールの詳細については、[リンカーのドキュメント](https://github.com/mono/linker/tree/master/docs)で確認できます。

## <a name="enable-trimming"></a>トリミングを有効にする

- `<PublishTrimmed>true</PublishTrimmed>`

   トリミングは、SDK で定義されている既定の設定を使用して、発行の間に有効にします。

`Microsoft.NET.Sdk` を使用しているときは、これにより netcoreapp ランタイム パックからのフレームワーク アセンブリのアセンブリ レベルのトリミングが実行されます。 アプリケーションのコードと非フレームワーク ライブラリはトリミングされません。 他の SDK では、異なる既定値が定義されている場合があります。

## <a name="trimming-granularity"></a>トリミングの最小単位

次の最小単位の設定により、使用されていない IL をどの程度まで破棄するかが制御されます。 これは、プロパティとして、または[個々のアセンブリ](#trimmed-assemblies)のメタデータとして、設定することができます。

- `<TrimMode>copyused</TrimMode>`

   アセンブリ レベルのトリミングを有効にします。一部でも使用されているアセンブリは、その全体が保持されます (静的に認識されます)。

- `<TrimMode>link</TrimMode>`

    メンバー レベルのトリミングを有効にします。これにより、使用されていないメンバーが型から削除されます。

`<IsTrimmable>true</IsTrimmable>` メタデータが設定されていても、`TrimMode` が明示的に設定されていないアセンブリでは、グローバルな `TrimMode` が使用されます。 `Microsoft.NET.Sdk` に対する既定の`TrimMode` は `copyused` です。

## <a name="trimmed-assemblies"></a>トリミングされたアセンブリ

トリミングされたアプリが発行されるとき、SDK では、トリミングで処理されるファイルのセットを表す、`ManagedAssemblyToLink` と呼ばれる `ItemGroup` が計算されます。 `ManagedAssemblyToLink` では、アセンブリごとのトリミング動作を制御するメタデータを使用できます。 このメタデータを設定するには、組み込みの `PrepareForILLink` ターゲットの前に実行されるターゲットを作成します。 次の例からは、`MyAssembly` のトリミングを有効にする方法がわかります。

```xml
<Target Name="ConfigureTrimming"
        BeforeTargets="PrepareForILLink">
  <ItemGroup>
    <ManagedAssemblyToLink Condition="'%(Filename)' == 'MyAssembly'">
      <IsTrimmable>true</IsTrimmable>
    </ManagedAssemblyToLink>
  </ItemGroup>
</Target>
```

`ManagedAssemblyToLink` の項目を追加または削除しないでください。このセットは発行時に SDK によって計算され、変更されないものと想定されているためです。 サポートされているメタデータは次のとおりです。

- `<IsTrimmable>true</IsTrimmable>`

  特定のアセンブリをトリミングするかどうかを制御します。

- `<TrimMode>copyused</TrimMode>` または `<TrimMode>link</TrimMode>`

  このアセンブリの[トリミングの最小単位](#trimming-granularity)を制御します。 これは、グローバルな `TrimMode` より優先されます。 アセンブリで `TrimMode` を設定すると、`<IsTrimmable>true</IsTrimmable>` を示します。

## <a name="root-assemblies"></a>ルート アセンブリ

`<IsTrimmable>true</IsTrimmable>` を持たないすべてのアセンブリは、分析のルートと見なされます。これは、それらおよびそれらの静的に認識されたすべての依存関係が保持されることを意味します。 追加のアセンブリは、名前 (`.dll` 拡張子を除く) によって "ルート化" できます。

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="MyAssembly" />
</ItemGroup>
```

## <a name="root-descriptors"></a>ルート記述子

分析に対するルートを指定するもう 1 つの方法は、リンカーの[記述子形式](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format)を使用する XML ファイルを使用することです。 これにより、アセンブリ全体ではなく、特定のメンバーをルートにすることができます。

```xml
<ItemGroup>
  <TrimmerRootDescriptor Include="MyRoots.xml" />
</ItemGroup>
```

たとえば、`MyRoots.xml` の場合、アプリケーションによって動的にアクセスされる特定のメソッドがルートになる可能性があります。

```xml
<linker>
  <assembly fullname="MyAssembly">
    <type fullname="MyAssembly.MyClass">
      <method name="DynamicallyAccessedMethod" />
    </type>
  </assembly>
</linker>
```

## <a name="analysis-warnings"></a>分析の警告

トリミングを行うと、静的に到達できない IL が削除されます。 リフレクションまたは動的な依存関係を作成するその他のパターンを使用するアプリは、トリミングによって壊れることがあります。 そのようなパターンについて警告するには、次のようにします。

- `<SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>`

    トリミング分析の警告を有効にします。

これには、独自のコード、ライブラリ コード、フレームワーク コードを含む、アプリ全体に関する警告が含まれます。

## <a name="warning-versions"></a>警告のバージョン

トリミング分析は、SDK 全体の分析警告のバージョンを制御する [`AnalysisLevel`](../project-sdk/msbuild-props.md#analysislevel) プロパティに従います。 トリミング分析の警告のバージョンを個別に制御するプロパティもあります (コンパイラの `WarningLevel` に似ています)。

- `<ILLinkWarningLevel>5</ILLinkWarningLevel>`

    特定のレベル以下の警告のみを出力します。 これを `9999` にすると、警告のすべてのバージョンが含まれます。

## <a name="suppressing-warnings"></a>警告の抑制

`NoWarn`、`WarningsAsErrors`、`WarningsNotAsErrors`、`TreatWarningsAsErrors` など、ツールチェーンによって適用される通常の MSBuild プロパティを使用して、個々の[警告コード](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes)を抑制できます。 ILLink のエラーとしての警告の動作を個別に制御する追加のオプションがあります。

- `<ILLinkTreatWarningsAsErrors>false</ILLinkTreatWarningsAsErrors>`

    ILLink の警告をエラーとして扱いません。 これは、コンパイラの警告をグローバルにエラーとして扱う場合に、トリミング分析の警告がエラーにならないようにするのに役立ちます。

## <a name="removing-symbols"></a>シンボルの削除

通常、シンボルは、トリミングされたアセンブリと一致するようにトリミングされます。 すべてのシンボルを削除することもできます。

- `<TrimmerRemoveSymbols>true</TrimmerRemoveSymbols>`

    埋め込み PDB や別の PDB ファイルなど、トリミングされたアプリケーションからシンボルを削除します。 これは、アプリケーションのコードと、シンボルに付属するすべての依存関係の両方に適用されます。

また、SDK では、`DebuggerSupport` プロパティを使用してデバッガーのサポートを無効にすることもできます。 デバッガーのサポートを無効にすると、トリミングによって自動的にシンボルが削除されます (`TrimmerRemoveSymbols` は既定で true に設定されます)。

## <a name="trimming-framework-library-features"></a>フレームワーク ライブラリ機能のトリミング

フレームワーク ライブラリのいくつかの機能領域には、リンカー ディレクティブが付属しています。これにより、無効な機能のコードを削除できます。

- `<DebuggerSupport>false</DebuggerSupport>`

    デバッグ エクスペリエンスを向上させるコードを削除します。 これにより、[シンボルも削除されます](#removing-symbols)。

- `<EnableUnsafeBinaryFormatterSerialization>false</EnableUnsafeBinaryFormatterSerialization>`

    BinaryFormatter のシリアル化サポートを削除します。 詳細については、[古い形式の BinaryFormatter シリアル化メソッド](../compatibility/core-libraries/5.0/binaryformatter-serialization-obsolete.md)に関する記事を参照してください。

- `<EnableUnsafeUTF7Encoding>false</EnableUnsafeUTF7Encoding>`

    安全でない UTF-7 エンコード コードを削除します。 詳細については、「[UTF-7 コード パスが古い形式に](../compatibility/core-libraries/5.0/utf-7-code-paths-obsolete.md)」を参照してください。

- `<EventSourceSupport>false</EventSourceSupport>`

    EventSource に関連するコードまたはロジックを削除します。

- `<HttpActivityPropagationSupport>false</HttpActivityPropagationSupport>`

    System.Net.Http の診断サポートに関連するコードを削除します。

- `<InvariantGlobalization>true</InvariantGlobalization>`

    グローバリゼーション固有のコードとデータを削除します。 詳細については、「[インバリアント モード](../run-time-config/globalization.md#invariant-mode)」を参照してください。

- `<UseSystemResourceKeys>true</UseSystemResourceKeys>`

    `System.*` アセンブリの例外メッセージを削除します。 `System.*` アセンブリから例外がスローされると、メッセージは完全なメッセージではなく、簡略化されたリソース ID になります。

 これらのプロパティを使用すると、関連するコードがトリミングされ、[runtimeconfig](../run-time-config/index.md) ファイルを介して機能も無効になります。 対応する runtimeconfig オプションなど、これらのプロパティの詳細については、[機能スイッチ](https://github.com/dotnet/runtime/blob/main/docs/workflow/trimming/feature-switches.md)に関するページを参照してください。 一部の SDK には、これらのプロパティに既定値が設定されている場合があります。
