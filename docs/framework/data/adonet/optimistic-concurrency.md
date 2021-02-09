---
description: '詳細情報: オプティミスティック コンカレンシー'
title: オプティミスティック コンカレンシー
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: 1034720b2c57b863b87eef440424a7e2f4c2c6c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739145"
---
# <a name="optimistic-concurrency"></a><span data-ttu-id="d8575-103">オプティミスティック コンカレンシー</span><span class="sxs-lookup"><span data-stu-id="d8575-103">Optimistic Concurrency</span></span>

<span data-ttu-id="d8575-104">マルチユーザー環境には、データベースのデータを更新するための 2 つのモデルがあります。オプティミスティック コンカレンシーとペシミスティック コンカレンシーです。</span><span class="sxs-lookup"><span data-stu-id="d8575-104">In a multiuser environment, there are two models for updating data in a database: optimistic concurrency and pessimistic concurrency.</span></span> <span data-ttu-id="d8575-105"><xref:System.Data.DataSet> オブジェクトは、データをリモート処理するときや、データと対話するときのように長時間にわたる利用状況では、オプティミスティック コンカレンシーの使用を奨励するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="d8575-105">The <xref:System.Data.DataSet> object is designed to encourage the use of optimistic concurrency for long-running activities, such as remoting data and interacting with data.</span></span>  
  
 <span data-ttu-id="d8575-106">ペシミスティック コンカレンシーでは、他のユーザーが現在のユーザーに影響を与えるようなデータ変更を実行するのを防ぐために、データ ソースで行をロックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8575-106">Pessimistic concurrency involves locking rows at the data source to prevent other users from modifying data in a way that affects the current user.</span></span> <span data-ttu-id="d8575-107">ペシミスティック モデルでは、あるユーザーがロックの適用される操作を実行すると、他のユーザーは、ロックが解除されるまで、競合する操作を実行できません。</span><span class="sxs-lookup"><span data-stu-id="d8575-107">In a pessimistic model, when a user performs an action that causes a lock to be applied, other users cannot perform actions that would conflict with the lock until the lock owner releases it.</span></span> <span data-ttu-id="d8575-108">このモデルは、コンカレンシーの競合が発生するときに、トランザクションをロールバックするよりもデータをロックで保護する方が低コストに抑えられるため、データの競合が多い環境で主に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d8575-108">This model is primarily used in environments where there is heavy contention for data, so that the cost of protecting data with locks is less than the cost of rolling back transactions if concurrency conflicts occur.</span></span>  
  
 <span data-ttu-id="d8575-109">したがって、ペシミスティック コンカレンシー モデルでは、行を更新するユーザーがロックを設定します。</span><span class="sxs-lookup"><span data-stu-id="d8575-109">Therefore, in a pessimistic concurrency model, a user who updates a row establishes a lock.</span></span> <span data-ttu-id="d8575-110">更新を終了してロックを解除するまでは、他のユーザーはその行を変更できません。</span><span class="sxs-lookup"><span data-stu-id="d8575-110">Until the user has finished the update and released the lock, no one else can change that row.</span></span> <span data-ttu-id="d8575-111">そのため、ペシミスティック コンカレンシーは、レコードをプログラムで処理する場合のようにロック時間が短いときの実装に適しています。</span><span class="sxs-lookup"><span data-stu-id="d8575-111">For this reason, pessimistic concurrency is best implemented when lock times will be short, as in programmatic processing of records.</span></span> <span data-ttu-id="d8575-112">ペシミスティック コンカレンシーは、ユーザーがデータと対話していてレコードが比較的長時間ロックされる場合には適していません。</span><span class="sxs-lookup"><span data-stu-id="d8575-112">Pessimistic concurrency is not a scalable option when users are interacting with data and causing records to be locked for relatively large periods of time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8575-113">同じ操作で複数の行を更新する必要がある場合は、ペシミスティック同時実行制御でロックするよりも、トランザクションを作成する方が有効です。</span><span class="sxs-lookup"><span data-stu-id="d8575-113">If you need to update multiple rows in the same operation, then creating a transaction is a more scalable option than using pessimistic locking.</span></span>  
  
 <span data-ttu-id="d8575-114">これに対して、オプティミスティック コンカレンシーを使用するユーザーは、行を読み取るときに行をロックしません。</span><span class="sxs-lookup"><span data-stu-id="d8575-114">By contrast, users who use optimistic concurrency do not lock a row when reading it.</span></span> <span data-ttu-id="d8575-115">ユーザーが行を更新するときは、行の読み取り後に別のユーザーがその行を変更したかどうかをアプリケーションで確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8575-115">When a user wants to update a row, the application must determine whether another user has changed the row since it was read.</span></span> <span data-ttu-id="d8575-116">オプティミスティック コンカレンシーは、一般に、データの競合が少ない環境で使用されます。</span><span class="sxs-lookup"><span data-stu-id="d8575-116">Optimistic concurrency is generally used in environments with a low contention for data.</span></span> <span data-ttu-id="d8575-117">オプティミスティック コンカレンシーを使用すると、レコードをロックする必要がないためパフォーマンスが向上します。レコードをロックするには、サーバー リソースを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8575-117">Optimistic concurrency improves performance because no locking of records is required, and locking of records requires additional server resources.</span></span> <span data-ttu-id="d8575-118">また、レコードのロックを管理するためにデータベース サーバーに永続的に接続している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8575-118">Also, in order to maintain record locks, a persistent connection to the database server is required.</span></span> <span data-ttu-id="d8575-119">オプティミスティック コンカレンシーモデルでは、サーバーとの接続が固定していないため、より短い時間で多数のクライアントを扱うことができます。</span><span class="sxs-lookup"><span data-stu-id="d8575-119">Because this is not the case in an optimistic concurrency model, connections to the server are free to serve a larger number of clients in less time.</span></span>  
  
 <span data-ttu-id="d8575-120">オプティミスティック コンカレンシー モデルでは、ユーザーがデータベースから値を受け取った後、その値を変更する前に別のユーザーがその値を変更した場合に、違反が発生したと見なされます。</span><span class="sxs-lookup"><span data-stu-id="d8575-120">In an optimistic concurrency model, a violation is considered to have occurred if, after a user receives a value from the database, another user modifies the value before the first user has attempted to modify it.</span></span> <span data-ttu-id="d8575-121">サーバーがコンカレンシー違反を解決する方法がよくわかる例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d8575-121">How the server resolves a concurrency violation is best shown by first describing the following example.</span></span>  
  
 <span data-ttu-id="d8575-122">オプティミスティック コンカレンシーの例を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="d8575-122">The following tables follow an example of optimistic concurrency.</span></span>  
  
 <span data-ttu-id="d8575-123">午後 1 時に、User1 が、次の値を持つデータベースから行を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="d8575-123">At 1:00 p.m., User1 reads a row from the database with the following values:</span></span>  
  
 <span data-ttu-id="d8575-124">**CustID     LastName     FirstName**</span><span class="sxs-lookup"><span data-stu-id="d8575-124">**CustID     LastName     FirstName**</span></span>  
  
 <span data-ttu-id="d8575-125">101          Smith             Bob</span><span class="sxs-lookup"><span data-stu-id="d8575-125">101          Smith             Bob</span></span>  
  
