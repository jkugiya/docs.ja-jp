---
title: .NET Framework ツール
description: .NET を対象とするアプリケーションやコンポーネントの作成、配置、管理が簡単になる .NET ツールの一覧をご覧ください。
ms.date: 03/30/2017
helpviewer_keywords:
- command line, .NET Framework tools
- .NET Framework, tools
- tools [.NET Framework]
- running .NET Framework tools
ms.assetid: a2ca532d-91f7-426a-9303-417c2ee1247c
ms.openlocfilehash: 606ead6010ddfd223e4ed38e0271642d36079bcc
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "104654093"
---
# <a name="net-framework-tools"></a><span data-ttu-id="8989c-103">.NET Framework ツール</span><span class="sxs-lookup"><span data-stu-id="8989c-103">.NET Framework tools</span></span>

<span data-ttu-id="8989c-104">.NET Framework ツールを使用すると、.NET Framework に対応したアプリケーションやコンポーネントを簡単に作成、配置、および管理できます。</span><span class="sxs-lookup"><span data-stu-id="8989c-104">The .NET Framework tools make it easier for you to create, deploy, and manage applications and components that target the .NET Framework.</span></span>

<span data-ttu-id="8989c-105">ここで説明する .NET Framework ツールの大半は、Visual Studio のインストール時に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="8989c-105">Most of the .NET Framework tools described in this section are automatically installed with Visual Studio.</span></span> <span data-ttu-id="8989c-106">Visual Studio は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ページからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="8989c-106">To download Visual Studio, visit the [Visual Studio Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) page.</span></span>

<span data-ttu-id="8989c-107">アセンブリ キャッシュ ビューアー (*Shfusion.dll*) を除き、これらのツールはすべてコマンド ラインから実行できます。</span><span class="sxs-lookup"><span data-stu-id="8989c-107">You can run all the tools from the command line, with the exception of the Assembly Cache Viewer (*Shfusion.dll*).</span></span> <span data-ttu-id="8989c-108">エクスプローラーから *Shfusion.dll* にアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8989c-108">You must access *Shfusion.dll* from File Explorer.</span></span>
  
<span data-ttu-id="8989c-109">コマンド ライン ツールの最適な実行方法は、Visual Studio によってインストールされる開発者シェルの 1 つを使用することです。</span><span class="sxs-lookup"><span data-stu-id="8989c-109">The best way to run the command-line tools is by using one of the developer shells that Visual Studio installs.</span></span> <span data-ttu-id="8989c-110">これらのユーティリティを使用すると、インストール フォルダーに移動することなくツールを簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="8989c-110">These utilities enable you to run the tools easily, without having to navigate to the installation folder.</span></span> <span data-ttu-id="8989c-111">詳細については、「[開発者コマンド プロンプトと開発者 PowerShell](/visualstudio/ide/reference/command-prompt-powershell)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8989c-111">For more information, see [Developer Command Prompt and Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>

> [!NOTE]
> <span data-ttu-id="8989c-112">ツールの中には、32 ビット コンピューターまたは 64 ビット コンピューターに固有のものもあります。</span><span class="sxs-lookup"><span data-stu-id="8989c-112">Some tools are specific to either 32-bit computers or 64-bit computers.</span></span> <span data-ttu-id="8989c-113">該当するコンピューターに適切なバージョンのツールを実行します。</span><span class="sxs-lookup"><span data-stu-id="8989c-113">Be sure to run the appropriate version of the tool for your computer.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8989c-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="8989c-114">In this section</span></span>

- [<span data-ttu-id="8989c-115">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="8989c-115">Al.exe (Assembly Linker)</span></span>](al-exe-assembly-linker.md)  
<span data-ttu-id="8989c-116">モジュール ファイルまたはリソース ファイルから、アセンブリ マニフェストを含むファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="8989c-116">Generates a file that has an assembly manifest from modules or resource files.</span></span>

