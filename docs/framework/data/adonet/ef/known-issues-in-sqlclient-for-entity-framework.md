---
description: '詳細情報: Entity Framework 用の .NET Framework Data Provider for SQL Server (SqlClient) の既知の問題'
title: Entity Framework 用の .NET Framework Data Provider for SQL Server (SqlClient) の既知の問題
ms.date: 03/30/2017
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
ms.openlocfilehash: c1a82657f1b43cddb858692d055df3bf2dca47ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697336"
---
# <a name="known-issues-in-sqlclient-for-entity-framework"></a><span data-ttu-id="1dd36-103">Entity Framework 用の .NET Framework Data Provider for SQL Server (SqlClient) の既知の問題</span><span class="sxs-lookup"><span data-stu-id="1dd36-103">Known Issues in SqlClient for Entity Framework</span></span>

<span data-ttu-id="1dd36-104">ここでは、.NET Framework Data Provider for SQL Server (SqlClient) に関連する既知の問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="1dd36-104">This section describes known issues related to the .NET Framework Data Provider for SQL Server (SqlClient).</span></span>  
  
## <a name="trailing-spaces-in-string-functions"></a><span data-ttu-id="1dd36-105">文字列関数の末尾のスペース</span><span class="sxs-lookup"><span data-stu-id="1dd36-105">Trailing Spaces in String Functions</span></span>  

 <span data-ttu-id="1dd36-106">SQL Server では、文字列値の末尾のスペースは無視されます。</span><span class="sxs-lookup"><span data-stu-id="1dd36-106">SQL Server ignores trailing spaces in string values.</span></span> <span data-ttu-id="1dd36-107">そのため、文字列の末尾にスペースを挿入すると、予期できない結果が生じたり、場合によってはエラーが発生することもあります。</span><span class="sxs-lookup"><span data-stu-id="1dd36-107">Therefore, passing trailing spaces in the string can lead to unpredictable results, even failures.</span></span>  
  
 <span data-ttu-id="1dd36-108">文字列の末尾にスペースを挿入する必要がある場合は、SQL Server で文字列が切り捨てられることがないように、空白文字を挿入することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="1dd36-108">If you have to have trailing spaces in your string, you should consider appending a white space character at the end, so that SQL Server does not trim the string.</span></span> <span data-ttu-id="1dd36-109">末尾のスペースが不要である場合は、クエリ パイプラインに渡す前にスペースを削除してください。</span><span class="sxs-lookup"><span data-stu-id="1dd36-109">If the trailing spaces are not required, they should be trimmed before they are passed down the query pipeline.</span></span>  
  
## <a name="right-function"></a><span data-ttu-id="1dd36-110">RIGHT 関数</span><span class="sxs-lookup"><span data-stu-id="1dd36-110">RIGHT Function</span></span>  

 <span data-ttu-id="1dd36-111">`RIGHT(nvarchar(max)`, 0`)` または `RIGHT(varchar(max)`, 0`)` に、最初の引数として `null` 以外の値を、2 番目の引数として 0 を渡すと、`empty` 文字列の代わりに `NULL` 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="1dd36-111">If a non-`null` value is passed as a first argument and 0 is passed as a second argument to `RIGHT(nvarchar(max)`, 0`)` or `RIGHT(varchar(max)`, 0`)`, a `NULL` value will be returned instead of an `empty` string.</span></span>  
  
## <a name="cross-and-outer-apply-operators"></a><span data-ttu-id="1dd36-112">CROSS APPLY 演算子および OUTER APPLY 演算子</span><span class="sxs-lookup"><span data-stu-id="1dd36-112">CROSS and OUTER APPLY Operators</span></span>  

 <span data-ttu-id="1dd36-113">CROSS APPLY 演算子および OUTER APPLY 演算子は SQL Server 2005 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="1dd36-113">CROSS and OUTER APPLY operators were introduced in SQL Server 2005.</span></span> <span data-ttu-id="1dd36-114">場合によっては、クエリ パイプラインにより、CROSS APPLY 演算子または OUTER APPLY 演算子を含む Transact-SQL ステートメントが生成されることがあります。</span><span class="sxs-lookup"><span data-stu-id="1dd36-114">In some cases the query pipeline might produce a Transact-SQL statement that contains CROSS APPLY and/or OUTER APPLY operators.</span></span> <span data-ttu-id="1dd36-115">一部のバックエンド プロバイダー (SQL Server 2005 より古いバージョンの SQL Server など) では、これらの演算子がサポートされていません。したがって、このようなクエリをこれらのバックエンド プロバイダーで実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="1dd36-115">Because some backend providers, including versions of SQL Server earlier than SQL Server 2005, do not support these operators, such queries cannot be executed on these backend providers.</span></span>  
  
 <span data-ttu-id="1dd36-116">CROSS APPLY 演算子または OUTER APPLY 演算子を含むクエリの生成につながる可能性がある一般的なシナリオを次に示します。</span><span class="sxs-lookup"><span data-stu-id="1dd36-116">The following are some typical scenarios that might lead to the presence of CROSS APPLY and/or OUTER APPLY operators in the output query:</span></span>  
  
