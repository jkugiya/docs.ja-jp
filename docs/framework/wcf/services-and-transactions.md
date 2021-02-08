---
description: 詳細については、「サービスとトランザクション」を参照してください。
title: サービスとトランザクション
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 4126ca139bd2097aeaaff756de694d0ff0061b5d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792974"
---
# <a name="services-and-transactions"></a><span data-ttu-id="b23b1-103">サービスとトランザクション</span><span class="sxs-lookup"><span data-stu-id="b23b1-103">Services and Transactions</span></span>

<span data-ttu-id="b23b1-104">Windows Communication Foundation (WCF) アプリケーションは、クライアント内からトランザクションを開始し、サービス操作内でトランザクションを調整できます。</span><span class="sxs-lookup"><span data-stu-id="b23b1-104">Windows Communication Foundation (WCF) applications can initiate a transaction from within a client and coordinate the transaction within the service operation.</span></span> <span data-ttu-id="b23b1-105">クライアントはトランザクションを開始し、複数のサービス操作を呼び出す可能性があります。サービス操作が、1 つの単位としてコミットまたはロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="b23b1-105">Clients can initiate a transaction and invoke several service operations and ensure that the service operations are either committed or rolled back as a single unit.</span></span>  
  
 <span data-ttu-id="b23b1-106">サービス コントラクトでトランザクション動作を有効にするには、<xref:System.ServiceModel.ServiceBehaviorAttribute> を指定し、クライアント トランザクションを必要とするサービス操作について <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> プロパティと <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="b23b1-106">You can enable the transaction behavior in the service contract by specifying a <xref:System.ServiceModel.ServiceBehaviorAttribute> and setting its <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> properties for service operations that require client transactions.</span></span> <span data-ttu-id="b23b1-107"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> パラメーターは、未処理の例外がスローされなかった場合に、メソッドが実行されているトランザクションが自動的に完了されるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b23b1-107">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parameter specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="b23b1-108">これらの属性の詳細については、「 [ServiceModel トランザクション属性](./feature-details/servicemodel-transaction-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b23b1-108">For more information about these attributes, see [ServiceModel Transaction Attributes](./feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
 <span data-ttu-id="b23b1-109">データベース更新の記録など、サービス操作で実行され、リソース マネージャーで管理される作業は、クライアント トランザクションの一部です。</span><span class="sxs-lookup"><span data-stu-id="b23b1-109">The work that is performed in the service operations and managed by a resource manager, such as logging database updates, is part of the client’s transaction.</span></span>  
  
 <span data-ttu-id="b23b1-110"><xref:System.ServiceModel.ServiceBehaviorAttribute> 属性と <xref:System.ServiceModel.OperationBehaviorAttribute> 属性を使用して、サービス側のトランザクション動作を制御する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="b23b1-110">The following sample demonstrates usage of the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes to control service-side transaction behavior.</span></span>  
  
```csharp
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService: ICalculatorLog  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                           TransactionAutoComplete = true)]  
    public double Add(double n1, double n2)  
    {  
        recordToLog($"Added {n1} to {n2}");
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                               TransactionAutoComplete = true)]  
    public double Subtract(double n1, double n2)  
    {  
        recordToLog($"Subtracted {n1} from {n2}");
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                       TransactionAutoComplete = true)]  
    public double Multiply(double n1, double n2)  
    {  
        recordToLog($"Multiplied {n1} by {n2}");
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                       TransactionAutoComplete = true)]  
    public double Divide(double n1, double n2)  
    {  
        recordToLog($"Divided {n1} by {n2}", n1, n2);
        return n1 / n2;  
    }  
  
}  
```  
  
 <span data-ttu-id="b23b1-111">[\<transactionFlow>](../configure-apps/file-schema/wcf/transactionflow.md) `true` 次のサンプル構成に示すように、WS-AtomicTransaction プロトコルを使用するようにクライアントとサービスのバインドを構成し、要素をに設定することにより、トランザクションとトランザクションフローを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="b23b1-111">You can enable transactions and transaction flow by configuring the client and service bindings to use the WS-AtomicTransaction protocol, and setting the [\<transactionFlow>](../configure-apps/file-schema/wcf/transactionflow.md) element to `true`, as shown in the following sample configuration.</span></span>  
  
```xml  
<client>  
    <endpoint address="net.tcp://localhost/ServiceModelSamples/service"
          binding="netTcpBinding"
          bindingConfiguration="netTcpBindingWSAT"
          contract="Microsoft.ServiceModel.Samples.ICalculatorLog" />  
</client>  
  
<bindings>  
    <netTcpBinding>  
        <binding name="netTcpBindingWSAT"  
                transactionFlow="true"  
                transactionProtocol="WSAtomicTransactionOctober2004" />  
     </netTcpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="b23b1-112">クライアントは、<xref:System.Transactions.TransactionScope> を作成し、トランザクションのスコープ内でサービス操作を呼び出すことにより、トランザクションを開始できます。</span><span class="sxs-lookup"><span data-stu-id="b23b1-112">Clients can begin a transaction by creating a <xref:System.Transactions.TransactionScope> and invoking service operations within the scope of the transaction.</span></span>  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b23b1-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b23b1-113">See also</span></span>

- [<span data-ttu-id="b23b1-114">System.ServiceModel でのトランザクション サポート</span><span class="sxs-lookup"><span data-stu-id="b23b1-114">Transactional Support in System.ServiceModel</span></span>](./feature-details/transactional-support-in-system-servicemodel.md)
- [<span data-ttu-id="b23b1-115">トランザクション モデル</span><span class="sxs-lookup"><span data-stu-id="b23b1-115">Transaction Models</span></span>](./feature-details/transaction-models.md)
- [<span data-ttu-id="b23b1-116">WS トランザクション フロー</span><span class="sxs-lookup"><span data-stu-id="b23b1-116">WS Transaction Flow</span></span>](./samples/ws-transaction-flow.md)
