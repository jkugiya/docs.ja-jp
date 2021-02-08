---
description: 詳細については、「WCF Web HTTP エラー処理」を参照してください。
title: WCF Web HTTP エラー処理
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: 88483c249bc1b6b866517ca10b348c0885fc34fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779480"
---
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="bec2c-103">WCF Web HTTP エラー処理</span><span class="sxs-lookup"><span data-stu-id="bec2c-103">WCF Web HTTP Error Handling</span></span>

<span data-ttu-id="bec2c-104">Windows Communication Foundation (WCF) Web HTTP エラー処理を使用すると、HTTP 状態コードを指定し、操作と同じ形式 (XML、JSON など) を使用してエラーの詳細を返す WCF Web HTTP サービスからエラーを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="bec2c-104">Windows Communication Foundation (WCF) Web HTTP error handling enables you to return errors from WCF Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="bec2c-105">WCF Web HTTP エラー処理</span><span class="sxs-lookup"><span data-stu-id="bec2c-105">WCF Web HTTP Error Handling</span></span>  

 <span data-ttu-id="bec2c-106"><xref:System.ServiceModel.Web.WebFaultException> クラスは、HTTP 状態コードを指定できるようにするコンストラクターを定義します。</span><span class="sxs-lookup"><span data-stu-id="bec2c-106">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="bec2c-107">この状態コードは、クライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="bec2c-107">This status code is then returned to the client.</span></span> <span data-ttu-id="bec2c-108"><xref:System.ServiceModel.Web.WebFaultException> クラスのジェネリック バージョンである <xref:System.ServiceModel.Web.WebFaultException%601> を使用すると、発生したエラーに関する情報を格納しているユーザー定義型を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="bec2c-108">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="bec2c-109">このカスタム オブジェクトは、操作で定義された形式を使用してシリアル化され、クライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="bec2c-109">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="bec2c-110">次の例は、HTTP 状態コードを返す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="bec2c-110">The following example shows how to return an HTTP status code.</span></span>  
  
```csharp
public string Operation1()
{
    // Operation logic  
   // ...
   throw new WebFaultException(HttpStatusCode.Forbidden);
}  
```  
  
 <span data-ttu-id="bec2c-111">次の例は、HTTP 状態コードおよび追加情報をユーザー定義型で返す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="bec2c-111">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> <span data-ttu-id="bec2c-112">`MyErrorDetail` は、発生したエラーに関する追加情報を格納しているユーザー定義型です。</span><span class="sxs-lookup"><span data-stu-id="bec2c-112">`MyErrorDetail` is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
```csharp
public string Operation2()
{
   // Operation logic  
   // ...
   MyErrorDetail detail = new MyErrorDetail()
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="bec2c-113">このコードは、禁止されている状態コード、および `MyErrorDetails` オブジェクトのインスタンスを格納している本文と共に、HTTP 応答を返します。</span><span class="sxs-lookup"><span data-stu-id="bec2c-113">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="bec2c-114">`MyErrorDetails` オブジェクトの形式は、次の値によって決まります。</span><span class="sxs-lookup"><span data-stu-id="bec2c-114">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
- <span data-ttu-id="bec2c-115">サービス操作で指定された `ResponseFormat` 属性または <xref:System.ServiceModel.Web.WebGetAttribute> 属性の <xref:System.ServiceModel.Web.WebInvokeAttribute> パラメーターの値。</span><span class="sxs-lookup"><span data-stu-id="bec2c-115">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
- <span data-ttu-id="bec2c-116"><xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> の値。</span><span class="sxs-lookup"><span data-stu-id="bec2c-116">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
- <span data-ttu-id="bec2c-117"><xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> プロパティの値 (<xref:System.ServiceModel.Web.OutgoingWebResponseContext> にアクセスして取得)。</span><span class="sxs-lookup"><span data-stu-id="bec2c-117">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 <span data-ttu-id="bec2c-118">これらの値が操作の書式設定に与える影響の詳細については、「 [WCF WEB HTTP 書式設定](wcf-web-http-formatting.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bec2c-118">For more information about how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](wcf-web-http-formatting.md).</span></span>  
  
 <span data-ttu-id="bec2c-119"><xref:System.ServiceModel.Web.WebFaultException> は <xref:System.ServiceModel.FaultException> であるため、SOAP エンドポイントと Web HTTP エンドポイントを公開するサービスのエラー例外プログラミング モデルとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="bec2c-119"><xref:System.ServiceModel.Web.WebFaultException> is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bec2c-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="bec2c-120">See also</span></span>

- [<span data-ttu-id="bec2c-121">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="bec2c-121">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="bec2c-122">WCF Web HTTP 形式</span><span class="sxs-lookup"><span data-stu-id="bec2c-122">WCF Web HTTP Formatting</span></span>](wcf-web-http-formatting.md)
- [<span data-ttu-id="bec2c-123">エラーの定義と指定</span><span class="sxs-lookup"><span data-stu-id="bec2c-123">Defining and Specifying Faults</span></span>](../defining-and-specifying-faults.md)
- [<span data-ttu-id="bec2c-124">例外とエラーの処理</span><span class="sxs-lookup"><span data-stu-id="bec2c-124">Handling Exceptions and Faults</span></span>](../extending/handling-exceptions-and-faults.md)
- [<span data-ttu-id="bec2c-125">エラーの送受信</span><span class="sxs-lookup"><span data-stu-id="bec2c-125">Sending and Receiving Faults</span></span>](../sending-and-receiving-faults.md)
