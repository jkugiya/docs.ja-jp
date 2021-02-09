---
description: '詳細情報: トラブルシューティング'
title: トラブルシューティング
ms.date: 03/30/2017
ms.assetid: 8cd4401c-b12c-4116-a421-f3dcffa65670
ms.openlocfilehash: f62d6dbcd8a248cd684bed224ee62b3a205d7174
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681020"
---
# <a name="troubleshooting"></a><span data-ttu-id="6439f-103">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="6439f-103">Troubleshooting</span></span>

<span data-ttu-id="6439f-104">ここでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションで発生する可能性のある問題をいくつか示し、そうした問題を回避または影響を軽減するための提案を示します。</span><span class="sxs-lookup"><span data-stu-id="6439f-104">The following information exposes some issues you might encounter in your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications, and provides suggestions to avoid or otherwise reduce the effect of these issues.</span></span>  
  
 <span data-ttu-id="6439f-105">その他の問題については、「[よく寄せられる質問](frequently-asked-questions.md)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6439f-105">Additional issues are addressed in [Frequently Asked Questions](frequently-asked-questions.md).</span></span>  
  
## <a name="unsupported-standard-query-operators"></a><span data-ttu-id="6439f-106">サポートされない標準クエリ演算子</span><span class="sxs-lookup"><span data-stu-id="6439f-106">Unsupported Standard Query Operators</span></span>  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="6439f-107">は、すべての標準クエリ演算子メソッド (たとえば <xref:System.Linq.Enumerable.ElementAt%2A>) をサポートするわけではありません。</span><span class="sxs-lookup"><span data-stu-id="6439f-107">does not support all standard query operator methods (for example, <xref:System.Linq.Enumerable.ElementAt%2A>).</span></span> <span data-ttu-id="6439f-108">このため、コンパイルできたプロジェクトでも、ランタイム エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6439f-108">As a result, projects that compile can still produce run-time errors.</span></span> <span data-ttu-id="6439f-109">詳細については、「[標準クエリ演算子の変換](standard-query-operator-translation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6439f-109">For more information, see [Standard Query Operator Translation](standard-query-operator-translation.md).</span></span>  
  
