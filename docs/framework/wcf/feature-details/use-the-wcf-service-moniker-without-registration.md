---
description: '詳細については、「方法: 登録せずに Windows Communication Foundation サービスモニカーを使用する」を参照してください。'
title: '方法: 未登録で Windows Communication Foundation のサービス モニカーを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: ed3ea221bc32c4334f609b6740fa10bb63cb2830
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632387"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a><span data-ttu-id="b0797-103">方法: 未登録で Windows Communication Foundation のサービス モニカーを使用する</span><span class="sxs-lookup"><span data-stu-id="b0797-103">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>

<span data-ttu-id="b0797-104">Windows Communication Foundation (WCF) サービスに接続して通信するには、WCF クライアントアプリケーションに、サービスアドレス、バインディング構成、およびサービスコントラクトの詳細が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0797-104">To connect to and communicate with a Windows Communication Foundation (WCF) service, a WCF client application must have the details of the service address, the binding configuration, and the service contract.</span></span>  
  
 <span data-ttu-id="b0797-105">通常、WCF サービスモニカーは、必要な属性の種類を事前に登録して、必要なコントラクトを取得しますが、これが不可能な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="b0797-105">The WCF service moniker typically obtains the required contract through prior registration of the required attribute types, but there might be cases where this is not feasible.</span></span> <span data-ttu-id="b0797-106">登録の代わりに、モニカーは、`wsdl` パラメーターまたは Metadata Exchange を使用し、`mexAddress` パラメーターを使用することによって、WSDL (Web Services Definition Language) ドキュメントの形でコントラクトの定義を取得できます。</span><span class="sxs-lookup"><span data-stu-id="b0797-106">In place of registration, the moniker can obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document, through the use of the `wsdl` parameter or through Metadata Exchange, through the use of the `mexAddress` parameter.</span></span>  
  
 <span data-ttu-id="b0797-107">これによって、セルの値の一部が Web サービスとの対話によって計算される Excel ワークシートの配布などのシナリオが可能になります。</span><span class="sxs-lookup"><span data-stu-id="b0797-107">This enables scenarios such as the distribution of an Excel spreadsheet where some of the cell values are calculated through Web service interactions.</span></span> <span data-ttu-id="b0797-108">このシナリオでは、ドキュメントを開く可能性があるすべてのクライアントにサービス コントラクト アセンブリを登録することが実現できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b0797-108">In this scenario, it might not be feasible to register the service contract assembly on all clients that might open the document.</span></span> <span data-ttu-id="b0797-109">`wsdl` パラメーターまたは `mexAddress` パラメーターによって、自己完結型のソリューションが可能になります。</span><span class="sxs-lookup"><span data-stu-id="b0797-109">The `wsdl` parameter or the `mexAddress` parameter enables a self-contained solution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b0797-110">要求と応答の改ざんまたはなりすましを防止するために、相互認証を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0797-110">Mutual authentication must be used to protect against request and response tampering or spoofing.</span></span> <span data-ttu-id="b0797-111">具体的には、応答している Metadata Exchange エンドポイントが目的の信頼されたパーティであることがクライアントに対して保証されることが重要です。</span><span class="sxs-lookup"><span data-stu-id="b0797-111">Specifically, it is important for clients to be assured that the Metadata Exchange endpoint that is responding is the intended trusted party.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0797-112">例</span><span class="sxs-lookup"><span data-stu-id="b0797-112">Example</span></span>  

 <span data-ttu-id="b0797-113">MEX コントラクトと共にサービス モニカーを使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b0797-113">This example shows the use of the service moniker with a MEX contract.</span></span> <span data-ttu-id="b0797-114">次のコントラクトが設定されたサービスは、wsHttpBinding で公開されます。</span><span class="sxs-lookup"><span data-stu-id="b0797-114">A service with the following contract is exposed with a wsHttpBinding.</span></span>  
  
```csharp
using System.ServiceModel;  
  
// ...
  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Demo")]  
public interface IAffiliate  
{  
    [OperationContract]  
    bool NewAffiliate(string ID, string company, string fullname, string accountsCode);  
    [OperationContract]  
    bool RemoveAffiliate(string ID);  
    [OperationContract]  
    double RevenueCheckMonthly(ref string ID);  
    [OperationContract]  
    double RevenueCheckTotal(ref string ID);  
}  
```  
  
 <span data-ttu-id="b0797-115">リモートサービス用の WCF クライアントを構築するには、次のモニカー文字列の例を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b0797-115">To construct a WCF client for the remote service the following example moniker string can be used.</span></span>  
  
```
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 <span data-ttu-id="b0797-116">クライアント アプリケーションの実行中に、クライアントは、指定された `WS-MetadataExchange` で `mexAddress` を実行します。</span><span class="sxs-lookup"><span data-stu-id="b0797-116">During the execution of the client application, the client performs a `WS-MetadataExchange` with the provided `mexAddress`.</span></span> <span data-ttu-id="b0797-117">これによって、複数のサービスのアドレス、バインディング、およびコントラクトの詳細が返される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b0797-117">This might return the address, binding and contract details for a number of services.</span></span> <span data-ttu-id="b0797-118">`address`、`contract`、`contractNamespace`、`binding`、および `bindingNamespace` の各パラメーターは、目的のサービスを識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b0797-118">The `address`, `contract`, `contractNamespace`, `binding` and `bindingNamespace` parameters are used to identify the intended service.</span></span> <span data-ttu-id="b0797-119">これらのパラメーターが一致すると、モニカーは適切なコントラクト定義を使用して WCF クライアントを構築します。その後、型指定されたコントラクトと同様に、WCF クライアントを使用して呼び出しを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b0797-119">Once those parameters have been matched, the moniker constructs a WCF client with the appropriate contract definition and calls can then be made using the WCF client, as with the typed contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b0797-120">モニカーの形式が正しくないか、サービスを使用できない場合は、`GetObject` を呼び出すと、"構文が無効です" というエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="b0797-120">If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error saying "Invalid Syntax".</span></span> <span data-ttu-id="b0797-121">このエラーが発生した場合は、使用しているモニカーが正しく、サービスが使用可能であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b0797-121">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0797-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0797-122">See also</span></span>

- [<span data-ttu-id="b0797-123">方法: サービス モニカーを登録および構成する</span><span class="sxs-lookup"><span data-stu-id="b0797-123">How to: Register and Configure a Service Moniker</span></span>](how-to-register-and-configure-a-service-moniker.md)
