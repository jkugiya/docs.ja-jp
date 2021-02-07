---
description: '詳細情報: セットアップに関する問題のトラブルシューティング'
title: セットアップに関する問題のトラブルシューティング
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 8beb404040c15ade8f435772fe1b947eef766702
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703472"
---
# <a name="troubleshoot-setup-issues"></a><span data-ttu-id="9cb64-103">セットアップに関する問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="9cb64-103">Troubleshoot setup issues</span></span>

<span data-ttu-id="9cb64-104">この記事では、Windows Communication Foundation (WCF) セットアップの問題をトラブルシューティングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9cb64-104">This article describes how to troubleshoot Windows Communication Foundation (WCF) setup issues.</span></span>  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a><span data-ttu-id="9cb64-105">.NET Framework 3.0 の MSI 修復操作の実行では修復されない一部の Windows Communication Foundation レジストリ キー</span><span class="sxs-lookup"><span data-stu-id="9cb64-105">Some Windows Communication Foundation Registry Keys are not Repaired by Performing an MSI Repair Operation on the .NET Framework 3.0</span></span>  

 <span data-ttu-id="9cb64-106">次のいずれかのレジストリ キーを削除した場合</span><span class="sxs-lookup"><span data-stu-id="9cb64-106">If you delete any of the following registry keys:</span></span>  
  
- <span data-ttu-id="9cb64-107">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="9cb64-107">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0</span></span>  
  
- <span data-ttu-id="9cb64-108">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="9cb64-108">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0</span></span>  
  
- <span data-ttu-id="9cb64-109">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="9cb64-109">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0</span></span>  
  
- <span data-ttu-id="9cb64-110">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="9cb64-110">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0</span></span>  
  
- <span data-ttu-id="9cb64-111">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="9cb64-111">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0</span></span>  
  
 <span data-ttu-id="9cb64-112">**コントロールパネル** の [**プログラムの追加と削除**] アプレットから起動した .NET Framework 3.0 インストーラーを使用して修復を実行した場合、キーは再作成されません。</span><span class="sxs-lookup"><span data-stu-id="9cb64-112">The keys are not re-created if you run repair by using the .NET Framework 3.0 installer launched from the **Add/Remove Programs** applet in **Control Panel**.</span></span> <span data-ttu-id="9cb64-113">これらのキーを正しく再作成するには、.NET Framework 3.0 をアンインストール後、再インストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cb64-113">To recreate these keys correctly, the user must uninstall and reinstall the .NET Framework 3.0.</span></span>  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-wmi-provider"></a><span data-ttu-id="9cb64-114">Wmi サービスの破損によって WMI プロバイダーのインストールがブロックされる</span><span class="sxs-lookup"><span data-stu-id="9cb64-114">WMI Service Corruption Blocks Installation of the WMI provider</span></span>

 <span data-ttu-id="9cb64-115">.NET Framework 3.0 パッケージをインストールすると、WMI サービスの破損によって Windows Communication Foundation WMI プロバイダーのインストールがブロックされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9cb64-115">WMI Service Corruption may block the installation of the Windows Communication Foundation WMI provider when installing the .NET Framework 3.0 package.</span></span> <span data-ttu-id="9cb64-116">インストール中に、Windows Communication Foundation インストーラーは、 *mofcomp.exe* コンポーネントを使用して、WCF *.mof* ファイルを登録できません。</span><span class="sxs-lookup"><span data-stu-id="9cb64-116">During installation, the Windows Communication Foundation installer is unable to register the WCF *.mof* file using the *mofcomp.exe* component.</span></span> <span data-ttu-id="9cb64-117">発生する現象を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9cb64-117">The following is a list of symptoms:</span></span>  
  
1. <span data-ttu-id="9cb64-118">.NET Framework 3.0 のインストールは正常に完了するのに、WCF WMI プロバイダーが登録されない。</span><span class="sxs-lookup"><span data-stu-id="9cb64-118">.NET Framework 3.0 installation completes successfully, but the WCF WMI provider is not registered.</span></span>  
  
2. <span data-ttu-id="9cb64-119">アプリケーション イベント ログに、WCF の WMI プロバイダーの登録、または mofcomp.exe の実行に関する問題を示すエラー イベントが表示される。</span><span class="sxs-lookup"><span data-stu-id="9cb64-119">An error event appears in the application event log that references problems registering the WMI provider for WCF, or running mofcomp.exe.</span></span>  
  
3. <span data-ttu-id="9cb64-120">ユーザーの %temp% ディレクトリの dd_wcf_retCA\* という名前のセットアップ ログ ファイルに、WCF WMI プロバイダーの登録に失敗したことが示される。</span><span class="sxs-lookup"><span data-stu-id="9cb64-120">The setup log file named dd_wcf_retCA\* in the user's %temp% directory contains references to failure to register the WCF WMI provider.</span></span>  
  
