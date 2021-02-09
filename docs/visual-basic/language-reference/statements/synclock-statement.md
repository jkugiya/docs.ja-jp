---
description: '詳細情報: SyncLock ステートメント'
title: SyncLock ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: 206c10c8bca85a496345576d0d5f9ff260db82e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740978"
---
# <a name="synclock-statement"></a><span data-ttu-id="46f9a-103">SyncLock ステートメント</span><span class="sxs-lookup"><span data-stu-id="46f9a-103">SyncLock Statement</span></span>

<span data-ttu-id="46f9a-104">ブロックを実行する前に、ステートメント ブロックの排他ロックを取得します。</span><span class="sxs-lookup"><span data-stu-id="46f9a-104">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46f9a-105">構文</span><span class="sxs-lookup"><span data-stu-id="46f9a-105">Syntax</span></span>  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="46f9a-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="46f9a-106">Parts</span></span>  

 `lockobject`  
 <span data-ttu-id="46f9a-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="46f9a-107">Required.</span></span> <span data-ttu-id="46f9a-108">オブジェクト参照として評価される式。</span><span class="sxs-lookup"><span data-stu-id="46f9a-108">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="46f9a-109">任意。</span><span class="sxs-lookup"><span data-stu-id="46f9a-109">Optional.</span></span> <span data-ttu-id="46f9a-110">ロックが取得されたときに実行されるステートメントのブロック。</span><span class="sxs-lookup"><span data-stu-id="46f9a-110">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="46f9a-111">`SyncLock` ブロックを終了します。</span><span class="sxs-lookup"><span data-stu-id="46f9a-111">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46f9a-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="46f9a-112">Remarks</span></span>  

 <span data-ttu-id="46f9a-113">`SyncLock` ステートメントは、複数のスレッドがステートメント ブロックを同時に実行しないようにします。</span><span class="sxs-lookup"><span data-stu-id="46f9a-113">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="46f9a-114">`SyncLock` は、ブロックを実行する他のスレッドがなくなるまで、各スレッドがそのブロックに入らないようにします。</span><span class="sxs-lookup"><span data-stu-id="46f9a-114">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="46f9a-115">`SyncLock` の最も一般的な使用方法は、複数のスレッドによってデータが同時に更新されないようにすることです。</span><span class="sxs-lookup"><span data-stu-id="46f9a-115">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="46f9a-116">データを操作するステートメントが中断せずに完了する必要がある場合は、`SyncLock` ブロック内に配置します。</span><span class="sxs-lookup"><span data-stu-id="46f9a-116">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="46f9a-117">排他ロックによって保護されているステートメント ブロックは、*クリティカル セクション* と呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="46f9a-117">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="46f9a-118">ルール</span><span class="sxs-lookup"><span data-stu-id="46f9a-118">Rules</span></span>  
  
- <span data-ttu-id="46f9a-119">分岐。</span><span class="sxs-lookup"><span data-stu-id="46f9a-119">Branching.</span></span> <span data-ttu-id="46f9a-120">ブロック外から `SyncLock` ブロックに分岐することはできません。</span><span class="sxs-lookup"><span data-stu-id="46f9a-120">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
- <span data-ttu-id="46f9a-121">ロック オブジェクトの値。</span><span class="sxs-lookup"><span data-stu-id="46f9a-121">Lock Object Value.</span></span> <span data-ttu-id="46f9a-122">`lockobject` の値を `Nothing` にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="46f9a-122">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="46f9a-123">`SyncLock` ステートメントで使用する前に、ロック オブジェクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46f9a-123">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="46f9a-124">`SyncLock` ブロックの実行中に `lockobject` の値を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="46f9a-124">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="46f9a-125">このメカニズムでは、ロック オブジェクトが変更されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="46f9a-125">The mechanism requires that the lock object remain unchanged.</span></span>  
  
- <span data-ttu-id="46f9a-126">`SyncLock` ブロックで [Await](../operators/await-operator.md) 演算子を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="46f9a-126">You can't use the [Await](../operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="46f9a-127">動作</span><span class="sxs-lookup"><span data-stu-id="46f9a-127">Behavior</span></span>  
  
