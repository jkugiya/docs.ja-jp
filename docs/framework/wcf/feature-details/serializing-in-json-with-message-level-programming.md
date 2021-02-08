---
description: 詳細については、「メッセージレベルのプログラミングによる Json でのシリアル化」を参照してください。
title: メッセージ レベルのプログラミングによる JSON 形式でのシリアル化
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: 715e44b0e2137197f5883e2327288555513f29cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793546"
---
# <a name="serializing-in-json-with-message-level-programming"></a><span data-ttu-id="e4d76-103">メッセージ レベルのプログラミングによる JSON 形式でのシリアル化</span><span class="sxs-lookup"><span data-stu-id="e4d76-103">Serializing in Json with Message Level Programming</span></span>

<span data-ttu-id="e4d76-104">WCF は、JSON 形式でのデータのシリアル化をサポートします。</span><span class="sxs-lookup"><span data-stu-id="e4d76-104">WCF supports serializing data in JSON format.</span></span> <span data-ttu-id="e4d76-105">このトピックでは、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> を使用して型をシリアル化することを WCF に命令する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e4d76-105">This topic describes how to tell WCF to serialize your types using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="typed-message-programming"></a><span data-ttu-id="e4d76-106">型指定されたメッセージのプログラミング</span><span class="sxs-lookup"><span data-stu-id="e4d76-106">Typed Message Programming</span></span>  

 <span data-ttu-id="e4d76-107"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> は、<xref:System.ServiceModel.Web.WebGetAttribute> または <xref:System.ServiceModel.Web.WebInvokeAttribute> がサービス操作に適用されるときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="e4d76-107">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is used when the <xref:System.ServiceModel.Web.WebGetAttribute> or the <xref:System.ServiceModel.Web.WebInvokeAttribute> is applied to a service operation.</span></span> <span data-ttu-id="e4d76-108">どちらの属性でも、`RequestFormat` と `ResponseFormat` を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e4d76-108">Both of these attributes allow you to specify the `RequestFormat` and `ResponseFormat`.</span></span> <span data-ttu-id="e4d76-109">要求と応答に JSON を使用する場合。</span><span class="sxs-lookup"><span data-stu-id="e4d76-109">To use JSON for requests and responses.</span></span> <span data-ttu-id="e4d76-110">両方をに設定 `WebMessageFormat.Json` します。</span><span class="sxs-lookup"><span data-stu-id="e4d76-110">set both of these to `WebMessageFormat.Json`.</span></span>  <span data-ttu-id="e4d76-111">JSON を使用するには、を使用する必要があります。これにより、が <xref:System.ServiceModel.WebHttpBinding> 自動的に構成され <xref:System.ServiceModel.Description.WebHttpBehavior> ます。</span><span class="sxs-lookup"><span data-stu-id="e4d76-111">In order to use JSON, you must use the <xref:System.ServiceModel.WebHttpBinding>, which automatically configures the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span> <span data-ttu-id="e4d76-112">WCF シリアル化の詳細については、「 [シリアル化と逆シリアル](serialization-and-deserialization.md)化」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4d76-112">For more information about WCF serialization, see [Serialization and Deserialization](serialization-and-deserialization.md).</span></span> <span data-ttu-id="e4d76-113">JSON と WCF の詳細については、「 [サービスステーション-wcf を使用した RESTful サービスの概要](/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4d76-113">For more information about JSON and WCF, see [Service Station - An Introduction To RESTful Services With WCF](/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e4d76-114">JSON を使用するには、SOAP 通信をサポートしていない <xref:System.ServiceModel.WebHttpBinding> と <xref:System.ServiceModel.Description.WebHttpBehavior> を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4d76-114">Using JSON requires use of <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior> which do not support SOAP communication.</span></span> <span data-ttu-id="e4d76-115">と通信するサービスは、 <xref:System.ServiceModel.WebHttpBinding> サービスメタデータの公開をサポートしていないため、クライアント側プロキシを生成するために Visual Studio のサービス参照の追加機能または svcutil.exe コマンドラインツールを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="e4d76-115">Services that communicate with the <xref:System.ServiceModel.WebHttpBinding> do not support exposing service metadata so you will not be able to use Visual Studio’s Add Service Reference functionality or the svcutil command-line tool to generate a client-side proxy.</span></span> <span data-ttu-id="e4d76-116">を使用するサービスをプログラムで呼び出す方法の詳細につい <xref:System.ServiceModel.WebHttpBinding> ては、「 [WCF で REST サービスを使用する方法](/archive/blogs/pedram/how-to-consume-rest-services-with-wcf)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4d76-116">For more information how you can programmatically call services that use <xref:System.ServiceModel.WebHttpBinding>, see [How to Consume REST Services with WCF](/archive/blogs/pedram/how-to-consume-rest-services-with-wcf).</span></span>  
  
## <a name="untyped-message-programming"></a><span data-ttu-id="e4d76-117">型指定されていないメッセージのプログラミング</span><span class="sxs-lookup"><span data-stu-id="e4d76-117">Untyped Message Programming</span></span>  

 <span data-ttu-id="e4d76-118">型指定されていないメッセージ オブジェクトを直接操作する場合は、型指定されていないメッセージのプロパティを明示的に設定して JSON としてシリアル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4d76-118">When working directly with untyped Message objects, you must explicitly set the properties on the untyped message to serialize it as JSON.</span></span> <span data-ttu-id="e4d76-119">これを行う方法を次のコード スニペットに示します。</span><span class="sxs-lookup"><span data-stu-id="e4d76-119">The following code snippet shows how to do this.</span></span>  
  
```csharp
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4d76-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="e4d76-120">See also</span></span>

- [<span data-ttu-id="e4d76-121">AJAX の統合と JSON のサポート</span><span class="sxs-lookup"><span data-stu-id="e4d76-121">AJAX Integration and JSON Support</span></span>](ajax-integration-and-json-support.md)
- [<span data-ttu-id="e4d76-122">スタンドアロン JSON のシリアル化</span><span class="sxs-lookup"><span data-stu-id="e4d76-122">Stand-Alone JSON Serialization</span></span>](stand-alone-json-serialization.md)
- [<span data-ttu-id="e4d76-123">JSON のシリアル化</span><span class="sxs-lookup"><span data-stu-id="e4d76-123">JSON Serialization</span></span>](../samples/json-serialization.md)
