---
description: '詳細情報: オプティミスティック コンカレンシー:概要'
title: オプティミスティック コンカレンシー:概要
ms.date: 03/30/2017
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
ms.openlocfilehash: fbf6714851dbb31982a110749c55e5fad7aa2206
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695425"
---
# <a name="optimistic-concurrency-overview"></a><span data-ttu-id="67db2-103">オプティミスティック コンカレンシー:概要</span><span class="sxs-lookup"><span data-stu-id="67db2-103">Optimistic Concurrency: Overview</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="67db2-104">はオプティミスティック コンカレンシーをサポートします。</span><span class="sxs-lookup"><span data-stu-id="67db2-104">supports optimistic concurrency control.</span></span> <span data-ttu-id="67db2-105">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のドキュメントでオプティミスティック コンカレンシーの説明に使用されている用語を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="67db2-105">The following table describes terms that apply to optimistic concurrency in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation:</span></span>  
  
|<span data-ttu-id="67db2-106">用語</span><span class="sxs-lookup"><span data-stu-id="67db2-106">Terms</span></span>|<span data-ttu-id="67db2-107">説明</span><span class="sxs-lookup"><span data-stu-id="67db2-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="67db2-108">コンカレンシー</span><span class="sxs-lookup"><span data-stu-id="67db2-108">concurrency</span></span>|<span data-ttu-id="67db2-109">2 人以上のユーザーがデータベースの同じ行を同時に更新しようとした状況のことです。</span><span class="sxs-lookup"><span data-stu-id="67db2-109">The situation in which two or more users at the same time try to update the same database row.</span></span>|  
|<span data-ttu-id="67db2-110">コンカレンシーの競合</span><span class="sxs-lookup"><span data-stu-id="67db2-110">concurrency conflict</span></span>|<span data-ttu-id="67db2-111">2 人以上のユーザーが、行の中の 1 つまたは複数の列に対し、互いに競合する値を送信しようとした状況のことです。</span><span class="sxs-lookup"><span data-stu-id="67db2-111">The situation in which two or more users at the same time try to submit conflicting values to one or more columns of a row.</span></span>|  
|<span data-ttu-id="67db2-112">コンカレンシー制御</span><span class="sxs-lookup"><span data-stu-id="67db2-112">concurrency control</span></span>|<span data-ttu-id="67db2-113">コンカレンシーの競合を解決するために使用する手法のことです。</span><span class="sxs-lookup"><span data-stu-id="67db2-113">The technique used to resolve concurrency conflicts.</span></span>|  
|<span data-ttu-id="67db2-114">オプティミスティック コンカレンシー</span><span class="sxs-lookup"><span data-stu-id="67db2-114">optimistic concurrency control</span></span>|<span data-ttu-id="67db2-115">他のトランザクションが行の値に変更を加えていないかどうかをまず調べたうえで変更の送信を許可する手法のことです。</span><span class="sxs-lookup"><span data-stu-id="67db2-115">The technique that first investigates whether other transactions have changed values in a row before permitting changes to be submitted.</span></span><br /><br /> <span data-ttu-id="67db2-116">これと対照的なのが "*ペシミスティック コンカレンシー制御*" で、レコードをロックすることでコンカレンシーの競合を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="67db2-116">Contrast with *pessimistic concurrency control*, which locks the record to avoid concurrency conflicts.</span></span><br /><br /> <span data-ttu-id="67db2-117">"*オプティミスティック*" (楽観的) という名前が付いているのは、トランザクションどうしが競合する可能性は小さいものと見なす方法であるためです。</span><span class="sxs-lookup"><span data-stu-id="67db2-117">*Optimistic* control is so termed because it considers the chances of one transaction interfering with another to be unlikely.</span></span>|  
|<span data-ttu-id="67db2-118">競合の解決</span><span class="sxs-lookup"><span data-stu-id="67db2-118">conflict resolution</span></span>|<span data-ttu-id="67db2-119">データベースを再度クエリしてから相違点を調整することによって競合する項目を更新する処理のことです。</span><span class="sxs-lookup"><span data-stu-id="67db2-119">The process of refreshing a conflicting item by querying the database again and then reconciling differences.</span></span><br /><br /> <span data-ttu-id="67db2-120">オブジェクトを更新するときには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の変更トラッカーによって、以下のデータが記録されます。</span><span class="sxs-lookup"><span data-stu-id="67db2-120">When an object is refreshed, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] change tracker holds the following data:</span></span><br /><br /> <span data-ttu-id="67db2-121">-   データベースからもともと取得され、更新チェックに使用された値。</span><span class="sxs-lookup"><span data-stu-id="67db2-121">-   The values originally taken from the database and used for the update check.</span></span><br /><span data-ttu-id="67db2-122">-   その後のクエリで取得された新しいデータベース値。</span><span class="sxs-lookup"><span data-stu-id="67db2-122">-   The new database values from the subsequent query.</span></span><br /><br /> <span data-ttu-id="67db2-123">次に [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、オブジェクトが競合しているかどうか (つまり 1 つまたは複数のメンバー値が変更されているかどうか) を判断します。</span><span class="sxs-lookup"><span data-stu-id="67db2-123">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] then determines whether the object is in conflict (that is, whether one or more of its member values has changed).</span></span> <span data-ttu-id="67db2-124">オブジェクトが競合している場合、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では次に、どのメンバーが競合しているかが判断されます。</span><span class="sxs-lookup"><span data-stu-id="67db2-124">If the object is in conflict, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] next determines which of its members are in conflict.</span></span><br /><br /> <span data-ttu-id="67db2-125">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が見つけたメンバーの競合は、競合の一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="67db2-125">Any member conflict that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] discovers is added to a conflict list.</span></span>|  
  
 <span data-ttu-id="67db2-126">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のオブジェクト モデルで "*オプティミスティック コンカレンシーの競合*" が発生するのは、次の 2 つの条件が両方とも成り立つ場合です。</span><span class="sxs-lookup"><span data-stu-id="67db2-126">In the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model, an *optimistic concurrency conflict* occurs when both of the following conditions are true:</span></span>  
  