- <span data-ttu-id="46f9a-128">メカニズム。</span><span class="sxs-lookup"><span data-stu-id="46f9a-128">Mechanism.</span></span> <span data-ttu-id="46f9a-129">スレッドが `SyncLock` ステートメントに達すると、`lockobject` 式が評価され、式によって返されたオブジェクトの排他ロックを取得するまで実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="46f9a-129">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="46f9a-130">別のスレッドが `SyncLock` ステートメントに達すると、最初のスレッドが `End SyncLock` ステートメントを実行するまでロックは取得されません。</span><span class="sxs-lookup"><span data-stu-id="46f9a-130">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
- <span data-ttu-id="46f9a-131">保護されたデータ。</span><span class="sxs-lookup"><span data-stu-id="46f9a-131">Protected Data.</span></span> <span data-ttu-id="46f9a-132">`lockobject` が `Shared` 変数の場合は、排他ロックによって、クラスのインスタンス内のスレッドが、他のスレッドが実行している間は `SyncLock` ブロックを実行できなくなります。</span><span class="sxs-lookup"><span data-stu-id="46f9a-132">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="46f9a-133">これにより、すべてのインスタンス間で共有されているデータが保護されます。</span><span class="sxs-lookup"><span data-stu-id="46f9a-133">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="46f9a-134">`lockobject` がインスタンス変数 (`Shared` ではなく) の場合は、ロックにより、現在のインスタンスで実行されているスレッドが、同じインスタンス内の別のスレッドと同時に `SyncLock` ブロックを実行できなくなります。</span><span class="sxs-lookup"><span data-stu-id="46f9a-134">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="46f9a-135">これにより、個々のインスタンスによって保持されるデータが保護されます。</span><span class="sxs-lookup"><span data-stu-id="46f9a-135">This protects data maintained by the individual instance.</span></span>  
  
- <span data-ttu-id="46f9a-136">取得と解放。</span><span class="sxs-lookup"><span data-stu-id="46f9a-136">Acquisition and Release.</span></span> <span data-ttu-id="46f9a-137">`SyncLock` ブロックは、`Try` ブロックが `lockobject` に対して排他ロックを取得する `Try...Finally` コンストラクションと同様に動作し、`Finally` ブロックによって解放されます。</span><span class="sxs-lookup"><span data-stu-id="46f9a-137">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="46f9a-138">このため、`SyncLock` ブロックは、ブロックを終了する方法に関係なく、ロックの解放を保証します。</span><span class="sxs-lookup"><span data-stu-id="46f9a-138">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="46f9a-139">これは、ハンドルされない例外が発生した場合でも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="46f9a-139">This is true even in the case of an unhandled exception.</span></span>  
  
