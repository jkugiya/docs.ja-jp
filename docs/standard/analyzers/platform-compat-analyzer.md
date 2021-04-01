---
title: プラットフォーム互換性アナライザー
description: クロスプラットフォームのアプリとライブラリにおいてプラットフォームの互換性に関する問題を検出するのに役立つ Roslyn アナライザーです。
author: buyaa-n
ms.date: 09/17/2020
ms.openlocfilehash: ce916a771f3fd885b37690183de74919aa01d6fb
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874044"
---
# <a name="platform-compatibility-analyzer"></a>プラットフォーム互換性アナライザー

"One .NET" という標語をお聞きになったことがあるかもしれません。あらゆる種類のアプリケーションを構築するための、1 つの統一プラットフォームという意味です。 .NET 5.0 SDK には、ASP.NET Core、Entity Framework Core、WinForms、WPF、Xamarin、ML.NET が含まれています。また、時間の経過と共にさらなるプラットフォームのサポートが追加されます。 .NET 5.0 では、.NET のさまざまなフレーバーを判断する必要がないエクスペリエンスの提供を目指していますが、基になるオペレーティング システム (OS) を完全に抽象化しようとしているわけではありません。 ユーザーは引き続き、P/Invoke、WinRT、または iOS および Android 用の Xamarin バインドなど、プラットフォーム固有の API を呼び出すことができます。

ただし、コンポーネント上でプラットフォーム固有の API を使用すると、一部のプラットフォームでそのコードが動作しなくなります。 デザイン時にこれを検出して、開発者が誤ってプラットフォーム固有の API を使用したときに診断を取得できるようにするための方法が必要でした。 この目標を達成するために、.NET 5.0 では[プラットフォーム互換性アナライザー](../../fundamentals/code-analysis/quality-rules/ca1416.md)と、開発者がプラットフォーム固有の API を特定して適切な場所で使用できるようにするための、補完的な API が導入されます。

新しい API には以下が含まれます。