- <span data-ttu-id="67db2-127">クライアントがデータベースに変更を送信しようとした。</span><span class="sxs-lookup"><span data-stu-id="67db2-127">The client tries to submit changes to the database.</span></span>  
  
- <span data-ttu-id="67db2-128">データベースで、そのクライアントによる最後の読み取り以降に、1 つまたは複数の更新チェック値が更新されている。</span><span class="sxs-lookup"><span data-stu-id="67db2-128">One or more update-check values have been updated in the database since the client last read them.</span></span>  
  
 <span data-ttu-id="67db2-129">この競合を解決するためには、オブジェクトのどのメンバーが競合しているかを判別し、どのように対処するかを決定することが必要です。</span><span class="sxs-lookup"><span data-stu-id="67db2-129">Resolution of this conflict includes discovering which members of the object are in conflict, and then deciding what you want to do about it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="67db2-130">オプティミスティック コンカレンシーのチェックに関与するのは、<xref:System.Data.Linq.Mapping.UpdateCheck.Always> または <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> として割り当てられているメンバーのみです。</span><span class="sxs-lookup"><span data-stu-id="67db2-130">Only members mapped as <xref:System.Data.Linq.Mapping.UpdateCheck.Always> or <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> participate in optimistic concurrency checks.</span></span> <span data-ttu-id="67db2-131"><xref:System.Data.Linq.Mapping.UpdateCheck.Never> と指定されているメンバーには、チェックは実行されません。</span><span class="sxs-lookup"><span data-stu-id="67db2-131">No check is performed for members marked <xref:System.Data.Linq.Mapping.UpdateCheck.Never>.</span></span> <span data-ttu-id="67db2-132">詳細については、「<xref:System.Data.Linq.Mapping.UpdateCheck>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67db2-132">For more information, see <xref:System.Data.Linq.Mapping.UpdateCheck>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67db2-133">例</span><span class="sxs-lookup"><span data-stu-id="67db2-133">Example</span></span>  

 <span data-ttu-id="67db2-134">次のシナリオは、ユーザー 1 が、更新の手始めとして、データベースの行をクエリした状況です。</span><span class="sxs-lookup"><span data-stu-id="67db2-134">For example, in the following scenario, User1 starts to prepare an update by querying the database for a row.</span></span> <span data-ttu-id="67db2-135">ユーザー 1 が取得した行には、Alfreds、Maria、および Sales という値が入っています。</span><span class="sxs-lookup"><span data-stu-id="67db2-135">User1 receives a row with values of Alfreds, Maria, and Sales.</span></span>  
  
 <span data-ttu-id="67db2-136">ユーザー 1 は、Manager 列の値を Alfred に、また Department 列の値を Marketing に、それぞれ変更しようと考えています。</span><span class="sxs-lookup"><span data-stu-id="67db2-136">User1 wants to change the value of the Manager column to Alfred and the value of the Department column to Marketing.</span></span> <span data-ttu-id="67db2-137">しかし、ユーザー 1 がその変更を発行する前に、ユーザー 2 がデータベースに変更を送信しました。</span><span class="sxs-lookup"><span data-stu-id="67db2-137">Before User1 can submit those changes, User2 has submitted changes to the database.</span></span> <span data-ttu-id="67db2-138">その結果、Assistant 列の値は Mary に、また Department 列の値は Service に、それぞれ変更されました。</span><span class="sxs-lookup"><span data-stu-id="67db2-138">So now the value of the Assistant column has been changed to Mary and the value of the Department column to Service.</span></span>  
  
 <span data-ttu-id="67db2-139">ここで、ユーザー 1 が変更を送信しようとすると、送信は失敗し、<xref:System.Data.Linq.ChangeConflictException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="67db2-139">When User1 now tries to submit changes, the submission fails and a <xref:System.Data.Linq.ChangeConflictException> exception is thrown.</span></span> <span data-ttu-id="67db2-140">このような結果になるのは、データベースの Assistant 列と Department 列の値が、予期した値と異なるためです。</span><span class="sxs-lookup"><span data-stu-id="67db2-140">This result occurs because the database values for the Assistant column and the Department column are not those that were expected.</span></span> <span data-ttu-id="67db2-141">Assistant 列と Department 列を表すメンバーが競合しています。</span><span class="sxs-lookup"><span data-stu-id="67db2-141">Members representing the Assistant and Department columns are in conflict.</span></span> <span data-ttu-id="67db2-142">この状況をまとめると次の表のようになります。</span><span class="sxs-lookup"><span data-stu-id="67db2-142">The following table summarizes the situation.</span></span>  
  
