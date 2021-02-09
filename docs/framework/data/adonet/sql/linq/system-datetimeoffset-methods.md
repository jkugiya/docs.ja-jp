---
description: '詳細情報: System.DateTimeOffset メソッド'
title: System.DateTimeOffset メソッド
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 050c710d4a3f3db8112d0d108338c010345afdda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681330"
---
# <a name="systemdatetimeoffset-methods"></a><span data-ttu-id="f720b-103">System.DateTimeOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="f720b-103">System.DateTimeOffset Methods</span></span>

<span data-ttu-id="f720b-104">オブジェクト モデルまたは外部マッピング ファイルにマッピングされると、<xref:System.DateTimeOffset?displayProperty=nameWithType> メソッド、演算子、プロパティのほとんどを LINQ to SQL のクエリ内から呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f720b-104">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call most of the <xref:System.DateTimeOffset?displayProperty=nameWithType> methods, operators, and properties from within your LINQ to SQL queries.</span></span>  
  
 <span data-ttu-id="f720b-105">サポートされていないメソッドは、<xref:System.Object?displayProperty=nameWithType>、`Finalize`、`GetHashCode`、`GetType` など、LINQ to SQL クエリ内のコンテキストで意味を持たない `MemberwiseClone` から継承されたメソッドだけです。</span><span class="sxs-lookup"><span data-stu-id="f720b-105">The only methods not supported are those inherited from <xref:System.Object?displayProperty=nameWithType> that do not make sense in the context of LINQ to SQL queries, such as: `Finalize`, `GetHashCode`, `GetType`, and `MemberwiseClone`.</span></span> <span data-ttu-id="f720b-106">これらのメソッドは LINQ to SQL で変換して SQL Server で実行することができないため、サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f720b-106">These methods are not supported because LINQ to SQL cannot translate them for execution on the SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f720b-107">共通言語ランタイム (CLR) の <xref:System.DateTimeOffset?displayProperty=nameWithType> 構造体、およびそれを LINQ to SQL で SQL の `DATETIMEOFFSET` 列にマッピングする機能を使用するには、.NET Framework 3.5 SP1 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="f720b-107">The common language runtime (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> structure, and the ability to map it to a SQL `DATETIMEOFFSET` column with LINQ to SQL, requires the .NET Framework 3.5 SP1 or beyond.</span></span> <span data-ttu-id="f720b-108">SQL の `DATETIMEOFFSET` 列は、Microsoft SQL Server 2008 以降でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f720b-108">The SQL `DATETIMEOFFSET` column is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="f720b-109">SQLMethods の日付と時刻のメソッド</span><span class="sxs-lookup"><span data-stu-id="f720b-109">SQLMethods Date and Time Methods</span></span>  

 <span data-ttu-id="f720b-110">LINQ to SQL では、<xref:System.DateTimeOffset> 構造体で提供されるメソッドの他に、次の表に示すように、日付と時刻を操作する <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> クラスのメソッドも提供しています。</span><span class="sxs-lookup"><span data-stu-id="f720b-110">In addition to the methods offered by the <xref:System.DateTimeOffset> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="f720b-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="f720b-111">See also</span></span>

- [<span data-ttu-id="f720b-112">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="f720b-112">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="f720b-113">オブジェクト モデルの作成</span><span class="sxs-lookup"><span data-stu-id="f720b-113">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="f720b-114">SQL と CLR の型マッピング</span><span class="sxs-lookup"><span data-stu-id="f720b-114">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