|<span data-ttu-id="d8575-126">列名</span><span class="sxs-lookup"><span data-stu-id="d8575-126">Column name</span></span>|<span data-ttu-id="d8575-127">元の値</span><span class="sxs-lookup"><span data-stu-id="d8575-127">Original value</span></span>|<span data-ttu-id="d8575-128">現在の値</span><span class="sxs-lookup"><span data-stu-id="d8575-128">Current value</span></span>|<span data-ttu-id="d8575-129">データベース内の値</span><span class="sxs-lookup"><span data-stu-id="d8575-129">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="d8575-130">CustID</span><span class="sxs-lookup"><span data-stu-id="d8575-130">CustID</span></span>|<span data-ttu-id="d8575-131">101</span><span class="sxs-lookup"><span data-stu-id="d8575-131">101</span></span>|<span data-ttu-id="d8575-132">101</span><span class="sxs-lookup"><span data-stu-id="d8575-132">101</span></span>|<span data-ttu-id="d8575-133">101</span><span class="sxs-lookup"><span data-stu-id="d8575-133">101</span></span>|  
|<span data-ttu-id="d8575-134">LastName</span><span class="sxs-lookup"><span data-stu-id="d8575-134">LastName</span></span>|<span data-ttu-id="d8575-135">Smith</span><span class="sxs-lookup"><span data-stu-id="d8575-135">Smith</span></span>|<span data-ttu-id="d8575-136">Smith</span><span class="sxs-lookup"><span data-stu-id="d8575-136">Smith</span></span>|<span data-ttu-id="d8575-137">Smith</span><span class="sxs-lookup"><span data-stu-id="d8575-137">Smith</span></span>|  
|<span data-ttu-id="d8575-138">FirstName</span><span class="sxs-lookup"><span data-stu-id="d8575-138">FirstName</span></span>|<span data-ttu-id="d8575-139">Bob</span><span class="sxs-lookup"><span data-stu-id="d8575-139">Bob</span></span>|<span data-ttu-id="d8575-140">Bob</span><span class="sxs-lookup"><span data-stu-id="d8575-140">Bob</span></span>|<span data-ttu-id="d8575-141">Bob</span><span class="sxs-lookup"><span data-stu-id="d8575-141">Bob</span></span>|  
  
 <span data-ttu-id="d8575-142">午後 1 時 1 分に、User2 が同じ行を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="d8575-142">At 1:01 p.m., User2 reads the same row.</span></span>  
  
 <span data-ttu-id="d8575-143">午後 1 時 3 分に、User2 が **FirstName** を "Bob" から "Robert" に変更し、データベースを更新します。</span><span class="sxs-lookup"><span data-stu-id="d8575-143">At 1:03 p.m., User2 changes **FirstName** from "Bob" to "Robert" and updates the database.</span></span>  
  
