---
description: 詳細については、「エンタープライズサービスのトランザクションコンポーネントの統合」を参照してください。
title: エンタープライズ サービスのトランザクション コンポーネントの統合
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 67b3a58900d2842c304d76ff6dd1325e961d8394
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802828"
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="350ef-103">エンタープライズ サービスのトランザクション コンポーネントの統合</span><span class="sxs-lookup"><span data-stu-id="350ef-103">Integrating Enterprise Services Transactional Components</span></span>

<span data-ttu-id="350ef-104">Windows Communication Foundation (WCF) は、エンタープライズサービスと統合するための自動メカニズムを提供します (「 [COM + アプリケーションとの統合](integrating-with-com-plus-applications.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="350ef-104">Windows Communication Foundation (WCF) provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="350ef-105">ただし、柔軟性を高めるために、エンタープライズ サービス内でホストされるトランザクション コンポーネントを内部的に使用するサービスを開発する場合があります。</span><span class="sxs-lookup"><span data-stu-id="350ef-105">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="350ef-106">WCF トランザクション機能はインフラストラクチャ上に構築されているため <xref:System.Transactions> 、Enterprise services と wcf を統合するプロセスは、エンタープライズサービス <xref:System.Transactions> [と com + トランザクションとの相互運用性](/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85))に関する説明にあるとおり、エンタープライズサービス間の相互運用性を指定するためのものと同じです。</span><span class="sxs-lookup"><span data-stu-id="350ef-106">Because the WCF Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with WCF is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).</span></span>  
  
 <span data-ttu-id="350ef-107">フローされる受信トランザクションと COM+ コンテキスト トランザクションの間に必要なレベルの相互運用性を提供するには、サービス実装で <xref:System.Transactions.TransactionScope> インスタンスを作成し、<xref:System.Transactions.EnterpriseServicesInteropOption> 列挙型の適切な値を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="350ef-107">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="350ef-108">エンタープライズ サービスとサービス操作の統合</span><span class="sxs-lookup"><span data-stu-id="350ef-108">Integrating Enterprise Services with a Service Operation</span></span>  

 <span data-ttu-id="350ef-109">Allowed トランザクション フローで、<xref:System.Transactions.TransactionScope> オプションを指定して <xref:System.Transactions.EnterpriseServicesInteropOption.Full> を作成する操作を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="350ef-109">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="350ef-110">このシナリオでは次の条件が適用されます。</span><span class="sxs-lookup"><span data-stu-id="350ef-110">The following conditions apply in this scenario:</span></span>  
  
- <span data-ttu-id="350ef-111">クライアントがトランザクションをフローする場合、エンタープライズ サービス コンポーネント呼び出しを含む操作は、トランザクションのスコープ内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="350ef-111">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="350ef-112"><xref:System.Transactions.EnterpriseServicesInteropOption.Full> を使用すると、トランザクションが <xref:System.EnterpriseServices> コンテキストと同期することが保証されます。つまり、<xref:System.Transactions> のアンビエント トランザクションと <xref:System.EnterpriseServices> とが同じになります。</span><span class="sxs-lookup"><span data-stu-id="350ef-112">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
- <span data-ttu-id="350ef-113">クライアントがトランザクションをフローしない場合、<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> を `true` に設定すると操作の新しいトランザクション スコープが作成されます。</span><span class="sxs-lookup"><span data-stu-id="350ef-113">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="350ef-114">同様に、<xref:System.Transactions.EnterpriseServicesInteropOption.Full> を使用すると、操作のトランザクションが <xref:System.EnterpriseServices> コンポーネントのコンテキスト内で使用されるトランザクションと同じになることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="350ef-114">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="350ef-115">任意の追加のメソッド呼び出しも、同じ操作のトランザクションのスコープ内で行われます。</span><span class="sxs-lookup"><span data-stu-id="350ef-115">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
```csharp
[ServiceContract()]  
public interface ICustomerServiceContract  
{  
   [OperationContract]  
   [TransactionFlow(TransactionFlowOption.Allowed)]  
   void UpdateCustomerNameOperation(int customerID, string newCustomerName);  
}  
  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CustomerService : ICustomerServiceContract  
{  
   [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
   public void UpdateCustomerNameOperation(int customerID, string newCustomerName)  
   {  
   // Create a transaction scope with full ES interop  
      using (TransactionScope ts = new TransactionScope(  
                     TransactionScopeOption.Required,  
                     new TransactionOptions(),  
                     EnterpriseServicesInteropOption.Full))  
      {  
         // Create an Enterprise Services component  
         // Call UpdateCustomer method on an Enterprise Services
         // component
  
         // Call UpdateOtherCustomerData method on an Enterprise
         // Services component
         ts.Complete();  
      }  
  
      // Do UpdateAdditionalData on an non-Enterprise Services  
      // component  
   }  
}  
```  
  
 <span data-ttu-id="350ef-116">操作の現在のトランザクションと、エンタープライズ サービスのトランザクション コンポーネント呼び出しとの間の同期が不要な場合は、<xref:System.Transactions.TransactionScope> インスタンスのインスタンス化時に <xref:System.Transactions.EnterpriseServicesInteropOption.None> オプションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="350ef-116">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="350ef-117">エンタープライズ サービスとクライアントの統合</span><span class="sxs-lookup"><span data-stu-id="350ef-117">Integrating Enterprise Services with a Client</span></span>  

 <span data-ttu-id="350ef-118"><xref:System.Transactions.TransactionScope> を設定した <xref:System.Transactions.EnterpriseServicesInteropOption.Full> インスタンスを使用するクライアント コードを次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="350ef-118">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="350ef-119">このシナリオでは、トランザクション フローをサポートするサービス操作の呼び出しが、エンタープライズ サービス コンポーネントへの呼び出しと同じトランザクションのスコープ内で発生します。</span><span class="sxs-lookup"><span data-stu-id="350ef-119">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
```csharp
static void Main()  
{  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
  
    // Create a transaction scope with full ES interop  
    using (TransactionScope ts = new TransactionScope(  
          TransactionScopeOption.Required,  
          new TransactionOptions(),  
          EnterpriseServicesInteropOption.Full))  
    {  
        // Call Add calculator service operation  
  
        // Create an Enterprise Services component  
  
        // Call UpdateCustomer method on an Enterprise Services
        // component
  
        ts.Complete();  
    }  
  
    // Closing the client gracefully closes the connection and
    // cleans up resources  
    client.Close();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="350ef-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="350ef-120">See also</span></span>

- [<span data-ttu-id="350ef-121">COM + アプリケーションとの統合</span><span class="sxs-lookup"><span data-stu-id="350ef-121">Integrating with COM+ Applications</span></span>](integrating-with-com-plus-applications.md)
- [<span data-ttu-id="350ef-122">COM アプリケーションとの統合</span><span class="sxs-lookup"><span data-stu-id="350ef-122">Integrating with COM Applications</span></span>](integrating-with-com-applications.md)
