---
description: '詳細情報: Windows Communication Foundation の導入の予測: 将来の移行の簡略化'
title: Windows Communication Foundation 導入の準備:将来の移行の簡略化
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 6ea81b1dd01ed45ff62fa50c1b17442f88fc05af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643814"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="989d8-103">Windows Communication Foundation 導入の準備:将来の移行の簡略化</span><span class="sxs-lookup"><span data-stu-id="989d8-103">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>

<span data-ttu-id="989d8-104">新しい ASP.NET アプリケーションを WCF に簡単に移行できるようにするには、前述の推奨事項に加えて、次の推奨事項に従ってください。</span><span class="sxs-lookup"><span data-stu-id="989d8-104">To ensure an easier future migration of new ASP.NET applications to WCF, follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="989d8-105">プロトコル</span><span class="sxs-lookup"><span data-stu-id="989d8-105">Protocols</span></span>  

 <span data-ttu-id="989d8-106">ASP.NET 2.0 の SOAP 1.2 サポートを無効にします。</span><span class="sxs-lookup"><span data-stu-id="989d8-106">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
```xml  
<configuration>  
     <system.web>  
      <webServices >  
          <protocols>  
           <remove name="HttpSoap12"/>  
          </protocols>
      </webServices>  
     </system.web>
</configuration>  
```  
  
 <span data-ttu-id="989d8-107">WCF では、SOAP 1.1 や SOAP 1.2 などのさまざまなプロトコルに準拠したメッセージをさまざまなエンドポイントを使用して処理する必要があるため、この方法をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="989d8-107">Doing so is advisable because WCF requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="989d8-108">ASP.NET 2.0 Web サービスが、既定の構成である SOAP 1.1 と SOAP 1.2 の両方をサポートするように構成されている場合は、すべての ASP.NET Web サービスの既存のクライアントと確実に互換性があるように、元のアドレスで単一の WCF エンドポイントに移行することはできません。</span><span class="sxs-lookup"><span data-stu-id="989d8-108">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single WCF endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="989d8-109">また、SOAP 1.1 ではなく 1.2 を選択すると、サービスの利用者がさらに厳しく制限されます。</span><span class="sxs-lookup"><span data-stu-id="989d8-109">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="989d8-110">サービスの開発</span><span class="sxs-lookup"><span data-stu-id="989d8-110">Service Development</span></span>  

 <span data-ttu-id="989d8-111">WCF では、を <xref:System.ServiceModel.ServiceContractAttribute> インターフェイスまたはクラスのいずれかに適用することで、サービスコントラクトを定義できます。</span><span class="sxs-lookup"><span data-stu-id="989d8-111">WCF allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="989d8-112">この属性は、クラスではなくインターフェイスに適用することをお勧めします。これにより、任意の数のクラスでさまざまに実装できるコントラクト定義が作成されます。</span><span class="sxs-lookup"><span data-stu-id="989d8-112">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="989d8-113">ASP.NET 2.0 では、<xref:System.Web.Services.WebService> 属性をクラスだけでなくインターフェイスに適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="989d8-113">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="989d8-114">ただし、既に説明したように ASP.NET 2.0 には不具合があり、<xref:System.Web.Services.WebService> 属性をクラスではなくインターフェイスに適用した場合、この属性の名前空間パラメーターが有効化されません。</span><span class="sxs-lookup"><span data-stu-id="989d8-114">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="989d8-115">通常は、サービスの名前空間を既定値から変更することをお勧めします。これは、 `http://tempuri.org` 属性の namespace パラメーターを使用して、 <xref:System.Web.Services.WebService> <xref:System.ServiceModel.ServiceContractAttribute> インターフェイスまたはクラスのいずれかに属性を適用することによって、ASP.NET Web サービスの定義を続ける必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="989d8-115">Since it is generally advisable to modify the namespace of a service from the default value, `http://tempuri.org`, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
- <span data-ttu-id="989d8-116">これらのインターフェイスを定義するメソッドに含めるコードは、できるだけ少なくします。</span><span class="sxs-lookup"><span data-stu-id="989d8-116">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="989d8-117">これらのメソッドの作業を他のクラスに委任します。</span><span class="sxs-lookup"><span data-stu-id="989d8-117">Have them delegate their work to other classes.</span></span> <span data-ttu-id="989d8-118">新しい WCF サービスの種類では、そのようなクラスに対して、そのような作業を委任することもできます。</span><span class="sxs-lookup"><span data-stu-id="989d8-118">New WCF service types could then also delegate their substantive work to those classes.</span></span>  
  
- <span data-ttu-id="989d8-119">`MessageName` の <xref:System.Web.Services.WebMethodAttribute> パラメーターを使用して、サービスの動作の明示的な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="989d8-119">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="989d8-120">ASP.NET での操作の既定の名前は、WCF によって提供される既定の名前とは異なるため、この操作は重要です。</span><span class="sxs-lookup"><span data-stu-id="989d8-120">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by WCF.</span></span> <span data-ttu-id="989d8-121">明示的な名前を指定することで、既定の名前への依存を避けることができます。</span><span class="sxs-lookup"><span data-stu-id="989d8-121">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
- <span data-ttu-id="989d8-122">ASP.NET Web サービス操作をポリモーフィックなメソッドで実装しないでください。 WCF では、ポリモーフィックなメソッドを使用した操作の実装はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="989d8-122">Do not implement ASP.NET Web service operations with polymorphic methods, because WCF does not support implementing operations with polymorphic methods.</span></span>  
  
