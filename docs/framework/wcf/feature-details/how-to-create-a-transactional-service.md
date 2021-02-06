---
description: '詳細については、「方法: トランザクションサービスを作成する」を参照してください。'
title: '方法: トランザクション サービスを作成する'
ms.date: 03/30/2017
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
ms.openlocfilehash: 78ad922a7e1f174715be7bd1a8466572425411be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643437"
---
# <a name="how-to-create-a-transactional-service"></a><span data-ttu-id="64eb0-103">方法: トランザクション サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="64eb0-103">How to: Create a Transactional Service</span></span>

<span data-ttu-id="64eb0-104">このサンプルでは、トランザクション サービスを作成する際のさまざまな側面と、サービス操作を調整するためにクライアントが起動するトランザクションの使用について説明します。</span><span class="sxs-lookup"><span data-stu-id="64eb0-104">This sample demonstrates various aspects of creating a transactional service and the use of a client-initiated transaction to coordinate service operations.</span></span>  
  
### <a name="creating-a-transactional-service"></a><span data-ttu-id="64eb0-105">トランザクション サービスの作成</span><span class="sxs-lookup"><span data-stu-id="64eb0-105">Creating a transactional service</span></span>  
  
1. <span data-ttu-id="64eb0-106">サービス コントラクトを作成し、<xref:System.ServiceModel.TransactionFlowOption> 列挙型の適切な設定を使用して操作に注釈を付け、受信トランザクションの要件を指定します。</span><span class="sxs-lookup"><span data-stu-id="64eb0-106">Create a service contract and annotate the operations with the desired setting from the <xref:System.ServiceModel.TransactionFlowOption> enumeration to specify the incoming transaction requirements.</span></span> <span data-ttu-id="64eb0-107"><xref:System.ServiceModel.TransactionFlowAttribute> は、実装するサービス クラスにも置くことができることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="64eb0-107">Note that you can also place the <xref:System.ServiceModel.TransactionFlowAttribute> on the service class being implemented.</span></span> <span data-ttu-id="64eb0-108">こうすると、これらのトランザクション設定を使用するインターフェイスを 1 回実装するだけで済むため、すべての実装で設定を行う必要がありません。</span><span class="sxs-lookup"><span data-stu-id="64eb0-108">This allows for a single implementation of an interface to use these transaction settings, instead of every implementation.</span></span>  
  
    ```csharp
    [ServiceContract]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // Use this to require an incoming transaction  
        [TransactionFlow(TransactionFlowOption.Mandatory)]  
        double Add(double n1, double n2);  
        [OperationContract]  
        // Use this to permit an incoming transaction  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        double Subtract(double n1, double n2);  
    }  
    ```  
  
2. <span data-ttu-id="64eb0-109">実装クラスを作成し、オプションとして <xref:System.ServiceModel.ServiceBehaviorAttribute> を使用して <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> および <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> を指定します。</span><span class="sxs-lookup"><span data-stu-id="64eb0-109">Create an implementation class, and use the <xref:System.ServiceModel.ServiceBehaviorAttribute> to optionally specify a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span></span> <span data-ttu-id="64eb0-110">多くの場合、<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> の既定値である 60 秒、および <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> の既定値である `Unspecified` が適切な設定値となります。</span><span class="sxs-lookup"><span data-stu-id="64eb0-110">You should note that in many cases, the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> of 60 seconds and the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> of `Unspecified` are appropriate.</span></span> <span data-ttu-id="64eb0-111">操作ごとに、<xref:System.ServiceModel.OperationBehaviorAttribute> 属性を使用して、メソッド内で実行される処理が、<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 属性の値に応じたトランザクション スコープの範囲内で行われる必要があるかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="64eb0-111">For each operation, you can use the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute to specify whether work performed within the method should occur within the scope of a transaction scope according to the value of the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> attribute.</span></span> <span data-ttu-id="64eb0-112">この場合、`Add` メソッドで使用されるトランザクションは、クライアントからフローしてくる必須の受信トランザクションと同じになり、`Subtract` メソッドで使用されるトランザクションは、受信トランザクションと同じになるか (クライアントからフローしてくる場合)、暗黙的にローカルで新たに作成されたトランザクションになります。</span><span class="sxs-lookup"><span data-stu-id="64eb0-112">In this case, the transaction used for the `Add` method is the same as the mandatory incoming transaction that is flowed from the client, and the transaction used for the `Subtract` method is either the same as the incoming transaction if one was flowed from the client, or a new implicitly and locally created transaction.</span></span>  
  
    ```csharp
    [ServiceBehavior(  
        TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
        TransactionTimeout = "00:00:45")]  
    public class CalculatorService : ICalculator  
    {  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog($"Adding {n1} to {n2}");
            return n1 + n2;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog($"Subtracting {n2} from {n1}");
            return n1 - n2;  
        }  
  
        private static void RecordToLog(string recordText)  
        {  
            // Database operations omitted for brevity  
            // This is where the transaction provides specific benefit  
            // - changes to the database will be committed only when  
            // the transaction completes.  
        }  
    }  
    ```  
  
