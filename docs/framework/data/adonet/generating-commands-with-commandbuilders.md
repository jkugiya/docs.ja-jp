---
description: '詳細情報: CommandBuilder でのコマンドの生成'
title: CommandBuilder でのコマンドの生成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e3fb8b5-373b-4f9e-ab03-a22693df8e91
ms.openlocfilehash: 495312f57d497421182384eff23b621130447940
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724103"
---
# <a name="generating-commands-with-commandbuilders"></a><span data-ttu-id="7d33e-103">CommandBuilder でのコマンドの生成</span><span class="sxs-lookup"><span data-stu-id="7d33e-103">Generating Commands with CommandBuilders</span></span>

<span data-ttu-id="7d33e-104">`SelectCommand` プロパティが実行時に動的に指定される場合、たとえばクエリ ツールを使用してユーザーの記述したクエリ構文を解釈する場合は、適切な `InsertCommand`、`UpdateCommand`、または `DeleteCommand` をデザイン時に指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="7d33e-104">When the `SelectCommand` property is dynamically specified at run time, such as through a query tool that takes a textual command from the user, you may not be able to specify the appropriate `InsertCommand`, `UpdateCommand`, or `DeleteCommand` at design time.</span></span> <span data-ttu-id="7d33e-105"><xref:System.Data.DataTable> を単一データベース テーブルに割り当てたり、単一データベースから生成する場合は、<xref:System.Data.Common.DbCommandBuilder> オブジェクトを利用して自動的に `DeleteCommand` の `InsertCommand`、`UpdateCommand`、および <xref:System.Data.Common.DbDataAdapter> を生成できます。</span><span class="sxs-lookup"><span data-stu-id="7d33e-105">If your <xref:System.Data.DataTable> maps to or is generated from a single database table, you can take advantage of the <xref:System.Data.Common.DbCommandBuilder> object to automatically generate the `DeleteCommand`, `InsertCommand`, and `UpdateCommand` of the <xref:System.Data.Common.DbDataAdapter>.</span></span>  
  
 <span data-ttu-id="7d33e-106">コマンドを自動的に生成するための最低限の条件として、`SelectCommand` プロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d33e-106">As a minimum requirement, you must set the `SelectCommand` property in order for automatic command generation to work.</span></span> <span data-ttu-id="7d33e-107">`SelectCommand` プロパティで取得したテーブル スキーマによって、自動的に生成される INSERT、UPDATE、DELETE の各ステートメントの構文が決定されます。</span><span class="sxs-lookup"><span data-stu-id="7d33e-107">The table schema retrieved by the `SelectCommand` property determines the syntax of the automatically generated INSERT, UPDATE, and DELETE statements.</span></span>  
  
 <span data-ttu-id="7d33e-108"><xref:System.Data.Common.DbCommandBuilder> は、INSERT、UPDATE、DELETE の各コマンドを生成するために `SelectCommand` を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d33e-108">The <xref:System.Data.Common.DbCommandBuilder> must execute the `SelectCommand` in order to return the metadata necessary to construct the INSERT, UPDATE, and DELETE SQL commands.</span></span> <span data-ttu-id="7d33e-109">その結果、データ ソースへの追加のトリップが必要になるため、パフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7d33e-109">As a result, an extra trip to the data source is necessary, and this can hinder performance.</span></span> <span data-ttu-id="7d33e-110">最適のパフォーマンスを実現するには、明示的にコマンドを指定し、<xref:System.Data.Common.DbCommandBuilder> を使用しないようにします。</span><span class="sxs-lookup"><span data-stu-id="7d33e-110">To achieve optimal performance, specify your commands explicitly rather than using the <xref:System.Data.Common.DbCommandBuilder>.</span></span>  
  
 <span data-ttu-id="7d33e-111">`SelectCommand` は少なくとも 1 つの主キーまたは一意の列を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d33e-111">The `SelectCommand` must also return at least one primary key or unique column.</span></span> <span data-ttu-id="7d33e-112">どちらも存在しない場合は、`InvalidOperation` 例外が生成され、コマンドは生成されません。</span><span class="sxs-lookup"><span data-stu-id="7d33e-112">If none are present, an `InvalidOperation` exception is generated, and the commands are not generated.</span></span>  
  
 <span data-ttu-id="7d33e-113">`DataAdapter` との関連付けが行われていて、<xref:System.Data.Common.DbCommandBuilder> の `InsertCommand`、`UpdateCommand`、`DeleteCommand` の各プロパティが null 参照である場合、`DataAdapter` は自動的にこれらのプロパティを生成します。</span><span class="sxs-lookup"><span data-stu-id="7d33e-113">When associated with a `DataAdapter`, the <xref:System.Data.Common.DbCommandBuilder> automatically generates the `InsertCommand`, `UpdateCommand`, and `DeleteCommand` properties of the `DataAdapter` if they are null references.</span></span> <span data-ttu-id="7d33e-114">プロパティに対して既に `Command` が存在する場合は、既存の `Command` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="7d33e-114">If a `Command` already exists for a property, the existing `Command` is used.</span></span>  
  
 <span data-ttu-id="7d33e-115">複数のテーブルを結合して作成したデータベース ビューは、単一データベース テーブルとは見なされません。</span><span class="sxs-lookup"><span data-stu-id="7d33e-115">Database views that are created by joining two or more tables together are not considered a single database table.</span></span> <span data-ttu-id="7d33e-116">この場合は、<xref:System.Data.Common.DbCommandBuilder> を使用してコマンドを自動的に生成できないため、コマンドを明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d33e-116">In this instance you cannot use the <xref:System.Data.Common.DbCommandBuilder> to automatically generate commands; you must specify your commands explicitly.</span></span> <span data-ttu-id="7d33e-117">`DataSet` に対する更新を元のデータ ソースに反映させるコマンドを明示的に設定する方法については、「[DataAdapter によるデータ ソースの更新](updating-data-sources-with-dataadapters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d33e-117">For information about explicitly setting commands to resolve updates to a `DataSet` back to the data source, see [Updating Data Sources with DataAdapters](updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="7d33e-118">出力パラメーターを `DataSet` の更新行に割り当てることが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="7d33e-118">You might want to map output parameters back to the updated row of a `DataSet`.</span></span> <span data-ttu-id="7d33e-119">一般的なタスクの 1 つは、データ ソースの自動的に生成された ID フィールドまたはタイムスタンプの値を取得することです。</span><span class="sxs-lookup"><span data-stu-id="7d33e-119">One common task would be retrieving the value of an automatically generated identity field or time stamp from the data source.</span></span> <span data-ttu-id="7d33e-120"><xref:System.Data.Common.DbCommandBuilder> は、既定では更新行の列に出力パラメーターを割り当てません。</span><span class="sxs-lookup"><span data-stu-id="7d33e-120">The <xref:System.Data.Common.DbCommandBuilder> will not map output parameters to columns in an updated row by default.</span></span> <span data-ttu-id="7d33e-121">その場合は、コマンドを明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d33e-121">In this instance you must specify your command explicitly.</span></span> <span data-ttu-id="7d33e-122">自動的に生成された ID フィールドを挿入行の列に割り当てる例については、「[ID 値および Autonumber 値の取得](retrieving-identity-or-autonumber-values.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d33e-122">For an example of mapping an automatically generated identity field back to a column of an inserted row, see [Retrieving Identity or Autonumber Values](retrieving-identity-or-autonumber-values.md).</span></span>  
  
## <a name="rules-for-automatically-generated-commands"></a><span data-ttu-id="7d33e-123">コマンドの自動生成規則</span><span class="sxs-lookup"><span data-stu-id="7d33e-123">Rules for Automatically Generated Commands</span></span>  

 <span data-ttu-id="7d33e-124">コマンドの自動生成規則を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="7d33e-124">The following table shows the rules for how automatically generated commands are generated.</span></span>  
  
|<span data-ttu-id="7d33e-125">コマンド</span><span class="sxs-lookup"><span data-stu-id="7d33e-125">Command</span></span>|<span data-ttu-id="7d33e-126">ルール</span><span class="sxs-lookup"><span data-stu-id="7d33e-126">Rule</span></span>|  
|-------------|----------|  
|`InsertCommand`|<span data-ttu-id="7d33e-127"><xref:System.Data.DataRow.RowState%2A> が <xref:System.Data.DataRowState.Added> に設定されているテーブル内のすべての行に対して、データ ソースの行を挿入します。</span><span class="sxs-lookup"><span data-stu-id="7d33e-127">Inserts a row at the data source for all rows in the table with a <xref:System.Data.DataRow.RowState%2A> of <xref:System.Data.DataRowState.Added>.</span></span> <span data-ttu-id="7d33e-128">更新可能なすべての列に対して値を挿入します (ただし、ID、式、タイムスタンプなどの列は除きます)。</span><span class="sxs-lookup"><span data-stu-id="7d33e-128">Inserts values for all columns that are updateable (but not columns such as identities, expressions, or timestamps).</span></span>|  
|`UpdateCommand`|<span data-ttu-id="7d33e-129">`RowState` が <xref:System.Data.DataRowState.Modified> に設定されているテーブル内のすべての行に対して、データ ソースの行を更新します。</span><span class="sxs-lookup"><span data-stu-id="7d33e-129">Updates rows at the data source for all rows in the table with a `RowState` of <xref:System.Data.DataRowState.Modified>.</span></span> <span data-ttu-id="7d33e-130">ID や式などの更新不可能な列を除く、すべての列の値を更新します。</span><span class="sxs-lookup"><span data-stu-id="7d33e-130">Updates the values of all columns except for columns that are not updateable, such as identities or expressions.</span></span> <span data-ttu-id="7d33e-131">データ ソースの列の値と該当行の主キー列の値が一致し、さらにデータ ソースのその他の列がその行の元の値と一致する、すべての行を更新します。</span><span class="sxs-lookup"><span data-stu-id="7d33e-131">Updates all rows where the column values at the data source match the primary key column values of the row, and where the remaining columns at the data source match the original values of the row.</span></span> <span data-ttu-id="7d33e-132">詳細については、このトピックで後述する「更新および削除のオプティミスティック コンカレンシー モデル」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d33e-132">For more information, see "Optimistic Concurrency Model for Updates and Deletes," later in this topic.</span></span>|  
|`DeleteCommand`|<span data-ttu-id="7d33e-133">`RowState` が <xref:System.Data.DataRowState.Deleted> に設定されているテーブル内のすべての行に対して、データ ソースの行を削除します。</span><span class="sxs-lookup"><span data-stu-id="7d33e-133">Deletes rows at the data source for all rows in the table with a `RowState` of <xref:System.Data.DataRowState.Deleted>.</span></span> <span data-ttu-id="7d33e-134">列の値とその行の主キー列の値が一致し、さらにデータ ソースのその他の列がその行の元の値と一致する、すべての行を削除します。</span><span class="sxs-lookup"><span data-stu-id="7d33e-134">Deletes all rows where the column values match the primary key column values of the row, and where the remaining columns at the data source match the original values of the row.</span></span> <span data-ttu-id="7d33e-135">詳細については、このトピックで後述する「更新および削除のオプティミスティック コンカレンシー モデル」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d33e-135">For more information, see "Optimistic Concurrency Model for Updates and Deletes," later in this topic.</span></span>|  
  
## <a name="optimistic-concurrency-model-for-updates-and-deletes"></a><span data-ttu-id="7d33e-136">更新および削除のオプティミスティック コンカレンシー</span><span class="sxs-lookup"><span data-stu-id="7d33e-136">Optimistic Concurrency Model for Updates and Deletes</span></span>  

 <span data-ttu-id="7d33e-137">UPDATE ステートメントおよび DELETE ステートメントに対するコマンドの自動生成ロジックは、"*オプティミスティック コンカレンシー*" に基づいています。これはつまり、編集時にレコードがロックされず、他のユーザーまたはプロセスがそのレコードをいつでも変更できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="7d33e-137">The logic for generating commands automatically for UPDATE and DELETE statements is based on *optimistic concurrency*--that is, records are not locked for editing and can be modified by other users or processes at any time.</span></span> <span data-ttu-id="7d33e-138">レコードは SELECT ステートメントによって返された後、UPDATE ステートメントまたは DELETE ステートメントの実行前に変更されている可能性もあるため、自動的に生成される UPDATE ステートメントまたは DELETE ステートメントには、元のすべての値を含み、データ ソースから削除されていない行だけを更新するように指定した WHERE 句が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7d33e-138">Because a record could have been modified after it was returned from the SELECT statement, but before the UPDATE or DELETE statement is issued, the automatically generated UPDATE or DELETE statement contains a WHERE clause, specifying that a row is only updated if it contains all original values and has not been deleted from the data source.</span></span> <span data-ttu-id="7d33e-139">これにより、新しいデータが上書きされるのを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="7d33e-139">This is done to avoid overwriting new data.</span></span> <span data-ttu-id="7d33e-140">自動的に生成された更新コマンドが削除済みの行、または <xref:System.Data.DataSet> にある元の値が含まれていない行を更新しようとすると、コマンドはどのレコードにも反映されずに、<xref:System.Data.DBConcurrencyException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="7d33e-140">Where an automatically generated update attempts to update a row that has been deleted or that does not contain the original values found in the <xref:System.Data.DataSet>, the command does not affect any records, and a <xref:System.Data.DBConcurrencyException> is thrown.</span></span>  
  
 <span data-ttu-id="7d33e-141">元の値とは関係なく UPDATE または DELETE を実行する場合は、`UpdateCommand` に明示的に `DataAdapter` を設定し、コマンドの自動生成は行わないでください。</span><span class="sxs-lookup"><span data-stu-id="7d33e-141">If you want the UPDATE or DELETE to complete regardless of original values, you must explicitly set the `UpdateCommand` for the `DataAdapter` and not rely on automatic command generation.</span></span>  
  
## <a name="limitations-of-automatic-command-generation-logic"></a><span data-ttu-id="7d33e-142">コマンドの自動生成ロジックの制限事項</span><span class="sxs-lookup"><span data-stu-id="7d33e-142">Limitations of Automatic Command Generation Logic</span></span>  

 <span data-ttu-id="7d33e-143">コマンドの自動生成には次の制限事項が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d33e-143">The following limitations apply to automatic command generation.</span></span>  
  
### <a name="unrelated-tables-only"></a><span data-ttu-id="7d33e-144">リレーションシップのないテーブルに限定</span><span class="sxs-lookup"><span data-stu-id="7d33e-144">Unrelated Tables Only</span></span>  

 <span data-ttu-id="7d33e-145">コマンドの自動生成ロジックでは、データ ソースの他のテーブルへのリレーションシップを考慮せずに、独立したテーブルを対象として INSERT、UPDATE、または DELETE の各ステートメントを生成します。</span><span class="sxs-lookup"><span data-stu-id="7d33e-145">The automatic command generation logic generates INSERT, UPDATE, or DELETE statements for stand-alone tables without taking into account any relationships to other tables at the data source.</span></span> <span data-ttu-id="7d33e-146">その結果、`Update` を呼び出してデータベースの外部キー制約に関係する列に対する変更を発行すると、エラーが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="7d33e-146">As a result, you may encounter a failure when calling `Update` to submit changes for a column that participates in a foreign key constraint in the database.</span></span> <span data-ttu-id="7d33e-147">このような例外を防ぐには、外部キー制約に関係する列の更新には <xref:System.Data.Common.DbCommandBuilder> を使用せず、更新操作を実行するステートメントを明示的に指定します。</span><span class="sxs-lookup"><span data-stu-id="7d33e-147">To avoid this exception, do not use the <xref:System.Data.Common.DbCommandBuilder> for updating columns involved in a foreign key constraint; instead, explicitly specify the statements used to perform the operation.</span></span>  
  
### <a name="table-and-column-names"></a><span data-ttu-id="7d33e-148">テーブル名と列名</span><span class="sxs-lookup"><span data-stu-id="7d33e-148">Table and Column Names</span></span>  

 <span data-ttu-id="7d33e-149">列名またはテーブル名にスペース、ピリオド (.)、疑問符 (?)、引用符、その他の英数字以外の特殊文字が含まれていると、それらの文字が角かっこで囲まれていても、コマンドの自動生成ロジックはエラーになる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7d33e-149">Automatic command generation logic may fail if column names or table names contain any special characters, such as spaces, periods, quotation marks, or other nonalphanumeric characters, even if delimited by brackets.</span></span> <span data-ttu-id="7d33e-150">プロバイダーによって異なりますが、QuotePrefix パラメーターと QuoteSuffix パラメーターを設定すると、生成ロジックではスペースを処理できる場合があっても、特殊文字をエスケープできません。</span><span class="sxs-lookup"><span data-stu-id="7d33e-150">Depending on the provider, setting the QuotePrefix and QuoteSuffix parameters may allow the generation logic to process spaces, but it cannot escape special characters.</span></span> <span data-ttu-id="7d33e-151">*catalog.schema.table* の形式をとる、テーブルの完全修飾名はサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7d33e-151">Fully qualified table names in the form of *catalog.schema.table* are supported.</span></span>  
  
## <a name="using-the-commandbuilder-to-automatically-generate-an-sql-statement"></a><span data-ttu-id="7d33e-152">CommandBuilder による SQL ステートメントの自動生成</span><span class="sxs-lookup"><span data-stu-id="7d33e-152">Using the CommandBuilder to Automatically Generate an SQL Statement</span></span>  

 <span data-ttu-id="7d33e-153">`DataAdapter` に対して SQL ステートメントを自動的に生成するには、まず `SelectCommand` の `DataAdapter` プロパティを設定します。次に、`CommandBuilder` オブジェクトを作成し、`DataAdapter` で SQL ステートメントを自動的に生成する `CommandBuilder` を引数として指定します。</span><span class="sxs-lookup"><span data-stu-id="7d33e-153">To automatically generate SQL statements for a `DataAdapter`, first set the `SelectCommand` property of the `DataAdapter`, then create a `CommandBuilder` object, and specify as an argument the `DataAdapter` for which the `CommandBuilder` will automatically generate SQL statements.</span></span>  
  
```vb  
' Assumes that connection is a valid SqlConnection object
' inside of a Using block.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers", connection)  
Dim builder As SqlCommandBuilder = New SqlCommandBuilder(adapter)  
builder.QuotePrefix = "["  
builder.QuoteSuffix = "]"  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object  
// inside of a using block.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers", connection);  
SqlCommandBuilder builder = new SqlCommandBuilder(adapter);  
builder.QuotePrefix = "[";  
builder.QuoteSuffix = "]";  
```  
  
## <a name="modifying-the-selectcommand"></a><span data-ttu-id="7d33e-154">SelectCommand の変更</span><span class="sxs-lookup"><span data-stu-id="7d33e-154">Modifying the SelectCommand</span></span>  

 <span data-ttu-id="7d33e-155">INSERT、UPDATE、または DELETE の各コマンドを自動生成した後に `CommandText` の `SelectCommand` を変更すると、例外が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="7d33e-155">If you modify the `CommandText` of the `SelectCommand` after the INSERT, UPDATE, or DELETE commands have been automatically generated, an exception may occur.</span></span> <span data-ttu-id="7d33e-156">変更された `SelectCommand.CommandText` に、INSERT、UPDATE、または DELETE の各コマンドの自動生成時に使用した `SelectCommand.CommandText` と矛盾するスキーマ情報が含まれている場合、後続の `DataAdapter.Update` メソッド呼び出しでアクセスする列は `SelectCommand` によって参照された現在のテーブルには存在しない可能性があり、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="7d33e-156">If the modified `SelectCommand.CommandText` contains schema information that is inconsistent with the `SelectCommand.CommandText` used when the insert, update, or delete commands were automatically generated, future calls to the `DataAdapter.Update` method may attempt to access columns that no longer exist in the current table referenced by the `SelectCommand`, and an exception will be thrown.</span></span>  
  
 <span data-ttu-id="7d33e-157">`CommandBuilder` の `RefreshSchema` メソッドを呼び出すことで、自動的にコマンドを生成する `CommandBuilder` が使用するスキーマ情報を更新できます。</span><span class="sxs-lookup"><span data-stu-id="7d33e-157">You can refresh the schema information used by the `CommandBuilder` to automatically generate commands by calling the `RefreshSchema` method of the `CommandBuilder`.</span></span>  
  
 <span data-ttu-id="7d33e-158">どのコマンドが自動的に生成されたかを確認するには、`GetInsertCommand` オブジェクトの `GetUpdateCommand`、`GetDeleteCommand`、`CommandBuilder` の各メソッドを使用して、自動的に生成されたコマンドへの参照を取得し、関連付けられているコマンドの `CommandText` プロパティを確認します。</span><span class="sxs-lookup"><span data-stu-id="7d33e-158">If you want to know what command was automatically generated, you can obtain a reference to the automatically generated commands by using the `GetInsertCommand`, `GetUpdateCommand`, and `GetDeleteCommand` methods of the `CommandBuilder` object and checking the `CommandText` property of the associated command.</span></span>  
  
 <span data-ttu-id="7d33e-159">自動的に生成された更新コマンドをコンソールに出力するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7d33e-159">The following code example writes to the console the update command that was automatically generated.</span></span>  
  
```vb
Console.WriteLine(builder.GetUpdateCommand().CommandText)  
```

```csharp
Console.WriteLine(builder.GetUpdateCommand().CommandText);
```
  
 <span data-ttu-id="7d33e-160">次の例では、`Customers` データセットに `custDS` テーブルを作成し直します。</span><span class="sxs-lookup"><span data-stu-id="7d33e-160">The following example recreates the `Customers` table in the `custDS` dataset.</span></span> <span data-ttu-id="7d33e-161">**RefreshSchema** メソッドを呼び出し、新しい列情報を使用して、自動的に生成されたコマンドを更新します。</span><span class="sxs-lookup"><span data-stu-id="7d33e-161">The **RefreshSchema** method is called to refresh the automatically generated commands with this new column information.</span></span>  
  
```vb  
' Assumes an open SqlConnection and SqlDataAdapter inside of a Using block.  
adapter.SelectCommand.CommandText = _  
  "SELECT CustomerID, ContactName FROM dbo.Customers"  
builder.RefreshSchema()  
  
custDS.Tables.Remove(custDS.Tables("Customers"))  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
// Assumes an open SqlConnection and SqlDataAdapter inside of a using block.  
adapter.SelectCommand.CommandText =
  "SELECT CustomerID, ContactName FROM dbo.Customers";  
builder.RefreshSchema();  
  
custDS.Tables.Remove(custDS.Tables["Customers"]);  
adapter.Fill(custDS, "Customers");  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d33e-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d33e-162">See also</span></span>

- [<span data-ttu-id="7d33e-163">コマンドおよびパラメーター</span><span class="sxs-lookup"><span data-stu-id="7d33e-163">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="7d33e-164">コマンドの実行</span><span class="sxs-lookup"><span data-stu-id="7d33e-164">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="7d33e-165">DbConnection、DbCommand、および DbException</span><span class="sxs-lookup"><span data-stu-id="7d33e-165">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="7d33e-166">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="7d33e-166">ADO.NET Overview</span></span>](ado-net-overview.md)
