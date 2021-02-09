---
description: '詳細情報: System.TimeSpan メソッド'
title: System.TimeSpan メソッド
ms.date: 03/30/2017
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
ms.openlocfilehash: fa3192d18a59e589f2c7510776f8510b2c12cac4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681189"
---
# <a name="systemtimespan-methods"></a><span data-ttu-id="72ea2-103">System.TimeSpan メソッド</span><span class="sxs-lookup"><span data-stu-id="72ea2-103">System.TimeSpan Methods</span></span>

<span data-ttu-id="72ea2-104"><xref:System.TimeSpan?displayProperty=nameWithType> のメンバー サポートは、使用している .NET Framework と Microsoft SQL Server のバージョンに大きく依存します。</span><span class="sxs-lookup"><span data-stu-id="72ea2-104">Member support for <xref:System.TimeSpan?displayProperty=nameWithType> greatly depends on the versions of the .NET Framework and Microsoft SQL Server that you are using.</span></span>  
  
 <span data-ttu-id="72ea2-105">メソッド、演算子、またはプロパティがサポートされていなければ、LINQ to SQL でメンバーを変換して SQL Server で実行することができません。</span><span class="sxs-lookup"><span data-stu-id="72ea2-105">When a method, operator, or property is unsupported; it means that LINQ to SQL cannot translate the member for execution on the SQL Server.</span></span> <span data-ttu-id="72ea2-106">それでもこれらのメンバーをコードで使用することはできますが、</span><span class="sxs-lookup"><span data-stu-id="72ea2-106">You may still be able to use these members in your code.</span></span> <span data-ttu-id="72ea2-107">クエリが Transact-SQL に変換される前か、データベースから結果が取得された後で評価する必要があります。</span><span class="sxs-lookup"><span data-stu-id="72ea2-107">However, they must be evaluated before the query is translated to Transact-SQL or after the results have been retrieved from the database.</span></span>  
  
## <a name="previous-limitations"></a><span data-ttu-id="72ea2-108">以前の制限</span><span class="sxs-lookup"><span data-stu-id="72ea2-108">Previous Limitations</span></span>  

 <span data-ttu-id="72ea2-109">.NET Framework 3.5 SP1 より前のバージョンの .NET Framework で LINQ to SQL を使用すると、SQL Server のデータベース フィールドを <xref:System.TimeSpan?displayProperty=nameWithType> にマッピングできません。</span><span class="sxs-lookup"><span data-stu-id="72ea2-109">When using LINQ to SQL with versions of the .NET Framework prior to .NET Framework 3.5 SP1, you cannot map SQL Server database fields to <xref:System.TimeSpan?displayProperty=nameWithType>.</span></span> <span data-ttu-id="72ea2-110">ただし、<xref:System.TimeSpan> 値を <xref:System.TimeSpan> 減算から返したり、リテラル変数またはバインド変数として式に取り込んだりできるため、<xref:System.DateTime> の操作はサポートされています。</span><span class="sxs-lookup"><span data-stu-id="72ea2-110">However, operations on <xref:System.TimeSpan> are supported because <xref:System.TimeSpan> values can be returned from <xref:System.DateTime> subtraction or introduced into an expression as a literal or bound variable.</span></span>  
  
## <a name="supported-systemtimespan-member-support"></a><span data-ttu-id="72ea2-111">サポートされている System.TimeSpan メンバーのサポート</span><span class="sxs-lookup"><span data-stu-id="72ea2-111">Supported System.TimeSpan member support</span></span>

 <span data-ttu-id="72ea2-112">LINQ to SQL でサポートされている以下のメソッド、演算子、およびプロパティは、LINQ to SQL のクエリで使用できます。</span><span class="sxs-lookup"><span data-stu-id="72ea2-112">The following LINQ to SQL-supported methods, operators, and properties are available for you to use in your LINQ to SQL queries.</span></span> <span data-ttu-id="72ea2-113">オブジェクト モデルまたは外部マッピング ファイルにマッピングされると、LINQ to SQL クエリ内で <xref:System.TimeSpan?displayProperty=nameWithType> メンバーの多くを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="72ea2-113">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call many of the <xref:System.TimeSpan?displayProperty=nameWithType> members inside your LINQ to SQL queries.</span></span>  
  
|<span data-ttu-id="72ea2-114">サポートされている <xref:System.TimeSpan> メソッド</span><span class="sxs-lookup"><span data-stu-id="72ea2-114">Supported <xref:System.TimeSpan> Methods</span></span>|<span data-ttu-id="72ea2-115">サポートされている <xref:System.TimeSpan> 演算子</span><span class="sxs-lookup"><span data-stu-id="72ea2-115">Supported <xref:System.TimeSpan> Operators</span></span>|<span data-ttu-id="72ea2-116">サポートされている <xref:System.TimeSpan> プロパティ</span><span class="sxs-lookup"><span data-stu-id="72ea2-116">Supported <xref:System.TimeSpan> Properties</span></span>|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<xref:System.TimeSpan.MinValue>|  
  
> [!NOTE]
> <span data-ttu-id="72ea2-117">LINQ to SQL で <xref:System.TimeSpan?displayProperty=nameWithType> を SQL の `TIME` 列にマッピングする機能を使用するには、.NET Framework 3.5 SP1 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="72ea2-117">The ability to map <xref:System.TimeSpan?displayProperty=nameWithType> to a SQL `TIME` column with LINQ to SQL requires the .NET Framework 3.5 SP1 and beyond.</span></span> <span data-ttu-id="72ea2-118">SQL の `TIME` データ型は Microsoft SQL Server 2008 以降でのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="72ea2-118">The SQL `TIME` data type is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
### <a name="addition-and-subtraction"></a><span data-ttu-id="72ea2-119">加算と減算</span><span class="sxs-lookup"><span data-stu-id="72ea2-119">Addition and Subtraction</span></span>  

 <span data-ttu-id="72ea2-120">加算と減算は、CLR の <xref:System.TimeSpan?displayProperty=nameWithType> 型ではサポートされていますが、SQL の `TIME` 型ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="72ea2-120">Although the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type does support addition and subtraction, the SQL `TIME` type does not.</span></span> <span data-ttu-id="72ea2-121">そのため、LINQ to SQL クエリにより、SQL の `TIME` 型にマッピングしたときに加算や減算を試みると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="72ea2-121">Because of this, your LINQ to SQL queries will generate errors if they attempt addition and subtraction when they are mapped to the SQL `TIME` type.</span></span> <span data-ttu-id="72ea2-122">SQL の日付/時刻型の操作に関するその他の注意点については、「[SQL と CLR の型マッピング](sql-clr-type-mapping.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72ea2-122">You can find other considerations for working with SQL date and time types in [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72ea2-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="72ea2-123">See also</span></span>

- [<span data-ttu-id="72ea2-124">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="72ea2-124">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="72ea2-125">オブジェクト モデルの作成</span><span class="sxs-lookup"><span data-stu-id="72ea2-125">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="72ea2-126">SQL と CLR の型マッピング</span><span class="sxs-lookup"><span data-stu-id="72ea2-126">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
- [<span data-ttu-id="72ea2-127">データ型と関数</span><span class="sxs-lookup"><span data-stu-id="72ea2-127">Data Types and Functions</span></span>](data-types-and-functions.md)
