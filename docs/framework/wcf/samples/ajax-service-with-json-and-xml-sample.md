---
description: '詳細情報: JSON と XML を使用した AJAX サービスのサンプル'
title: JSON および XML 形式の AJAX サービスのサンプル
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: e47f6cbd7e4659488325e158e5594ca94322c520
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779063"
---
# <a name="ajax-service-with-json-and-xml-sample"></a><span data-ttu-id="27aae-103">JSON および XML 形式の AJAX サービスのサンプル</span><span class="sxs-lookup"><span data-stu-id="27aae-103">AJAX Service with JSON and XML Sample</span></span>

<span data-ttu-id="27aae-104">このサンプルでは、Windows Communication Foundation (WCF) を使用して、JavaScript Object Notation (JSON) データまたは XML データを返す非同期 JavaScript and XML (AJAX) サービスを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="27aae-104">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an Asynchronous JavaScript and XML (AJAX) service that returns either JavaScript Object Notation (JSON) or XML data.</span></span> <span data-ttu-id="27aae-105">AJAX サービスには、Web ブラウザー クライアントから JavaScript コードを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="27aae-105">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="27aae-106">このサンプルは、 [基本的な AJAX サービス](basic-ajax-service.md) のサンプルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="27aae-106">This sample builds on the [Basic AJAX Service](basic-ajax-service.md) sample.</span></span>