- [<span data-ttu-id="8989c-117">Aximp.exe (Windows フォーム ActiveX コントロール インポーター)</span><span class="sxs-lookup"><span data-stu-id="8989c-117">Aximp.exe (Windows Forms ActiveX Control Importer)</span></span>](aximp-exe-windows-forms-activex-control-importer.md)  
<span data-ttu-id="8989c-118">ActiveX コントロール用の COM タイプ ライブラリに属する型定義を Windows フォーム コントロールに変換します。</span><span class="sxs-lookup"><span data-stu-id="8989c-118">Converts type definitions in a COM type library for an ActiveX control into a Windows Forms control.</span></span>

- [<span data-ttu-id="8989c-119">Caspol.exe (コード アクセス セキュリティ ポリシー ツール)</span><span class="sxs-lookup"><span data-stu-id="8989c-119">Caspol.exe (Code Access Security Policy Tool)</span></span>](caspol-exe-code-access-security-policy-tool.md)  
<span data-ttu-id="8989c-120">コンピューター ポリシー レベル、ユーザー ポリシー レベル、およびエンタープライズ ポリシー レベルのセキュリティ ポリシーを表示および構成できます。</span><span class="sxs-lookup"><span data-stu-id="8989c-120">Enables you to view and configure security policy for the machine policy level, the user policy level, and the enterprise policy level.</span></span> <span data-ttu-id="8989c-121">.NET Framework 4 以降では、[\<legacyCasPolicy> 要素](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)が `true` に設定されていない限り、このツールがコード アクセス セキュリティ (CAS) ポリシーに影響を与えることはありません。</span><span class="sxs-lookup"><span data-stu-id="8989c-121">In the .NET Framework 4 and later, this tool does not affect code access security (CAS) policy unless the [\<legacyCasPolicy> element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) is set to `true`.</span></span> <span data-ttu-id="8989c-122">詳細については、「[セキュリティの変更点](/previous-versions/dotnet/framework/security/security-changes)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8989c-122">For more information, see [Security Changes](/previous-versions/dotnet/framework/security/security-changes).</span></span>

