---
title: '破壊的変更:CA1416: プラットフォームの互換性'
description: .NET 5 での破壊的変更について学習します。これは、コード分析ルール CA1416 の有効化によって発生します。
ms.date: 09/29/2020
ms.openlocfilehash: 0464e7bb5a494543c0201efa4630e82897b464c0
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257857"
---
# <a name="warning-ca1416-platform-compatibility"></a>警告 CA1416:プラットフォームの互換性

.NET コード アナライザー ルール [CA1416](/visualstudio/code-quality/ca1416) は、.NET 5.0 以降では既定で有効になっています。 オペレーティング システムが検証されていない呼び出しサイトからのプラットフォーム固有の API への呼び出しに対し、ビルドの警告が生成されます。

## <a name="change-description"></a>変更内容

.NET 5 以降、.NET SDK には [.NET ソース コード アナライザー](../../../../fundamentals/code-analysis/overview.md)が含まれています。 これらのルールのいくつかは、[CA1416](/visualstudio/code-quality/ca1416) を含め、既定で有効になっています。 このルールに違反し、警告をエラーとして扱うように構成されているコードがプロジェクトに含まれている場合、この変更によってビルドが破損する可能性があります。 ルール CA1416 では、プラットフォームのコンテキストが検証されていない場所からプラットフォーム固有の API を使用していることが通知されます。

ルール [CA1416](/visualstudio/code-quality/ca1416) のプラットフォーム互換性アナライザーは、.NET 5.0 の他の新機能の一部と連携して動作します。 .NET 5 において導入された <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> と <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> では、API がサポートされて "*いる*"、またはサポートされて "*いない*" プラットフォームを指定できます。 これらの属性が存在しない場合、API はすべてのプラットフォームでサポートされているものと見なされます。 これらの属性は、Core .NET ライブラリ内のプラットフォーム固有の API に適用されています。

プロジェクトで使用されている API が、プロジェクトのターゲット プラットフォームでは使用できないものである場合、ルール [CA1416](/visualstudio/code-quality/ca1416) により、プラットフォームのコンテキストが検証されないプラットフォーム固有のすべての API 呼び出しに、フラグが設定されます。 <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> 属性および <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> 属性で装飾されている API のほとんどでは、サポートされていないオペレーティング システムで呼び出されると、<xref:System.PlatformNotSupportedException> 例外がスローされます。 これらの API はプラットフォーム固有としてマークされるようになったので、ルール [CA1416](/visualstudio/code-quality/ca1416) は、OS のチェックを呼び出しサイトに追加することで、実行時の <xref:System.PlatformNotSupportedException> 例外を回避するのに役立ちます。

## <a name="examples"></a>例

- <xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType> メソッドは Windows でのみサポートされており、`[SupportedOSPlatform("windows")]` で修飾されます。 次のコードでは、プロジェクトの[ターゲット](../../../../standard/frameworks.md)が `net5.0` である場合 (ただし `net5.0-windows` は除きます)、ビルド時に CA1416 警告が生成されます。 警告を回避するために実行できる対応については、「[推奨アクション](#recommended-action)」を参照してください。

  ```csharp
  public void PlayCMajor()
  {
      Console.Beep(261, 1000);
  }
  ```

- <xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType> メソッドは、ブラウザーではサポートされておらず、`[UnsupportedOSPlatform("browser")]` で修飾されます。 次のコードでは、プロジェクトでブラウザー プラットフォームがサポートされている場合、ビルド時に CA1416 警告が生成されます。

  ```csharp
  public void CreateImage()
  {
      Image newImage = Image.FromFile("SampImag.jpg");
  }
  ```

  > [!TIP]
  >
  > - Blazor WebAssembly プロジェクトおよび Razor クラス ライブラリ プロジェクトには、ブラウザー サポートが自動的に含まれます。
  > - プロジェクトのサポート対象プラットフォームとしてブラウザーを手動で追加するには、プロジェクト ファイルに次のエントリを追加します。
  >
  >  ```xml
  >  <ItemGroup>
  >    <SupportedPlatform Include="browser" />
  >  </ItemGroup>
  >  ```

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

コードが適切なプラットフォームで実行されている場合にのみ、プラットフォーム固有の API を呼び出すようにします。 プラットフォーム固有の API を呼び出す前に、<xref:System.OperatingSystem?displayProperty=nameWithType> クラスの `Is<Platform>` メソッドのいずれか (<xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType> など) を使用して、現在のオペレーティング システムを調べることができます。

`if` ステートメントの条件内で、`Is<Platform>` メソッドのいずれかを使用できます。

```csharp
public void PlayCMajor()
{
    if (OperatingSystem.IsWindows())
    {
        Console.Beep(261, 1000);
    }
}
```

または、`if` ステートメントを追加して実行時のオーバーヘッドを増やしたくない場合は、代わりに <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> を呼び出します。

```csharp
public void PlayCMajor()
{
    Debug.Assert(OperatingSystem.IsWindows());
    Console.Beep(261, 1000);
}
```

ライブラリを作成している場合は、API をプラットフォーム固有としてマークできます。 この場合、要件を確認する責任は呼び出し元にあります。 特定のメソッドや型、またはアセンブリ全体をマークできます。

```csharp
[SupportedOSPlatform("windows")]
public void PlayCMajor()
{
    Console.Beep(261, 1000);
}
```

すべての呼び出しサイトを修正したくない場合は、次のいずれかのオプションを選択して警告を抑制できます。

- ルール CA1416 を抑制するには、`#pragma` または [-nowarn](../../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) コンパイラ フラグを使用するか、.editorconfig ファイルで[ルールの重大度を `none` に設定](../../../../fundamentals/code-analysis/configuration-options.md#severity-level)します。

  ```csharp
  public void PlayCMajor()
  {
  #pragma warning disable CA1416
      Console.Beep(261, 1000);
  #pragma warning restore CA1416
  }
  ```

- コード分析を完全に無効にするには、プロジェクト ファイルで `EnableNETAnalyzers` を `false` に設定します。 詳細については、「[EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)」を参照してください。

## <a name="affected-apis"></a>影響を受ける API

Windows プラットフォームの場合:

- <https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md> に記載されているすべての API。
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>

Blazor WebAssembly の場合:

- <https://github.com/dotnet/runtime/issues/41087> に記載されているすべての API。

<!--

### Affected APIs

- ``

### Category

- Code analysis
- Core .NET libraries

-->

## <a name="see-also"></a>関連項目

- [CA1416:プラットフォームの互換性を検証する](/visualstudio/code-quality/ca1416)
- [.NET API アナライザー](../../../../standard/analyzers/api-analyzer.md)