|<span data-ttu-id="d8575-144">列名</span><span class="sxs-lookup"><span data-stu-id="d8575-144">Column name</span></span>|<span data-ttu-id="d8575-145">元の値</span><span class="sxs-lookup"><span data-stu-id="d8575-145">Original value</span></span>|<span data-ttu-id="d8575-146">現在の値</span><span class="sxs-lookup"><span data-stu-id="d8575-146">Current value</span></span>|<span data-ttu-id="d8575-147">データベース内の値</span><span class="sxs-lookup"><span data-stu-id="d8575-147">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="d8575-148">CustID</span><span class="sxs-lookup"><span data-stu-id="d8575-148">CustID</span></span>|<span data-ttu-id="d8575-149">101</span><span class="sxs-lookup"><span data-stu-id="d8575-149">101</span></span>|<span data-ttu-id="d8575-150">101</span><span class="sxs-lookup"><span data-stu-id="d8575-150">101</span></span>|<span data-ttu-id="d8575-151">101</span><span class="sxs-lookup"><span data-stu-id="d8575-151">101</span></span>|  
|<span data-ttu-id="d8575-152">LastName</span><span class="sxs-lookup"><span data-stu-id="d8575-152">LastName</span></span>|<span data-ttu-id="d8575-153">Smith</span><span class="sxs-lookup"><span data-stu-id="d8575-153">Smith</span></span>|<span data-ttu-id="d8575-154">Smith</span><span class="sxs-lookup"><span data-stu-id="d8575-154">Smith</span></span>|<span data-ttu-id="d8575-155">Smith</span><span class="sxs-lookup"><span data-stu-id="d8575-155">Smith</span></span>|  
|<span data-ttu-id="d8575-156">FirstName</span><span class="sxs-lookup"><span data-stu-id="d8575-156">FirstName</span></span>|<span data-ttu-id="d8575-157">Bob</span><span class="sxs-lookup"><span data-stu-id="d8575-157">Bob</span></span>|<span data-ttu-id="d8575-158">Robert</span><span class="sxs-lookup"><span data-stu-id="d8575-158">Robert</span></span>|<span data-ttu-id="d8575-159">Bob</span><span class="sxs-lookup"><span data-stu-id="d8575-159">Bob</span></span>|  
  
 <span data-ttu-id="d8575-160">更新時のデータベース内の値は User2 が持つ元の値と一致しているため、更新は成功します。</span><span class="sxs-lookup"><span data-stu-id="d8575-160">The update succeeds because the values in the database at the time of update match the original values that User2 has.</span></span>  
  
 <span data-ttu-id="d8575-161">午後 1 時 5 分に、User1 が "Bob" の名を "James" に変更し、行の更新を試みます。</span><span class="sxs-lookup"><span data-stu-id="d8575-161">At 1:05 p.m., User1 changes "Bob"'s first name to "James" and tries to update the row.</span></span>  
  
