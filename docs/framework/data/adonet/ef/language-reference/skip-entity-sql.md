---
description: '詳細情報: SKIP (Entity SQL)'
title: SKIP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: f4924acae6e351e076b5795cf47d63966ebdcb43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768013"
---
# <a name="skip-entity-sql"></a><span data-ttu-id="0b3dd-103">SKIP (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0b3dd-103">SKIP (Entity SQL)</span></span>

<span data-ttu-id="0b3dd-104">物理的なページングは、ORDER BY 句の SKIP サブ句を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="0b3dd-104">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="0b3dd-105">SKIP を ORDER BY 句と切り離して使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="0b3dd-105">SKIP cannot be used separately from the ORDER BY clause.</span></span>

## <a name="syntax"></a><span data-ttu-id="0b3dd-106">構文</span><span class="sxs-lookup"><span data-stu-id="0b3dd-106">Syntax</span></span>

```sql
[ SKIP n ]
```

## <a name="arguments"></a><span data-ttu-id="0b3dd-107">引数</span><span class="sxs-lookup"><span data-stu-id="0b3dd-107">Arguments</span></span>

`n` \
<span data-ttu-id="0b3dd-108">スキップするアイテムの数。</span><span class="sxs-lookup"><span data-stu-id="0b3dd-108">The number of items to skip.</span></span>

## <a name="remarks"></a><span data-ttu-id="0b3dd-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="0b3dd-109">Remarks</span></span>

<span data-ttu-id="0b3dd-110">SKIP 式のサブ句が ORDER BY 句に存在する場合、結果は並べ替え順序に従って並べ替えられ、結果セットには SKIP 式の直後の行から始まる行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0b3dd-110">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="0b3dd-111">たとえば、SKIP 5 は、先頭の 5 行をスキップし、6 行目以降を返します。</span><span class="sxs-lookup"><span data-stu-id="0b3dd-111">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>

> [!NOTE]
> <span data-ttu-id="0b3dd-112">TOP 修飾子と SKIP サブ句が同じクエリ式内に存在する場合、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリは無効です。</span><span class="sxs-lookup"><span data-stu-id="0b3dd-112">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="0b3dd-113">TOP 式を LIMIT 式に変更してクエリを記述し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="0b3dd-113">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>

> [!NOTE]
> <span data-ttu-id="0b3dd-114">SQL Server 2000 では、キー以外の列で ORDER BY と共に SKIP を使用すると、不適切な結果が返される場合があります。</span><span class="sxs-lookup"><span data-stu-id="0b3dd-114">In SQL Server 2000, using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="0b3dd-115">キー以外の列に重複するデータが存在する場合、指定された数を超える行はスキップされます。</span><span class="sxs-lookup"><span data-stu-id="0b3dd-115">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="0b3dd-116">これは、SQL Server 2000 での SKIP の変換方法によるものです。</span><span class="sxs-lookup"><span data-stu-id="0b3dd-116">This is due to how SKIP is translated for SQL Server 2000.</span></span> <span data-ttu-id="0b3dd-117">たとえば、次のコードでは、 `E.NonKeyColumn` に重複値が存在する場合、5 行を超える行はスキップされます。</span><span class="sxs-lookup"><span data-stu-id="0b3dd-117">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>
>
> ```sql
> SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L
> ```

<span data-ttu-id="0b3dd-118">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のクエリ (「[クエリの結果をページングする方法](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))」で示されているもの) では、ORDER BY 演算子と SKIP を使用して、SELECT ステートメントで返されるオブジェクトで使用される並べ替え順序が指定されています。</span><span class="sxs-lookup"><span data-stu-id="0b3dd-118">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b3dd-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b3dd-119">See also</span></span>

- [<span data-ttu-id="0b3dd-120">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="0b3dd-120">ORDER BY</span></span>](order-by-entity-sql.md)
- <span data-ttu-id="0b3dd-121">[方法: クエリの結果をページングする](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0b3dd-121">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="0b3dd-122">ページング</span><span class="sxs-lookup"><span data-stu-id="0b3dd-122">Paging</span></span>](paging-entity-sql.md)
- [<span data-ttu-id="0b3dd-123">TOP</span><span class="sxs-lookup"><span data-stu-id="0b3dd-123">TOP</span></span>](top-entity-sql.md)