- [<span data-ttu-id="8989c-123">Cert2spc.exe (ソフトウェア発行元証明書テスト ツール)</span><span class="sxs-lookup"><span data-stu-id="8989c-123">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>](cert2spc-exe-software-publisher-certificate-test-tool.md)  
<span data-ttu-id="8989c-124">1 つ以上の X.509 証明書からソフトウェア発行元証明書 (SPC: Software Publisher's Certificate) を作成します。</span><span class="sxs-lookup"><span data-stu-id="8989c-124">Creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="8989c-125">このツールはテスト専用です。</span><span class="sxs-lookup"><span data-stu-id="8989c-125">This tool is for testing purposes only.</span></span>

- [<span data-ttu-id="8989c-126">Certmgr.exe (証明書マネージャー ツール)</span><span class="sxs-lookup"><span data-stu-id="8989c-126">Certmgr.exe (Certificate Manager Tool)</span></span>](certmgr-exe-certificate-manager-tool.md)  
<span data-ttu-id="8989c-127">証明書、証明書信頼リスト (CTL: Certificate Trust Lists)、および証明書失効リスト (CRL: Certificate Revocation Lists) を管理します。</span><span class="sxs-lookup"><span data-stu-id="8989c-127">Manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>

- [<span data-ttu-id="8989c-128">Clrver.exe (CLR バージョン ツール)</span><span class="sxs-lookup"><span data-stu-id="8989c-128">Clrver.exe (CLR Version Tool)</span></span>](clrver-exe-clr-version-tool.md)  
<span data-ttu-id="8989c-129">コンピューターにインストールされている共通言語ランタイム (CLR) のすべてのバージョンを報告します。</span><span class="sxs-lookup"><span data-stu-id="8989c-129">Reports all the installed versions of the common language runtime (CLR) on the computer.</span></span>

- [<span data-ttu-id="8989c-130">CorFlags.exe (CorFlags 変換ツール)</span><span class="sxs-lookup"><span data-stu-id="8989c-130">CorFlags.exe (CorFlags Conversion Tool)</span></span>](corflags-exe-corflags-conversion-tool.md)  
<span data-ttu-id="8989c-131">移植可能な実行可能 (PE) イメージのヘッダー内の CorFlags セクションを構成します。</span><span class="sxs-lookup"><span data-stu-id="8989c-131">Lets you configure the CorFlags section of the header of a portable executable (PE) image.</span></span>

- [<span data-ttu-id="8989c-132">Fuslogvw.exe (アセンブリ バインディング ログ ビューアー)</span><span class="sxs-lookup"><span data-stu-id="8989c-132">Fuslogvw.exe (Assembly Binding Log Viewer)</span></span>](fuslogvw-exe-assembly-binding-log-viewer.md)  
<span data-ttu-id="8989c-133">アセンブリ バインドに関する情報を表示します。これは、.NET Framework が実行時にアセンブリを見つけられない原因を診断する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8989c-133">Displays information about assembly binds to help you diagnose why the .NET Framework cannot locate an assembly at run time.</span></span>

- [<span data-ttu-id="8989c-134">Gacutil.exe (グローバル アセンブリ キャッシュ ツール)</span><span class="sxs-lookup"><span data-stu-id="8989c-134">Gacutil.exe (Global Assembly Cache Tool)</span></span>](gacutil-exe-gac-tool.md)  
<span data-ttu-id="8989c-135">グローバル アセンブリ キャッシュおよびダウンロード キャッシュの内容の表示と操作を行います。</span><span class="sxs-lookup"><span data-stu-id="8989c-135">Lets you view and manipulate the contents of the global assembly cache and download cache.</span></span>

- [<span data-ttu-id="8989c-136">Ilasm.exe (IL アセンブラー)</span><span class="sxs-lookup"><span data-stu-id="8989c-136">Ilasm.exe (IL Assembler)</span></span>](ilasm-exe-il-assembler.md)  
<span data-ttu-id="8989c-137">中間言語 (IL) から移植可能な実行可能 (PE) ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="8989c-137">Generates a portable executable (PE) file from intermediate language (IL).</span></span> <span data-ttu-id="8989c-138">生成された実行可能ファイルを実行すると、IL が期待どおりに動作するかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="8989c-138">You can run the resulting executable to determine whether the IL performs as expected.</span></span>

- [<span data-ttu-id="8989c-139">Ildasm.exe (IL 逆アセンブラー)</span><span class="sxs-lookup"><span data-stu-id="8989c-139">Ildasm.exe (IL Disassembler)</span></span>](ildasm-exe-il-disassembler.md)  
<span data-ttu-id="8989c-140">中間言語 (IL) コードを含む移植可能な実行可能 (PE) ファイルを受け取り、IL アセンブラー (Ilasm.exe) への入力として使用できるテキスト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="8989c-140">Takes a portable executable (PE) file that contains intermediate language (IL) code and creates a text file that can be input to the IL Assembler (Ilasm.exe).</span></span>

- [<span data-ttu-id="8989c-141">Installutil.exe (インストーラー ツール)</span><span class="sxs-lookup"><span data-stu-id="8989c-141">Installutil.exe (Installer Tool)</span></span>](installutil-exe-installer-tool.md)  
<span data-ttu-id="8989c-142">指定したアセンブリのインストーラー コンポーネントを実行することによって、サーバー リソースのインストールとアンインストールを実行できます</span><span class="sxs-lookup"><span data-stu-id="8989c-142">Enables you to install and uninstall server resources by executing the installer components in a specified assembly.</span></span> <span data-ttu-id="8989c-143">(<xref:System.Configuration.Install> 名前空間のクラスと連携して動作します)。</span><span class="sxs-lookup"><span data-stu-id="8989c-143">(Works with classes in the <xref:System.Configuration.Install> namespace.)</span></span>

- [<span data-ttu-id="8989c-144">Lc.exe (ライセンス コンパイラ)</span><span class="sxs-lookup"><span data-stu-id="8989c-144">Lc.exe (License Compiler)</span></span>](lc-exe-license-compiler.md)  
<span data-ttu-id="8989c-145">ライセンス情報を含むテキスト ファイルを読み込んで、 *.licenses* ファイルを生成します。これは、共通言語ランタイムの実行可能ファイルにリソースとして埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="8989c-145">Reads text files that contain licensing information and produces a *.licenses* file that can be embedded in a common language runtime executable as a resource.</span></span>

- [<span data-ttu-id="8989c-146">Mage.exe (マニフェストの生成および編集ツール)</span><span class="sxs-lookup"><span data-stu-id="8989c-146">Mage.exe (Manifest Generation and Editing Tool)</span></span>](mage-exe-manifest-generation-and-editing-tool.md)  
<span data-ttu-id="8989c-147">アプリケーション マニフェストと配置マニフェストの作成、編集、および署名を行います。</span><span class="sxs-lookup"><span data-stu-id="8989c-147">Lets you create, edit, and sign application and deployment manifests.</span></span> <span data-ttu-id="8989c-148">*Mage.exe* はコマンド ライン ツールであるため、バッチ スクリプトから実行したり、ASP.NET アプリケーションなどの他の Windows ベースのアプリケーションから実行したりできます。</span><span class="sxs-lookup"><span data-stu-id="8989c-148">As a command-line tool, *Mage.exe* can be run from both batch scripts and other Windows-based applications, including ASP.NET applications.</span></span>

- [<span data-ttu-id="8989c-149">MageUI.exe (マニフェスト生成および編集ツールのグラフィカル クライアント)</span><span class="sxs-lookup"><span data-stu-id="8989c-149">MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)</span></span>](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)  
<span data-ttu-id="8989c-150">コマンド ライン ツールの Mage.exe と同じ機能をサポートしますが、Windows ベースのユーザー インターフェイス (UI) を使用します。</span><span class="sxs-lookup"><span data-stu-id="8989c-150">Supports the same functionality as the command-line tool Mage.exe, but uses a Windows-based user interface (UI).</span></span> <span data-ttu-id="8989c-151">コマンド ライン ツールの *Mage.exe* と同じ機能がサポートされますが、Windows ベースのユーザー インターフェイス (UI) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="8989c-151">Supports the same functionality as the command-line tool *Mage.exe*, but uses a Windows-based user interface (UI).</span></span>

