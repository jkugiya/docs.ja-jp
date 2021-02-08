---
description: '詳細情報: 複合型を使用した AJAX サービスのサンプル'
title: 複合型を使用した AJAX サービスのサンプル
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: 438bceb91f10f5ba91d02272d2ba266a50a05f82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779128"
---
# <a name="ajax-service-using-complex-types-sample"></a><span data-ttu-id="1cb14-103">複合型を使用した AJAX サービスのサンプル</span><span class="sxs-lookup"><span data-stu-id="1cb14-103">AJAX Service Using Complex Types Sample</span></span>

<span data-ttu-id="1cb14-104">このサンプルでは、Windows Communication Foundation (WCF) を使用して、複合型のインスタンスを作成し、それらをサービスとクライアントの間で JavaScript Object Notation (JSON) として送信する、ASP.NET の非同期 JavaScript and XML (AJAX) サービスを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1cb14-104">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that creates instances of complex types and sends them between service and client as JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="1cb14-105">AJAX サービスには、Web ブラウザー クライアントから JavaScript コードを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1cb14-105">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="1cb14-106">このサンプルは、 [基本的な AJAX サービス](basic-ajax-service.md) のサンプルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="1cb14-106">This sample builds on the [Basic AJAX Service](basic-ajax-service.md) sample.</span></span>

<span data-ttu-id="1cb14-107">WCF での AJAX サポートは、コントロールを介して ASP.NET AJAX で使用できるように最適化されてい <xref:System.Web.UI.ScriptManager> ます。</span><span class="sxs-lookup"><span data-stu-id="1cb14-107">AJAX support in WCF is optimized for use with ASP.NET AJAX through the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="1cb14-108">ASP.NET AJAX で WCF を使用する例については、 [ajax のサンプル](ajax.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1cb14-108">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>

> [!NOTE]
> <span data-ttu-id="1cb14-109">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1cb14-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="1cb14-110">次のサンプルのサービスは、AJAX 固有のコードを持たない WCF サービスです。</span><span class="sxs-lookup"><span data-stu-id="1cb14-110">The service in the following sample is a WCF service with no AJAX-specific code.</span></span> <span data-ttu-id="1cb14-111"><xref:System.ServiceModel.Web.WebGetAttribute> 属性は適用されないため、既定の HTTP 動詞 ("POST") が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1cb14-111">Because the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="1cb14-112">サービスには 1 つの `DoMath` 操作があります。この操作は、`MathResult` という名前の複合型を返します。</span><span class="sxs-lookup"><span data-stu-id="1cb14-112">The service has one operation, `DoMath`, which returns a complex type named `MathResult`.</span></span> <span data-ttu-id="1cb14-113">複合型は標準のデータ コントラクト型で、AJAX 固有のコードも含まれていません。</span><span class="sxs-lookup"><span data-stu-id="1cb14-113">The complex type is a standard data contract type, which also contains no AJAX-specific code.</span></span>

```csharp
[DataContract]
public class MathResult
{
    [DataMember]
    public double sum;
    [DataMember]
    public double difference;
    [DataMember]
    public double product;
    [DataMember]
    public double quotient;
}
```

<span data-ttu-id="1cb14-114">基本的な AJAX サービスのサンプルの場合と同様に、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> を使用してサービスに AJAX エンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="1cb14-114">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>

<span data-ttu-id="1cb14-115">クライアント Web ページ Complextypeclientpage.aspx には、ユーザーがページの [ **計算の実行** ] ボタンをクリックしたときにサービスを呼び出すための ASP.NET と JavaScript のコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1cb14-115">The client Web page ComplexTypeClientPage.aspx contains ASP.NET and JavaScript code to invoke the service when the user clicks the **Perform calculation** button on the page.</span></span> <span data-ttu-id="1cb14-116">サービスを呼び出すコードは、 [HTTP post サンプルを使用する AJAX サービス](ajax-service-using-http-post.md) と同様に、JSON 本文を構築し、http post を使用して送信します。</span><span class="sxs-lookup"><span data-stu-id="1cb14-116">The code to invoke the service constructs a JSON body and sends it using HTTP POST, similar to the [AJAX Service Using HTTP POST](ajax-service-using-http-post.md) sample.</span></span>

<span data-ttu-id="1cb14-117">サービス呼び出しに成功したら、生成された JavaScript オブジェクトのそれぞれのデータ メンバー (`sum`、`difference`、`product`、および `quotient`) にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1cb14-117">After the service call succeeds, you can access the individual data members (`sum`, `difference`, `product` and `quotient`) on the resulting JavaScript object.</span></span>

```javascript
function onSuccess(mathResult){
     document.getElementById("sum").value = mathResult.sum;
     document.getElementById("difference").value = mathResult.difference;
     document.getElementById("product").value = mathResult.product;
     document.getElementById("quotient").value = mathResult.quotient;
}
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1cb14-118">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="1cb14-118">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="1cb14-119">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="1cb14-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="1cb14-120">「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の説明に従って、ソリューション ComplexTypeAjaxService をビルドします。</span><span class="sxs-lookup"><span data-stu-id="1cb14-120">Build the solution ComplexTypeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="1cb14-121">に移動 `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` します (プロジェクトディレクトリからブラウザーで complextypeclientpage.aspx を開かないでください)。</span><span class="sxs-lookup"><span data-stu-id="1cb14-121">Navigate to `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (do not open ComplexTypeClientPage.aspx in the browser from the project directory).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1cb14-122">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="1cb14-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1cb14-123">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1cb14-123">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="1cb14-124">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="1cb14-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1cb14-125">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1cb14-125">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`

## <a name="see-also"></a><span data-ttu-id="1cb14-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="1cb14-126">See also</span></span>

- [<span data-ttu-id="1cb14-127">基本的な AJAX サービス</span><span class="sxs-lookup"><span data-stu-id="1cb14-127">Basic AJAX Service</span></span>](basic-ajax-service.md)