4. <span data-ttu-id="9cb64-121">イベント ログまたはセットアップ トレース ログ ファイルに、次の例外のいずれかが記録される。</span><span class="sxs-lookup"><span data-stu-id="9cb64-121">An exception such as one the following may be listed in the event log or setup trace log file:</span></span>  
  
     <span data-ttu-id="9cb64-122">ServiceModelReg [11:09:59:046]: System.ApplicationException : "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof" で E:\WINDOWS\system32\wbem\mofcomp.exe を実行している間に予期しない結果 3 が発生しました</span><span class="sxs-lookup"><span data-stu-id="9cb64-122">ServiceModelReg [11:09:59:046]: System.ApplicationException: Unexpected result 3 executing E:\WINDOWS\system32\wbem\mofcomp.exe with "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof"</span></span>  
  
     <span data-ttu-id="9cb64-123">または</span><span class="sxs-lookup"><span data-stu-id="9cb64-123">or:</span></span>  
  
     <span data-ttu-id="9cb64-124">ServiceModelReg [07:19:33:843]: System.TypeInitializationException : 'System.Management.ManagementPath' の型初期化子が例外をスローしました。</span><span class="sxs-lookup"><span data-stu-id="9cb64-124">ServiceModelReg [07:19:33:843]: System.TypeInitializationException: The type initializer for 'System.Management.ManagementPath' threw an exception.</span></span> <span data-ttu-id="9cb64-125">---> InteropServices (0x80040154 が): 次のエラーにより、CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} のコンポーネントの COM クラスファクトリを取得できませんでした: 80040154。</span><span class="sxs-lookup"><span data-stu-id="9cb64-125">---> System.Runtime.InteropServices.COMException (0x80040154): Retrieving the COM class factory for component with CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} failed due to the following error: 80040154.</span></span>  
  
     <span data-ttu-id="9cb64-126">または</span><span class="sxs-lookup"><span data-stu-id="9cb64-126">or:</span></span>  
  
     <span data-ttu-id="9cb64-127">ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException : ファイルまたはアセンブリ 'C:\WINDOWS\system32\wbem\mofcomp.exe'、またはその依存関係の 1 つが読み込めませんでした。</span><span class="sxs-lookup"><span data-stu-id="9cb64-127">ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: Could not load file or assembly 'C:\WINDOWS\system32\wbem\mofcomp.exe' or one of its dependencies.</span></span> <span data-ttu-id="9cb64-128">指定されたファイルが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="9cb64-128">The system cannot find the file specified.</span></span>  
  
     <span data-ttu-id="9cb64-129">ファイル名 : C:\WINDOWS\system32\wbem\mofcomp.exe</span><span class="sxs-lookup"><span data-stu-id="9cb64-129">File name: 'C:\WINDOWS\system32\wbem\mofcomp.exe</span></span>  
  
 <span data-ttu-id="9cb64-130">上で説明した問題を解決するためには、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cb64-130">The following steps must be followed to resolve the problem described previously.</span></span>  
  
