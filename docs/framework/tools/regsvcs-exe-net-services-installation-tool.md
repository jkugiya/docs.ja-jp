---
title: Regsvcs.exe (.NET サービス インストール ツール)
description: Regsvcs.exe (.NET サービス インストール ツール) を使用します。 アセンブリの読み込みと登録、プログラムによってクラスに追加したサービスの構成などを行います。
ms.date: 03/30/2017
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
ms.openlocfilehash: 03787ecacc00c35f31f1fa5101fff5882e5314f6
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653310"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="3641b-104">Regsvcs.exe (.NET サービス インストール ツール)</span><span class="sxs-lookup"><span data-stu-id="3641b-104">Regsvcs.exe (.NET Services Installation Tool)</span></span>

<span data-ttu-id="3641b-105">.NET サービス インストール ツールは、次のアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="3641b-105">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="3641b-106">アセンブリの読み込みと登録。</span><span class="sxs-lookup"><span data-stu-id="3641b-106">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="3641b-107">タイプ ライブラリの生成、登録、および指定された COM+ アプリケーションへのインストール。</span><span class="sxs-lookup"><span data-stu-id="3641b-107">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="3641b-108">プログラムでクラスに追加したサービスの設定。</span><span class="sxs-lookup"><span data-stu-id="3641b-108">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="3641b-109">ツールを実行するには、[、Visual Studio 開発者コマンド プロンプトまたは Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell) を使用します。</span><span class="sxs-lookup"><span data-stu-id="3641b-109">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
 <span data-ttu-id="3641b-110">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="3641b-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3641b-111">構文</span><span class="sxs-lookup"><span data-stu-id="3641b-111">Syntax</span></span>  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll
```  
  
## <a name="parameters"></a><span data-ttu-id="3641b-112">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3641b-112">Parameters</span></span>  
  
|<span data-ttu-id="3641b-113">引数</span><span class="sxs-lookup"><span data-stu-id="3641b-113">Argument</span></span>|<span data-ttu-id="3641b-114">説明</span><span class="sxs-lookup"><span data-stu-id="3641b-114">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="3641b-115">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="3641b-115">*assemblyFile.dll*</span></span>|<span data-ttu-id="3641b-116">ソース アセンブリ ファイル。</span><span class="sxs-lookup"><span data-stu-id="3641b-116">The source assembly file.</span></span> <span data-ttu-id="3641b-117">アセンブリは、厳密な名前で署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3641b-117">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="3641b-118">詳しくは、「[厳密な名前でのアセンブリへの署名](../../standard/assembly/sign-strong-name.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3641b-118">For more information, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span>|  
  
|<span data-ttu-id="3641b-119">オプション</span><span class="sxs-lookup"><span data-stu-id="3641b-119">Option</span></span>|<span data-ttu-id="3641b-120">説明</span><span class="sxs-lookup"><span data-stu-id="3641b-120">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3641b-121">**/appdir:** *path*</span><span class="sxs-lookup"><span data-stu-id="3641b-121">**/appdir:** *path*</span></span>|<span data-ttu-id="3641b-122">アプリケーションのルート ディレクトリを示します。</span><span class="sxs-lookup"><span data-stu-id="3641b-122">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="3641b-123">**/appname:** *applicationName*</span><span class="sxs-lookup"><span data-stu-id="3641b-123">**/appname:** *applicationName*</span></span>|<span data-ttu-id="3641b-124">検索または作成する COM+ アプリケーションの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3641b-124">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="3641b-125">**/c**</span><span class="sxs-lookup"><span data-stu-id="3641b-125">**/c**</span></span>|<span data-ttu-id="3641b-126">ターゲット アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="3641b-126">Creates the target application.</span></span>|  
|<span data-ttu-id="3641b-127">**/componly**</span><span class="sxs-lookup"><span data-stu-id="3641b-127">**/componly**</span></span>|<span data-ttu-id="3641b-128">コンポーネントだけを設定します。メソッドとインターフェイスは無視されます。</span><span class="sxs-lookup"><span data-stu-id="3641b-128">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="3641b-129">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="3641b-129">**/exapp**</span></span>|<span data-ttu-id="3641b-130">このツールが既存のアプリケーションを要求するように指定します。</span><span class="sxs-lookup"><span data-stu-id="3641b-130">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="3641b-131">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="3641b-131">**/extlb**</span></span>|<span data-ttu-id="3641b-132">既存のタイプ ライブラリを使用します。</span><span class="sxs-lookup"><span data-stu-id="3641b-132">Uses an existing type library.</span></span>|  
|<span data-ttu-id="3641b-133">**/fc**</span><span class="sxs-lookup"><span data-stu-id="3641b-133">**/fc**</span></span>|<span data-ttu-id="3641b-134">対象アプリケーションを検索または作成します。</span><span class="sxs-lookup"><span data-stu-id="3641b-134">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="3641b-135">**/help**</span><span class="sxs-lookup"><span data-stu-id="3641b-135">**/help**</span></span>|<span data-ttu-id="3641b-136">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="3641b-136">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="3641b-137">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="3641b-137">**/noreconfig**</span></span>|<span data-ttu-id="3641b-138">既存の対象アプリケーションを再設定しません。</span><span class="sxs-lookup"><span data-stu-id="3641b-138">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="3641b-139">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="3641b-139">**/nologo**</span></span>|<span data-ttu-id="3641b-140">Microsoft 著作権情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="3641b-140">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="3641b-141">**/parname:** *name*</span><span class="sxs-lookup"><span data-stu-id="3641b-141">**/parname:** *name*</span></span>|<span data-ttu-id="3641b-142">検索または作成する COM+ アプリケーションの名前または ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="3641b-142">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="3641b-143">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="3641b-143">**/reconfig**</span></span>|<span data-ttu-id="3641b-144">既存の対象アプリケーションを再設定します。</span><span class="sxs-lookup"><span data-stu-id="3641b-144">Reconfigures an existing target application.</span></span> <span data-ttu-id="3641b-145">既定値です。</span><span class="sxs-lookup"><span data-stu-id="3641b-145">This is the default.</span></span>|  
|<span data-ttu-id="3641b-146">**/tlb:** *typelibraryfile*</span><span class="sxs-lookup"><span data-stu-id="3641b-146">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="3641b-147">インストールするタイプ ライブラリ ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="3641b-147">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="3641b-148">**/u**</span><span class="sxs-lookup"><span data-stu-id="3641b-148">**/u**</span></span>|<span data-ttu-id="3641b-149">対象アプリケーションをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="3641b-149">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="3641b-150">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="3641b-150">**/quiet**</span></span>|<span data-ttu-id="3641b-151">クワイエット モードを指定します。ロゴと成功メッセージは表示されません。</span><span class="sxs-lookup"><span data-stu-id="3641b-151">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="3641b-152">**/?**</span><span class="sxs-lookup"><span data-stu-id="3641b-152">**/?**</span></span>|<span data-ttu-id="3641b-153">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="3641b-153">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3641b-154">Remarks</span><span class="sxs-lookup"><span data-stu-id="3641b-154">Remarks</span></span>  

 <span data-ttu-id="3641b-155">Regsvcs.exe には、*assemblyFile.dll* で指定されているソース アセンブリ ファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="3641b-155">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="3641b-156">このアセンブリは、厳密な名前で署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3641b-156">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="3641b-157">厳密な名前での署名について詳しくは、「[厳密な名前でのアセンブリへの署名](../../standard/assembly/sign-strong-name.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3641b-157">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span> <span data-ttu-id="3641b-158">対象アプリケーションおよびタイプ ライブラリの名前は、オプションです。</span><span class="sxs-lookup"><span data-stu-id="3641b-158">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="3641b-159">引数 *applicationName* はソース アセンブリ ファイルから生成できます。存在しない場合は、Regsvcs.exe によって作成されます。</span><span class="sxs-lookup"><span data-stu-id="3641b-159">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="3641b-160">引数 *typelibraryfile* にはタイプ ライブラリ名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3641b-160">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="3641b-161">タイプ ライブラリ名を指定しない場合、Regsvcs.exe は既定値としてアセンブリ名を使用します。</span><span class="sxs-lookup"><span data-stu-id="3641b-161">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="3641b-162">Regsvcs.exe がコンポーネントのメソッドを登録する場合は、それらのメソッドに対する[確認要求](/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100))と[リンク確認要求](../misc/link-demands.md)の影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="3641b-162">When Regsvcs.exe registers a component's methods, it is subject to the [demands](/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="3641b-163">このツールは完全に信頼された環境で実行されるため、アクセス許可に対するほとんどの確認要求は成功します。</span><span class="sxs-lookup"><span data-stu-id="3641b-163">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="3641b-164">ただし、Regsvcs.exe では、<xref:System.Security.Permissions.StrongNameIdentityPermission> または <xref:System.Security.Permissions.PublisherIdentityPermission> に対する確認要求やリンク確認要求によって保護されたメソッドを含むコンポーネントを登録することはできません。</span><span class="sxs-lookup"><span data-stu-id="3641b-164">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="3641b-165">Regsvcs.exe を使用するには、ローカル コンピューターの管理特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="3641b-165">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="3641b-166">上記のアクションの実行中に Regsvcs.exe が異常終了した場合は、対応するエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3641b-166">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3641b-167">使用例</span><span class="sxs-lookup"><span data-stu-id="3641b-167">Examples</span></span>  

 <span data-ttu-id="3641b-168">`myTest.dll` に含まれるすべてのパブリック クラスを `myTargetApp` (既存の COM+ アプリケーション) に追加し、タイプ ライブラリ `myTest.tlb` を生成するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3641b-168">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="3641b-169">`myTest.dll` に含まれるすべてのパブリック クラスを `myTargetApp` (既存の COM+ アプリケーション) に追加し、タイプ ライブラリ `newTest.tlb` を生成するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3641b-169">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="3641b-170">関連項目</span><span class="sxs-lookup"><span data-stu-id="3641b-170">See also</span></span>

- [<span data-ttu-id="3641b-171">ツール</span><span class="sxs-lookup"><span data-stu-id="3641b-171">Tools</span></span>](index.md)
- [<span data-ttu-id="3641b-172">方法: 厳密な名前でアセンブリに署名する</span><span class="sxs-lookup"><span data-stu-id="3641b-172">How to: Sign an Assembly with a Strong Name</span></span>](../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="3641b-173">開発者コマンドライン シェル</span><span class="sxs-lookup"><span data-stu-id="3641b-173">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