||<span data-ttu-id="67db2-143">管理者</span><span class="sxs-lookup"><span data-stu-id="67db2-143">Manager</span></span>|<span data-ttu-id="67db2-144">Assistant</span><span class="sxs-lookup"><span data-stu-id="67db2-144">Assistant</span></span>|<span data-ttu-id="67db2-145">Department</span><span class="sxs-lookup"><span data-stu-id="67db2-145">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="67db2-146">元の状態</span><span class="sxs-lookup"><span data-stu-id="67db2-146">Original state</span></span>|<span data-ttu-id="67db2-147">Alfreds</span><span class="sxs-lookup"><span data-stu-id="67db2-147">Alfreds</span></span>|<span data-ttu-id="67db2-148">Maria</span><span class="sxs-lookup"><span data-stu-id="67db2-148">Maria</span></span>|<span data-ttu-id="67db2-149">Sales</span><span class="sxs-lookup"><span data-stu-id="67db2-149">Sales</span></span>|  
|<span data-ttu-id="67db2-150">ユーザー 1</span><span class="sxs-lookup"><span data-stu-id="67db2-150">User1</span></span>|<span data-ttu-id="67db2-151">Alfred</span><span class="sxs-lookup"><span data-stu-id="67db2-151">Alfred</span></span>||<span data-ttu-id="67db2-152">Marketing</span><span class="sxs-lookup"><span data-stu-id="67db2-152">Marketing</span></span>|  
|<span data-ttu-id="67db2-153">ユーザー 2</span><span class="sxs-lookup"><span data-stu-id="67db2-153">User2</span></span>||<span data-ttu-id="67db2-154">Mary</span><span class="sxs-lookup"><span data-stu-id="67db2-154">Mary</span></span>|<span data-ttu-id="67db2-155">サービス</span><span class="sxs-lookup"><span data-stu-id="67db2-155">Service</span></span>|  
  
 <span data-ttu-id="67db2-156">このような競合は、いくつかの方法で解決できます。</span><span class="sxs-lookup"><span data-stu-id="67db2-156">You can resolve conflicts such as this in different ways.</span></span> <span data-ttu-id="67db2-157">詳細については、[変更の競合を管理する](how-to-manage-change-conflicts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67db2-157">For more information, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="conflict-detection-and-resolution-checklist"></a><span data-ttu-id="67db2-158">競合の検出と解決のチェック リスト</span><span class="sxs-lookup"><span data-stu-id="67db2-158">Conflict Detection and Resolution Checklist</span></span>  

 <span data-ttu-id="67db2-159">競合の検出と解決は、さまざまな詳細レベルで行うことができます。</span><span class="sxs-lookup"><span data-stu-id="67db2-159">You can detect and resolve conflicts at any level of detail.</span></span> <span data-ttu-id="67db2-160">極端な方法としては、すべての競合を 3 つの方法 (<xref:System.Data.Linq.RefreshMode> を参照) のいずれかで 1 つで解決し、それ以外の考慮を一切加えないという方法もあります。</span><span class="sxs-lookup"><span data-stu-id="67db2-160">At one extreme, you can resolve all conflicts in one of three ways (see <xref:System.Data.Linq.RefreshMode>) without additional consideration.</span></span> <span data-ttu-id="67db2-161">正反対の方法としては、競合している各メンバーについて、それぞれの競合の種類ごとに、特定の処理を指定するという方法もあります。</span><span class="sxs-lookup"><span data-stu-id="67db2-161">At the other extreme, you can designate a specific action for each type of conflict on every member in conflict.</span></span>  
  
- <span data-ttu-id="67db2-162">オブジェクト モデルの <xref:System.Data.Linq.Mapping.UpdateCheck> オプションを指定または変更します。</span><span class="sxs-lookup"><span data-stu-id="67db2-162">Specify or revise <xref:System.Data.Linq.Mapping.UpdateCheck> options in your object model.</span></span>  
  
     <span data-ttu-id="67db2-163">詳細については、[コンカレンシーの競合を検査するメンバーを指定する](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67db2-163">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span></span>  
  
- <span data-ttu-id="67db2-164"><xref:System.Data.Linq.DataContext.SubmitChanges%2A> の呼び出しの try/catch ブロックで、例外がどの時点でスローされるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="67db2-164">In the try/catch block of your call to <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, specify at what point you want exceptions to be thrown.</span></span>  
  
     <span data-ttu-id="67db2-165">詳細については、[コンカレンシー例外をいつスローするかを指定する](how-to-specify-when-concurrency-exceptions-are-thrown.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67db2-165">For more information, see [How to: Specify When Concurrency Exceptions are Thrown](how-to-specify-when-concurrency-exceptions-are-thrown.md).</span></span>  
  
- <span data-ttu-id="67db2-166">取得する競合の詳細さを判断し、それに応じたコードを try/catch ブロックに記述します。</span><span class="sxs-lookup"><span data-stu-id="67db2-166">Determine how much conflict detail you want to retrieve, and include code in your try/catch block accordingly.</span></span>  
  
     <span data-ttu-id="67db2-167">詳細については、[エンティティの競合情報を取得する](how-to-retrieve-entity-conflict-information.md)」および「[方法: メンバーの競合情報を取得する](how-to-retrieve-member-conflict-information.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67db2-167">For more information, see [How to: Retrieve Entity Conflict Information](how-to-retrieve-entity-conflict-information.md) and [How to: Retrieve Member Conflict Information](how-to-retrieve-member-conflict-information.md).</span></span>  
  
- <span data-ttu-id="67db2-168">`try`/`catch` コードで、発見されたさまざまな競合を解決する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="67db2-168">Include in your `try`/`catch` code how you want to resolve the various conflicts you discover.</span></span>  
  
     <span data-ttu-id="67db2-169">詳細については、[データベース値を維持することで競合を解決する](how-to-resolve-conflicts-by-retaining-database-values.md)」、「[方法: データベース値を上書きすることで競合を解決する](how-to-resolve-conflicts-by-overwriting-database-values.md)」、「[方法: データベース値とマージすることで競合を解決する](how-to-resolve-conflicts-by-merging-with-database-values.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67db2-169">For more information, see [How to: Resolve Conflicts by Retaining Database Values](how-to-resolve-conflicts-by-retaining-database-values.md), [How to: Resolve Conflicts by Overwriting Database Values](how-to-resolve-conflicts-by-overwriting-database-values.md), and [How to: Resolve Conflicts by Merging with Database Values](how-to-resolve-conflicts-by-merging-with-database-values.md).</span></span>  
  
## <a name="linq-to-sql-types-that-support-conflict-discovery-and-resolution"></a><span data-ttu-id="67db2-170">競合の発見と解決をサポートする LINQ to SQL の型</span><span class="sxs-lookup"><span data-stu-id="67db2-170">LINQ to SQL Types That Support Conflict Discovery and Resolution</span></span>  

 <span data-ttu-id="67db2-171">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で、オプティミスティック コンカレンシーの競合の解決をサポートするクラスと機能を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="67db2-171">Classes and features to support the resolution of conflicts in optimistic concurrency in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] include the following:</span></span>  
  
- <xref:System.Data.Linq.ObjectChangeConflict?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.MemberChangeConflict?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.ChangeConflictCollection?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.ChangeConflictException?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.ChangeConflicts%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.Refresh%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.Mapping.UpdateCheck?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.RefreshMode?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="67db2-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="67db2-172">See also</span></span>

- [<span data-ttu-id="67db2-173">方法: 変更の競合を管理する</span><span class="sxs-lookup"><span data-stu-id="67db2-173">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