1. <span data-ttu-id="9cb64-131">WMI Diagnosis Utility を実行して、WMI サービスを修復します。</span><span class="sxs-lookup"><span data-stu-id="9cb64-131">Run the WMI Diagnosis Utility to repair the WMI service.</span></span> <span data-ttu-id="9cb64-132">このツールの使用方法の詳細については、「 [WMI Diagnosis Utility](/previous-versions/tn-archive/ff404265(v%3dmsdn.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9cb64-132">For more information about using this tool, see [WMI Diagnosis Utility](/previous-versions/tn-archive/ff404265(v%3dmsdn.10)).</span></span>  
  
 <span data-ttu-id="9cb64-133">**コントロールパネル** にある [**プログラムの追加と削除**] アプレットを使用して .NET Framework 3.0 インストールを修復するか、.NET Framework 3.0 をアンインストールまたは再インストールします。</span><span class="sxs-lookup"><span data-stu-id="9cb64-133">Repair the .NET Framework 3.0 installation by using the **Add/Remove Programs** applet located in **Control Panel**, or uninstall/reinstall the .NET Framework 3.0.</span></span>  
  
## <a name="repair-net-framework-30-after-net-framework-35-installation"></a><span data-ttu-id="9cb64-134">3.5 のインストール .NET Framework 後に .NET Framework 3.0 を修復する</span><span class="sxs-lookup"><span data-stu-id="9cb64-134">Repair .NET Framework 3.0 after .NET Framework 3.5 Installation</span></span>

 <span data-ttu-id="9cb64-135">.NET Framework 3.5 をインストールした後に .NET Framework 3.0 の修復を実行すると、 *machine.config* で .NET Framework 3.5 によって導入された構成要素が削除されます。</span><span class="sxs-lookup"><span data-stu-id="9cb64-135">If you do a repair of .NET Framework 3.0 after you installed .NET Framework 3.5, configuration elements introduced by .NET Framework 3.5 in *machine.config* are removed.</span></span> <span data-ttu-id="9cb64-136">ただし、 *web.config* ファイルはそのまま残ります。</span><span class="sxs-lookup"><span data-stu-id="9cb64-136">However, the *web.config* file remains intact.</span></span> <span data-ttu-id="9cb64-137">この回避策としては、ARP を使用して .NET Framework 3.5 を修復するか、またはスイッチで [ワークフローサービス登録ツール (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) を使用し `/c` ます。</span><span class="sxs-lookup"><span data-stu-id="9cb64-137">The workaround is to repair .NET Framework 3.5 after this via ARP, or use the [WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) with the `/c` switch.</span></span>  
  
 <span data-ttu-id="9cb64-138">[ワークフローサービス登録ツール (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) については、microsoft.net \framework\v3.5\ または%windir%\Microsoft.NET\framework64\v3.5\ を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9cb64-138">[WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) can be found at %windir%\Microsoft.NET\framework\v3.5\ or %windir%\Microsoft.NET\framework64\v3.5\</span></span>  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a><span data-ttu-id="9cb64-139">.NET Framework 3.5 のインストール後に WCF/WF Webhost に対して IIS を適切に構成する</span><span class="sxs-lookup"><span data-stu-id="9cb64-139">Configure IIS Properly for WCF/WF Webhost after Installing .NET Framework 3.5</span></span>  

 <span data-ttu-id="9cb64-140">.NET Framework 3.5 インストールで WCF 関連の追加の IIS 構成設定の構成に失敗した場合、インストールログにエラーが記録されて続行されます。</span><span class="sxs-lookup"><span data-stu-id="9cb64-140">When .NET Framework 3.5 installation fails to configure additional WCF-related IIS configuration settings, it logs an error in the installation log and continues.</span></span> <span data-ttu-id="9cb64-141">WorkflowServices アプリケーションを実行しようとしても、必要な構成設定がないため、実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="9cb64-141">Any attempt to run WorkflowServices applications will fail, since the required configuration settings are missing.</span></span> <span data-ttu-id="9cb64-142">たとえば、xoml やルール サービスの読み込みに失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9cb64-142">For example, loading xoml or rules service can fail.</span></span>  
  
 <span data-ttu-id="9cb64-143">この問題を回避するには、 [ワークフローサービス登録ツール (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) とスイッチを使用して、 `/c` コンピューター上で IIS スクリプトマップを適切に構成します。</span><span class="sxs-lookup"><span data-stu-id="9cb64-143">To workaround this problem, use the [WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) with the `/c` switch to properly configure IIS script maps on the machine.</span></span> <span data-ttu-id="9cb64-144">[ワークフローサービス登録ツール (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) については、microsoft.net \framework\v3.5\ または%windir%\Microsoft.NET\framework64\v3.5\ を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9cb64-144">[WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) can be found at %windir%\Microsoft.NET\framework\v3.5\ or %windir%\Microsoft.NET\framework64\v3.5\</span></span>  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule"></a><span data-ttu-id="9cb64-145">型 ' HttpModule ' を読み込めませんでした</span><span class="sxs-lookup"><span data-stu-id="9cb64-145">Could not load type 'System.ServiceModel.Activation.HttpModule'</span></span>

<span data-ttu-id="9cb64-146">**アセンブリ ' System.servicemodel, Version 3.0.0.0, Culture = ニュートラル, PublicKeyToken = b77a5c561934e089 ' から型 ' HttpModule ' を読み込めませんでした**</span><span class="sxs-lookup"><span data-stu-id="9cb64-146">**Could not load type 'System.ServiceModel.Activation.HttpModule' from assembly 'System.ServiceModel, Version 3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'**</span></span>

 <span data-ttu-id="9cb64-147">このエラーは .NET Framework 4 がインストールされ、WCF HTTP アクティブ化が有効になっている場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="9cb64-147">This error occurs if .NET Framework 4 is installed and then WCF HTTP Activation is enabled.</span></span> <span data-ttu-id="9cb64-148">この問題を解決するには、Visual Studio の開発者コマンドプロンプト内から次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9cb64-148">To resolve the issue, run the following command from inside the Developer Command Prompt for Visual Studio:</span></span>  
  
```console
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a><span data-ttu-id="9cb64-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="9cb64-149">See also</span></span>

- [<span data-ttu-id="9cb64-150">セットアップ手順</span><span class="sxs-lookup"><span data-stu-id="9cb64-150">Set-Up Instructions</span></span>](./samples/set-up-instructions.md)
