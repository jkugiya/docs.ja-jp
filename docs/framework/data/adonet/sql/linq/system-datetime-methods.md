---
description: '詳細情報: System.DateTime メソッド'
title: System.DateTime メソッド
ms.date: 03/30/2017
ms.assetid: 4f80700c-e83f-4ab6-af0f-1c9a606e1133
ms.openlocfilehash: b4b732bf41be2a943610a26f5abc33d1bb080d2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681384"
---
# <a name="systemdatetime-methods"></a><span data-ttu-id="610a2-103">System.DateTime メソッド</span><span class="sxs-lookup"><span data-stu-id="610a2-103">System.DateTime Methods</span></span>

<span data-ttu-id="610a2-104">LINQ to SQL でサポートされている以下のメソッド、演算子、およびプロパティは、LINQ to SQL のクエリで使用できます。</span><span class="sxs-lookup"><span data-stu-id="610a2-104">The following LINQ to SQL-supported methods, operators, and properties are available to use in LINQ to SQL queries.</span></span> <span data-ttu-id="610a2-105">メソッド、演算子、またはプロパティがサポートされていない場合は、LINQ to SQL でメンバーを変換して SQL Server で実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="610a2-105">When a method, operator or property is unsupported, LINQ to SQL cannot translate the member for execution on the SQL Server.</span></span> <span data-ttu-id="610a2-106">これらのメンバーはコード内で使用できますが、クエリが Transact-SQL に変換される前、またはデータベースから結果が取得された後で評価する必要があります。</span><span class="sxs-lookup"><span data-stu-id="610a2-106">You may use these members in your code, however, they must be evaluated before the query is translated to Transact-SQL or after the results have been retrieved from the database.</span></span>  
  
## <a name="supported-systemdatetime-members"></a><span data-ttu-id="610a2-107">サポートされている System.DateTime メンバー</span><span class="sxs-lookup"><span data-stu-id="610a2-107">Supported System.DateTime Members</span></span>  

 <span data-ttu-id="610a2-108">オブジェクト モデルまたは外部マッピング ファイルにマッピングされると、LINQ to SQL クエリ内で次の <xref:System.DateTime?displayProperty=nameWithType> メンバーを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="610a2-108">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call the following <xref:System.DateTime?displayProperty=nameWithType> members inside LINQ to SQL queries.</span></span>  
  
|<span data-ttu-id="610a2-109">サポートされている <xref:System.DateTime> メソッド</span><span class="sxs-lookup"><span data-stu-id="610a2-109">Supported <xref:System.DateTime> Methods</span></span>|<span data-ttu-id="610a2-110">サポートされている <xref:System.DateTime> 演算子</span><span class="sxs-lookup"><span data-stu-id="610a2-110">Supported <xref:System.DateTime> Operators</span></span>|<span data-ttu-id="610a2-111">サポートされている <xref:System.DateTime> プロパティ</span><span class="sxs-lookup"><span data-stu-id="610a2-111">Supported <xref:System.DateTime> Properties</span></span>|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Add%2A>|<xref:System.DateTime.op_Addition%2A>|<xref:System.DateTime.Date%2A>|  
|<xref:System.DateTime.AddDays%2A>|<xref:System.DateTime.op_Equality%2A>|<xref:System.DateTime.Day%2A>|  
|<xref:System.DateTime.AddHours%2A>|<xref:System.DateTime.op_GreaterThan%2A>|<xref:System.DateTime.DayOfWeek%2A>|  
|<xref:System.DateTime.AddMilliseconds%2A>|<xref:System.DateTime.op_GreaterThanOrEqual%2A>|<xref:System.DateTime.DayOfYear%2A>|  
|<xref:System.DateTime.AddMinutes%2A>|<xref:System.DateTime.op_Inequality%2A>|<xref:System.DateTime.Hour%2A>|  
|<xref:System.DateTime.AddMonths%2A>|<xref:System.DateTime.op_LessThan%2A>|<xref:System.DateTime.Millisecond%2A>|  
|<xref:System.DateTime.AddSeconds%2A>|<xref:System.DateTime.op_LessThanOrEqual%2A>|<xref:System.DateTime.Minute%2A>|  
|<xref:System.DateTime.AddTicks%2A>|<xref:System.DateTime.op_Subtraction%2A>|<xref:System.DateTime.Month%2A>|  
|<xref:System.DateTime.AddYears%2A>||<xref:System.DateTime.Now%2A>|  
|<xref:System.DateTime.Compare%2A>||<xref:System.DateTime.Second%2A>|  
|<xref:System.DateTime.CompareTo%28System.DateTime%29>||<xref:System.DateTime.TimeOfDay%2A>|  
|<xref:System.DateTime.Equals%28System.DateTime%29>||<xref:System.DateTime.Today%2A>|  
|||<xref:System.DateTime.Year%2A>|  
  
