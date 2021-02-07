---
description: '詳細については、「方法: カスタムの永続参加要素を作成する」を参照してください。'
title: '方法: カスタム永続参加要素を作成する'
ms.date: 03/30/2017
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
ms.openlocfilehash: a0bdd8407bf409e7e485f4f32a0dd3f61e6f82b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742096"
---
# <a name="how-to-create-a-custom-persistence-participant"></a><span data-ttu-id="abda1-103">方法: カスタム永続参加要素を作成する</span><span class="sxs-lookup"><span data-stu-id="abda1-103">How to: Create a Custom Persistence Participant</span></span>

<span data-ttu-id="abda1-104">次の手順では、永続参加要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="abda1-104">The following procedure has steps to create a persistence participant.</span></span> <span data-ttu-id="abda1-105">永続参加要素の実装例については、永続化のサンプルと[ストアの機能拡張](store-extensibility.md)[に](/previous-versions/dotnet/netframework-4.0/dd699769(v=vs.100))関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="abda1-105">See the [Participating in Persistence](/previous-versions/dotnet/netframework-4.0/dd699769(v=vs.100)) sample and [Store Extensibility](store-extensibility.md) topic for sample implementations of persistence participants.</span></span>  
  
1. <span data-ttu-id="abda1-106"><xref:System.Activities.Persistence.PersistenceParticipant> または <xref:System.Activities.Persistence.PersistenceIOParticipant> クラスから派生するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="abda1-106">Create a class deriving from the <xref:System.Activities.Persistence.PersistenceParticipant> or the <xref:System.Activities.Persistence.PersistenceIOParticipant> class.</span></span> <span data-ttu-id="abda1-107">PersistenceIOParticipant クラスは、i/o 操作に参加できるだけでなく、PersistenceParticipant クラスと同じ機能拡張ポイントを提供します。</span><span class="sxs-lookup"><span data-stu-id="abda1-107">The PersistenceIOParticipant class offers the same extensibility points as the PersistenceParticipant class in addition to being able to participate in I/O operations.</span></span> <span data-ttu-id="abda1-108">次のうち、必要な手順を行います。</span><span class="sxs-lookup"><span data-stu-id="abda1-108">Follow one or more of the following steps.</span></span>  
  
2. <span data-ttu-id="abda1-109"><xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="abda1-109">Implement the <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> method.</span></span> <span data-ttu-id="abda1-110">**Collectvalues** メソッドには、2つのディクショナリパラメーターがあります。1つは読み取り/書き込み値を格納するためのもので、もう1つは書き込み専用の値を格納するためのもので、後でクエリで使用します。</span><span class="sxs-lookup"><span data-stu-id="abda1-110">The **CollectValues** method has two dictionary parameters, one for storing read/write values and the other one for storing write-only values (used later in queries).</span></span> <span data-ttu-id="abda1-111">このメソッドでは、永続参加要素に固有のデータをこれらのディクショナリに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="abda1-111">In this method, you should populate these dictionaries with data that is specific to a persistence participant.</span></span> <span data-ttu-id="abda1-112">各ディクショナリには、値の名前がキーとして格納されているほか、値そのものが <xref:System.Runtime.DurableInstancing.InstanceValue> オブジェクトとして格納されています。</span><span class="sxs-lookup"><span data-stu-id="abda1-112">Each dictionary contains the name of the value as the key and the value itself as an <xref:System.Runtime.DurableInstancing.InstanceValue> object.</span></span>  
  
    <span data-ttu-id="abda1-113">ReadWriteValues ディクショナリ内の値は、 **Instancevalue** オブジェクトとしてパッケージ化されます。</span><span class="sxs-lookup"><span data-stu-id="abda1-113">The values in the readWriteValues dictionary are packaged as **InstanceValue** objects.</span></span> <span data-ttu-id="abda1-114">書き込み専用辞書の値は、InstanceValueOptions を使用して **Instancevalue** オブジェクトとしてパッケージ化されます。省略可能で、InstanceValueOption. WriteOnly set です。</span><span class="sxs-lookup"><span data-stu-id="abda1-114">The values in the write-only dictionary are packaged as **InstanceValue** objects with InstanceValueOptions.Optional and InstanceValueOption.WriteOnly set.</span></span> <span data-ttu-id="abda1-115">すべての永続参加要素の **Collectvalues** 実装によって提供される各 **instancevalue** には、一意の名前を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="abda1-115">Each **InstanceValue** provided by the **CollectValues** implementations across all persistence participants must have a unique name.</span></span>
  
    ```csharp  
    protected virtual void CollectValues(out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)
    {
    }
    ```  
  