|<span data-ttu-id="d8575-162">列名</span><span class="sxs-lookup"><span data-stu-id="d8575-162">Column name</span></span>|<span data-ttu-id="d8575-163">元の値</span><span class="sxs-lookup"><span data-stu-id="d8575-163">Original value</span></span>|<span data-ttu-id="d8575-164">現在の値</span><span class="sxs-lookup"><span data-stu-id="d8575-164">Current value</span></span>|<span data-ttu-id="d8575-165">データベース内の値</span><span class="sxs-lookup"><span data-stu-id="d8575-165">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="d8575-166">CustID</span><span class="sxs-lookup"><span data-stu-id="d8575-166">CustID</span></span>|<span data-ttu-id="d8575-167">101</span><span class="sxs-lookup"><span data-stu-id="d8575-167">101</span></span>|<span data-ttu-id="d8575-168">101</span><span class="sxs-lookup"><span data-stu-id="d8575-168">101</span></span>|<span data-ttu-id="d8575-169">101</span><span class="sxs-lookup"><span data-stu-id="d8575-169">101</span></span>|  
|<span data-ttu-id="d8575-170">LastName</span><span class="sxs-lookup"><span data-stu-id="d8575-170">LastName</span></span>|<span data-ttu-id="d8575-171">Smith</span><span class="sxs-lookup"><span data-stu-id="d8575-171">Smith</span></span>|<span data-ttu-id="d8575-172">Smith</span><span class="sxs-lookup"><span data-stu-id="d8575-172">Smith</span></span>|<span data-ttu-id="d8575-173">Smith</span><span class="sxs-lookup"><span data-stu-id="d8575-173">Smith</span></span>|  
|<span data-ttu-id="d8575-174">FirstName</span><span class="sxs-lookup"><span data-stu-id="d8575-174">FirstName</span></span>|<span data-ttu-id="d8575-175">Bob</span><span class="sxs-lookup"><span data-stu-id="d8575-175">Bob</span></span>|<span data-ttu-id="d8575-176">James</span><span class="sxs-lookup"><span data-stu-id="d8575-176">James</span></span>|<span data-ttu-id="d8575-177">Robert</span><span class="sxs-lookup"><span data-stu-id="d8575-177">Robert</span></span>|  
  
 <span data-ttu-id="d8575-178">この時点で、データベース内の値 ("Robert") は User1 が期待していた元の値 ("Bob") と一致していないため、User1 による更新はオプティミスティック コンカレンシー違反となります。</span><span class="sxs-lookup"><span data-stu-id="d8575-178">At this point, User1 encounters an optimistic concurrency violation because the value in the database ("Robert") no longer matches the original value that User1 was expecting ("Bob").</span></span> <span data-ttu-id="d8575-179">コンカレンシー違反は、更新が失敗したことを通知するだけです。</span><span class="sxs-lookup"><span data-stu-id="d8575-179">The concurrency violation simply lets you know that the update failed.</span></span> <span data-ttu-id="d8575-180">ここで、User2 による変更を User1 による変更で上書きするか、または User1 による変更をキャンセルするかの決定が必要になります。</span><span class="sxs-lookup"><span data-stu-id="d8575-180">The decision now needs to be made whether to overwrite the changes supplied by User2 with the changes supplied by User1, or to cancel the changes by User1.</span></span>  
  