- <span data-ttu-id="1dd36-117">ページングを使用した相関サブクエリ</span><span class="sxs-lookup"><span data-stu-id="1dd36-117">A correlated subquery with paging.</span></span>  
  
- <span data-ttu-id="1dd36-118">相関サブクエリ全体、またはナビゲーションによって生成されたコレクション全体を対象とした `AnyElement`</span><span class="sxs-lookup"><span data-stu-id="1dd36-118">An `AnyElement` over a correlated sub-query, or over a collection produced by navigation.</span></span>  
  
- <span data-ttu-id="1dd36-119">要素セレクターを受け取るグループ化メソッドを使用する LINQ クエリ</span><span class="sxs-lookup"><span data-stu-id="1dd36-119">LINQ queries that use grouping methods that accept an element selector.</span></span>  
  
- <span data-ttu-id="1dd36-120">CROSS APPLY 演算子または OUTER APPLY 演算子が明示的に指定されたクエリ</span><span class="sxs-lookup"><span data-stu-id="1dd36-120">A query in which a CROSS APPLY or an OUTER APPLY is explicitly specified</span></span>  
  
- <span data-ttu-id="1dd36-121">REF コンストラクターを引数に取る DEREF コンストラクターを含むクエリ。</span><span class="sxs-lookup"><span data-stu-id="1dd36-121">A query that has a DEREF construct over a REF construct.</span></span>  
  
## <a name="skip-operator"></a><span data-ttu-id="1dd36-122">SKIP 演算子</span><span class="sxs-lookup"><span data-stu-id="1dd36-122">SKIP Operator</span></span>  

 <span data-ttu-id="1dd36-123">SQL Server 2000 を使用している場合、キー以外の列で ORDER BY と共に SKIP を使用すると、不適切な結果が返される場合があります。</span><span class="sxs-lookup"><span data-stu-id="1dd36-123">If you are using SQL Server 2000, using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="1dd36-124">キー以外の列に重複するデータが存在する場合、指定された数を超える行はスキップされます。</span><span class="sxs-lookup"><span data-stu-id="1dd36-124">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="1dd36-125">これは、SQL Server 2000 での SKIP の変換方法によるものです。</span><span class="sxs-lookup"><span data-stu-id="1dd36-125">This is due to how SKIP is translated for SQL Server 2000.</span></span> <span data-ttu-id="1dd36-126">たとえば、次のクエリでは、`E.NonKeyColumn` に重複値が存在する場合、5 行を超える行はスキップされます。</span><span class="sxs-lookup"><span data-stu-id="1dd36-126">For example, in the following query, more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>  
  