- [<span data-ttu-id="8989c-152">MDbg.exe (.NET Framework コマンド ライン デバッガー)</span><span class="sxs-lookup"><span data-stu-id="8989c-152">MDbg.exe (.NET Framework Command-Line Debugger)</span></span>](mdbg-exe.md)  
<span data-ttu-id="8989c-153">.NET Framework 共通言語ランタイムを対象としたプログラムに含まれるバグの発見と修正について、ツールの販売元とアプリケーション開発者を支援するツールです。</span><span class="sxs-lookup"><span data-stu-id="8989c-153">Helps tools vendors and application developers find and fix bugs in programs that target the .NET Framework common language runtime.</span></span> <span data-ttu-id="8989c-154">このツールは、ランタイムのデバッグ API を使用してデバッグ サービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="8989c-154">This tool uses the runtime debugging API to provide debugging services.</span></span>

- [<span data-ttu-id="8989c-155">Mgmtclassgen.exe (厳密型クラス ジェネレーター)</span><span class="sxs-lookup"><span data-stu-id="8989c-155">Mgmtclassgen.exe (Management Strongly Typed Class Generator)</span></span>](mgmtclassgen-exe.md)  
<span data-ttu-id="8989c-156">指定した WMI (Windows Management Instrumentation) クラスに対して、事前バインディングされたマネージド クラスを生成できます。</span><span class="sxs-lookup"><span data-stu-id="8989c-156">Enables you to generate an early-bound managed class for a specified Windows Management Instrumentation (WMI) class.</span></span>

- [<span data-ttu-id="8989c-157">Mpgo.exe (マネージド プロファイル ガイド付き最適化ツール)</span><span class="sxs-lookup"><span data-stu-id="8989c-157">Mpgo.exe (Managed Profile Guided Optimization Tool)</span></span>](mpgo-exe-managed-profile-guided-optimization-tool.md)  
<span data-ttu-id="8989c-158">一般的なエンド ユーザーのシナリオを使用してネイティブ イメージのアセンブリを調整できるようにします。</span><span class="sxs-lookup"><span data-stu-id="8989c-158">Enables you to tune native image assemblies using common end-user scenarios.</span></span> <span data-ttu-id="8989c-159">Mpgo.exe により、アプリケーション開発者によって選択されたトレーニング シナリオを使用したネイティブ イメージ アプリケーション アセンブリ (.NET Framework アセンブリではない) のプロファイル データの生成と消費が可能になります。</span><span class="sxs-lookup"><span data-stu-id="8989c-159">Mpgo.exe allows the generation and consumption of profile data for native image application assemblies (not the .NET Framework assemblies) using training scenarios selected by the application developer.</span></span>