## <a name="testing-for-optimistic-concurrency-violations"></a><span data-ttu-id="d8575-181">オプティミスティック コンカレンシー違反テスト</span><span class="sxs-lookup"><span data-stu-id="d8575-181">Testing for Optimistic Concurrency Violations</span></span>  

 <span data-ttu-id="d8575-182">オプティミスティック コンカレンシー違反をテストするには、いくつか方法があります。</span><span class="sxs-lookup"><span data-stu-id="d8575-182">There are several techniques for testing for an optimistic concurrency violation.</span></span> <span data-ttu-id="d8575-183">1 つは、テーブルにタイムスタンプ列を含める方法です。</span><span class="sxs-lookup"><span data-stu-id="d8575-183">One involves including a timestamp column in the table.</span></span> <span data-ttu-id="d8575-184">一般に、データベースには、レコードを最後に更新した日付と時刻を識別するために使用するタイムスタンプ機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d8575-184">Databases commonly provide timestamp functionality that can be used to identify the date and time when the record was last updated.</span></span> <span data-ttu-id="d8575-185">この機能を使用すると、timestamp 列がテーブル定義に組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="d8575-185">Using this technique, a timestamp column is included in the table definition.</span></span> <span data-ttu-id="d8575-186">レコードが更新されると、タイムスタンプが更新されて現在の日付と時刻が反映されます。</span><span class="sxs-lookup"><span data-stu-id="d8575-186">Whenever the record is updated, the timestamp is updated to reflect the current date and time.</span></span> <span data-ttu-id="d8575-187">オプティミスティック コンカレンシー違反テストでは、テーブル内容についてのクエリによって timestamp 列が返されます。</span><span class="sxs-lookup"><span data-stu-id="d8575-187">In a test for optimistic concurrency violations, the timestamp column is returned with any query of the contents of the table.</span></span> <span data-ttu-id="d8575-188">更新しようとすると、データベースのタイムスタンプ値と、変更行に格納されている元のタイムスタンプ値が比較されます。</span><span class="sxs-lookup"><span data-stu-id="d8575-188">When an update is attempted, the timestamp value in the database is compared to the original timestamp value contained in the modified row.</span></span> <span data-ttu-id="d8575-189">一致した場合、更新が実行され、timestamp 列が現在の時刻に更新されてその更新が反映されます。</span><span class="sxs-lookup"><span data-stu-id="d8575-189">If they match, the update is performed and the timestamp column is updated with the current time to reflect the update.</span></span> <span data-ttu-id="d8575-190">一致しなかった場合は、オプティミスティック コンカレンシー違反が発生します。</span><span class="sxs-lookup"><span data-stu-id="d8575-190">If they do not match, an optimistic concurrency violation has occurred.</span></span>  
  
 <span data-ttu-id="d8575-191">オプティミスティック コンカレンシー違反をテストするためのもう 1 つの方法は、行のすべての列の元の値が、データベース内の値とまだ一致しているかどうかを検証することです。</span><span class="sxs-lookup"><span data-stu-id="d8575-191">Another technique for testing for an optimistic concurrency violation is to verify that all the original column values in a row still match those found in the database.</span></span> <span data-ttu-id="d8575-192">たとえば、次のクエリを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="d8575-192">For example, consider the following query:</span></span>  
  