<span data-ttu-id="27aae-107">他の AJAX サンプルとは異なり、このサンプルでは ASP.NET AJAX および <xref:System.Web.UI.ScriptManager> コントロールを使用しません。</span><span class="sxs-lookup"><span data-stu-id="27aae-107">Unlike the other AJAX samples, this sample does not use ASP.NET AJAX and the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="27aae-108">いくつかの追加構成では、JavaScript を通じて任意の HTML ページから WCF AJAX サービスにアクセスできます。このシナリオを次に示します。</span><span class="sxs-lookup"><span data-stu-id="27aae-108">With some additional configuration, WCF AJAX services can be accessed from any HTML page through JavaScript, and this scenario is shown here.</span></span> <span data-ttu-id="27aae-109">ASP.NET AJAX で WCF を使用する例については、「 [ajax のサンプル](ajax.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27aae-109">For an example of using WCF with ASP.NET AJAX, see [AJAX Samples](ajax.md).</span></span>

<span data-ttu-id="27aae-110">このサンプルでは、JSON と XML 間で操作の応答のタイプを切り替える方法を示します。</span><span class="sxs-lookup"><span data-stu-id="27aae-110">This sample shows how to switch the response type of an operation between JSON and XML.</span></span> <span data-ttu-id="27aae-111">この機能は、サービスが ASP.NET AJAX または HTML/JavaScript クライアント ページでアクセスできるように構成されているかどうかにかかわらず使用できます。</span><span class="sxs-lookup"><span data-stu-id="27aae-111">This functionality is available regardless of whether the service is configured to be accessed by ASP.NET AJAX or by an HTML/JavaScript client page.</span></span>

> [!NOTE]
> <span data-ttu-id="27aae-112">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27aae-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="27aae-113">ASP.NET AJAX 以外のクライアントを使用するには、.svc ファイルで <xref:System.ServiceModel.Activation.WebServiceHostFactory> (<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ではありません) を使用します。</span><span class="sxs-lookup"><span data-stu-id="27aae-113">To enable the use of non-ASP.NET AJAX clients, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (not <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) in the .svc file.</span></span> <span data-ttu-id="27aae-114"><xref:System.ServiceModel.Activation.WebServiceHostFactory> によって、<xref:System.ServiceModel.Description.WebHttpEndpoint> 標準エンドポイントがサービスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="27aae-114"><xref:System.ServiceModel.Activation.WebServiceHostFactory> adds a <xref:System.ServiceModel.Description.WebHttpEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="27aae-115">エンドポイントは、.svc ファイルを基準とした空のアドレスで構成されます。これは、サービスのアドレスが `http://localhost/ServiceModelSamples/service.svc` で、操作名以外の追加のサフィックスがないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="27aae-115">The endpoint is configured at an empty address relative to the .svc file; this means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>`

<span data-ttu-id="27aae-116">Web.config 内の次のセクションを使用して、エンドポイントに対する構成変更を追加できます。</span><span class="sxs-lookup"><span data-stu-id="27aae-116">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="27aae-117">追加の変更が不要な場合は、このセクションを削除できます。</span><span class="sxs-lookup"><span data-stu-id="27aae-117">It can be removed if no extra changes are needed.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <!-- Use this element to configure the endpoint -->
      <standardEndpoint name="" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="27aae-118">の既定のデータ形式 <xref:System.ServiceModel.Description.WebHttpEndpoint> は XML ですが、の既定のデータ形式は <xref:System.ServiceModel.Description.WebScriptEndpoint> JSON です。</span><span class="sxs-lookup"><span data-stu-id="27aae-118">The default data format for <xref:System.ServiceModel.Description.WebHttpEndpoint> is XML, while the default data format for <xref:System.ServiceModel.Description.WebScriptEndpoint> is JSON.</span></span> <span data-ttu-id="27aae-119">詳細については、「 [ASP.NET を使用せずに WCF AJAX サービスを作成する](../feature-details/creating-wcf-ajax-services-without-aspnet.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27aae-119">For more information, see [Creating WCF AJAX Services without ASP.NET](../feature-details/creating-wcf-ajax-services-without-aspnet.md).</span></span>

<span data-ttu-id="27aae-120">次のサンプルのサービスは、2つの操作を持つ標準の WCF サービスです。</span><span class="sxs-lookup"><span data-stu-id="27aae-120">The service in the following sample is a standard WCF service with two operations.</span></span> <span data-ttu-id="27aae-121">どちらの操作でも <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> または <xref:System.ServiceModel.Web.WebGetAttribute> 属性に <xref:System.ServiceModel.Web.WebInvokeAttribute> の本文スタイルが必要です。この本文スタイルは、`webHttp` 動作に固有で、JSON/XML データ形式の切り替えに影響しません。</span><span class="sxs-lookup"><span data-stu-id="27aae-121">Both operations require the <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body style on the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes, which is specific to the `webHttp` behavior and has no bearing on the JSON/XML data format switch.</span></span>

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathXml(double n1, double n2);
```

<span data-ttu-id="27aae-122">操作の応答形式は XML として指定されます。これは、動作の既定の設定です [\<webHttp>](../../configure-apps/file-schema/wcf/webhttp.md) 。</span><span class="sxs-lookup"><span data-stu-id="27aae-122">The response format for the operation is specified as XML, which is the default setting for the [\<webHttp>](../../configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="27aae-123">ただし、応答形式を明示的に指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="27aae-123">However, it is good practice explicitly specify the response format.</span></span>

<span data-ttu-id="27aae-124">その他の操作では `WebInvokeAttribute` 属性を使用し、応答に XML ではなく JSON を明示的に指定します。</span><span class="sxs-lookup"><span data-stu-id="27aae-124">The other operation uses the `WebInvokeAttribute` attribute and explicitly specifies JSON instead of XML for the response.</span></span>

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathJson(double n1, double n2);
```

<span data-ttu-id="27aae-125">どちらの場合も、操作は、 `MathResult` 標準の WCF データコントラクト型である複合型を返します。</span><span class="sxs-lookup"><span data-stu-id="27aae-125">Note that in both cases the operations return a complex type, `MathResult`, which is a standard WCF data contract type.</span></span>

<span data-ttu-id="27aae-126">クライアント Web ページ XmlAjaxClientPage.htm には、ユーザーが [ **計算の実行] (JSON を返す)** または [ **計算の実行] (XML を返す)** ボタンをクリックしたときに、上記の2つの操作のいずれかを呼び出す JavaScript コードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="27aae-126">The client Web page XmlAjaxClientPage.htm contains JavaScript code that invokes one of the preceding two operations when the user clicks the **Perform calculation (return JSON)** or **Perform calculation (return XML)** buttons on the page.</span></span> <span data-ttu-id="27aae-127">サービスを呼び出すコードによって JSON 本文が作成され、HTTP POST を使用して送信されます。</span><span class="sxs-lookup"><span data-stu-id="27aae-127">The code to invoke the service constructs a JSON body and sends it using HTTP POST.</span></span> <span data-ttu-id="27aae-128">[基本的な Ajax サービス](basic-ajax-service.md)サンプルと ASP.NET ajax を使用したその他のサンプルとは異なり、要求は JavaScript で手動で作成されます。</span><span class="sxs-lookup"><span data-stu-id="27aae-128">The request is created manually in JavaScript, unlike the [Basic AJAX Service](basic-ajax-service.md) sample and the other samples using ASP.NET AJAX.</span></span>

```csharp
// Create HTTP request
var xmlHttp;
// Request instantiation code omitted…
// Result handler code omitted…

// Build the operation URL
var url = "service.svc/ajaxEndpoint/";
url = url + operation;

// Build the body of the JSON message
var body = '{"n1":';
body = body + document.getElementById("num1").value + ',"n2":';
body = body + document.getElementById("num2").value + '}';

// Send the HTTP request
xmlHttp.open("POST", url, true);
xmlHttp.setRequestHeader("Content-type", "application/json");
xmlHttp.send(body);
```

<span data-ttu-id="27aae-129">サービスが応答すると、応答はこれ以上の処理を行わずにページ上のテキスト ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="27aae-129">When the service responds, the response is displayed without any further processing in a textbox on the page.</span></span> <span data-ttu-id="27aae-130">これは、使用される XML および JSON データ形式を直接確認できるように、デモンストレーションの目的で実装されています。</span><span class="sxs-lookup"><span data-stu-id="27aae-130">This is implemented for demonstration purposes to allow you to directly observe the XML and JSON data formats used.</span></span>

```javascript
// Create result handler
xmlHttp.onreadystatechange=function(){
     if(xmlHttp.readyState == 4){
          document.getElementById("result").value = xmlHttp.responseText;
     }
}
```

> [!IMPORTANT]
> <span data-ttu-id="27aae-131">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="27aae-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="27aae-132">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="27aae-132">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="27aae-133">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="27aae-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="27aae-134">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="27aae-134">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="27aae-135">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="27aae-135">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="27aae-136">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="27aae-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="27aae-137">「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の説明に従って、ソリューション XmlAjaxService をビルドします。</span><span class="sxs-lookup"><span data-stu-id="27aae-137">Build the solution XmlAjaxService.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="27aae-138">に移動 `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` します (プロジェクトディレクトリからブラウザーで XmlAjaxClientPage.htm を開かないでください)。</span><span class="sxs-lookup"><span data-stu-id="27aae-138">Navigate to `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (do not open XmlAjaxClientPage.htm in the browser from the project directory).</span></span>

## <a name="see-also"></a><span data-ttu-id="27aae-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="27aae-139">See also</span></span>

- [<span data-ttu-id="27aae-140">HTTP POST を使用する AJAX サービス</span><span class="sxs-lookup"><span data-stu-id="27aae-140">AJAX Service Using HTTP POST</span></span>](ajax-service-using-http-post.md)
