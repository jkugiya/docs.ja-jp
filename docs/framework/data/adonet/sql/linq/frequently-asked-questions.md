---
description: '詳細情報: よく寄せられる質問'
title: よく寄せられる質問
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 476e9adc3dc88bce786b8b8423e05e800c821320
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739080"
---
# <a name="frequently-asked-questions"></a><span data-ttu-id="a558e-103">よく寄せられる質問</span><span class="sxs-lookup"><span data-stu-id="a558e-103">Frequently Asked Questions</span></span>

<span data-ttu-id="a558e-104">ここでは、LINQ を実装するときに発生する可能性のある一般的な問題の対処法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a558e-104">The following sections answer some common issues that you might encounter when you implement LINQ.</span></span>

<span data-ttu-id="a558e-105">その他の問題については、「[トラブルシューティング](troubleshooting.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a558e-105">Additional issues are addressed in [Troubleshooting](troubleshooting.md).</span></span>

## <a name="cannot-connect"></a><span data-ttu-id="a558e-106">接続できない</span><span class="sxs-lookup"><span data-stu-id="a558e-106">Cannot Connect</span></span>

<span data-ttu-id="a558e-107">Q.</span><span class="sxs-lookup"><span data-stu-id="a558e-107">Q.</span></span> <span data-ttu-id="a558e-108">データベースに接続できません。</span><span class="sxs-lookup"><span data-stu-id="a558e-108">I cannot connect to my database.</span></span>

<span data-ttu-id="a558e-109">A: </span><span class="sxs-lookup"><span data-stu-id="a558e-109">A.</span></span> <span data-ttu-id="a558e-110">接続文字列が正しいこと、および SQL Server のインスタンスが実行中であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a558e-110">Make sure your connection string is correct and that your SQL Server instance is running.</span></span> <span data-ttu-id="a558e-111">また、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、名前付きパイプ プロトコルを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a558e-111">Note also that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] requires the Named Pipes protocol to be enabled.</span></span> <span data-ttu-id="a558e-112">詳しくは、「[チュートリアルによる学習](learning-by-walkthroughs.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a558e-112">For more information, see [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>

## <a name="changes-to-database-lost"></a><span data-ttu-id="a558e-113">データベースの変更内容が失われる</span><span class="sxs-lookup"><span data-stu-id="a558e-113">Changes to Database Lost</span></span>

<span data-ttu-id="a558e-114">Q.</span><span class="sxs-lookup"><span data-stu-id="a558e-114">Q.</span></span> <span data-ttu-id="a558e-115">データベース内のデータを変更しましたが、アプリケーションを再実行すると、変更が元に戻っています。</span><span class="sxs-lookup"><span data-stu-id="a558e-115">I made a change to data in the database, but when I reran my application, the change was no longer there.</span></span>

<span data-ttu-id="a558e-116">A: </span><span class="sxs-lookup"><span data-stu-id="a558e-116">A.</span></span> <span data-ttu-id="a558e-117">変更結果をデータベースに保存するために、必ず <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出してください。</span><span class="sxs-lookup"><span data-stu-id="a558e-117">Make sure that you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> to save results to the database.</span></span>

## <a name="database-connection-open-how-long"></a><span data-ttu-id="a558e-118">データベース接続: どれほどの時間開いているか</span><span class="sxs-lookup"><span data-stu-id="a558e-118">Database Connection: Open How Long?</span></span>

<span data-ttu-id="a558e-119">Q.</span><span class="sxs-lookup"><span data-stu-id="a558e-119">Q.</span></span> <span data-ttu-id="a558e-120">データベース接続が開いている時間は、どれほどですか。</span><span class="sxs-lookup"><span data-stu-id="a558e-120">How long does my database connection remain open?</span></span>

<span data-ttu-id="a558e-121">A: </span><span class="sxs-lookup"><span data-stu-id="a558e-121">A.</span></span> <span data-ttu-id="a558e-122">通常、接続は、クエリ結果を処理するまでは開いた状態を保ちます。</span><span class="sxs-lookup"><span data-stu-id="a558e-122">A connection typically remains open until you consume the query results.</span></span> <span data-ttu-id="a558e-123">すべての結果を処理するのに時間がかかる可能性がある場合、結果をキャッシュに入れることが可能であれば、クエリに対して <xref:System.Linq.Enumerable.ToList%2A> を適用してください。</span><span class="sxs-lookup"><span data-stu-id="a558e-123">If you expect to take time to process all the results and are not opposed to caching the results, apply <xref:System.Linq.Enumerable.ToList%2A> to the query.</span></span> <span data-ttu-id="a558e-124">通常のシナリオでは、各オブジェクトが一度だけ処理されるため、`DataReader` と [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のどちらの場合もストリーミング モデルがより優れています。</span><span class="sxs-lookup"><span data-stu-id="a558e-124">In common scenarios where each object is processed only one time, the streaming model is superior in both `DataReader` and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>

<span data-ttu-id="a558e-125">接続が厳密にどのように使用されるかは、以下に応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="a558e-125">The exact details of connection usage depend on the following:</span></span>

- <span data-ttu-id="a558e-126">接続オブジェクトを使って <xref:System.Data.Linq.DataContext> が作成されている場合は、接続状態。</span><span class="sxs-lookup"><span data-stu-id="a558e-126">Connection status if the <xref:System.Data.Linq.DataContext> is constructed with a connection object.</span></span>

- <span data-ttu-id="a558e-127">接続文字列の設定 (たとえば、複数のアクティブな結果セット (MARS) の有効化)。</span><span class="sxs-lookup"><span data-stu-id="a558e-127">Connection string settings (for example, enabling Multiple Active Result Sets (MARS).</span></span> <span data-ttu-id="a558e-128">詳細については、「 [複数のアクティブな結果セット (MARS)](../multiple-active-result-sets-mars.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a558e-128">For more information, see [Multiple Active Result Sets (MARS)](../multiple-active-result-sets-mars.md).</span></span>

## <a name="updating-without-querying"></a><span data-ttu-id="a558e-129">クエリを使用しない更新</span><span class="sxs-lookup"><span data-stu-id="a558e-129">Updating Without Querying</span></span>

<span data-ttu-id="a558e-130">Q.</span><span class="sxs-lookup"><span data-stu-id="a558e-130">Q.</span></span> <span data-ttu-id="a558e-131">データベースに対してあらかじめクエリを実行せずに、テーブル データを更新できますか?</span><span class="sxs-lookup"><span data-stu-id="a558e-131">Can I update table data without first querying the database?</span></span>

<span data-ttu-id="a558e-132">A: </span><span class="sxs-lookup"><span data-stu-id="a558e-132">A.</span></span> <span data-ttu-id="a558e-133">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] にはセットベースの更新コマンドはありませんが、次のいずれかの技法を使用すると、あらかじめクエリを実行せずに更新できます。</span><span class="sxs-lookup"><span data-stu-id="a558e-133">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not have set-based update commands, you can use either of the following techniques to update without first querying:</span></span>

- <span data-ttu-id="a558e-134"><xref:System.Data.Linq.DataContext.ExecuteCommand%2A> を使って SQL コードを送信する。</span><span class="sxs-lookup"><span data-stu-id="a558e-134">Use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to send SQL code.</span></span>

- <span data-ttu-id="a558e-135">オブジェクトの新しいインスタンスを作成し、更新に関連したすべての現在値 (フィールド) を初期化する。</span><span class="sxs-lookup"><span data-stu-id="a558e-135">Create a new instance of the object and initialize all the current values (fields) that affect the update.</span></span> <span data-ttu-id="a558e-136">その後、<xref:System.Data.Linq.DataContext> を使ってオブジェクトを <xref:System.Data.Linq.Table%601.Attach%2A> に関連付け、更新対象のフィールドを変更します。</span><span class="sxs-lookup"><span data-stu-id="a558e-136">Then attach the object to the <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.Table%601.Attach%2A> and modify the field you want to change.</span></span>

## <a name="unexpected-query-results"></a><span data-ttu-id="a558e-137">予期しないクエリ結果</span><span class="sxs-lookup"><span data-stu-id="a558e-137">Unexpected Query Results</span></span>

<span data-ttu-id="a558e-138">Q.</span><span class="sxs-lookup"><span data-stu-id="a558e-138">Q.</span></span> <span data-ttu-id="a558e-139">予期しない結果がクエリから返されます。</span><span class="sxs-lookup"><span data-stu-id="a558e-139">My query is returning unexpected results.</span></span> <span data-ttu-id="a558e-140">どうなっているのか調べる方法はありますか。</span><span class="sxs-lookup"><span data-stu-id="a558e-140">How can I inspect what is occurring?</span></span>

<span data-ttu-id="a558e-141">A: </span><span class="sxs-lookup"><span data-stu-id="a558e-141">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a558e-142">には、生成された SQL コードを調べるためのツールがいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="a558e-142">provides several tools for inspecting the SQL code it generates.</span></span> <span data-ttu-id="a558e-143">このうち、最も重要なものは <xref:System.Data.Linq.DataContext.Log%2A> です。</span><span class="sxs-lookup"><span data-stu-id="a558e-143">One of the most important is <xref:System.Data.Linq.DataContext.Log%2A>.</span></span> <span data-ttu-id="a558e-144">詳しくは、「[デバッグのサポート](debugging-support.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a558e-144">For more information, see [Debugging Support](debugging-support.md).</span></span>

## <a name="unexpected-stored-procedure-results"></a><span data-ttu-id="a558e-145">予期しないストアド プロシージャ結果</span><span class="sxs-lookup"><span data-stu-id="a558e-145">Unexpected Stored Procedure Results</span></span>

<span data-ttu-id="a558e-146">Q.</span><span class="sxs-lookup"><span data-stu-id="a558e-146">Q.</span></span> <span data-ttu-id="a558e-147">戻り値が `MAX()` によって計算されるストアド プロシージャがあります。</span><span class="sxs-lookup"><span data-stu-id="a558e-147">I have a stored procedure whose return value is calculated by `MAX()`.</span></span> <span data-ttu-id="a558e-148">このストアド プロシージャを O/R デザイナーのサーフェイスにドラッグすると、戻り値が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="a558e-148">When I drag the stored procedure to the O/R Designer surface, the return value is not correct.</span></span>

<span data-ttu-id="a558e-149">A: </span><span class="sxs-lookup"><span data-stu-id="a558e-149">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a558e-150">には、ストアド プロシージャを介して、データベースによって生成される値を返す方法が 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="a558e-150">provides two ways to return database-generated values by way of stored procedures:</span></span>

- <span data-ttu-id="a558e-151">出力結果に名前を付ける。</span><span class="sxs-lookup"><span data-stu-id="a558e-151">By naming the output result.</span></span>

- <span data-ttu-id="a558e-152">出力パラメーターを明示的に指定する。</span><span class="sxs-lookup"><span data-stu-id="a558e-152">By explicitly specifying an output parameter.</span></span>

<span data-ttu-id="a558e-153">間違っている出力例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="a558e-153">The following is an example of incorrect output.</span></span> <span data-ttu-id="a558e-154">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は結果をマップできないため、常に 0 が返されます。</span><span class="sxs-lookup"><span data-stu-id="a558e-154">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot map the results, it always returns 0:</span></span>

```sql
create procedure proc2

as

begin

select max(i) from t where name like 'hello'

end
```

<span data-ttu-id="a558e-155">出力パラメーターを使用して正しい出力をする例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a558e-155">The following is an example of correct output by using an output parameter:</span></span>

```sql
create procedure proc2

@result int OUTPUT

as

select @result = MAX(i) from t where name like 'hello'

go
```

<span data-ttu-id="a558e-156">出力結果に名前を付けて正しい出力をする例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a558e-156">The following is an example of correct output by naming the output result:</span></span>

```sql
create procedure proc2

as

begin

select nax(i) AS MaxResult from t where name like 'hello'

end
```

<span data-ttu-id="a558e-157">詳しくは、「[ストアド プロシージャによる操作のカスタマイズ](customizing-operations-by-using-stored-procedures.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a558e-157">For more information, see [Customizing Operations By Using Stored Procedures](customizing-operations-by-using-stored-procedures.md).</span></span>

## <a name="serialization-errors"></a><span data-ttu-id="a558e-158">シリアル化のエラー</span><span class="sxs-lookup"><span data-stu-id="a558e-158">Serialization Errors</span></span>

<span data-ttu-id="a558e-159">Q.</span><span class="sxs-lookup"><span data-stu-id="a558e-159">Q.</span></span> <span data-ttu-id="a558e-160">シリアル化を試みると、次のエラーが発生します: "アセンブリ ... の型 'System.Data.Linq.ChangeTracker+StandardChangeTracker' はシリアル化可能として設定されていません。"</span><span class="sxs-lookup"><span data-stu-id="a558e-160">When I try to serialize, I get the following error: "Type 'System.Data.Linq.ChangeTracker+StandardChangeTracker' ... is not marked as serializable."</span></span>

<span data-ttu-id="a558e-161">A: </span><span class="sxs-lookup"><span data-stu-id="a558e-161">A.</span></span> <span data-ttu-id="a558e-162">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のコード生成では、<xref:System.Runtime.Serialization.DataContractSerializer> のシリアル化がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a558e-162">Code generation in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports <xref:System.Runtime.Serialization.DataContractSerializer> serialization.</span></span> <span data-ttu-id="a558e-163"><xref:System.Xml.Serialization.XmlSerializer> および <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="a558e-163">It does not support <xref:System.Xml.Serialization.XmlSerializer> or <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="a558e-164">詳細については、「[Serialization](serialization.md)」 (シリアル化) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a558e-164">For more information, see [Serialization](serialization.md).</span></span>

## <a name="multiple-dbml-files"></a><span data-ttu-id="a558e-165">複数の DBML ファイル</span><span class="sxs-lookup"><span data-stu-id="a558e-165">Multiple DBML Files</span></span>

<span data-ttu-id="a558e-166">Q.</span><span class="sxs-lookup"><span data-stu-id="a558e-166">Q.</span></span> <span data-ttu-id="a558e-167">いくつかのテーブルを共有する複数の DBML ファイルが存在する場合は、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="a558e-167">When I have multiple DBML files that share some tables in common, I get a compiler error.</span></span>

<span data-ttu-id="a558e-168">A: </span><span class="sxs-lookup"><span data-stu-id="a558e-168">A.</span></span> <span data-ttu-id="a558e-169">オブジェクト リレーショナル デザイナーで、 **[コンテキストの名前空間]** プロパティと **[エンティティの名前空間]** プロパティに、DBML ファイルごとに個別の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="a558e-169">Set the **Context Namespace** and **Entity Namespace** properties from the Object Relational Designer to a distinct value for each DBML file.</span></span> <span data-ttu-id="a558e-170">この手法により、名前および名前空間の競合を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="a558e-170">This approach eliminates the name/namespace collision.</span></span>

## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a><span data-ttu-id="a558e-171">挿入または更新で、データベース生成値を明示的に設定しなくても良いようにする</span><span class="sxs-lookup"><span data-stu-id="a558e-171">Avoiding Explicit Setting of Database-Generated Values on Insert or Update</span></span>

<span data-ttu-id="a558e-172">Q.</span><span class="sxs-lookup"><span data-stu-id="a558e-172">Q.</span></span> <span data-ttu-id="a558e-173">あるデータベース テーブルに `DateCreated` という列があり、その既定値は SQL `Getdate()` です。</span><span class="sxs-lookup"><span data-stu-id="a558e-173">I have a database table with a `DateCreated` column that defaults to SQL `Getdate()`.</span></span> <span data-ttu-id="a558e-174">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用して新しいレコードを挿入しようとすると、値が `NULL` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="a558e-174">When I try to insert a new record by using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the value gets set to `NULL`.</span></span> <span data-ttu-id="a558e-175">データベースの既定値が設定されるようにするには、どうしたらいいですか。</span><span class="sxs-lookup"><span data-stu-id="a558e-175">I would expect it to be set to the database default.</span></span>

<span data-ttu-id="a558e-176">A: </span><span class="sxs-lookup"><span data-stu-id="a558e-176">A.</span></span> <span data-ttu-id="a558e-177">ID 列 (自動インクリメント)、rowguidcol 列 (データベースが生成した GUID)、およびタイムスタンプ列の場合は、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が、このような状況に自動的に対処します。</span><span class="sxs-lookup"><span data-stu-id="a558e-177">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] handles this situation automatically for identity (auto-increment) and rowguidcol (database-generated GUID) and timestamp columns.</span></span> <span data-ttu-id="a558e-178">それ以外の場合には、<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>=`true` および <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>=<xref:System.Data.Linq.Mapping.AutoSync.Always>/<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>/<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> プロパティを手動で設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a558e-178">In other cases, you should manually set <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>=`true` and <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>=<xref:System.Data.Linq.Mapping.AutoSync.Always>/<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>/<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> properties.</span></span>

## <a name="multiple-dataloadoptions"></a><span data-ttu-id="a558e-179">複数の DataLoadOptions</span><span class="sxs-lookup"><span data-stu-id="a558e-179">Multiple DataLoadOptions</span></span>

<span data-ttu-id="a558e-180">Q.</span><span class="sxs-lookup"><span data-stu-id="a558e-180">Q.</span></span> <span data-ttu-id="a558e-181">最初の読み込みオプションを上書きせずに、追加の読み込みオプションを指定できますか?</span><span class="sxs-lookup"><span data-stu-id="a558e-181">Can I specify additional load options without overwriting the first?</span></span>

<span data-ttu-id="a558e-182">A: </span><span class="sxs-lookup"><span data-stu-id="a558e-182">A.</span></span> <span data-ttu-id="a558e-183">はい。</span><span class="sxs-lookup"><span data-stu-id="a558e-183">Yes.</span></span> <span data-ttu-id="a558e-184">次の例のように、最初のオプションは上書きされません。</span><span class="sxs-lookup"><span data-stu-id="a558e-184">The first is not overwritten, as in the following example:</span></span>

```vb
Dim dlo As New DataLoadOptions()
dlo.LoadWith(Of Order)(Function(o As Order) o.Customer)
dlo.LoadWith(Of Order)(Function(o As Order) o.OrderDetails)
```

```csharp
DataLoadOptions dlo = new DataLoadOptions();
dlo.LoadWith<Order>(o => o.Customer);
dlo.LoadWith<Order>(o => o.OrderDetails);
```

## <a name="errors-using-sql-compact-35"></a><span data-ttu-id="a558e-185">SQL Compact 3.5 の使用に関するエラー</span><span class="sxs-lookup"><span data-stu-id="a558e-185">Errors Using SQL Compact 3.5</span></span>

<span data-ttu-id="a558e-186">Q.</span><span class="sxs-lookup"><span data-stu-id="a558e-186">Q.</span></span> <span data-ttu-id="a558e-187">テーブルを SQL Server Compact 3.5 データベースからドラッグすると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="a558e-187">I get an error when I drag tables out of a SQL Server Compact 3.5 database.</span></span>

<span data-ttu-id="a558e-188">A: </span><span class="sxs-lookup"><span data-stu-id="a558e-188">A.</span></span> <span data-ttu-id="a558e-189">オブジェクト リレーショナル デザイナーでは SQL Server Compact 3.5 はサポートされていませんが、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ランタイムではサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a558e-189">The Object Relational Designer does not support SQL Server Compact 3.5, although the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime does.</span></span> <span data-ttu-id="a558e-190">この場合、独自のエンティティ クラスを作成して適切な属性を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a558e-190">In this situation, you must create your own entity classes and add the appropriate attributes.</span></span>

## <a name="errors-in-inheritance-relationships"></a><span data-ttu-id="a558e-191">継承関係でのエラー</span><span class="sxs-lookup"><span data-stu-id="a558e-191">Errors in Inheritance Relationships</span></span>

<span data-ttu-id="a558e-192">Q.</span><span class="sxs-lookup"><span data-stu-id="a558e-192">Q.</span></span> <span data-ttu-id="a558e-193">オブジェクト リレーショナル デザイナーでツールボックスの継承図形を使って、2 つのエンティティを接続すると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="a558e-193">I used the toolbox inheritance shape in the Object Relational Designer to connect two entities, but I get errors.</span></span>

<span data-ttu-id="a558e-194">A: </span><span class="sxs-lookup"><span data-stu-id="a558e-194">A.</span></span> <span data-ttu-id="a558e-195">関係を作成するだけでは不十分です。</span><span class="sxs-lookup"><span data-stu-id="a558e-195">Creating the relationship is not enough.</span></span> <span data-ttu-id="a558e-196">識別子の列、基本クラスの識別子の値、派生クラスの識別子の値などの情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a558e-196">You must provide information such as the discriminator column, base class discriminator value, and derived class discriminator value.</span></span>

## <a name="provider-model"></a><span data-ttu-id="a558e-197">プロバイダー モデル</span><span class="sxs-lookup"><span data-stu-id="a558e-197">Provider Model</span></span>

<span data-ttu-id="a558e-198">Q.</span><span class="sxs-lookup"><span data-stu-id="a558e-198">Q.</span></span> <span data-ttu-id="a558e-199">パブリック プロバイダー モデルを利用できますか?</span><span class="sxs-lookup"><span data-stu-id="a558e-199">Is a public provider model available?</span></span>

<span data-ttu-id="a558e-200">A: </span><span class="sxs-lookup"><span data-stu-id="a558e-200">A.</span></span> <span data-ttu-id="a558e-201">いいえ。使用可能なパブリック プロバイダー モデルはありません。</span><span class="sxs-lookup"><span data-stu-id="a558e-201">No public provider model is available.</span></span> <span data-ttu-id="a558e-202">現時点では、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では SQL Server と SQL Server Compact 3.5 のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a558e-202">At this time, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports SQL Server and SQL Server Compact 3.5 only.</span></span>

## <a name="sql-injection-attacks"></a><span data-ttu-id="a558e-203">SQL 注入攻撃</span><span class="sxs-lookup"><span data-stu-id="a558e-203">SQL-Injection Attacks</span></span>

<span data-ttu-id="a558e-204">Q.</span><span class="sxs-lookup"><span data-stu-id="a558e-204">Q.</span></span> <span data-ttu-id="a558e-205">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、SQL 注入攻撃からどのように保護されますか?</span><span class="sxs-lookup"><span data-stu-id="a558e-205">How is [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] protected from SQL-injection attacks?</span></span>

<span data-ttu-id="a558e-206">A: </span><span class="sxs-lookup"><span data-stu-id="a558e-206">A.</span></span> <span data-ttu-id="a558e-207">ユーザー入力の連結により形成される従来の SQL クエリでは、SQL 注入が大きなリスクでした。</span><span class="sxs-lookup"><span data-stu-id="a558e-207">SQL injection has been a significant risk for traditional SQL queries formed by concatenating user input.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a558e-208">では、クエリで <xref:System.Data.SqlClient.SqlParameter> を使用することにより、そのような注入を防止します。</span><span class="sxs-lookup"><span data-stu-id="a558e-208">avoids such injection by using <xref:System.Data.SqlClient.SqlParameter> in queries.</span></span> <span data-ttu-id="a558e-209">ユーザー入力はパラメーター値に変換されます。</span><span class="sxs-lookup"><span data-stu-id="a558e-209">User input is turned into parameter values.</span></span> <span data-ttu-id="a558e-210">この手法は、顧客の入力で悪意のあるコマンドが使用されることを防止します。</span><span class="sxs-lookup"><span data-stu-id="a558e-210">This approach prevents malicious commands from being used from customer input.</span></span>

## <a name="changing-read-only-flag-in-dbml-files"></a><span data-ttu-id="a558e-211">DBML ファイル内の読み取り専用フラグの変更</span><span class="sxs-lookup"><span data-stu-id="a558e-211">Changing Read-only Flag in DBML Files</span></span>

<span data-ttu-id="a558e-212">Q.</span><span class="sxs-lookup"><span data-stu-id="a558e-212">Q.</span></span> <span data-ttu-id="a558e-213">DBML ファイルからオブジェクト モデルを作成するときに、どうすれば、特定のプロパティから setter を取り除くことができますか?</span><span class="sxs-lookup"><span data-stu-id="a558e-213">How do I eliminate setters from some properties when I create an object model from a DBML file?</span></span>

<span data-ttu-id="a558e-214">A: </span><span class="sxs-lookup"><span data-stu-id="a558e-214">A.</span></span> <span data-ttu-id="a558e-215">これは高度なシナリオですが、以下の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="a558e-215">Take the following steps for this advanced scenario:</span></span>

1. <span data-ttu-id="a558e-216">.dbml ファイル内で、<xref:System.Data.Linq.ITable.IsReadOnly%2A> フラグを `True` に変更することにより、プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="a558e-216">In the .dbml file, modify the property by changing the <xref:System.Data.Linq.ITable.IsReadOnly%2A> flag to `True`.</span></span>

2. <span data-ttu-id="a558e-217">部分クラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="a558e-217">Add a partial class.</span></span> <span data-ttu-id="a558e-218">読み取り専用メンバー用のパラメーターを使ってコンストラクターを作成します。</span><span class="sxs-lookup"><span data-stu-id="a558e-218">Create a constructor with parameters for the read-only members.</span></span>

3. <span data-ttu-id="a558e-219">既定の <xref:System.Data.Linq.Mapping.UpdateCheck> 値 (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) がアプリケーションにとって適切な値かどうかを検討します。</span><span class="sxs-lookup"><span data-stu-id="a558e-219">Review the default <xref:System.Data.Linq.Mapping.UpdateCheck> value (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) to determine whether that is the correct value for your application.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="a558e-220">Visual Studio でオブジェクト リレーショナル デザイナーを使用している場合は、変更内容が上書きされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a558e-220">If you are using the Object Relational Designer in Visual Studio, your changes might be overwritten.</span></span>

## <a name="aptca"></a><span data-ttu-id="a558e-221">APTCA</span><span class="sxs-lookup"><span data-stu-id="a558e-221">APTCA</span></span>

<span data-ttu-id="a558e-222">Q.</span><span class="sxs-lookup"><span data-stu-id="a558e-222">Q.</span></span> <span data-ttu-id="a558e-223">System.Data.Linq は、部分的に信頼されているコードが使用できるようにマークされていますか?</span><span class="sxs-lookup"><span data-stu-id="a558e-223">Is System.Data.Linq marked for use by partially trusted code?</span></span>

<span data-ttu-id="a558e-224">A: </span><span class="sxs-lookup"><span data-stu-id="a558e-224">A.</span></span> <span data-ttu-id="a558e-225">はい。System.Data.Linq.dll アセンブリは、<xref:System.Security.AllowPartiallyTrustedCallersAttribute> 属性でマークされている .NET Framework アセンブリの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="a558e-225">Yes, the System.Data.Linq.dll assembly is among those .NET Framework assemblies marked with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="a558e-226">このマークがないと、.NET Framework のアセンブリは完全に信頼されたコードによってのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="a558e-226">Without this marking, assemblies in the .NET Framework are intended for use only by fully trusted code.</span></span>

<span data-ttu-id="a558e-227">部分的に信頼される呼び出し元を許可する [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] での主なシナリオは、"*信頼*" の構成が中のときに、Web アプリケーションから [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アセンブリにアクセスできるようにする場合です。</span><span class="sxs-lookup"><span data-stu-id="a558e-227">The principal scenario in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] for allowing partially trusted callers is to enable the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly to be accessed from Web applications, where the *trust* configuration is Medium.</span></span>

## <a name="mapping-data-from-multiple-tables"></a><span data-ttu-id="a558e-228">複数のテーブルからのデータのマッピング</span><span class="sxs-lookup"><span data-stu-id="a558e-228">Mapping Data from Multiple Tables</span></span>

<span data-ttu-id="a558e-229">Q.</span><span class="sxs-lookup"><span data-stu-id="a558e-229">Q.</span></span> <span data-ttu-id="a558e-230">エンティティに、複数のテーブルから取得されたデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a558e-230">The data in my entity comes from multiple tables.</span></span> <span data-ttu-id="a558e-231">どのようにマップできますか?</span><span class="sxs-lookup"><span data-stu-id="a558e-231">How do I map it?</span></span>

<span data-ttu-id="a558e-232">A: </span><span class="sxs-lookup"><span data-stu-id="a558e-232">A.</span></span> <span data-ttu-id="a558e-233">データベース内にビューを作成して、エンティティをそのビューにマップすることができます。</span><span class="sxs-lookup"><span data-stu-id="a558e-233">You can create a view in a database and map the entity to the view.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a558e-234">は、テーブル用と同じ SQL をビュー用に生成します。</span><span class="sxs-lookup"><span data-stu-id="a558e-234">generates the same SQL for views as it does for tables.</span></span>

> [!NOTE]
> <span data-ttu-id="a558e-235">このシナリオでのビューの使用には、制限があります。</span><span class="sxs-lookup"><span data-stu-id="a558e-235">The use of views in this scenario has limitations.</span></span> <span data-ttu-id="a558e-236">この手法は、<xref:System.Data.Linq.Table%601> に対して実行される操作が、基になるビューでサポートされるような場合に、最も安全に機能します。</span><span class="sxs-lookup"><span data-stu-id="a558e-236">This approach works most safely when the operations performed on <xref:System.Data.Linq.Table%601> are supported by the underlying view.</span></span> <span data-ttu-id="a558e-237">どのような操作が意図されるかは、開発者だけが知っています。</span><span class="sxs-lookup"><span data-stu-id="a558e-237">Only you know which operations are intended.</span></span> <span data-ttu-id="a558e-238">たとえば、ほとんどのアプリケーションは読み取り専用です。他の多くのアプリケーションでは、ビューに対してストアド プロシージャを使用することによってのみ、`Create`/`Update`/`Delete` 操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="a558e-238">For example, most applications are read-only, and another sizeable number perform `Create`/`Update`/`Delete` operations only by using stored procedures against views.</span></span>

## <a name="connection-pooling"></a><span data-ttu-id="a558e-239">接続プール</span><span class="sxs-lookup"><span data-stu-id="a558e-239">Connection Pooling</span></span>

<span data-ttu-id="a558e-240">Q.</span><span class="sxs-lookup"><span data-stu-id="a558e-240">Q.</span></span> <span data-ttu-id="a558e-241"><xref:System.Data.Linq.DataContext> プールに役立つコンストラクトはありますか?</span><span class="sxs-lookup"><span data-stu-id="a558e-241">Is there a construct that can help with <xref:System.Data.Linq.DataContext> pooling?</span></span>

<span data-ttu-id="a558e-242">A: </span><span class="sxs-lookup"><span data-stu-id="a558e-242">A.</span></span> <span data-ttu-id="a558e-243"><xref:System.Data.Linq.DataContext> のインスタンスは再使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="a558e-243">Do not try to reuse instances of <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="a558e-244"><xref:System.Data.Linq.DataContext> はそれぞれ、特定の 1 つの編集/クエリ セッション用の状態 (ID キャッシュを含む) を保持します。</span><span class="sxs-lookup"><span data-stu-id="a558e-244">Each <xref:System.Data.Linq.DataContext> maintains state (including an identity cache) for one particular edit/query session.</span></span> <span data-ttu-id="a558e-245">データベースの現在の状態に基づく新しいインスタンスを得るには、新しい <xref:System.Data.Linq.DataContext> を使用してください。</span><span class="sxs-lookup"><span data-stu-id="a558e-245">To obtain new instances based on the current state of the database, use a new <xref:System.Data.Linq.DataContext>.</span></span>

<span data-ttu-id="a558e-246">それでも、基になる ADO.NET 接続プールは使用できます。</span><span class="sxs-lookup"><span data-stu-id="a558e-246">You can still use underlying ADO.NET connection pooling.</span></span> <span data-ttu-id="a558e-247">詳しくは、「[SQL Server の接続プール (ADO.NET)](../../sql-server-connection-pooling.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a558e-247">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../sql-server-connection-pooling.md).</span></span>

## <a name="second-datacontext-is-not-updated"></a><span data-ttu-id="a558e-248">2 番目の DataContext が更新されない</span><span class="sxs-lookup"><span data-stu-id="a558e-248">Second DataContext Is Not Updated</span></span>

<span data-ttu-id="a558e-249">Q.</span><span class="sxs-lookup"><span data-stu-id="a558e-249">Q.</span></span> <span data-ttu-id="a558e-250">データベース内の値を格納するために、<xref:System.Data.Linq.DataContext> の 1 つのインスタンスを使用しました。</span><span class="sxs-lookup"><span data-stu-id="a558e-250">I used one instance of <xref:System.Data.Linq.DataContext> to store values in the database.</span></span> <span data-ttu-id="a558e-251">しかし、同じデータベースに対する 2 番目の <xref:System.Data.Linq.DataContext> では、更新された値が反映されません。</span><span class="sxs-lookup"><span data-stu-id="a558e-251">However, a second <xref:System.Data.Linq.DataContext> on the same database does not reflect the updated values.</span></span> <span data-ttu-id="a558e-252">2 番目の <xref:System.Data.Linq.DataContext> インスタンスは、キャッシュされた値を返すようです。</span><span class="sxs-lookup"><span data-stu-id="a558e-252">The second <xref:System.Data.Linq.DataContext> instance seems to return cached values.</span></span>

<span data-ttu-id="a558e-253">A: </span><span class="sxs-lookup"><span data-stu-id="a558e-253">A.</span></span> <span data-ttu-id="a558e-254">この動作は意図されたものです。</span><span class="sxs-lookup"><span data-stu-id="a558e-254">This behavior is by design.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a558e-255">は、最初のインスタンスと同じインスタンス/値を返し続けます。</span><span class="sxs-lookup"><span data-stu-id="a558e-255">continues to return the same instances/values that you saw in the first instance.</span></span> <span data-ttu-id="a558e-256">更新の際には、オプティミスティック コンカレンシーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a558e-256">When you make updates, you use optimistic concurrency.</span></span> <span data-ttu-id="a558e-257">元のデータを使ってデータベースの現在の状態を検査し、実際に未変更であることをアサートします。</span><span class="sxs-lookup"><span data-stu-id="a558e-257">The original data is used to check against the current database state to assert that it is in fact still unchanged.</span></span> <span data-ttu-id="a558e-258">変更されている場合は競合が発生するため、アプリケーションでそれを解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a558e-258">If it has changed, a conflict occurs and your application must resolve it.</span></span> <span data-ttu-id="a558e-259">1 つのオプションとして、アプリケーションは、元の状態をデータベースの現在の状態にリセットして、更新を再試行できます。</span><span class="sxs-lookup"><span data-stu-id="a558e-259">One option of your application is to reset the original state to the current database state and to try the update again.</span></span> <span data-ttu-id="a558e-260">詳細については、「[方法: 変更の競合を管理する](how-to-manage-change-conflicts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a558e-260">For more information, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>

<span data-ttu-id="a558e-261">また、<xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> を false に設定することもできます。この場合、キャッシュと変更追跡が無効になります。</span><span class="sxs-lookup"><span data-stu-id="a558e-261">You can also set <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to false, which turns off caching and change tracking.</span></span> <span data-ttu-id="a558e-262">その後は、クエリを実行するたびに最新の値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="a558e-262">You can then retrieve the latest values every time that you query.</span></span>

## <a name="cannot-call-submitchanges-in-read-only-mode"></a><span data-ttu-id="a558e-263">読み取り専用モードで SubmitChanges を呼び出すことができない</span><span class="sxs-lookup"><span data-stu-id="a558e-263">Cannot Call SubmitChanges in Read-only Mode</span></span>

<span data-ttu-id="a558e-264">Q.</span><span class="sxs-lookup"><span data-stu-id="a558e-264">Q.</span></span> <span data-ttu-id="a558e-265">読み取り専用モードで <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出そうとすると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="a558e-265">When I try to call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> in read-only mode, I get an error.</span></span>

<span data-ttu-id="a558e-266">A: </span><span class="sxs-lookup"><span data-stu-id="a558e-266">A.</span></span> <span data-ttu-id="a558e-267">読み取り専用モードでは、変更を追跡するコンテキスト機能は無効です。</span><span class="sxs-lookup"><span data-stu-id="a558e-267">Read-only mode turns off the ability of the context to track changes.</span></span>

## <a name="see-also"></a><span data-ttu-id="a558e-268">関連項目</span><span class="sxs-lookup"><span data-stu-id="a558e-268">See also</span></span>

- [<span data-ttu-id="a558e-269">参照</span><span class="sxs-lookup"><span data-stu-id="a558e-269">Reference</span></span>](reference.md)
- [<span data-ttu-id="a558e-270">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="a558e-270">Troubleshooting</span></span>](troubleshooting.md)
- [<span data-ttu-id="a558e-271">LINQ to SQL におけるセキュリティ</span><span class="sxs-lookup"><span data-stu-id="a558e-271">Security in LINQ to SQL</span></span>](security-in-linq-to-sql.md)