```sql
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 <span data-ttu-id="d8575-193">**Table1** 内の行の更新時にオプティミスティック コンカレンシー違反についてテストするために、次の UPDATE ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="d8575-193">To test for an optimistic concurrency violation when updating a row in **Table1**, you would issue the following UPDATE statement:</span></span>  
  
```sql
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 <span data-ttu-id="d8575-194">元の値がデータベース内の値と一致する間は、更新が実行されます。</span><span class="sxs-lookup"><span data-stu-id="d8575-194">As long as the original values match the values in the database, the update is performed.</span></span> <span data-ttu-id="d8575-195">値が変更された場合は、WHERE 句の条件と一致する行を見つけることができないため更新できません。</span><span class="sxs-lookup"><span data-stu-id="d8575-195">If a value has been modified, the update will not modify the row because the WHERE clause will not find a match.</span></span>  
  
 <span data-ttu-id="d8575-196">クエリで、常に一意の主キー値を返すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d8575-196">Note that it is recommended to always return a unique primary key value in your query.</span></span> <span data-ttu-id="d8575-197">一意の主キーを返さないと、UPDATE ステートメントによって複数の行が更新されることがあり、意図に反した結果となります。</span><span class="sxs-lookup"><span data-stu-id="d8575-197">Otherwise, the preceding UPDATE statement may update more than one row, which might not be your intent.</span></span>  
  
 <span data-ttu-id="d8575-198">データ ソースの列で null が使用できる場合は、ローカル テーブルおよびデータ ソースで一致する null 参照がないかどうかをチェックするように WHERE 句を拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8575-198">If a column at your data source allows nulls, you may need to extend your WHERE clause to check for a matching null reference in your local table and at the data source.</span></span> <span data-ttu-id="d8575-199">たとえば、次の UPDATE ステートメントは、ローカル行の null 参照がデータ ソースの null 参照とまだ一致しているかどうか、つまり、ローカル行の値がデータ ソースの値とまだ一致しているかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="d8575-199">For example, the following UPDATE statement verifies that a null reference in the local row still matches a null reference at the data source, or that the value in the local row still matches the value at the data source.</span></span>  
  