3. <span data-ttu-id="64eb0-113">構成ファイルでバインディングを構成して、トランザクション コンテキストのフローを指定し、そのとき使用されるプロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="64eb0-113">Configure the bindings in the configuration file, specifying that the transaction context should be flowed, and the protocols to be used to do so.</span></span> <span data-ttu-id="64eb0-114">詳細については、「 [ServiceModel トランザクションの構成](servicemodel-transaction-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64eb0-114">For more information, see [ServiceModel Transaction Configuration](servicemodel-transaction-configuration.md).</span></span> <span data-ttu-id="64eb0-115">具体的には、エンドポイント要素の `binding` 属性でバインド型を指定します。</span><span class="sxs-lookup"><span data-stu-id="64eb0-115">Specifically, the binding type is specified in the endpoint element’s `binding` attribute.</span></span> <span data-ttu-id="64eb0-116">要素には [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) `bindingConfiguration` `transactionalOleTransactionsTcpBinding` 、次のサンプル構成に示すように、という名前のバインディング構成を参照する属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="64eb0-116">The [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element contains a `bindingConfiguration` attribute that references a binding configuration named `transactionalOleTransactionsTcpBinding`, as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     <span data-ttu-id="64eb0-117">次の構成で示すように、トランザクション フローは、`transactionFlow` 属性を使用して構成レベルで有効にすることができ、トランザクション プロトコルは、`transactionProtocol` 属性を使用して指定できます。</span><span class="sxs-lookup"><span data-stu-id="64eb0-117">Transaction flow is enabled at the configuration level by using the `transactionFlow` attribute, and the transaction protocol is specified using the `transactionProtocol` attribute, as shown in the following configuration.</span></span>  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a><span data-ttu-id="64eb0-118">複数のトランザクション プロトコルのサポート</span><span class="sxs-lookup"><span data-stu-id="64eb0-118">Supporting multiple transaction protocols</span></span>  
  
1. <span data-ttu-id="64eb0-119">最適なパフォーマンスを得るには、Windows Communication Foundation (WCF) を使用して記述されたクライアントとサービスに関連するシナリオには、OleTransactions プロトコルを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="64eb0-119">For optimal performance, you should use the OleTransactions protocol for scenarios involving a client and service written using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="64eb0-120">ただし、サード パーティのプロトコル スタックとの相互運用性が必要なシナリオでは、WS-AT (WS-AtomicTransaction) プロトコルが有用です。</span><span class="sxs-lookup"><span data-stu-id="64eb0-120">However, the WS-AtomicTransaction (WS-AT) protocol is useful for scenarios when interoperability with third-party protocol stacks is required.</span></span> <span data-ttu-id="64eb0-121">次のサンプル構成に示すように、適切なプロトコル固有のバインドを持つ複数のエンドポイントを提供することで、両方のプロトコルを受け入れるように WCF サービスを構成できます。</span><span class="sxs-lookup"><span data-stu-id="64eb0-121">You can configure WCF services to accept both protocols by providing multiple endpoints with appropriate protocol-specific bindings, as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="http://localhost:8000/CalcService"  
        binding="wsHttpBinding"  
        bindingConfiguration="transactionalWsatHttpBinding"  
        contract="ICalculator"  
        name="WSAtomicTransaction_endpoint" />  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     <span data-ttu-id="64eb0-122">トランザクション プロトコルは、`transactionProtocol` 属性を使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="64eb0-122">The transaction protocol is specified using the `transactionProtocol` attribute.</span></span> <span data-ttu-id="64eb0-123">ただし、このバインディングは WS-AT プロトコルのみを使用するため、この属性は、システム指定の `wsHttpBinding` には存在しません。</span><span class="sxs-lookup"><span data-stu-id="64eb0-123">However, this attribute is absent from the system-provided `wsHttpBinding`, because this binding can only use the WS-AT protocol.</span></span>  
  
    ```xml  
    <bindings>  
      <wsHttpBinding>  
        <binding name="transactionalWsatHttpBinding"  
          transactionFlow="true" />  
      </wsHttpBinding>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="controlling-the-completion-of-a-transaction"></a><span data-ttu-id="64eb0-124">トランザクションの完了の制御</span><span class="sxs-lookup"><span data-stu-id="64eb0-124">Controlling the completion of a transaction</span></span>  
  
1. <span data-ttu-id="64eb0-125">既定では、未処理の例外がスローされなかった場合、WCF 操作は自動的にトランザクションを完了します。</span><span class="sxs-lookup"><span data-stu-id="64eb0-125">By default, WCF operations automatically complete transactions if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="64eb0-126">この動作を変更するには、<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> プロパティと <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="64eb0-126">You can modify this behavior by using the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property and the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method.</span></span> <span data-ttu-id="64eb0-127">ある操作を他の操作と同じトランザクション内で行う必要がある場合 (借方と貸方の操作など)、次の <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> 操作の例に示すように、`false` プロパティを `Debit` に設定することで自動完了の動作を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="64eb0-127">When an operation is required to occur within the same transaction as another operation (for example, a debit and credit operation), you can disable the autocomplete behavior by setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` as shown in the following `Debit` operation example.</span></span> <span data-ttu-id="64eb0-128">`Debit` 操作で使用されるトランザクションは、<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> 操作に示すように `true` プロパティが `Credit1` に設定されているメソッドが呼び出されるまで、または <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> 操作に示すように、`Credit2` メソッドを呼び出してトランザクションの完了が明示的に示されるまで、完了しません。</span><span class="sxs-lookup"><span data-stu-id="64eb0-128">The transaction the `Debit` operation uses is not completed until a method with the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property set to `true` is called, as shown in the operation `Credit1`, or when the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method is called to explicitly mark the transaction as complete, as shown in the operation `Credit2`.</span></span> <span data-ttu-id="64eb0-129">2 つの貸方操作は説明のために示されています。一般には単一の貸方処理が使用されます。</span><span class="sxs-lookup"><span data-stu-id="64eb0-129">Note that the two credit operations are shown for illustration purposes, and that a single credit operation would be more typical.</span></span>  
  
    ```csharp
    [ServiceBehavior]  
    public class CalculatorService : IAccount  
    {  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = false)]  
        public void Debit(double n)  
        {  
            // Perform debit operation  
  
            return;  
        }  
  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = true)]  
        public void Credit1(double n)  
        {  
            // Perform credit operation  
  
            return;  
        }  
  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = false)]  
        public void Credit2(double n)  
        {  
            // Perform alternate credit operation  
  
            OperationContext.Current.SetTransactionComplete();  
            return;  
        }  
    }  
    ```  
  
2. <span data-ttu-id="64eb0-130">トランザクションの関連付けを行うため、<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> プロパティを `false` に設定するには、セッションの多いバインディングを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="64eb0-130">For the purposes of transaction correlation, setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` requires the use of a sessionful binding.</span></span> <span data-ttu-id="64eb0-131">この要件は、`SessionMode` の <xref:System.ServiceModel.ServiceContractAttribute> プロパティで指定します。</span><span class="sxs-lookup"><span data-stu-id="64eb0-131">This requirement is specified with the `SessionMode` property on the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span>  
  
    ```csharp
    [ServiceContract(SessionMode = SessionMode.Required)]  
    public interface IAccount  
    {  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Debit(double n);  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Credit1(double n);  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Credit2(double n);  
    }  
    ```  
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a><span data-ttu-id="64eb0-132">トランザクション サービス インスタンスの有効期間の制御</span><span class="sxs-lookup"><span data-stu-id="64eb0-132">Controlling the lifetime of a transactional service instance</span></span>  
  
1. <span data-ttu-id="64eb0-133">WCF では、プロパティを使用して、 <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> トランザクションの完了時に基になるサービスインスタンスを解放するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="64eb0-133">WCF uses the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to specify whether the underlying service instance is released when a transaction completes.</span></span> <span data-ttu-id="64eb0-134">これは既定 `true` でに設定されていないため、WCF は、効率的で予測可能な "ジャストインタイム" アクティベーション動作を実行します。</span><span class="sxs-lookup"><span data-stu-id="64eb0-134">Since this defaults to `true`, unless configured otherwise, WCF exhibits an efficient and predictable "just-in-time" activation behavior.</span></span> <span data-ttu-id="64eb0-135">後続するトランザクションでサービスを呼び出すと、前回のトランザクションの状態が残らない新規のサービス インスタンスが必ず呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="64eb0-135">Calls to a service on a subsequent transaction are assured a new service instance with no remnants of the previous transaction's state.</span></span> <span data-ttu-id="64eb0-136">これは通常は便利ですが、トランザクションの完了後もサービス インスタンス内に状態を保持する必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="64eb0-136">While this is often useful, sometimes you may want to maintain state within the service instance beyond the transaction completion.</span></span> <span data-ttu-id="64eb0-137">この例としては、必要な状態やリソースへのハンドルの取得または再構成に負荷がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="64eb0-137">Examples of this would be when required state or handles to resources are expensive to retrieve or reconstitute.</span></span> <span data-ttu-id="64eb0-138">これを実行するには、<xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> プロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="64eb0-138">You can do this by setting the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to `false`.</span></span> <span data-ttu-id="64eb0-139">このように設定することで、インスタンスとこれに関連する任意の状態が、後続する呼び出しからも利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="64eb0-139">With that setting, the instance and any associated state will be available on subsequent calls.</span></span> <span data-ttu-id="64eb0-140">この設定を使用する場合は、状態とトランザクションを消去して完了するタイミングと方法を入念に考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="64eb0-140">When using this, give careful consideration to when and how state and transactions will be cleared and completed.</span></span> <span data-ttu-id="64eb0-141">`runningTotal` 変数を使用してインスタンスを保持することで、これを行う方法を次のサンプルに示します。</span><span class="sxs-lookup"><span data-stu-id="64eb0-141">The following sample demonstrates how to do this by maintaining the instance with the `runningTotal` variable.</span></span>  
  
    ```csharp
    [ServiceBehavior(TransactionIsolationLevel = [ServiceBehavior(  
        ReleaseServiceInstanceOnTransactionComplete = false)]  
    public class CalculatorService : ICalculator  
    {  
        double runningTotal = 0;  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n)  
        {  
            // Perform transactional operation  
            RecordToLog($"Adding {n} to {runningTotal}");
            runningTotal = runningTotal + n;  
            return runningTotal;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n)  
        {  
            // Perform transactional operation  
            RecordToLog($"Subtracting {n} from {runningTotal}");
            runningTotal = runningTotal - n;  
            return runningTotal;  
        }  
  
        private static void RecordToLog(string recordText)  
        {  
            // Database operations omitted for brevity  
        }  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="64eb0-142">インスタンスの有効期間はサービスの内部に属する動作であり、<xref:System.ServiceModel.ServiceBehaviorAttribute> プロパティを介して制御できるため、インスタンスの動作を設定するためにサービス構成やサービス コントラクトを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="64eb0-142">Since the instance lifetime is a behavior that is internal to the service, and controlled through the <xref:System.ServiceModel.ServiceBehaviorAttribute> property, no modification to the service configuration or service contract is required to set the instance behavior.</span></span> <span data-ttu-id="64eb0-143">また、ネットワーク上にもこれに相当する表現はありません。</span><span class="sxs-lookup"><span data-stu-id="64eb0-143">In addition, the wire will contain no representation of this.</span></span>