- [<span data-ttu-id="8989c-160">Ngen.exe (ネイティブ イメージ ジェネレーター)</span><span class="sxs-lookup"><span data-stu-id="8989c-160">Ngen.exe (Native Image Generator)</span></span>](ngen-exe-native-image-generator.md)  
<span data-ttu-id="8989c-161">ネイティブ イメージ (コンパイルされたプロセッサ固有のマシン語コードを格納しているファイル) を使用することで、マネージド アプリケーションのパフォーマンスを改善します。</span><span class="sxs-lookup"><span data-stu-id="8989c-161">Improves the performance of managed applications through the use of native images (files containing compiled processor-specific machine code).</span></span> <span data-ttu-id="8989c-162">ランタイムは、Just-In-Time (JIT) コンパイラを使用してオリジナルのアセンブリをコンパイルする代わりに、キャッシュにあるネイティブ イメージを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8989c-162">The runtime can use native images from the cache instead of using the just-in-time (JIT) compiler to compile the original assembly.</span></span>

- [<span data-ttu-id="8989c-163">Peverify.exe (PEVerify ツール)</span><span class="sxs-lookup"><span data-stu-id="8989c-163">Peverify.exe (PEVerify Tool)</span></span>](peverify-exe-peverify-tool.md)  
<span data-ttu-id="8989c-164">Microsoft Intermediate Language (MSIL) コードと関連メタデータがタイプ セーフ要件を満たしているかどうかを検証する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8989c-164">Helps you verify whether your Microsoft intermediate language (MSIL) code and associated metadata meet type safety requirements.</span></span>

- [<span data-ttu-id="8989c-165">Regasm.exe (アセンブリ登録ツール)</span><span class="sxs-lookup"><span data-stu-id="8989c-165">Regasm.exe (Assembly Registration Tool)</span></span>](regasm-exe-assembly-registration-tool.md)  
<span data-ttu-id="8989c-166">アセンブリ内のメタデータを読み取り、必要なエントリをレジストリに追加します。</span><span class="sxs-lookup"><span data-stu-id="8989c-166">Reads the metadata within an assembly and adds the necessary entries to the registry.</span></span> <span data-ttu-id="8989c-167">これにより、COM クライアントが .NET Framework クラスとして表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="8989c-167">This enables COM clients to appear as .NET Framework classes.</span></span>

- [<span data-ttu-id="8989c-168">Regsvcs.exe (.NET サービス インストール ツール)</span><span class="sxs-lookup"><span data-stu-id="8989c-168">Regsvcs.exe (.NET Services Installation Tool)</span></span>](regsvcs-exe-net-services-installation-tool.md)  
<span data-ttu-id="8989c-169">アセンブリを読み込んで登録し、タイプ ライブラリを生成して指定された COM+ Version 1.0 アプリケーションにインストールし、プログラムによってクラスに追加されたサービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="8989c-169">Loads and registers an assembly, generates and installs a type library into a specified COM+ version 1.0 application, and configures services that you have added programmatically to a class.</span></span>

- [<span data-ttu-id="8989c-170">Resgen.exe (リソース ファイル ジェネレーター)</span><span class="sxs-lookup"><span data-stu-id="8989c-170">Resgen.exe (Resource File Generator)</span></span>](resgen-exe-resource-file-generator.md)  
<span data-ttu-id="8989c-171">テキスト ファイル ( *.txt* または *.restext*) と XML ベースのリソース形式ファイル ( *.resx*) を、共通言語ランタイムのバイナリ ファイル ( *.resources*) に変換します。これは、ランタイム バイナリ実行可能ファイルに埋め込んだり、サテライト アセンブリにコンパイルしたりできます。</span><span class="sxs-lookup"><span data-stu-id="8989c-171">Converts text (*.txt* or *.restext*) files and XML-based resource format (*.resx*) files to common language runtime binary (*.resources*) files that can be embedded in a runtime binary executable or compiled into satellite assemblies.</span></span>