```sql
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 <span data-ttu-id="d8575-200">オプティミスティック コンカレンシー モデルを使用するときは、より制限の少ない抽出条件を適用するように選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="d8575-200">You may also choose to apply less restrictive criteria when using an optimistic concurrency model.</span></span> <span data-ttu-id="d8575-201">たとえば、WHERE 句で主キー列だけを使用すると、前回のクエリ実行後に主キー以外の列が更新されたかどうかに関係なく、データが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="d8575-201">For example, using only the primary key columns in the WHERE clause causes the data to be overwritten regardless of whether the other columns have been updated since the last query.</span></span> <span data-ttu-id="d8575-202">WHERE 句を特定の列だけに適用することもできます。特定の列だけに WHERE 句を適用した場合は、特定のフィールドが前回のクエリ実行後に更新されていない限りデータが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="d8575-202">You can also apply a WHERE clause only to specific columns, resulting in data being overwritten unless particular fields have been updated since they were last queried.</span></span>  
  
### <a name="the-dataadapterrowupdated-event"></a><span data-ttu-id="d8575-203">DataAdapter.RowUpdated イベント</span><span class="sxs-lookup"><span data-stu-id="d8575-203">The DataAdapter.RowUpdated Event</span></span>  

 <span data-ttu-id="d8575-204">これまでに説明した方法と併せて、<xref:System.Data.Common.DataAdapter> オブジェクトの **RowUpdated** イベントを使用しても、オプティミスティック コンカレンシー違反をアプリケーションに通知できます。</span><span class="sxs-lookup"><span data-stu-id="d8575-204">The **RowUpdated** event of the <xref:System.Data.Common.DataAdapter> object can be used in conjunction with the techniques described earlier, to provide notification to your application of optimistic concurrency violations.</span></span> <span data-ttu-id="d8575-205">**RowUpdated** は、**DataSet** から **Modified** 行の更新を行ったときに発生します。</span><span class="sxs-lookup"><span data-stu-id="d8575-205">**RowUpdated** occurs after each attempt to update a **Modified** row from a **DataSet**.</span></span> <span data-ttu-id="d8575-206">これにより、例外発生時の処理、カスタム エラー情報の追加、再試行ロジックの追加などの特別の処理コードを追加できます。</span><span class="sxs-lookup"><span data-stu-id="d8575-206">This enables you to add special handling code, including processing when an exception occurs, adding custom error information, adding retry logic, and so on.</span></span> <span data-ttu-id="d8575-207"><xref:System.Data.Common.RowUpdatedEventArgs> オブジェクトは、テーブルの行を変更する特定の更新コマンドの影響を受けた行数を含む **RecordsAffected** プロパティを返します。</span><span class="sxs-lookup"><span data-stu-id="d8575-207">The <xref:System.Data.Common.RowUpdatedEventArgs> object returns a **RecordsAffected** property containing the number of rows affected by a particular update command for a modified row in a table.</span></span> <span data-ttu-id="d8575-208">オプティミスティック コンカレンシーをテストするように更新コマンドを設定した場合は、オプティミスティック コンカレンシー違反の発生時に、**RecordsAffected** プロパティは値 0 を結果として返します。値が 0 なのはレコードが更新されないためです。</span><span class="sxs-lookup"><span data-stu-id="d8575-208">By setting the update command to test for optimistic concurrency, the **RecordsAffected** property will, as a result, return a value of 0 when an optimistic concurrency violation has occurred, because no records were updated.</span></span> <span data-ttu-id="d8575-209">この場合、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="d8575-209">If this is the case, an exception is thrown.</span></span> <span data-ttu-id="d8575-210">**RowUpdated** イベントを使用すると、発生したイベントを処理したり、**UpdateStatus.SkipCurrentRow** のような適切な **RowUpdatedEventArgs.Status** 値を設定することで例外を回避したりできます。</span><span class="sxs-lookup"><span data-stu-id="d8575-210">The **RowUpdated** event enables you to handle this occurrence and avoid the exception by setting an appropriate **RowUpdatedEventArgs.Status** value, such as **UpdateStatus.SkipCurrentRow**.</span></span> <span data-ttu-id="d8575-211">**RowUpdated** イベントについて詳しくは、「[DataAdapter のイベント処理](handling-dataadapter-events.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d8575-211">For more information about the **RowUpdated** event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>  
  
 <span data-ttu-id="d8575-212">必要に応じて、**Update** を呼び出す前に **DataAdapter.ContinueUpdateOnError** を **true** に設定し、**Update** 完了時に特定の行の **RowError** プロパティに格納されたエラー情報に対処することができます。</span><span class="sxs-lookup"><span data-stu-id="d8575-212">Optionally, you can set **DataAdapter.ContinueUpdateOnError** to **true**, before calling **Update**, and respond to the error information stored in the **RowError** property of a particular row when the **Update** is completed.</span></span> <span data-ttu-id="d8575-213">詳しくは、「[行エラー情報](./dataset-datatable-dataview/row-error-information.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d8575-213">For more information, see [Row Error Information](./dataset-datatable-dataview/row-error-information.md).</span></span>  
  
## <a name="optimistic-concurrency-example"></a><span data-ttu-id="d8575-214">オプティミスティック コンカレンシーの例</span><span class="sxs-lookup"><span data-stu-id="d8575-214">Optimistic Concurrency Example</span></span>  

 <span data-ttu-id="d8575-215">**DataAdapter** の **UpdateCommand** をオプティミスティック コンカレンシーをテストするように設定してから、**RowUpdated** イベントを使用してオプティミスティック コンカレンシー違反がないかどうかをテストする簡単な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d8575-215">The following is a simple example that sets the **UpdateCommand** of a **DataAdapter** to test for optimistic concurrency, and then uses the **RowUpdated** event to test for optimistic concurrency violations.</span></span> <span data-ttu-id="d8575-216">オプティミスティック コンカレンシー違反が検出されると、アプリケーションは、オプティミスティック コンカレンシー違反が反映されるように更新が実行された行の **RowError** を設定します。</span><span class="sxs-lookup"><span data-stu-id="d8575-216">When an optimistic concurrency violation is encountered, the application sets the **RowError** of the row that the update was issued for to reflect an optimistic concurrency violation.</span></span>  
  
 <span data-ttu-id="d8575-217">UPDATE コマンドの WHERE 句に渡されたパラメーター値は、それぞれの列の **Original** 値に割り当てられることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d8575-217">Note that the parameter values passed to the WHERE clause of the UPDATE command are mapped to the **Original** values of their respective columns.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID", _  
  connection)  
  
' The Update command checks for optimistic concurrency violations  
' in the WHERE clause.  
adapter.UpdateCommand = New SqlCommand("UPDATE Customers " &  
  "(CustomerID, CompanyName) VALUES(@CustomerID, @CompanyName) " & _  
  "WHERE CustomerID = @oldCustomerID AND CompanyName = " &  
  "@oldCompanyName", connection)  
adapter.UpdateCommand.Parameters.Add( _  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
adapter.UpdateCommand.Parameters.Add( _  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
  
' Pass the original values to the WHERE clause parameters.  
Dim parameter As SqlParameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
parameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
parameter.SourceVersion = DataRowVersion.Original  
  
' Add the RowUpdated event handler.  
AddHandler adapter.RowUpdated, New SqlRowUpdatedEventHandler( _  
  AddressOf OnRowUpdated)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Customers")  
  
' Modify the DataSet contents.  
adapter.Update(dataSet, "Customers")  
  
Dim dataRow As DataRow  
  
For Each dataRow In dataSet.Tables("Customers").Rows  
    If dataRow.HasErrors Then
       Console.WriteLine(dataRow (0) & vbCrLf & dataRow.RowError)  
    End If  
Next  
  
Private Shared Sub OnRowUpdated( _  
  sender As object, args As SqlRowUpdatedEventArgs)  
   If args.RecordsAffected = 0  
      args.Row.RowError = "Optimistic Concurrency Violation!"  
      args.Status = UpdateStatus.SkipCurrentRow  
   End If  
End Sub  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID",  
  connection);  
  
// The Update command checks for optimistic concurrency violations  
// in the WHERE clause.  
adapter.UpdateCommand = new SqlCommand("UPDATE Customers Set CustomerID = @CustomerID, CompanyName = @CompanyName " +  
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName", connection);  
adapter.UpdateCommand.Parameters.Add(  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
adapter.UpdateCommand.Parameters.Add(  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
  
// Pass the original values to the WHERE clause parameters.  
SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
parameter.SourceVersion = DataRowVersion.Original;  
parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
parameter.SourceVersion = DataRowVersion.Original;  
  
// Add the RowUpdated event handler.  
adapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Customers");  
  
// Modify the DataSet contents.  
  
adapter.Update(dataSet, "Customers");  
  
foreach (DataRow dataRow in dataSet.Tables["Customers"].Rows)  
{  
    if (dataRow.HasErrors)  
       Console.WriteLine(dataRow [0] + "\n" + dataRow.RowError);  
}  
  
protected static void OnRowUpdated(object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.RecordsAffected == 0)
  {  
    args.Row.RowError = "Optimistic Concurrency Violation Encountered";  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8575-218">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8575-218">See also</span></span>

- [<span data-ttu-id="d8575-219">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="d8575-219">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="d8575-220">DataAdapter によるデータ ソースの更新</span><span class="sxs-lookup"><span data-stu-id="d8575-220">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="d8575-221">行エラー情報</span><span class="sxs-lookup"><span data-stu-id="d8575-221">Row Error Information</span></span>](./dataset-datatable-dataview/row-error-information.md)
- [<span data-ttu-id="d8575-222">トランザクションとコンカレンシー</span><span class="sxs-lookup"><span data-stu-id="d8575-222">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="d8575-223">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="d8575-223">ADO.NET Overview</span></span>](ado-net-overview.md)