## <a name="members-not-supported-by-linq-to-sql"></a><span data-ttu-id="610a2-112">LINQ to SQL でサポートされていないメンバー</span><span class="sxs-lookup"><span data-stu-id="610a2-112">Members Not Supported by LINQ to SQL</span></span>  

 <span data-ttu-id="610a2-113">以下のメンバーは LINQ to SQL クエリ内でサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="610a2-113">The following members are not supported inside LINQ to SQL queries.</span></span>  
  
|||  
|-|-|  
|<xref:System.DateTime.IsDaylightSavingTime%2A>|<xref:System.DateTime.IsLeapYear%2A>|  
|<xref:System.DateTime.DaysInMonth%2A>|<xref:System.DateTime.ToBinary%2A>|  
|<xref:System.DateTime.ToFileTime%2A>|<xref:System.DateTime.ToFileTimeUtc%2A>|  
|<xref:System.DateTime.ToLongDateString%2A>|<xref:System.DateTime.ToLongTimeString%2A>|  
|<xref:System.DateTime.ToOADate%2A>|<xref:System.DateTime.ToShortDateString%2A>|  
|<xref:System.DateTime.ToShortTimeString%2A>|<xref:System.DateTime.ToUniversalTime%2A>|  
|<xref:System.DateTime.FromBinary%2A>|<xref:System.DateTime.UtcNow%2A>|  
|<xref:System.DateTime.FromFileTime%2A>|<xref:System.DateTime.FromFileTimeUtc%2A>|  
|<xref:System.DateTime.FromOADate%2A>|<xref:System.DateTime.GetDateTimeFormats%2A>|  
  
## <a name="method-translation-example"></a><span data-ttu-id="610a2-114">メソッドの変換例</span><span class="sxs-lookup"><span data-stu-id="610a2-114">Method Translation Example</span></span>  

 <span data-ttu-id="610a2-115">LINQ to SQL でサポートされているメソッドはすべて、SQL Server に送信される前に Transact-SQL に変換されます。</span><span class="sxs-lookup"><span data-stu-id="610a2-115">All methods supported by LINQ to SQL are translated to Transact-SQL before they are sent to   SQL Server.</span></span> <span data-ttu-id="610a2-116">たとえば、次のようなパターンを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="610a2-116">For example, consider the following pattern.</span></span>  
  
 `(dateTime1 – dateTime2).{Days, Hours, Milliseconds, Minutes, Months, Seconds, Years}`  
  
 <span data-ttu-id="610a2-117">認識されると、次のように SQL Server の `DATEDIFF` 関数の直接呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="610a2-117">When it is recognized, it is translated into a direct call to the SQL Server `DATEDIFF` function, as follows:</span></span>  
  
 `DATEDIFF({DatePart}, @dateTime1, @dateTime2)`  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="610a2-118">SQLMethods の日付と時刻のメソッド</span><span class="sxs-lookup"><span data-stu-id="610a2-118">SQLMethods Date and Time Methods</span></span>  

 <span data-ttu-id="610a2-119">LINQ to SQL では、<xref:System.DateTime> 構造体で提供されるメソッドの他に、次の表に示すように、日付と時刻を操作する <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> クラスのメソッドも提供しています。</span><span class="sxs-lookup"><span data-stu-id="610a2-119">In addition to the methods offered by the <xref:System.DateTime> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="610a2-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="610a2-120">See also</span></span>

- [<span data-ttu-id="610a2-121">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="610a2-121">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="610a2-122">オブジェクト モデルの作成</span><span class="sxs-lookup"><span data-stu-id="610a2-122">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="610a2-123">SQL と CLR の型マッピング</span><span class="sxs-lookup"><span data-stu-id="610a2-123">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
- [<span data-ttu-id="610a2-124">データ型と関数</span><span class="sxs-lookup"><span data-stu-id="610a2-124">Data Types and Functions</span></span>](data-types-and-functions.md)