- [<span data-ttu-id="8989c-172">SecAnnotate.exe (.NET Security Annotator ツール)</span><span class="sxs-lookup"><span data-stu-id="8989c-172">SecAnnotate.exe (.NET Security Annotator Tool)</span></span>](secannotate-exe-net-security-annotator-tool.md)  
<span data-ttu-id="8989c-173">アセンブリの `SecurityCritical` 部分と `SecuritySafeCritical` 部分を識別します。</span><span class="sxs-lookup"><span data-stu-id="8989c-173">Identifies the `SecurityCritical` and `SecuritySafeCritical` portions of an assembly.</span></span>

- [<span data-ttu-id="8989c-174">SignTool.exe (署名ツール)</span><span class="sxs-lookup"><span data-stu-id="8989c-174">SignTool.exe (Sign Tool)</span></span>](signtool-exe.md)  
<span data-ttu-id="8989c-175">ファイルにデジタル署名を添付し、ファイルの署名を検証し、ファイルにタイム スタンプを付けます。</span><span class="sxs-lookup"><span data-stu-id="8989c-175">Digitally signs files, verifies signatures in files, and time-stamps files.</span></span>

- [<span data-ttu-id="8989c-176">Sn.exe (厳密名ツール)</span><span class="sxs-lookup"><span data-stu-id="8989c-176">Sn.exe (Strong Name Tool)</span></span>](sn-exe-strong-name-tool.md)  
<span data-ttu-id="8989c-177">厳密な名前を持つアセンブリを作成するときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8989c-177">Helps create assemblies with strong names.</span></span> <span data-ttu-id="8989c-178">このツールには、キーの管理、署名の生成、署名の検査に関する各オプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="8989c-178">This tool provides options for key management, signature generation, and signature verification.</span></span>

- [<span data-ttu-id="8989c-179">SOS.dll (SOS デバッガー拡張)</span><span class="sxs-lookup"><span data-stu-id="8989c-179">SOS.dll (SOS Debugging Extension)</span></span>](sos-dll-sos-debugging-extension.md)  
<span data-ttu-id="8989c-180">内部の共通言語ランタイム環境に関する情報を提供して、WinDbg.exe デバッガーおよび Visual Studio におけるマネージド プログラムのデバッグを支援します。</span><span class="sxs-lookup"><span data-stu-id="8989c-180">Helps you debug managed programs in the WinDbg.exe debugger and in Visual Studio by providing information about the internal common language runtime environment.</span></span>

- [<span data-ttu-id="8989c-181">SqlMetal.exe (コード生成ツール)</span><span class="sxs-lookup"><span data-stu-id="8989c-181">SqlMetal.exe (Code Generation Tool)</span></span>](sqlmetal-exe-code-generation-tool.md)  
<span data-ttu-id="8989c-182">.NET Framework の LINQ to SQL コンポーネント用のコードとマッピングを生成します。</span><span class="sxs-lookup"><span data-stu-id="8989c-182">Generates code and mapping for the LINQ to SQL component of the .NET Framework.</span></span>

- [<span data-ttu-id="8989c-183">Storeadm.exe (分離ストレージ ツール)</span><span class="sxs-lookup"><span data-stu-id="8989c-183">Storeadm.exe (Isolated Storage Tool)</span></span>](storeadm-exe-isolated-storage-tool.md)  
<span data-ttu-id="8989c-184">分離ストレージを管理します。ユーザーのストアの一覧表示や削除を行うためのオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="8989c-184">Manages isolated storage; provides options for listing the user's stores and deleting them.</span></span>