- API にプラットフォーム固有という注釈を付けるための <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> と、API に特定の OS でサポートされていないという注釈を付けるための <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute>。 これらの属性には必要に応じてバージョン番号を含めることができます。コア .NET ライブラリに含まれている一部のプラットフォーム固有の API には既に適用されています。
- プラットフォーム固有の API を安全に呼び出すための、<xref:System.OperatingSystem?displayProperty=nameWithType> クラスの `Is<Platform>()` および `Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)` 静的メソッド。 たとえば、<xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType> を使用して Windows 固有の API 呼び出しを保護したり、<xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType>() を使用してバージョン付きの Windows 固有の API 呼び出しを保護したりできます。 これらのメソッドを使用してプラットフォーム固有の API 参照を保護する方法については、以下の[例](#guard-platform-specific-apis-with-guard-methods)をご覧ください。

> [!TIP]
> プラットフォーム互換性アナライザーによって、[.NET API アナライザー](../../standard/analyzers/api-analyzer.md)の[クロスプラットフォームの問題の検出](../../standard/analyzers/api-analyzer.md#discover-cross-platform-issues)機能がアップグレードされ、置き換えられます。

## <a name="prerequisites"></a>[前提条件]

プラットフォーム互換性アナライザーは、Roslyn コード品質アナライザーの 1 つです。 .NET 5.0 以降、これらのアナライザーは [.NET SDK に含まれる](../../fundamentals/code-analysis/overview.md)ようになりました。 プラットフォーム互換性アナライザーは、`net5.0` 以降のバージョンをターゲットとするプロジェクトに対してのみ既定で有効になります。 ただし、他のフレームワークをターゲットとするプロジェクトに対しても[有効にする](../../fundamentals/code-analysis/quality-rules/ca1416.md#configure-code-to-analyze)ことができます。

## <a name="how-the-analyzer-determines-platform-dependency"></a>アナライザーによってプラットフォームの依存関係が判断されるしくみ

- **属性なしの API** は **全 OS プラットフォーム** で動作すると見なされます。
- `[SupportedOSPlatform("platform")]` でマークされた API は、指定された OS `platform` にのみ移植可能であると見なされます。
  - この属性を複数回適用して、**複数プラットフォームのサポート** (`[SupportedOSPlatform("windows"), SupportedOSPlatform("Android6.0")]`) を示すことができます。
  - 適切な **プラットフォーム コンテキスト** を使用せずにプラットフォーム固有の API が参照されている場合は、アナライザーによって **警告** が生成されます。
    - プロジェクトがサポート対象プラットフォームをターゲットとしていない場合 (たとえば、Windows 固有の API 呼び出しでプロジェクトが `<TargetFramework>net5.0-ios14.0</TargetFramework>` をターゲットとしている場合)、**警告が表示されます**。
    - プロジェクトに複数のターゲットがある場合 (`<TargetFrameworks>net5.0;netstandard2.0</TargetFrameworks>` など)、**警告が表示されます**。
    - プラットフォーム固有の API が、**指定されたプラットフォーム** のいずれかをターゲットとしているプロジェクト内で参照される場合、**警告は表示されません** (たとえば、Windows 固有の API 呼び出しでプロジェクトが `<TargetFramework>net5.0-windows</TargetFramework>` をターゲットとしている場合)。
    - プラットフォーム固有の API 呼び出しが、対応するプラットフォーム チェック メソッド (例: `if(OperatingSystem.IsWindows())`) によって保護されている場合、**警告は表示されません**。
    - プラットフォーム固有の API が、同じプラットフォーム固有のコンテキストから参照されている場合 (**呼び出しサイトにも属性 `[SupportedOSPlatform("platform")` が設定されている場合**)、**警告は表示されません**。
- `[UnsupportedOSPlatform("platform")]` でマークされた API は、指定した OS `platform` でのみサポートされず、他のすべてのプラットフォームでサポートされると見なされます。
  - この属性は、異なるプラットフォームで複数回適用できます (例: `[UnsupportedOSPlatform("iOS"), UnsupportedOSPlatform("Android6.0")]`)。
  - アナライザーによって **警告** が生成されるのは、`platform` が呼び出しサイトに対して有効である場合のみです。
    - サポート対象外の属性が設定されているプラットフォームをプロジェクトがターゲットとしている場合、**警告が表示されます** (たとえば、API に属性 `[UnsupportedOSPlatform("windows")]` が設定されていて、呼び出しサイトが `<TargetFramework>net5.0-windows</TargetFramework>` をターゲットとしている場合)。
    - プロジェクトに複数のターゲットがあり、`platform` が既定の [MSBuild `<SupportedPlatform>`](https://github.com/dotnet/sdk/blob/main/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props) 項目グループに含まれている場合、または `platform` が手動で `MSBuild` \<SupportedPlatform> 項目グループ内に含まれている場合、**警告が表示されます**。

      ```XML
      <ItemGroup>
          <SupportedPlatform Include="platform" />
      </ItemGroup>
      ```

    - サポート対象外のプラットフォームをターゲットとしていないアプリをビルドする場合、またはビルドするアプリに複数のターゲットがあり、platform が既定の [MSBuild `<SupportedPlatform>`](https://github.com/dotnet/sdk/blob/main/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props) 項目グループに含まれていない場合、**警告は表示されません**。
- どちらの属性も、プラットフォーム名の一部としてバージョン番号を含めても、含めなくてもインスタンス化できます。
  - バージョン番号は `major.minor[.build[.revision]]` の形式です。`major.minor` は必須であり、`build` と `revision` の部分は省略可能です。 たとえば、"Windows7.0" は Windows バージョン 7.0 を示しますが、"Windows" は Windows 0.0 として解釈されます。

詳細については、[属性の動作方法とそれらによって発生する診断の例](#examples-of-how-the-attributes-work-and-what-diagnostics-they-produce)に関するセクションをご覧ください。

### <a name="advanced-scenarios-for-combining-attributes"></a>属性を組み合わせる高度なシナリオ

- `[SupportedOSPlatform]` 属性と `[UnsupportedOSPlatform]` 属性の組み合わせが存在する場合、すべての属性は OS プラットフォーム識別子によってグループ化されます。
  - **サポート対象のみのリスト**。 各 OS プラットフォームの最小バージョンが `[SupportedOSPlatform]` 属性である場合、その API はリストに含まれているプラットフォームでのみサポートされ、他のすべてのプラットフォームではサポートされないと見なされます。 各プラットフォームの省略可能な `[UnsupportedOSPlatform]` 属性には、サポートされる最小バージョンより上位のバージョンのみを設定できます。これは、指定されたバージョン以降で API が削除されることを示します。

    ```csharp
    // The API only supported on Windows 8.0 and later, not supported for all other.
    // The API is removed/unsupported from version 10.0.19041.0.
    [SupportedOSPlatform("windows8.0")]
    [UnsupportedOSPlatform("windows10.0.19041.0")]
    public void ApiSupportedFromWindows80SupportFromCertainVersion();
    ```

  - **サポート対象外のみのリスト**。 各 OS プラットフォームの最小バージョンが `[UnsupportedOSPlatform]` 属性である場合、その API はリストに含まれているプラットフォームでのみサポートされず、他のすべてのプラットフォームではサポートされると見なされます。 リストには、同じプラットフォームのより上位のバージョンの `[SupportedOSPlatform]` 属性を含めることができます。これは、そのバージョン以降で API がサポートされることを示します。

    ```csharp
    // The API was unsupported on Windows until version 10.0.19041.0.
    // The API is considered supported everywhere else without constraints.
    [UnsupportedOSPlatform("windows")]
    [SupportedOSPlatform("windows10.0.19041.0")]
    public void ApiSupportedFromWindows8UnsupportFromWindows10();
    ```

  - **不整合なリスト**。 あるプラットフォームの最小バージョンが `[SupportedOSPlatform]` であり、それが別のプラットフォームでは `[UnsupportedOSPlatform]` であった場合は、不整合と見なされます。これはアナライザーでサポートされません。
  - `[SupportedOSPlatform]` 属性と `[UnsupportedOSPlatform]` 属性の最小バージョンが等しい場合、アナライザーではそのプラットフォームが **サポート対象のみのリスト** に含まれていると見なされます。
- プラットフォーム属性は、型、メンバー (メソッド、フィールド、プロパティ、イベント)、およびプラットフォーム名やバージョンが異なるアセンブリに適用できます。
  - 最上位レベルの `target` に適用される属性は、そのすべてのメンバーと型に影響します。
  - 子レベルの属性が適用されるのは、それが "子注釈によってプラットフォームのサポートを絞り込むことはできるが、拡大することはできない" という規則に準拠している場合のみです。
    - 親が **サポート対象のみ** のリストを持っている場合、子のメンバー属性で新しいプラットフォームのサポートを追加することはできません。親のサポートが拡大されるためです。 新しいプラットフォームのサポートは、親自体にのみ追加できます。 ただし、子が同じプラットフォームのそれ以降のバージョンに対して `Supported` 属性を持つことはできます。それによりサポートが絞り込まれるためです。 また、子が同じプラットフォームで `Unsupported` 属性を持つこともできます。親のサポートも絞り込まれるためです。
    - 親が **サポート対象外のみ** のリストを持っている場合、親のサポートを絞り込むために、子のメンバー属性で新しいプラットフォームのサポートを追加することができます。 しかし、親と同じプラットフォームの `Supported` 属性を持つことはできません。親のサポートが拡張されるからです。 同じプラットフォームのサポートは、元の `Unsupported` 属性が適用された親に対してのみ追加できます。
  - 同じ `platform` 名の API に対して `[SupportedOSPlatform("platformVersion")]` が 2 回以上適用されている場合、最小バージョンのものだけがアナライザーによって考慮されます。
  - 同じ `platform` 名の API に対して `[UnsupportedOSPlatform("platformVersion")]` が 3 回以上適用されている場合、最も古いバージョンの 2 つだけがアナライザーによって考慮されます。

  > [!NOTE]
  > 最初はサポートされていたが後のバージョンではサポートされていない (削除された) API は、さらに後のバージョンで再びサポートされることはないと想定されます。

### <a name="examples-of-how-the-attributes-work-and-what-diagnostics-they-produce"></a>属性の動作方法とそれらによって生成される診断の例

  ```csharp
  // An API supported only on Windows.
  [SupportedOSPlatform("Windows")]
  public void WindowsOnlyApi() { }

  // an API supported on Windows and Linux.
  [SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("Linux")]
  public void SupportedOnWindowsAndLinuxOnly() { }

  // an API only supported on Windows 8.0 and later, not supported for all other.
  // an API is removed/unsupported from version 10.0.19041.0.
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void ApiSupportedFromWindows8UnsupportFromWindows10() { }

  // an Assembly supported on Windows, the API added from version 10.0.19041.0.
  [assembly: SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("windows10.0.19041.0")]
  public void AssemblySupportedOnWindowsApiSupportedFromWindows10() { }

  public void Caller()
  {
      WindowsOnlyApi(); // warns: 'WindowsOnlyApi' is supported on 'windows'

      // warns: 'SupportedOnWindowsAndLinuxOnly' is supported on 'Windows'
      // warns: 'SupportedOnWindowsAndLinuxOnly' is supported on 'Linux'
      SupportedOnWindowsAndLinuxOnly();

      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 8.0 and later
      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is unsupported on 'windows' 10.0.19041.0 and later
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 10.0.19041.0 and later
      // for same platform analyzer only warn for the latest version.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  // an API not supported on android but supported on all other.
  [UnsupportedOSPlatform("android")]
  public void DoesNotWorkOnAndroid() { }

  // an API was unsupported on Windows until version 8.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  public void StartedWindowsSupportFromVersion8() { }

  // an API was unsupported on Windows until version8.0.
  // Then the API is removed (unsupported) from version 10.0.19041.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void StartedWindowsSupportFrom8UnsupportedFrom10() { }

  public void Caller2()
  {
      DoesNotWorkOnAndroid(); // warns 'DoesNotWorkOnAndroid' is unsupported on 'android'

      // warns:'StartedWindowsSupportFromVersion8' is unsupported on 'windows'
      // warns:'StartedWindowsSupportFromVersion8' is supported on 'windows' 8.0 and later
      StartedWindowsSupportFromVersion8();

      // warns:'StartedWindowsSupportFrom8UnsupportedFrom10' is unsupported on 'windows'
      // warns:'StartedWindowsSupportFrom8UnsupportedFrom10' is supported on 'windows' 8.0 and later
      // even there were 3 diagnostics found analyzer warn only for the first 2.
      StartedWindowsSupportFrom8UnsupportedFrom10();
  }
  ```

## <a name="handle-reported-warnings"></a>報告された警告の処理

これらの診断に対処するための推奨される方法は、適切なプラットフォーム上で実行する場合にのみプラットフォーム固有の API を呼び出すようにすることです。 警告に対処するために使用できるオプションを以下に示します。ご自身の状況に最も適したものを選択してください。

- **呼び出しを保護する**。 これは、実行時にコードを条件付きで呼び出すことによって実現できます。 プラットフォーム チェック メソッド (`OperatingSystem.Is<Platform>()`、`OperatingSystem.Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)` など) のいずれかを使用して、目的の `Platform` で実行しているかどうかを確認します。

- **呼び出しサイトをプラットフォーム固有としてマークする**。 独自の API をプラットフォーム固有としてマークすることもできます。これにより、実質的には要求を呼び出し元に転送するだけで済みます。 含まれているメソッドや型、またはアセンブリ全体を、参照されているプラットフォーム依存の呼び出しと同じ属性でマークします。 [例](#mark-call-site-as-platform-specific)。

- **プラットフォーム チェックを使用して呼び出しサイトをアサートする**。 `if` ステートメントを追加して実行時のオーバーヘッドを増やしたくない場合は、<xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> を使用します。 [例](#assert-the-call-site-with-platform-check)。

- **コードを削除する**。 通常は望ましい方法ではありません。Windows ユーザーがコードを使用する場合に忠実性が失われることを意味するためです。 クロスプラットフォームの代替手段が存在する場合は、プラットフォーム固有の API よりもそちらを使用した方がよい可能性があります。

- **警告を抑制する**。 [EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) エントリまたは `#pragma warning disable CA1416` を使用して、単に警告を抑制することもできます。 ただし、プラットフォーム固有の API を使用する場合、このオプションは最後の手段にするべきです。

  > [!TIP]
  > `#pragma` プリコンパイラ ディレクティブを使用して警告を無効にすると、ターゲットとする識別子の大文字と小文字が区別されます。 たとえば、`ca1416` は、実際には警告 CA1416 を無効にしません。

### <a name="guard-platform-specific-apis-with-guard-methods"></a>保護メソッドを使用してプラットフォーム固有の API を保護する

保護メソッドのプラットフォーム名は、呼び出し元のプラットフォーム依存 API のプラットフォーム名と一致している必要があります。 呼び出し元 API のプラットフォーム文字列にバージョンが含まれている場合は、次のようになります。

- `[SupportedOSPlatform("platformVersion")]` 属性の場合、保護メソッドのプラットフォームの `version` は、呼び出し元のプラットフォームの `Version` 以上である必要があります。
- `[UnsupportedOSPlatform("platformVersion")]` 属性の場合、保護メソッドのプラットフォームの `version` は、呼び出し元のプラットフォームの `Version` 以下である必要があります。

  ```csharp
  public void CallingSupportedOnlyApis() // Allow list calls
  {
      if (OperatingSystem.IsWindows())
      {
          WindowsOnlyApi(); // will not warn
      }

      if (OperatingSystem.IsLinux())
      {
          SupportedOnWindowsAndLinuxOnly(); // will not warn, within one of the supported context
      }

      // Can use &&, || logical operators to guard combined attributes
      if (OperatingSystem.IsWindowsVersionAtLeast(8) && !OperatingSystem.IsWindowsVersionAtLeast(10.0.19041)))
      {
          ApiSupportedFromWindows8UnsupportFromWindows10();
      }

      if (OperatingSystem.IsWindowsVersionAtLeast(10, 0, 1903))
      {
          AssemblySupportedOnWindowsApiSupportedFromWindows10(); // Only need to check latest supported version
      }
  }

  public void CallingUnsupportedApis()
  {
      if (!OperatingSystem.IsAndroid())
      {
          DoesNotWorkOnAndroid(); // will not warn
      }

      if (!OperatingSystem.IsWindows() || OperatingSystem.IsWindowsVersionAtLeast(8))
      {
          StartedWindowsSupportFromVersion8(); // will not warn
      }

      if (!OperatingSystem.IsWindows() || // supported all other platforms
         (OperatingSystem.IsWindowsVersionAtLeast(8) && !OperatingSystem.IsWindowsVersionAtLeast(10, 0, 1903)))
      {
          StartedWindowsSupportFrom8UnsupportedFrom10(); // will not warn
      }
  }
  ```

- 新しい <xref:System.OperatingSystem> API を使用できない `netstandard` または `netcoreapp` をターゲットとするコードを保護する必要がある場合、<xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform%2A?displayProperty=nameWithType> API が使用可能であり、アナライザーによって考慮されます。 ただし、これは <xref:System.OperatingSystem> に追加された新しい API ほど最適化されていません。 プラットフォームが <xref:System.Runtime.InteropServices.OSPlatform> 構造体でサポートされていない場合は、<xref:System.Runtime.InteropServices.OSPlatform.Create(System.String)?displayProperty=nameWithType> を呼び出して、アナライザーでも考慮される、プラットフォーム名を渡すことができます。

  ```csharp
  public void CallingSupportedOnlyApis()
  {
      if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
      {
          SupportedOnWindowsAndLinuxOnly(); // will not warn
      }

      if (RuntimeInformation.IsOSPlatform(OSPlatform.Create("browser")))
      {
          ApiOnlySupportedOnBrowser(); // call of browser specific API
      }
  }
  ```

### <a name="mark-call-site-as-platform-specific"></a>呼び出しサイトをプラットフォーム固有としてマークする

プラットフォーム名は、呼び出し元のプラットフォームに依存する API と一致している必要があります。 プラットフォーム文字列にバージョンが含まれている場合は、次のようになります。

- `[SupportedOSPlatform("platformVersion")]` 属性の場合、呼び出しサイトのプラットフォームの `version` は、呼び出し元のプラットフォームの `Version` 以上である必要があります
- `[UnsupportedOSPlatform("platformVersion")]` 属性の場合、呼び出しサイトのプラットフォームの `version` は、呼び出し元のプラットフォームの `Version` 以下である必要があります

  ```csharp
  // an API supported only on Windows.
  [SupportedOSPlatform("windows")]
  public void WindowsOnlyApi() { }

  // an API supported on Windows and Linux.
  [SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("Linux")]
  public void SupportedOnWindowsAndLinuxOnly() { }

  // an API only supported on Windows 8.0 and later, not supported for all other.
  // an API is removed/unsupported from version 10.0.19041.0.
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void ApiSupportedFromWindows8UnsupportFromWindows10() { }

  // an Assembly supported on Windows, the API added from version 10.0.19041.0.
  [assembly: SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("windows10.0.19041.0")]
  public void AssemblySupportedOnWindowsApiSupportedFromWindows10() { }

  [SupportedOSPlatform("windows8.0")] // call site attributed Windows 8.0 or above.
  public void Caller()
  {
      WindowsOnlyApi(); // will not warn as call site is for Windows.

      // will not warn as call site is for Windows.
      SupportedOnWindowsAndLinuxOnly();

      // will not warn for the API's [SupportedOSPlatform("windows8.0")] attribute.
      // Warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is unsupported on 'windows' 10.0.19041.0 and later
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 10.0.19041.0 and later
      // as the call site version is lower than calling version.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  [SupportedOSPlatform("windows11.0")] // call site attributed with windows 11.0 or above.
  public void Caller2()
  {
      // Warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is unsupported on 'windows' 10.0.19041.0 and later
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // will not warn as call site version higher than calling API.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")] // call site supports Windows from version 8.0 to 10.0.19041.0.
  public void Caller3()
  {
      // will not warn as caller has exact same attributes.
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // Warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 10.0.19041.0 and later
      // As call site stopped support from that version.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  // an API not supported on Android but supported on all other.
  [UnsupportedOSPlatform("android")]
  public void DoesNotWorkOnAndroid() { }

  // an API was unsupported on Windows until version 8.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  public void StartedWindowsSupportFromVersion8() { }

  // an API was unsupported on Windows until version8.0.
  // Then the API is removed (unsupported) from version 10.0.19041.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void StartedWindowsSupportFrom8UnsupportedFrom10() { }

  [UnsupportedOSPlatform("windows")] // Caller no support Windows for any version.
  public void Caller4()
  {
      DoesNotWorkOnAndroid(); // warns 'DoesNotWorkOnAndroid' is unsupported on 'Android'.

      // will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFromVersion8();

      // same, will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFrom8UnsupportedFrom10();
  }

  [UnsupportedOSPlatform("windows")]
  [UnsupportedOSPlatform("android")] // Caller not support Windows and Android for any version.
  public void Caller4()
  {
      DoesNotWorkOnAndroid(); // will not warn as call site not supports Android.

      // will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFromVersion8();

      // same, will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFrom8UnsupportedFrom10();
  }
  ```

### <a name="assert-the-call-site-with-platform-check"></a>プラットフォーム チェックを使用して呼び出しサイトをアサートする

[プラットフォーム保護の例](#guard-platform-specific-apis-with-guard-methods)で使用されているすべての条件チェックは、<xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> の条件として使用することもできます。

  ```csharp
  // An API supported only on Linux.
  [SupportedOSPlatform("linux")]
  public void LinuxOnlyApi() { }

  public void Caller()
  {
      Debug.Assert(OperatingSystem.IsLinux());

      LinuxOnlyApi(); // will not warn
  }
  ```

## <a name="see-also"></a>関連項目

- [.NET 5 でのターゲット フレームワーク名](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md)
- [プラットフォーム固有の API に注釈を付け、その使用を検出する](https://github.com/dotnet/designs/blob/main/accepted/2020/platform-checks/platform-checks.md)
- [特定のプラットフォームでサポートされていない API に注釈を付ける](https://github.com/dotnet/designs/blob/main/accepted/2020/platform-exclusion/platform-exclusion.md)
- [CA1416 プラットフォーム互換性アナライザー](../../fundamentals/code-analysis/quality-rules/ca1416.md)
- [.NET API アナライザー](../../standard/analyzers/api-analyzer.md)