```sql  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## <a name="targeting-the-correct-sql-server-version"></a><span data-ttu-id="1dd36-127">適切なバージョンの SQL Server を対象としたクエリの実行</span><span class="sxs-lookup"><span data-stu-id="1dd36-127">Targeting the Correct SQL Server Version</span></span>  

 <span data-ttu-id="1dd36-128">Entity Framework では、ストレージ モデル (.ssdl) ファイルの Schema 要素の `ProviderManifestToken` 属性で指定されている SQL Server のバージョンに基づいて、実行対象の Transact-SQL クエリが決定されます。</span><span class="sxs-lookup"><span data-stu-id="1dd36-128">The Entity Framework targets the Transact-SQL query based on the SQL Server version that is specified in the `ProviderManifestToken` attribute of the Schema element in the storage model (.ssdl) file.</span></span> <span data-ttu-id="1dd36-129">このバージョンは、実際に接続する SQL Server のバージョンとは異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="1dd36-129">This version might differ from the version of the actual SQL Server you are connected to.</span></span> <span data-ttu-id="1dd36-130">たとえば、使用している SQL Server のバージョンが 2005 で、`ProviderManifestToken` 属性が 2008 に設定されている場合、生成された Transact-SQL クエリがサーバーで実行されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="1dd36-130">For example, if you are using SQL Server 2005, but your `ProviderManifestToken` attribute is set to 2008, the generated Transact-SQL query might not execute on the server.</span></span> <span data-ttu-id="1dd36-131">たとえば、SQL Server 2008 で導入された新しい日時型を使用するクエリは、以前のバージョンの SQL Server では実行されません。</span><span class="sxs-lookup"><span data-stu-id="1dd36-131">For example, a query that uses the new date time types that were introduced in SQL Server 2008 will not execute on earlier versions of the SQL Server.</span></span> <span data-ttu-id="1dd36-132">使用している SQL Server のバージョンが 2005 で、`ProviderManifestToken` 属性が 2000 に設定されている場合、生成された Transact-SQL クエリが十分に最適化されなかったり、クエリがサポートされていないことを示す例外が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="1dd36-132">If you are using SQL Server 2005, but your `ProviderManifestToken` attribute is set to 2000, the generated Transact-SQL query might be less optimized, or you might get an exception that says that the query is not supported.</span></span> <span data-ttu-id="1dd36-133">詳細については、このトピックの「CROSS APPLY 演算子および OUTER APPLY 演算子」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1dd36-133">For more information, see the CROSS and OUTER APPLY Operators section, earlier in this topic.</span></span>  
  
 <span data-ttu-id="1dd36-134">データベースの一部の動作は、データベースの互換性レベルの設定に依存します。</span><span class="sxs-lookup"><span data-stu-id="1dd36-134">Certain database behaviors depend on the compatibility level set to the database.</span></span> <span data-ttu-id="1dd36-135">使用している SQL Server のバージョンが 2005 で、`ProviderManifestToken` 属性が 2005 に、データベースの互換性レベルが "80" (SQL Server 2000) に設定されている場合、生成された Transact-SQL の実行対象は SQL Server 2005 になりますが、互換性レベルの設定が原因で予期したとおりに実行されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="1dd36-135">If your `ProviderManifestToken` attribute is set to 2005 and your SQL Server version is 2005, but the compatibility level of a database is set to "80" (SQL Server 2000), the generated Transact-SQL will be targeting SQL Server 2005, but might not execute as expected due to the compatibility level setting.</span></span> <span data-ttu-id="1dd36-136">たとえば、ORDER BY リストの列名とセレクターの列名が一致する場合、順序付けが失われることがあります。</span><span class="sxs-lookup"><span data-stu-id="1dd36-136">For example, you might lose ordering information if a column name in the ORDER BY list matches a column name in the selector.</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="1dd36-137">投影内の入れ子になったクエリ</span><span class="sxs-lookup"><span data-stu-id="1dd36-137">Nested Queries in Projection</span></span>  

 <span data-ttu-id="1dd36-138">projection 句内の入れ子になったクエリは、サーバーでデカルト積に変換されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="1dd36-138">Nested queries in a projection clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="1dd36-139">SQL Server などの一部のバックエンド サーバーでは、これにより TempDB テーブルが非常に大きくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="1dd36-139">On some back-end servers, including SQL Server, this can cause the TempDB table to get quite large.</span></span> <span data-ttu-id="1dd36-140">サーバーのパフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1dd36-140">This can decrease server performance.</span></span>  
  
 <span data-ttu-id="1dd36-141">projection 句内の入れ子になったクエリの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1dd36-141">The following is an example of a nested query in a projection clause:</span></span>  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="server-generated-guid-identity-values"></a><span data-ttu-id="1dd36-142">サーバー生成の GUID ID 値</span><span class="sxs-lookup"><span data-stu-id="1dd36-142">Server Generated GUID Identity Values</span></span>  

 <span data-ttu-id="1dd36-143">Entity Framework では、サーバー生成の GUID 型 ID 値がサポートされますが、プロバイダーは、サーバー生成の ID 値を行の挿入後に返す動作をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1dd36-143">The Entity Framework supports server-generated GUID type identity values, but the provider must support returning the server-generated identity value after a row was inserted.</span></span> <span data-ttu-id="1dd36-144">SQL Server 2005 以降では、SQL Server データベース内のサーバー生成 GUID 型を [OUTPUT 句](/sql/t-sql/queries/output-clause-transact-sql)で返すことができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="1dd36-144">Starting with SQL Server 2005, you can return the server-generated GUID type in a SQL Server database through the [OUTPUT clause](/sql/t-sql/queries/output-clause-transact-sql).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1dd36-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="1dd36-145">See also</span></span>

- [<span data-ttu-id="1dd36-146">Entity Framework 用 SqlClient</span><span class="sxs-lookup"><span data-stu-id="1dd36-146">SqlClient for the Entity Framework</span></span>](sqlclient-for-the-entity-framework.md)
- [<span data-ttu-id="1dd36-147">LINQ to Entities の既知の問題および注意点</span><span class="sxs-lookup"><span data-stu-id="1dd36-147">Known Issues and Considerations in LINQ to Entities</span></span>](./language-reference/known-issues-and-considerations-in-linq-to-entities.md)