## <a name="memory-issues"></a><span data-ttu-id="6439f-110">メモリの問題</span><span class="sxs-lookup"><span data-stu-id="6439f-110">Memory Issues</span></span>  

 <span data-ttu-id="6439f-111">クエリにメモリ内コレクションと [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の <xref:System.Data.Linq.Table%601> が含まれる場合、2 つのコレクションの指定順序に応じて、メモリ内でクエリが実行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6439f-111">If a query involves an in-memory collection and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601>, the query might be executed in memory, depending on the order in which the two collections are specified.</span></span> <span data-ttu-id="6439f-112">クエリをメモリ内で実行する必要がある場合、データベース テーブルのデータを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6439f-112">If the query must be executed in memory, then the data from the database table will need to be retrieved.</span></span>  
  
 <span data-ttu-id="6439f-113">この手法は非効率的で、メモリとプロセッサの消費量が非常に大きくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6439f-113">This approach is inefficient and could result in significant memory and processor usage.</span></span> <span data-ttu-id="6439f-114">このような複数ドメインのクエリはできる限り使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="6439f-114">Try to avoid such multi-domain queries.</span></span>  
  
## <a name="file-names-and-sqlmetal"></a><span data-ttu-id="6439f-115">ファイル名と SQLMetal</span><span class="sxs-lookup"><span data-stu-id="6439f-115">File Names and SQLMetal</span></span>  

 <span data-ttu-id="6439f-116">入力ファイル名を指定するには、その名前をコマンド ラインに入力ファイルとして追加します。</span><span class="sxs-lookup"><span data-stu-id="6439f-116">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="6439f-117">( **/conn** オプションを使用して) 接続文字列にファイル名を含める操作は、サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6439f-117">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span> <span data-ttu-id="6439f-118">詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6439f-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="class-library-projects"></a><span data-ttu-id="6439f-119">クラス ライブラリ プロジェクト</span><span class="sxs-lookup"><span data-stu-id="6439f-119">Class Library Projects</span></span>  

 <span data-ttu-id="6439f-120">オブジェクト リレーショナル デザイナーによって、プロジェクトの `app.config` ファイルの中に接続文字列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="6439f-120">The Object Relational Designer creates a connection string in the `app.config` file of the project.</span></span> <span data-ttu-id="6439f-121">クラス ライブラリ プロジェクトでは `app.config` ファイルが使用されません。</span><span class="sxs-lookup"><span data-stu-id="6439f-121">In class library projects, the `app.config` file is not used.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="6439f-122">は、デザイン時のファイルで提供される接続文字列を使用します。</span><span class="sxs-lookup"><span data-stu-id="6439f-122">uses the Connection String provided in the design-time files.</span></span> <span data-ttu-id="6439f-123">`app.config` 内の値を変更しても、アプリケーションの接続先データベースは変更されません。</span><span class="sxs-lookup"><span data-stu-id="6439f-123">Changing the value in `app.config` does not change the database to which your application connects.</span></span>  
  
## <a name="cascade-delete"></a><span data-ttu-id="6439f-124">連鎖削除</span><span class="sxs-lookup"><span data-stu-id="6439f-124">Cascade Delete</span></span>  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="6439f-125">は連鎖削除操作をサポートせず、認識もしません。</span><span class="sxs-lookup"><span data-stu-id="6439f-125">does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="6439f-126">制約を持つテーブルの行を削除するには、次のいずれかを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="6439f-126">If you want to delete a row in a table that has constraints against it, you must do either of the following:</span></span>  
  
- <span data-ttu-id="6439f-127">データベース内の外部キー制約で `ON DELETE CASCADE` 規則を設定する。</span><span class="sxs-lookup"><span data-stu-id="6439f-127">Set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database.</span></span>  
  
- <span data-ttu-id="6439f-128">独自のコードを使用して、親オブジェクトの削除を妨げる子オブジェクトを最初に削除する。</span><span class="sxs-lookup"><span data-stu-id="6439f-128">Use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span>  
  
 <span data-ttu-id="6439f-129">このような操作を行わない場合、<xref:System.Data.SqlClient.SqlException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="6439f-129">Otherwise, a <xref:System.Data.SqlClient.SqlException> exception is thrown.</span></span>  
  
 <span data-ttu-id="6439f-130">詳細については、[行をデータベースから削除する](how-to-delete-rows-from-the-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6439f-130">For more information, see [How to: Delete Rows From the Database](how-to-delete-rows-from-the-database.md).</span></span>  
  
## <a name="expression-not-queryable"></a><span data-ttu-id="6439f-131">クエリ可能でない式</span><span class="sxs-lookup"><span data-stu-id="6439f-131">Expression Not Queryable</span></span>  

 <span data-ttu-id="6439f-132">「'型' の式はクエリ不可能です。LINQ プロバイダーに対してアセンブリ参照や名前空間インポートが不足していないことを確認してください」</span><span class="sxs-lookup"><span data-stu-id="6439f-132">If you get the "Expression [expression] is not queryable; are you missing an assembly reference?"</span></span> <span data-ttu-id="6439f-133">というエラーが発生した場合、次の点を確認してください。</span><span class="sxs-lookup"><span data-stu-id="6439f-133">error, make sure of the following:</span></span>  
  
- <span data-ttu-id="6439f-134">アプリケーションが .NET Compact Framework 3.5 を対象としている。</span><span class="sxs-lookup"><span data-stu-id="6439f-134">Your application is targeting .NET Compact Framework 3.5.</span></span>  
  
- <span data-ttu-id="6439f-135">`System.Core.dll` および `System.Data.Linq.dll` への参照が存在する。</span><span class="sxs-lookup"><span data-stu-id="6439f-135">You have a reference to `System.Core.dll` and `System.Data.Linq.dll`.</span></span>  
  
- <span data-ttu-id="6439f-136"><xref:System.Linq> および <xref:System.Data.Linq> のための `Imports` (Visual Basic) または `using` (C#) ディレクティブが存在する。</span><span class="sxs-lookup"><span data-stu-id="6439f-136">You have an `Imports` (Visual Basic) or `using` (C#) directive for <xref:System.Linq> and <xref:System.Data.Linq>.</span></span>  
  
## <a name="duplicatekeyexception"></a><span data-ttu-id="6439f-137">DuplicateKeyException</span><span class="sxs-lookup"><span data-stu-id="6439f-137">DuplicateKeyException</span></span>  

 <span data-ttu-id="6439f-138">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] プロジェクトのデバッグ時に、エンティティのリレーションシップを走査する場合があります。</span><span class="sxs-lookup"><span data-stu-id="6439f-138">In the course of debugging a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project, you might traverse an entity's relations.</span></span> <span data-ttu-id="6439f-139">その際、これらの項目はキャッシュに入り、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] はこれらの存在を認識します。</span><span class="sxs-lookup"><span data-stu-id="6439f-139">Doing so brings these items into the cache, and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] becomes aware of their presence.</span></span> <span data-ttu-id="6439f-140">その後、同じキーの複数の行を生成する <xref:System.Data.Linq.Table%601.Attach%2A> や <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> などのメソッドを実行しようとした場合、<xref:System.Data.Linq.DuplicateKeyException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="6439f-140">If you then try to execute <xref:System.Data.Linq.Table%601.Attach%2A> or <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> or a similar method that produces multiple rows that have the same key, a <xref:System.Data.Linq.DuplicateKeyException> is thrown.</span></span>  
  
## <a name="string-concatenation-exceptions"></a><span data-ttu-id="6439f-141">文字列連結の例外</span><span class="sxs-lookup"><span data-stu-id="6439f-141">String Concatenation Exceptions</span></span>  

 <span data-ttu-id="6439f-142">`[n]text` と他の `[n][var]char` にマップされる複数のオペランドを連結する操作はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="6439f-142">Concatenation on operands mapped to `[n]text` and other `[n][var]char` is not supported.</span></span> <span data-ttu-id="6439f-143">異なる 2 つの型のセットにマップされる文字列を連結しようとすると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="6439f-143">An exception is thrown for concatenation of strings mapped to the two different sets of types.</span></span> <span data-ttu-id="6439f-144">詳細については、「[System.String メソッド](system-string-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6439f-144">For more information, see [System.String Methods](system-string-methods.md).</span></span>  
  
## <a name="skip-and-take-exceptions-in-sql-server-2000"></a><span data-ttu-id="6439f-145">SQL Server 2000 の Skip 例外と Take 例外</span><span class="sxs-lookup"><span data-stu-id="6439f-145">Skip and Take Exceptions in SQL Server 2000</span></span>  

 <span data-ttu-id="6439f-146">SQL Server 2000 データベースに対して <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> または <xref:System.Linq.Queryable.Take%2A> を使用する際には、ID メンバー (<xref:System.Linq.Queryable.Skip%2A>) を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6439f-146">You must use identity members (<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>) when you use <xref:System.Linq.Queryable.Take%2A> or <xref:System.Linq.Queryable.Skip%2A> against a SQL Server 2000 database.</span></span> <span data-ttu-id="6439f-147">クエリは、(結合ではなく) 1 つのテーブルに対して実行されるか、<xref:System.Linq.Queryable.Distinct%2A>、<xref:System.Linq.Queryable.Except%2A>、<xref:System.Linq.Queryable.Intersect%2A>、または <xref:System.Linq.Queryable.Union%2A> 操作である必要があります。さらに、クエリに <xref:System.Linq.Queryable.Concat%2A> 操作を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="6439f-147">The query must be against a single table (that is, not a join), or be a <xref:System.Linq.Queryable.Distinct%2A>, <xref:System.Linq.Queryable.Except%2A>, <xref:System.Linq.Queryable.Intersect%2A>, or <xref:System.Linq.Queryable.Union%2A> operation, and must not include a <xref:System.Linq.Queryable.Concat%2A> operation.</span></span> <span data-ttu-id="6439f-148">詳細については、「[標準クエリ演算子の変換](standard-query-operator-translation.md)」の「SQL Server 2000 のサポート」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6439f-148">For more information, see the "SQL Server 2000 Support" section in [Standard Query Operator Translation](standard-query-operator-translation.md).</span></span>  
  
 <span data-ttu-id="6439f-149">この要件は SQL Server 2005 には適用されません。</span><span class="sxs-lookup"><span data-stu-id="6439f-149">This requirement does not apply to SQL Server 2005.</span></span>  
  
## <a name="groupby-invalidoperationexception"></a><span data-ttu-id="6439f-150">GroupBy InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="6439f-150">GroupBy InvalidOperationException</span></span>  

 <span data-ttu-id="6439f-151">この例外は、たとえば <xref:System.Linq.Enumerable.GroupBy%2A> のように、`boolean` 式でグループ分けする `group x by (Phone==@phone)` クエリ内の列値が null である場合にスローされます。</span><span class="sxs-lookup"><span data-stu-id="6439f-151">This exception is thrown when a column value is null in a <xref:System.Linq.Enumerable.GroupBy%2A> query that groups by a `boolean` expression, such as `group x by (Phone==@phone)`.</span></span> <span data-ttu-id="6439f-152">式が `boolean` であるため、キーは `nullable` `boolean` ではなく、`boolean` と推論されます。</span><span class="sxs-lookup"><span data-stu-id="6439f-152">Because the expression is a `boolean`, the key is inferred to be `boolean`, not `nullable` `boolean`.</span></span> <span data-ttu-id="6439f-153">変換された比較で null が生成される場合、`nullable` `boolean` を `boolean` に割り当てようとして、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="6439f-153">When the translated comparison produces a null, an attempt is made to assign a `nullable` `boolean` to a `boolean`, and the exception is thrown.</span></span>  
  
 <span data-ttu-id="6439f-154">この状態を回避する (null を false と扱う) には、次のような手法を使用してください。</span><span class="sxs-lookup"><span data-stu-id="6439f-154">To avoid this situation (assuming you want to treat nulls as false), use an approach such as the following:</span></span>  
  
 `GroupBy="(Phone != null) && (Phone=@Phone)"`  
  
## <a name="oncreated-partial-method"></a><span data-ttu-id="6439f-155">OnCreated() 部分メソッド</span><span class="sxs-lookup"><span data-stu-id="6439f-155">OnCreated() Partial Method</span></span>  

 <span data-ttu-id="6439f-156">オブジェクト コンストラクターが呼び出されるたびに、生成されたメソッド `OnCreated()` が呼び出されます。これは、元の値をコピーするために [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] がコンストラクターを呼び出す場合にも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="6439f-156">The generated method `OnCreated()` is called each time the object constructor is called, including the scenario in which [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] calls the constructor to make a copy for original values.</span></span> <span data-ttu-id="6439f-157">独自の部分クラスに `OnCreated()` メソッドを実装する場合には、この動作を考慮に入れてください。</span><span class="sxs-lookup"><span data-stu-id="6439f-157">Take this behavior into account if you implement the `OnCreated()` method in your own partial class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6439f-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="6439f-158">See also</span></span>

- [<span data-ttu-id="6439f-159">デバッグのサポート</span><span class="sxs-lookup"><span data-stu-id="6439f-159">Debugging Support</span></span>](debugging-support.md)
- [<span data-ttu-id="6439f-160">よく寄せられる質問</span><span class="sxs-lookup"><span data-stu-id="6439f-160">Frequently Asked Questions</span></span>](frequently-asked-questions.md)