- <span data-ttu-id="989d8-123"><xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> を使用して、HTTP 要求をメソッドにルーティングする SOAPAction HTTP ヘッダーの明示的な値を指定します。</span><span class="sxs-lookup"><span data-stu-id="989d8-123">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="989d8-124">このアプローチを採用すると、ASP.NET と WCF で使用される既定の SOAPAction 値に依存しなくても済むようになります。</span><span class="sxs-lookup"><span data-stu-id="989d8-124">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and WCF being the same.</span></span>  
  
- <span data-ttu-id="989d8-125">SOAP 拡張機能は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="989d8-125">Avoid using SOAP extensions.</span></span> <span data-ttu-id="989d8-126">SOAP 拡張機能が必要な場合は、その目的が WCF によって既に提供されている機能であるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="989d8-126">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by WCF.</span></span> <span data-ttu-id="989d8-127">そのような場合は、WCF をすぐに導入しないことを再検討してください。</span><span class="sxs-lookup"><span data-stu-id="989d8-127">If that is indeed the case, then reconsider the choice to not adopt WCF right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="989d8-128">状態管理</span><span class="sxs-lookup"><span data-stu-id="989d8-128">State Management</span></span>  

 <span data-ttu-id="989d8-129">サービスで状態を維持する必要がないようにします。</span><span class="sxs-lookup"><span data-stu-id="989d8-129">Avoid having to maintain state in services.</span></span> <span data-ttu-id="989d8-130">状態を維持することは、アプリケーションのスケーラビリティを損なう傾向があるだけでなく、ASP.NET と WCF の状態管理メカニズムは大きく異なりますが、WCF では ASP.NET 互換モードの ASP.NET メカニズムがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="989d8-130">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and WCF are very different, although WCF does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="989d8-131">例外処理</span><span class="sxs-lookup"><span data-stu-id="989d8-131">Exception Handling</span></span>  

 <span data-ttu-id="989d8-132">サービスで送受信するデータ型の構造を設計するときは、クライアントに伝達する必要があり、サービス内で発生する可能性のあるさまざまな種類の例外を表現する構造も設計します。</span><span class="sxs-lookup"><span data-stu-id="989d8-132">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
```csharp  
[Serializable]  
[XmlRoot(Namespace="ExplicitNamespace", IsNullable=true)]  
public partial class AnticipatedException
{
    private string anticipatedExceptionInformationField;  

    public string AnticipatedExceptionInformation
    {  
        get {
            return this.anticipatedExceptionInformationField;  
        }  
        set {  
            this.anticipatedExceptionInformationField = value;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="989d8-133">これらのクラスには、自分自身を XML にシリアル化する機能を与えます。</span><span class="sxs-lookup"><span data-stu-id="989d8-133">Give such classes the ability to serialize themselves to XML:</span></span>  
  
```csharp  
public XmlNode ToXML()  
{  
     XmlSerializer serializer = new XmlSerializer(  
      typeof(AnticipatedException));  
     MemoryStream memoryStream = new MemoryStream();  
     XmlTextWriter writer = new XmlTextWriter(  
     memoryStream, UnicodeEncoding.UTF8);  
     serializer.Serialize(writer, this);  
     XmlDocument document = new XmlDocument();  
     document.LoadXml(new string(  
     UnicodeEncoding.UTF8.GetChars(  
     memoryStream.GetBuffer())).Trim());  
    return document.DocumentElement;  
}  
```  
  
 <span data-ttu-id="989d8-134">これでこのクラスを使用して、明示的にスローされた <xref:System.Web.Services.Protocols.SoapException> インスタンスの詳細を指定できます。</span><span class="sxs-lookup"><span data-stu-id="989d8-134">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="989d8-135">これらの例外クラスは、WCF クラスを使用して簡単に再利用でき、 <xref:System.ServiceModel.FaultException%601> 新しいをスローします。 `FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="989d8-135">These exception classes will be readily reusable with the WCF <xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="989d8-136">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="989d8-136">Security</span></span>  

 <span data-ttu-id="989d8-137">セキュリティに関する推奨事項を次にいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="989d8-137">The following are some security recommendations.</span></span>  
  
- <span data-ttu-id="989d8-138">ASP.NET 2.0 プロファイルは使用しないでください。これを使用すると、サービスが WCF に移行された場合に ASP.NET 統合モードの使用が制限されます。</span><span class="sxs-lookup"><span data-stu-id="989d8-138">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to WCF.</span></span>  
  
- <span data-ttu-id="989d8-139">サービスへのアクセスを制御するために Acl を使用しないでください。 ASP.NET Web サービスはインターネットインフォメーションサービス (IIS) を使用して Acl をサポートしています。 ASP.NET Web サービスはホスト用の IIS に依存しているため、WCF は必ずしも IIS でホストされている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="989d8-139">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), WCF does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
- <span data-ttu-id="989d8-140">サービスのリソースへのアクセスを承認するには、ASP.NET 2.0 ロール プロバイダーの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="989d8-140">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="989d8-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="989d8-141">See also</span></span>

- [<span data-ttu-id="989d8-142">Windows Communication Foundation 導入の準備:将来的な統合の容易化</span><span class="sxs-lookup"><span data-stu-id="989d8-142">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](anticipating-adopting-the-wcf-easing-future-integration.md)