- [<span data-ttu-id="8989c-185">Tlbexp.exe (タイプ ライブラリ エクスポーター)</span><span class="sxs-lookup"><span data-stu-id="8989c-185">Tlbexp.exe (Type Library Exporter)</span></span>](tlbexp-exe-type-library-exporter.md)  
<span data-ttu-id="8989c-186">共通言語ランタイム アセンブリで定義されている型を記述するタイプ ライブラリを生成します。</span><span class="sxs-lookup"><span data-stu-id="8989c-186">Generates a type library that describes the types that are defined in a common language runtime assembly.</span></span>

- [<span data-ttu-id="8989c-187">Tlbimp.exe (タイプ ライブラリ インポーター)</span><span class="sxs-lookup"><span data-stu-id="8989c-187">Tlbimp.exe (Type Library Importer)</span></span>](tlbimp-exe-type-library-importer.md)  
<span data-ttu-id="8989c-188">COM タイプ ライブラリ内の型定義を、共通言語ランタイム アセンブリで等価な定義に変換します。</span><span class="sxs-lookup"><span data-stu-id="8989c-188">Converts the type definitions found in a COM type library into equivalent definitions in a common language runtime assembly.</span></span>

- [<span data-ttu-id="8989c-189">Winmdexp.exe (Windows ランタイム メタデータのエクスポート ツール)</span><span class="sxs-lookup"><span data-stu-id="8989c-189">Winmdexp.exe (Windows Runtime Metadata Export Tool)</span></span>](winmdexp-exe-windows-runtime-metadata-export-tool.md)  
<span data-ttu-id="8989c-190">*.winmdobj* ファイルとしてコンパイルされた .NET Framework アセンブリを Windows ランタイム コンポーネントにエクスポートします。このコンポーネントは、Windows ランタイム メタデータと実装に関する情報の両方を含む *.winmd* ファイルとしてパッケージされます。</span><span class="sxs-lookup"><span data-stu-id="8989c-190">Exports a .NET Framework assembly that is compiled as a *.winmdobj* file into a Windows Runtime component, which is packaged as a *.winmd* file that contains both Windows Runtime metadata and implementation information.</span></span>

- [<span data-ttu-id="8989c-191">Winres.exe (Windows フォーム リソース エディター)</span><span class="sxs-lookup"><span data-stu-id="8989c-191">Winres.exe (Windows Forms Resource Editor)</span></span>](winres-exe-windows-forms-resource-editor.md)  
<span data-ttu-id="8989c-192">Windows フォームで使用されるユーザー インターフェイス (UI) リソース ( *.resx* ファイルまたは *.resources* ファイル) をローカライズするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8989c-192">Helps you localize user interface (UI) resources (*.resx* or *.resources* files) that are used by Windows Forms.</span></span> <span data-ttu-id="8989c-193">文字列を翻訳した後、ローカライズされた文字列に合わせて、コントロールのサイズを変更したり、コントロールを移動したり、非表示にしたりできます。</span><span class="sxs-lookup"><span data-stu-id="8989c-193">You can translate strings, and then size, move, and hide controls to accommodate the localized strings.</span></span>

## <a name="related-sections"></a><span data-ttu-id="8989c-194">関連項目</span><span class="sxs-lookup"><span data-stu-id="8989c-194">Related sections</span></span>

- <span data-ttu-id="8989c-195">[WPF ツール](/previous-versions/ms742404(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="8989c-195">[WPF Tools](/previous-versions/ms742404(v=vs.110))</span></span>  
<span data-ttu-id="8989c-196">isXPS 適合性ツール (isXPS.exe) およびパフォーマンス プロファイリング ツールなどのツールを含みます。</span><span class="sxs-lookup"><span data-stu-id="8989c-196">Includes tools such as the isXPS Conformance tool (isXPS.exe) and performance profiling tools.</span></span>

- [<span data-ttu-id="8989c-197">Windows Communication Foundation ツール</span><span class="sxs-lookup"><span data-stu-id="8989c-197">Windows Communication Foundation Tools</span></span>](../wcf/tools.md)  
<span data-ttu-id="8989c-198">WCF (Windows Communication Foundation) アプリケーションの作成、配置、および管理を効率化するツールを含みます。</span><span class="sxs-lookup"><span data-stu-id="8989c-198">Includes tools that make it easier for you to create, deploy, and manage Windows Communication Foundation (WCF) applications.</span></span>