- <span data-ttu-id="46f9a-140">フレームワークの呼び出し。</span><span class="sxs-lookup"><span data-stu-id="46f9a-140">Framework Calls.</span></span> <span data-ttu-id="46f9a-141">`SyncLock` ブロックは、<xref:System.Threading> 名前空間の `Monitor` クラスの `Enter` および `Exit` メソッドを呼び出すことによって、排他ロックを取得したり解放したりします。</span><span class="sxs-lookup"><span data-stu-id="46f9a-141">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="46f9a-142">プログラミング プラクティス</span><span class="sxs-lookup"><span data-stu-id="46f9a-142">Programming Practices</span></span>  

 <span data-ttu-id="46f9a-143">`lockobject` 式は、常に、クラスに排他的に属しているオブジェクトに評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="46f9a-143">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="46f9a-144">現在のインスタンスに属するデータを保護するには `Private` オブジェクト変数を宣言し、すべてのインスタンスに共通のデータを保護するには `Private Shared` オブジェクト変数を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46f9a-144">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="46f9a-145">インスタンス データ用のロック オブジェクトを指定するために、`Me` キーワードを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="46f9a-145">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="46f9a-146">クラスの外部のコードにクラスのインスタンスへの参照が含まれている場合、その参照を、ユーザーのものとはまったく異なる `SyncLock` ブロックのロック オブジェクトとして使用して、さまざまなデータを保護することができます。</span><span class="sxs-lookup"><span data-stu-id="46f9a-146">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="46f9a-147">このようにして、ユーザーのクラスとその他のクラスは、関連付けられていない `SyncLock` ブロックの実行を互いにブロックできます。</span><span class="sxs-lookup"><span data-stu-id="46f9a-147">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="46f9a-148">同様に、文字列のロックも問題になる可能性があります。同じ文字列を使用するコードがプロセス内に他にも存在した場合、そのコードも同じロックを共有するためです。</span><span class="sxs-lookup"><span data-stu-id="46f9a-148">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="46f9a-149">また、共有データのロック オブジェクトを指定するために、`Me.GetType` メソッドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="46f9a-149">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="46f9a-150">これは、`GetType` は常に、指定されたクラス名に対して同じ `Type` オブジェクトを返すためです。</span><span class="sxs-lookup"><span data-stu-id="46f9a-150">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="46f9a-151">外部コードは、クラスで `GetType` を呼び出し、使用しているものと同じロック オブジェクトを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="46f9a-151">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="46f9a-152">これにより、2 つのクラスが `SyncLock` ブロックから互いにブロックされることになります。</span><span class="sxs-lookup"><span data-stu-id="46f9a-152">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="46f9a-153">使用例</span><span class="sxs-lookup"><span data-stu-id="46f9a-153">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="46f9a-154">説明</span><span class="sxs-lookup"><span data-stu-id="46f9a-154">Description</span></span>  

 <span data-ttu-id="46f9a-155">次の例では、メッセージの単純なリストを保持するクラスを示します。</span><span class="sxs-lookup"><span data-stu-id="46f9a-155">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="46f9a-156">これは、メッセージを配列内に保持し、その配列の最後に使用された要素を変数に保持します。</span><span class="sxs-lookup"><span data-stu-id="46f9a-156">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="46f9a-157">`addAnotherMessage` プロシージャは、最後の要素をインクリメントし、新しいメッセージを格納します。</span><span class="sxs-lookup"><span data-stu-id="46f9a-157">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="46f9a-158">これら 2 つの操作は、`SyncLock` および `End SyncLock` ステートメントによって保護されます。最後の要素がインクリメントされた後、他のすべてのスレッドが最後の要素を再度インクリメントできるようになる前に、新しいメッセージが格納される必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="46f9a-158">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="46f9a-159">`simpleMessageList` クラスがそのすべてのインスタンス間で 1 つのメッセージ リストを共有している場合、変数 `messagesList` および `messagesLast` は `Shared` として宣言されます。</span><span class="sxs-lookup"><span data-stu-id="46f9a-159">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="46f9a-160">この場合、変数 `messagesLock` も `Shared` にして、すべてのインスタンスで 1 つのロック オブジェクトが使用されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="46f9a-160">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="46f9a-161">コード</span><span class="sxs-lookup"><span data-stu-id="46f9a-161">Code</span></span>  

 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a><span data-ttu-id="46f9a-162">説明</span><span class="sxs-lookup"><span data-stu-id="46f9a-162">Description</span></span>  

 <span data-ttu-id="46f9a-163">次の例では、スレッドと `SyncLock` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="46f9a-163">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="46f9a-164">`SyncLock` ステートメントが存在する限り、このステートメント ブロックはクリティカル セクションとなり、`balance` が負の数になることはありません。</span><span class="sxs-lookup"><span data-stu-id="46f9a-164">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="46f9a-165">`SyncLock` および `End SyncLock` ステートメントをコメント アウトして、`SyncLock` キーワードを残すことによる影響を確認できます。</span><span class="sxs-lookup"><span data-stu-id="46f9a-165">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="46f9a-166">コード</span><span class="sxs-lookup"><span data-stu-id="46f9a-166">Code</span></span>  

 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a><span data-ttu-id="46f9a-167">コメント</span><span class="sxs-lookup"><span data-stu-id="46f9a-167">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46f9a-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="46f9a-168">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="46f9a-169">同期プリミティブの概要</span><span class="sxs-lookup"><span data-stu-id="46f9a-169">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
