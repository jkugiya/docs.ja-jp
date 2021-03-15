---
title: .NET Framework から .NET 5 に移植する
description: 移植プロセスを理解し、.NET Framework プロジェクトを .NET 5 (および .NET Core 3.1) に移植する際に役立つツールを確認します。
author: adegeo
ms.date: 03/03/2020
no-loc:
- package.config
- PackageReference
ms.openlocfilehash: 8515689cf4a1be917f12bb8f3315cda89988d773
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605049"
---
# <a name="overview-of-porting-from-net-framework-to-net"></a>.NET Framework から .NET への移植の概要

この記事では、.NET Framework から .NET (旧称 .NET Core) にコードを移植する際に考慮する必要がある事項の概要について説明します。 多くのプロジェクトでは、.NET Framework から .NET に比較的簡単に移植できます。 プロジェクトの複雑さによって、プロジェクト ファイルを最初に移行した後に実行する作業の量が決まります。

.NET にアプリ モデルがあるプロジェクト (ライブラリ、コンソール アプリ、デスクトップ アプリなど) では、通常ほとんど変更することはありません。 ASP.NET から ASP.NET Core への移行など、新しいアプリ モデルを必要とするプロジェクトではさらに作業が必要となります。 古いアプリ モデルの多くのパターンには、変換中に使用できる同等のものがあります。

## <a name="unavailable-technologies"></a>利用できないテクノロジ

.NET Framework には .NET に存在しない、次のようないくつかのテクノロジがあります。