3. <span data-ttu-id="abda1-116"><xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="abda1-116">Implement the <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> method.</span></span> <span data-ttu-id="abda1-117">**Mapvalues** メソッドは、 **collectvalues** メソッドが受け取るパラメーターに似た2つのパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="abda1-117">The **MapValues** method takes two parameters that are similar to the parameters that the **CollectValues** method receives.</span></span> <span data-ttu-id="abda1-118">**Collectvalues** ステージで収集されたすべての値は、これらのディクショナリパラメーターを通じて渡されます。</span><span class="sxs-lookup"><span data-stu-id="abda1-118">All the values collected in the **CollectValues** stage are passed through these dictionary parameters.</span></span> <span data-ttu-id="abda1-119">**Mapvalues** ステージによって追加された新しい値は、書き込み専用の値に追加されます。</span><span class="sxs-lookup"><span data-stu-id="abda1-119">The new values added by the **MapValues** stage are added to the write-only values.</span></span>  <span data-ttu-id="abda1-120">書き込み専用のディクショナリが、インスタンスの値に直接関連付けられていない外部ソースにデータを提供するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="abda1-120">The write-only dictionary is used to provide data to an external source not directly associated with the instance values.</span></span> <span data-ttu-id="abda1-121">すべての永続参加要素で **Mapvalues** メソッドの実装によって提供される各値には、一意の名前を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="abda1-121">Each value provided by implementations of the **MapValues** method across all persistence participants must have a unique name.</span></span>  
  
    ```csharp  
    protected virtual IDictionary<XName,Object> MapValues(IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)
    {
    }
    ```  
  
     <span data-ttu-id="abda1-122"><xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> メソッドは <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> が提供しない機能を提供し、<xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> が処理しなかった別の永続参加により提供される、別の値への依存関係が許可されます。</span><span class="sxs-lookup"><span data-stu-id="abda1-122">The <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> method provides functionality that <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> does not, in that it allows for a dependency on another value provided by another persistence participant that hasn’t been processed by <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> yet.</span></span>  
  
4. <span data-ttu-id="abda1-123">**Publishvalues** メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="abda1-123">Implement the **PublishValues** method.</span></span> <span data-ttu-id="abda1-124">**Publishvalues** メソッドは、永続化ストアから読み込まれたすべての値を含むディクショナリを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="abda1-124">The **PublishValues** method receives a dictionary containing all the values loaded from the persistence store.</span></span>  
  
    ```csharp  
    protected virtual void PublishValues(IDictionary<XName,Object> readWriteValues)
    {
    }
    ```  
  
5. <span data-ttu-id="abda1-125">参加要素が永続 i/o 参加要素の場合は、 **Beginonsave** メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="abda1-125">Implement the **BeginOnSave** method if the participant is a persistence I/O participant.</span></span> <span data-ttu-id="abda1-126">このメソッドは保存操作中に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="abda1-126">This method is called during a Save operation.</span></span> <span data-ttu-id="abda1-127">この方法では、ワークフローインスタンスの永続化 (保存) を行うために i/o 補完を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="abda1-127">In this method, you should perform I/O adjunct to the persisting (saving) workflow instances.</span></span>  <span data-ttu-id="abda1-128">ホストが、対応する永続化コマンドのトランザクションを使用している場合、同じトランザクションが Transaction.Current で確立されます。</span><span class="sxs-lookup"><span data-stu-id="abda1-128">If the host is using a transaction for the corresponding persistence command, the same transaction is provided in Transaction.Current.</span></span>  <span data-ttu-id="abda1-129">さらに、PersistenceIOParticipant はトランザクションの一貫性の要件を通知することがあります。この場合、ホストはほかに使用されなければ、永続化のトランザクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="abda1-129">Additionally, PersistenceIOParticipants may advertise a transactional consistency requirement, in which case the host creates a transaction for the persistence episode if one would not otherwise be used.</span></span>  
  
    ```csharp  
    protected virtual IAsyncResult BeginOnSave(IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)
    {
    }
    ```  
  
6. <span data-ttu-id="abda1-130">参加要素が永続 i/o 参加要素の場合は、 **Beginonload** メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="abda1-130">Implement the **BeginOnLoad** method if the participant is a persistence I/O participant.</span></span> <span data-ttu-id="abda1-131">このメソッドは読み込み操作中に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="abda1-131">This method is called during a Load operation.</span></span> <span data-ttu-id="abda1-132">このメソッドでは、ワークフローインスタンスの読み込みに対して i/o 補完を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="abda1-132">In this method, you should perform I/O adjunct to the loading of workflow instances.</span></span> <span data-ttu-id="abda1-133">ホストが、対応する永続化コマンドのトランザクションを使用している場合、同じトランザクションが Transaction.Current で確立されます。</span><span class="sxs-lookup"><span data-stu-id="abda1-133">If the host is using a transaction for the corresponding persistence command, the same transaction is provided in Transaction.Current.</span></span> <span data-ttu-id="abda1-134">さらに、永続化 i/o の参加者はトランザクションの一貫性の要件を提供する場合があります。その場合、ホストは永続化のためのトランザクションを作成します (これを使用しない場合)。</span><span class="sxs-lookup"><span data-stu-id="abda1-134">Additionally, Persistence I/O participants may advertise a transactional consistency requirement, in which case the host creates a transaction for the persistence episode if one would not otherwise be used.</span></span>  
  
    ```csharp  
    protected virtual IAsyncResult BeginOnLoad(IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)
    {
    }
    ```
