---
description: 詳細については、「構成を使用しない AJAX サービス」を参照してください。
title: 構成を使用しない AJAX サービス
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: 137f0845f042d1919c1cb070c91a473ff81863cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779037"
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="7894b-103">構成を使用しない AJAX サービス</span><span class="sxs-lookup"><span data-stu-id="7894b-103">AJAX Service Without Configuration</span></span>

<span data-ttu-id="7894b-104">このサンプルでは、Windows Communication Foundation (WCF) を使用して、構成設定を使用せずに、基本的な ASP.NET 非同期 JavaScript and XML (AJAX) サービス (Web ブラウザークライアントから JavaScript コードを使用してアクセスできるサービス) を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7894b-104">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="7894b-105">このサービスは .svc ファイルの特殊な構文を使用して AJAX エンドポイントを自動的に有効にします。</span><span class="sxs-lookup"><span data-stu-id="7894b-105">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>

<span data-ttu-id="7894b-106">WCF での AJAX サポートは、コントロールを介して ASP.NET AJAX で使用できるように最適化されてい `ScriptManager` ます。</span><span class="sxs-lookup"><span data-stu-id="7894b-106">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="7894b-107">ASP.NET AJAX で WCF を使用する例については、 [ajax のサンプル](ajax.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7894b-107">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](ajax.md).</span></span>

> [!NOTE]
> <span data-ttu-id="7894b-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7894b-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="7894b-109">このサンプルは、HTTP POST を使用した AJAX サービスに基づいています。</span><span class="sxs-lookup"><span data-stu-id="7894b-109">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="7894b-110">「 [基本的な AJAX サービス](basic-ajax-service.md) のサンプル」で説明されているように、を使用して <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> サービスをホストします。</span><span class="sxs-lookup"><span data-stu-id="7894b-110">As described in the [Basic AJAX Service](basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>

```text
<%ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"
%>
```

<span data-ttu-id="7894b-111"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> は、<xref:System.ServiceModel.Description.WebScriptEndpoint> をサービスに自動的に追加します。</span><span class="sxs-lookup"><span data-stu-id="7894b-111"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="7894b-112">エンドポイントに対する構成変更が不要な場合、`<system.ServiceModel>` セクションはサービスの Web.config ファイルから完全に削除できます。</span><span class="sxs-lookup"><span data-stu-id="7894b-112">If no configuration changes need to be made to the endpoint, the `<system.ServiceModel>` section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="7894b-113">Web.config ファイルには、ConfigFreeClientPage.aspx で使用される ASP.NET 設定がいくつか含まれます。</span><span class="sxs-lookup"><span data-stu-id="7894b-113">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="7894b-114">そうでない場合は、Web.config ファイル全体を削除できます。</span><span class="sxs-lookup"><span data-stu-id="7894b-114">If that were not the case, the entire Web.config file could be removed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7894b-115">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="7894b-115">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7894b-116">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7894b-116">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="7894b-117">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="7894b-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7894b-118">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="7894b-118">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7894b-119">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="7894b-119">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="7894b-120">Windows Communication Foundation のサンプルについては、 [1 回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)に従ってセットアップ手順を実行してください。</span><span class="sxs-lookup"><span data-stu-id="7894b-120">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="7894b-121">「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の説明に従って、ソリューション ConfigFreeAjaxService をビルドします。</span><span class="sxs-lookup"><span data-stu-id="7894b-121">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="7894b-122">に移動 `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` します (プロジェクトディレクトリ内からブラウザーで configfreeclientpage.aspx を開かないでください)。</span><span class="sxs-lookup"><span data-stu-id="7894b-122">Navigate to `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>

> [!NOTE]
> <span data-ttu-id="7894b-123">このサンプルを実行する場合、IIS の ServiceModelSamples フォルダーで匿名認証と Windows 認証が同時に有効になっていないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7894b-123">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="7894b-124">有効になっている場合は、Windows 認証を無効にしてください。</span><span class="sxs-lookup"><span data-stu-id="7894b-124">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="7894b-125">サンプルの実行が終了したら、Windows 認証を有効にし、"iisreset" を実行します。</span><span class="sxs-lookup"><span data-stu-id="7894b-125">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>

## <a name="see-also"></a><span data-ttu-id="7894b-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="7894b-126">See also</span></span>

- [<span data-ttu-id="7894b-127">基本的な AJAX サービス</span><span class="sxs-lookup"><span data-stu-id="7894b-127">Basic AJAX Service</span></span>](basic-ajax-service.md)
