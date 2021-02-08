---
description: 詳細については、「HTTP POST を使用した AJAX サービス」を参照してください。
title: HTTP POST を使用する AJAX サービス
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: 4d319d4120310d79af5bda6026a2192d1270943b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779102"
---
# <a name="ajax-service-using-http-post"></a><span data-ttu-id="e79de-103">HTTP POST を使用する AJAX サービス</span><span class="sxs-lookup"><span data-stu-id="e79de-103">AJAX Service Using HTTP POST</span></span>

<span data-ttu-id="e79de-104">このサンプルでは、Windows Communication Foundation (WCF) を使用して、HTTP POST を使用する AJAX (ASP.NET 非同期 JavaScript and XML) サービスを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e79de-104">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that uses HTTP POST.</span></span> <span data-ttu-id="e79de-105">AJAX サービスには、Web ブラウザー クライアントから基本的な JavaScript コードを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e79de-105">An AJAX service is one that you can access by using basic JavaScript code from a Web browser client.</span></span> <span data-ttu-id="e79de-106">このサンプルは、 [基本的な AJAX サービス](basic-ajax-service.md) のサンプルに基づいています。2つのサンプルの唯一の違いは、http GET の代わりに HTTP POST を使用することです。</span><span class="sxs-lookup"><span data-stu-id="e79de-106">This sample builds on the [Basic AJAX Service](basic-ajax-service.md) sample; the only difference between the two samples is the use of HTTP POST instead of HTTP GET.</span></span>

<span data-ttu-id="e79de-107">Windows Communication Foundation (WCF) での AJAX サポートは、コントロールを介して ASP.NET AJAX で使用できるように最適化されてい `ScriptManager` ます。</span><span class="sxs-lookup"><span data-stu-id="e79de-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="e79de-108">ASP.NET AJAX で WCF を使用する例については、 [ajax のサンプル](ajax-service-using-http-post.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e79de-108">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](ajax-service-using-http-post.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e79de-109">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e79de-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="e79de-110">次のサンプルのサービスは、AJAX 固有のコードを持たない WCF サービスです。</span><span class="sxs-lookup"><span data-stu-id="e79de-110">The service in the following sample is a WCF service with no AJAX-specific code.</span></span>

<span data-ttu-id="e79de-111">属性が操作に適用されている場合、または属性が適用されていない場合は、 <xref:System.ServiceModel.Web.WebInvokeAttribute> <xref:System.ServiceModel.Web.WebGetAttribute> 既定の HTTP 動詞 ("POST") が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e79de-111">If the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute is applied on an operation, or the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="e79de-112">POST 要求は、GET 要求よりも作成が困難ですが、キャッシュされません。キャッシュが不適切な操作に対しては、POST 要求を使用します。</span><span class="sxs-lookup"><span data-stu-id="e79de-112">POST requests are harder to construct than GET requests, but they are not cached; use POST requests for all operations where caching is not appropriate.</span></span>

```csharp
[ServiceContract(Namespace = "PostAjaxService")]
public interface ICalculator
{
    [WebInvoke]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

<span data-ttu-id="e79de-113">基本的な AJAX サービスのサンプルの場合と同様に、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> を使用してサービスに AJAX エンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="e79de-113">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>

<span data-ttu-id="e79de-114">GET 要求とは異なり、POST サービスはブラウザーから呼び出すことができません。</span><span class="sxs-lookup"><span data-stu-id="e79de-114">Unlike GET requests, you cannot invoke POST services from the browser.</span></span> <span data-ttu-id="e79de-115">たとえば、に移動する `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` と、エラーが発生します。これは、POST サービスでは、 `n1` `n2` URL ではなく JSON 形式のメッセージ本文で、およびパラメーターが送信されることを想定しているためです。</span><span class="sxs-lookup"><span data-stu-id="e79de-115">For example, navigating to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` results in an error, because the POST service expects the `n1` and `n2` parameters to be sent in the message body in the JSON format, and not in the URL.</span></span>

<span data-ttu-id="e79de-116">クライアントの Web ページの PostAjaxClientPage.aspx には、ユーザーがページ上のいずれかの操作ボタンをクリックするとサービスを呼び出す ASP.NET コードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e79de-116">The client Web page PostAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="e79de-117">サービスは、 [基本 AJAX サービス](basic-ajax-service.md) サンプルと同じ方法で GET 要求を使用して応答します。</span><span class="sxs-lookup"><span data-stu-id="e79de-117">The service responds in the same way as in the [Basic AJAX Service](basic-ajax-service.md) sample, with the GET request.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e79de-118">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="e79de-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e79de-119">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e79de-119">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e79de-120">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="e79de-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e79de-121">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e79de-121">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e79de-122">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="e79de-122">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="e79de-123">[Windows Communication Foundation のサンプルについ](one-time-setup-procedure-for-the-wcf-samples.md)ては、セットアップ手順の1回限りのセットアップ手順を実行してください。</span><span class="sxs-lookup"><span data-stu-id="e79de-123">Ensure that you perform the setup instructions [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="e79de-124">「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の説明に従って、ソリューション postajaxservice.sln をビルドします。</span><span class="sxs-lookup"><span data-stu-id="e79de-124">Build the solution PostAjaxService.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="e79de-125">に移動 `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` します (プロジェクトディレクトリからブラウザーで postajaxclientpage.aspx を開かないでください)。</span><span class="sxs-lookup"><span data-stu-id="e79de-125">Navigate to `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (do not open PostAjaxClientPage.aspx in the browser from the project directory).</span></span>