- [アプリケーション ドメイン](net-framework-tech-unavailable.md#application-domains)

  追加のアプリケーション ドメインの作成はサポートされていません。 コードの分離のためには、代替方法として別個のプロセスやコンテナーを使用します。

- [リモート処理](net-framework-tech-unavailable.md#remoting)

  リモート処理は、現在サポートされていないアプリケーション ドメインとの間の通信に使用されます。 プロセスとの間の通信については、リモート処理に代わる方法として、<xref:System.IO.Pipes> クラスまたは <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> クラスなどのプロセス間通信 (IPC) メカニズムを検討してください。

- [コード アクセス セキュリティ (CAS)](net-framework-tech-unavailable.md#code-access-security-cas)

  CAS は .NET Framework でサポートされているサンドボックス化手法でしたが、.NET Framework 4.0 では非推奨とされました。 これはセキュリティ透過性によって置き換えられており、.NET ではサポートされていません。 代わりに、仮想化、コンテナー、ユーザー アカウントなど、オペレーティング システムが提供するセキュリティ境界を使用してください。

- [セキュリティ透過性](net-framework-tech-unavailable.md#security-transparency)

  CAS と同様に、このサンドボックス化手法は .NET Framework アプリケーションでは推奨されなくなり、.NET ではサポートされません。 代わりに、仮想化、コンテナー、ユーザー アカウントなど、オペレーティング システムが提供するセキュリティ境界を使用してください。
  
- <xref:System.EnterpriseServices?displayProperty=fullName>

  <xref:System.EnterpriseServices?displayProperty=fullName> (COM+) は .NET ではサポートされていません。

- Windows Workflow Foundation (WF) と Windows Communication Foundation (WCF)

  WF と WCF は .NET 5 以降 (.NET Core を含む) ではサポートされていません。 代替方法については、「[CoreWF](https://github.com/UiPath/corewf)」、および [CoreWCF](https://github.com/CoreWCF/CoreWCF) に関するページを参照してください。

サポートされないテクノロジの詳細については、「[.NET Core と .NET 5 以降で使用できない .NET Framework テクノロジ](net-framework-tech-unavailable.md)」を参照してください。

## <a name="windows-desktop-technologies"></a>Windows デスクトップ テクノロジ

.NET Framework 用に作成された多くのアプリケーションでは、Windows フォームや Windows Presentation Foundation (WPF) などのデスクトップ テクノロジが使用されます。 Windows フォームと WPF はどちらも .NET に移植されていますが、これらは引き続き Windows 専用のテクノロジです。

Windows フォームまたは WPF アプリケーションを移行する前に、次の依存関係を考慮してください。

01. .NET 用のプロジェクト ファイルでは、.NET Framework とは異なる形式が使用されます。
01. ご利用のプロジェクトで、.NET では利用できない API が使用される場合があります。
01. サードパーティ製のコントロールとライブラリが .NET に移植されていなく、引き続き .NET Framework でしか使用できない可能性があります。
01. ご利用のプロジェクトでは、.NET で[使用できなくなったテクノロジ](net-framework-tech-unavailable.md)が使用されます。

.NET ではオープンソース バージョンの Windows フォームと WPF が使用されており、.NET Framework に対する拡張機能が含まれています。

デスクトップ アプリケーションを .NET 5 に移行するチュートリアルについては、次の記事のいずれかを参照してください。

- [.NET Framework WPF アプリを .NET に移行する](/dotnet/desktop/wpf/migration/convert-project-from-net-framework?view=netdesktop-5.0&preserve-view=true)
- [.NET Framework Windows フォーム アプリを .NET に移行する](/dotnet/desktop/winforms/migration/?view=netdesktop-5.0&preserve-view=true)

## <a name="windows-specific-apis"></a>Windows 固有の API

アプリケーションでは、.NET でサポートされているプラットフォームで引き続きネイティブ ライブラリを P/Invoke できます。 このテクノロジは、Windows に限定されていません。 ただし、参照しているライブラリが _user32.dll_ や _kernel32.dll_ などの Windows 固有のものである場合、コードは Windows 上でのみ機能します。 アプリを実行するプラットフォームごとに、プラットフォーム固有のバージョンを見つけるか、すべてのプラットフォームで実行できるようにコードを汎用的にする必要があります。

アプリケーションを .NET Framework から .NET に移植する場合、アプリケーションでは、.NET Framework と共に配布されるライブラリがおそらく使用されます。 .NET Framework で使用できた API の多くは、Windows レジストリや GDI+ 描画モデルなどの Windows 固有のテクノロジに依存しているため、.NET に移植されていませんでした。

**Windows 互換機能パック** は、.NET に .NET Framework API サーフェイスの大部分を提供し、[Microsoft.Windows.Compatibility NuGet パッケージ](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)を通じて提供されます。

詳細については、「[Windows 互換機能パックを使用してコードを .NET に移植する](windows-compat-pack.md)」を参照してください。

## <a name="net-framework-compatibility-mode"></a>.NET Framework 互換モード

.NET Standard 2.0 で、.NET Framework 互換モードが導入されました。 この互換モードにより、.NET Standard と .NET 5+ (および .NET Core 3.1) プロジェクトが Windows 専用の .NET Framework ライブラリを参照できるようになります。 .NET Framework ライブラリの参照はすべてのプロジェクトで機能するわけではありません (例えばライブラリで Windows Presentation Foundation (WPF) API を使用していても、多くの移植シナリオがブロック解除される場合など)。 詳細については、[依存関係の分析による .NET Framework から .NET へのコードの移植](third-party-deps.md#net-framework-compatibility-mode)に関する記事を参照してください。

## <a name="cross-platform"></a>クロスプラットフォーム

.NET (旧称 .NET Core) は、クロスプラットフォームになるように設計されています。 コードが Windows 固有のテクノロジに依存していない場合は、macOS、Linux、Android などの他のプラットフォームで実行することができます。 これには、次のようなプロジェクト タイプが含まれます。

- ライブラリ
- コンソールベースのツール
- オートメーション
- ASP.NET サイト

.NET Framework は、Windows のみのコンポーネントです。 コードで Windows フォームや Windows Presentation Foundation (WPF) などの Windows 固有のテクノロジまたは API を使用している場合でも、コードは .NET で実行できますが、他のオペレーティング システムでは実行できません。

ライブラリまたはコンソールベースのアプリケーションは、ほとんど変更せずにクロスプラットフォームで使用できる可能性があります。 .NET に移植する場合は、これを考慮して、他のプラットフォームでアプリケーションをテストすることができます。

## <a name="the-future-of-net-standard"></a>今後の .NET Standard

[.NET Standard](https://github.com/dotnet/standard) は、複数の .NET 実装で使用できる .NET API の正式な仕様です。 .NET Standard の背後にある意図は、.NET エコシステムの高度な統一性を確立することでした。 .NET 5 以降では、統一性を確立するための別のアプローチが採用されており、この新しいアプローチによって、多くのシナリオで .NET Standard が不要になります。 詳細については、「[.NET 5 と .NET Standard](../../standard/net-standard.md#net-5-and-net-standard)」を参照してください。

.NET Standard 2.0 は、.NET Framework をサポートする最後のバージョンでした。

## <a name="tools-to-assist-porting"></a>移植を支援するツール

アプリケーションを .NET Framework から .NET に手動で移植する代わりに、さまざまなツールを使用して、移行のいくつかの側面を自動化できます。 複雑なプロジェクトの移植は、それ自体が複雑なプロセスです。 これらのツールが、その過程で役立つ場合があります。

アプリケーションの移植に役立つツールを使用する場合でも、この記事の[「移植時の考慮事項」のセクション](#considerations-when-porting)を確認してください。

### <a name="net-upgrade-assistant"></a>.NET Upgrade Assistant

[.NET Upgrade Assistant](upgrade-assistant-overview.md) は、さまざまな種類の .NET Framework アプリに対して実行できるコマンド ライン ツールです。 これは、.NET Framework アプリの .NET 5 へのアップグレードを支援するように設計されています。 このツールを実行した後、**ほとんどの場合、アプリでは移行を完遂するためにより多くの作業が必要になります**。 このツールには、移行を完遂するのを支援するアナライザーのインストールが含まれています。 このツールは、次の種類の .NET Framework アプリケーションで動作します。

- Windows フォーム
- WPF
- ASP.NET MVC
- コンソール
- クラス ライブラリ

このツールは、この記事に記載されている他のツールを使用して、移行プロセスを支援します。 ツールの詳細については、「[.NET Upgrade Assistant の概要](upgrade-assistant-overview.md)」を参照してください。

### <a name="try-convert"></a>try-convert

try-convert は、デスクトップ アプリを .NET 5 に移動するなど、プロジェクトかソリューション全体を .NET SDK に変換できる .NET グローバル ツールです。 ただし、カスタム タスク、ターゲット、インポートなどの複雑なビルド プロセスがプロジェクトに含まれている場合は、このツールをお勧めしません。

詳細については、[try-convert の GitHub リポジトリ](https://github.com/dotnet/try-convert)を参照してください。

### <a name="net-portability-analyzer"></a>.NET Portability Analyzer

.NET Portability Analyzer というツールがアセンブリを分析し、指定された対象の .NET プラットフォームでアプリケーションまたはライブラリを移植するために不足している .NET API の詳細なレポートを提供します。

Visual Studio で .NET Portability Analyzer を使用するには、[マーケットプレイスの拡張機能](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)をインストールします。

詳細については、[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) に関するページを参照してください。

### <a name="net-api-analyzer"></a>.NET API アナライザー

[.NET API アナライザー](../../standard/analyzers/api-analyzer.md)は、実行時に <xref:System.PlatformNotSupportedException> をスローする API を使用しているかどうかを分析します。 .NET Framework 4.7.2 以上から移行する場合、これは一般的ではありませんが、確認することをお勧めします。 .NET で例外をスローする API の詳細については、[.NET Core で常に例外をスローする API](../compatibility/unsupported-apis.md) に関する記事を参照してください。

API アナライザーは、プロジェクトに追加する NuGet パッケージ [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/) として提供されています。

詳細については、「[.NET API アナライザー](../../standard/analyzers/api-analyzer.md)」をご覧ください。

## <a name="considerations-when-porting"></a>移植時の考慮事項

アプリケーションを .NET に移植する場合は、次の提案を順番に検討してください。

✔️ [.NET Upgrade Assistant](upgrade-assistant-overview.md) を使用してプロジェクトを移行することを検討します。 このツールはプレビュー段階ですが、この記事で説明している手動の手順のほとんどは自動化されており、移行パスを続行するための開始点として最適です。

✔️ 依存関係を最初に調べることを検討します。 依存関係は、.NET 5、.NET Standard、または .NET Core を対象にする必要があります。

✔️ NuGet の _packages.config_ ファイルを、プロジェクト ファイルの [PackageReference](/nuget/consume-packages/package-references-in-project-files) 設定に移行します。 Visual Studio を使用して [、 _package.config_ ファイルを変換します](/nuget/consume-packages/migrate-packages-config-to-package-reference#migration-steps)。

✔️ アプリをまだ移植できない場合でも、最新のプロジェクト ファイル形式にアップグレードすることを検討します。 .NET Framework プロジェクトでは、古いプロジェクト形式が使用されます。 SDK スタイルのプロジェクトとして知られている最新のプロジェクト形式は、.NET Core 以降に対して作成されていますが、.NET Framework でも動作します。 プロジェクト ファイルを最新の形式にすると、それを基盤として今後もアプリを移植できます。

✔️ .NET Framework プロジェクトを少なくとも .NET Framework 4.7.2 に再ターゲットします。 これにより、.NET Standard が既存の API をサポートしていない場合に、最新の代替 API を使用できるようになります。

✔️ .NET Core 3.1 ではなく、.NET 5 を対象にすることを検討します。 .NET Core 3.1 は長期サポート (LTS) の対象になっていますが、最新は .NET 5 であり、.NET 6 はリリースされると LTS になります。

✔️ **Windows フォームと WPF** のプロジェクトの対象を .NET 5 とします。 .NET 5 には、デスクトップ アプリの多くの機能強化が含まれています。

✔️ .NET Framework プロジェクトでも使用可能なライブラリを移行している場合は、.NET Standard 2.0 を対象とすることを検討します。 また、ライブラリをマルチターゲットに設定し、.NET Framework と .NET Standard の両方をターゲットにすることもできます。

✔️ 移行後に API 不足のエラーが発生した場合は、[Microsoft.Windows.Compatibility NuGet パッケージ](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)に参照を追加します。 .NET Framework API サーフェイスの大部分は、NuGet パッケージを使用して .NET で使用できます。

## <a name="see-also"></a>関連項目

- [.NET Upgrade Assistant の概要](upgrade-assistant-overview.md)
- [ASP.NET から ASP.NET Core への移行](/aspnet/core/migration/proper-to-2x)
- [.NET Framework WPF アプリを .NET に移行する](/dotnet/desktop/wpf/migration/convert-project-from-net-framework?view=netdesktop-5.0&preserve-view=true)
- [.NET Framework Windows フォーム アプリを .NET に移行する](/dotnet/desktop/winforms/migration/?view=netdesktop-5.0&preserve-view=true)
- [.NET Framework ライブラリを .NET に移植する](libraries.md)
- [サーバー アプリ用 .NET 5 と .NET Framework](../../standard/choosing-core-framework-server.md)
