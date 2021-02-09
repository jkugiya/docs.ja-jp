---
description: '詳細情報: SQL と CLR の型の不一致'
title: SQL と CLR の型の不一致
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
ms.openlocfilehash: 9a2e1d360fc2a54f401572e46d92654f2b9284db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803725"
---
# <a name="sql-clr-type-mismatches"></a><span data-ttu-id="2deac-103">SQL と CLR の型の不一致</span><span class="sxs-lookup"><span data-stu-id="2deac-103">SQL-CLR Type Mismatches</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="2deac-104">はオブジェクト モデルと SQL Server 間の変換のほとんどを自動化します。</span><span class="sxs-lookup"><span data-stu-id="2deac-104">automates much of the translation between the object model and SQL Server.</span></span> <span data-ttu-id="2deac-105">ただし、正確な変換が実行されない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="2deac-105">Nevertheless, some situations prevent exact translation.</span></span> <span data-ttu-id="2deac-106">以下のセクションでは、共通言語ランタイム (CLR) の型と SQL Server データベースの型の主な不一致について概要を示します。</span><span class="sxs-lookup"><span data-stu-id="2deac-106">These key mismatches between the common language runtime (CLR) types and the SQL Server database types are summarized in the following sections.</span></span> <span data-ttu-id="2deac-107">特定の型のマッピングと関数の変換については、「[SQL と CLR の型マッピング](sql-clr-type-mapping.md)」と「[データ型と関数](data-types-and-functions.md)」で詳しく説明しています。</span><span class="sxs-lookup"><span data-stu-id="2deac-107">You can find more details about specific type mappings and function translation at [SQL-CLR Type Mapping](sql-clr-type-mapping.md) and [Data Types and Functions](data-types-and-functions.md).</span></span>

## <a name="data-types"></a><span data-ttu-id="2deac-108">データの種類</span><span class="sxs-lookup"><span data-stu-id="2deac-108">Data Types</span></span>

<span data-ttu-id="2deac-109">CLR と SQL Server 間の変換は、クエリがデータベースに送信されるときと、結果がオブジェクト モデルに返されるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="2deac-109">Translation between the CLR and SQL Server occurs when a query is being sent to the database, and when the results are sent back to your object model.</span></span> <span data-ttu-id="2deac-110">たとえば、次の Transact-SQL では 2 つの値の変換が必要です。</span><span class="sxs-lookup"><span data-stu-id="2deac-110">For example, the following Transact-SQL query requires two value conversions:</span></span>

```sql
Select DateOfBirth From Customer Where CustomerId = @id
```

<span data-ttu-id="2deac-111">SQL Server にクエリを実行する前に、Transact-SQL パラメーターの値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2deac-111">Before the query can be executed on SQL Server, the value for the Transact-SQL parameter must be specified.</span></span> <span data-ttu-id="2deac-112">この例では、データベースが値を認識できるように、最初に `id` パラメーターの値を CLR の <xref:System.Int32?displayProperty=nameWithType> 型から SQL Server の `INT` 型に変換します。</span><span class="sxs-lookup"><span data-stu-id="2deac-112">In this example, the `id` parameter value must first be translated from a CLR <xref:System.Int32?displayProperty=nameWithType> type to a SQL Server `INT` type so that the database can understand what the value is.</span></span> <span data-ttu-id="2deac-113">次に、結果を取得するために、SQL Server の `DateOfBirth` 列を SQL Server の `DATETIME` 型から、オブジェクト モデルで使用できる CLR の <xref:System.DateTime?displayProperty=nameWithType> 型に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2deac-113">Then to retrieve the results, the SQL Server `DateOfBirth` column must be translated from a SQL Server `DATETIME` type to a CLR <xref:System.DateTime?displayProperty=nameWithType> type for use in the object model.</span></span> <span data-ttu-id="2deac-114">この例では、CLR オブジェクト モデルの型と SQL Server データベースの型をそのままマッピングできますが、</span><span class="sxs-lookup"><span data-stu-id="2deac-114">In this example, the types in the CLR object model and SQL Server database have natural mappings.</span></span> <span data-ttu-id="2deac-115">これが常に可能であるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="2deac-115">But, this is not always the case.</span></span>

### <a name="missing-counterparts"></a><span data-ttu-id="2deac-116">対応する型の欠落</span><span class="sxs-lookup"><span data-stu-id="2deac-116">Missing Counterparts</span></span>

<span data-ttu-id="2deac-117">次の型には、対応する適切な型がありません。</span><span class="sxs-lookup"><span data-stu-id="2deac-117">The following types do not have reasonable counterparts.</span></span>

- <span data-ttu-id="2deac-118">CLR <xref:System> 名前空間の不一致 :</span><span class="sxs-lookup"><span data-stu-id="2deac-118">Mismatches in the CLR <xref:System> namespace:</span></span>

  - <span data-ttu-id="2deac-119">**符号なし整数**。</span><span class="sxs-lookup"><span data-stu-id="2deac-119">**Unsigned integers**.</span></span> <span data-ttu-id="2deac-120">通常、この型はオーバーフローを避けるため、大きいサイズの符号付きの型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="2deac-120">These types are typically mapped to their signed counterparts of larger size to avoid overflow.</span></span> <span data-ttu-id="2deac-121">リテラルは、値に基づいて、同じサイズまたはより小さいサイズの符号付きの型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="2deac-121">Literals can be converted to a signed numeric of the same or smaller size, based on value.</span></span>

  - <span data-ttu-id="2deac-122">**[Boolean]** 。</span><span class="sxs-lookup"><span data-stu-id="2deac-122">**Boolean**.</span></span> <span data-ttu-id="2deac-123">この型は、1 ビット以上の数値型または文字列型に変換できます。</span><span class="sxs-lookup"><span data-stu-id="2deac-123">These types can be mapped to a bit or larger numeric or string.</span></span> <span data-ttu-id="2deac-124">リテラルは、同じ値に評価される式に (たとえば SQL の `1=1` は CLS の `True` に) 変換できます。</span><span class="sxs-lookup"><span data-stu-id="2deac-124">A literal can be mapped to an expression that evaluates to the same value (for example, `1=1` in SQL for `True` in CLS).</span></span>

  - <span data-ttu-id="2deac-125">**TimeSpan**。</span><span class="sxs-lookup"><span data-stu-id="2deac-125">**TimeSpan**.</span></span> <span data-ttu-id="2deac-126">この型は、2 つの `DateTime` 値の差分を表します。SQL Server の `timestamp` には相当しません。</span><span class="sxs-lookup"><span data-stu-id="2deac-126">This type represents the difference between two `DateTime` values and does not correspond to the `timestamp` of SQL Server.</span></span> <span data-ttu-id="2deac-127">CLR の <xref:System.TimeSpan?displayProperty=nameWithType> は、場合によっては SQL Server の `TIME` 型にもマッピングします。</span><span class="sxs-lookup"><span data-stu-id="2deac-127">The CLR <xref:System.TimeSpan?displayProperty=nameWithType> may also map to the SQL Server `TIME` type in some cases.</span></span> <span data-ttu-id="2deac-128">SQL Server の `TIME` 型は、24 時間未満の正の値を表すだけが目的でした。</span><span class="sxs-lookup"><span data-stu-id="2deac-128">The SQL Server `TIME` type was only intended to represent positive values less than 24 hours.</span></span> <span data-ttu-id="2deac-129">CLR の <xref:System.TimeSpan> の範囲はこれよりずっと大きくなります。</span><span class="sxs-lookup"><span data-stu-id="2deac-129">The CLR <xref:System.TimeSpan> has a much larger range.</span></span>

  > [!NOTE]
  > <span data-ttu-id="2deac-130"><xref:System.Data.SqlTypes> にある SQL Server に固有の .NET Framework 型は、この比較には含まれていません。</span><span class="sxs-lookup"><span data-stu-id="2deac-130">SQL Server-specific .NET Framework types in <xref:System.Data.SqlTypes> are not included in this comparison.</span></span>

- <span data-ttu-id="2deac-131">SQL Server の不一致 :</span><span class="sxs-lookup"><span data-stu-id="2deac-131">Mismatches in SQL Server:</span></span>

  - <span data-ttu-id="2deac-132">**固定長文字型**。</span><span class="sxs-lookup"><span data-stu-id="2deac-132">**Fixed length character types**.</span></span> <span data-ttu-id="2deac-133">Transact-SQL では、Unicode カテゴリと Unicode 以外のカテゴリが区別され、それぞれのカテゴリに 3 つの型 (固定長 `nchar`/`char`、可変長 `nvarchar`/`varchar`、および大きいサイズの `ntext`/`text`) があります。</span><span class="sxs-lookup"><span data-stu-id="2deac-133">Transact-SQL distinguishes between Unicode and non-Unicode categories and has three distinct types in each category: fixed length `nchar`/`char`, variable length `nvarchar`/`varchar`, and larger-sized `ntext`/`text`.</span></span> <span data-ttu-id="2deac-134">固定長文字型は、文字を取得するために CLR の <xref:System.Char?displayProperty=nameWithType> 型に変換できますが、この型の変換と動作に正確には対応していません。</span><span class="sxs-lookup"><span data-stu-id="2deac-134">The fixed length character types could be mapped to the CLR <xref:System.Char?displayProperty=nameWithType> type for retrieving characters, but they do not really correspond to the same type in conversions and behavior.</span></span>

  - <span data-ttu-id="2deac-135">**ビット**。</span><span class="sxs-lookup"><span data-stu-id="2deac-135">**Bit**.</span></span> <span data-ttu-id="2deac-136">`bit` ドメインに格納される値の数は `Nullable<Boolean>` と同じですが、両者の型は異なります。</span><span class="sxs-lookup"><span data-stu-id="2deac-136">Although the `bit` domain has the same number of values as `Nullable<Boolean>`, the two are different types.</span></span> <span data-ttu-id="2deac-137">`Bit` が受け取る値は `1` と `0` であり、`true`/`false` ではありません。また、ブール式に相当する型としては使用できません。</span><span class="sxs-lookup"><span data-stu-id="2deac-137">`Bit` takes values `1` and `0` instead of `true`/`false`, and cannot be used as an equivalent to Boolean expressions.</span></span>

  - <span data-ttu-id="2deac-138">**Timestamp**。</span><span class="sxs-lookup"><span data-stu-id="2deac-138">**Timestamp**.</span></span> <span data-ttu-id="2deac-139">CLR の <xref:System.TimeSpan?displayProperty=nameWithType> 型とは異なり、SQL Server の `TIMESTAMP` 型は、各更新に固有のデータベースで生成される 8 バイトの数字を表し、<xref:System.DateTime> の値の差異に基づくものではありません。</span><span class="sxs-lookup"><span data-stu-id="2deac-139">Unlike the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type, the SQL Server `TIMESTAMP` type represents an 8-byte number generated by the database that is unique for each update and is not based on the difference between <xref:System.DateTime> values.</span></span>

  - <span data-ttu-id="2deac-140">**Money** および **SmallMoney**。</span><span class="sxs-lookup"><span data-stu-id="2deac-140">**Money** and **SmallMoney**.</span></span> <span data-ttu-id="2deac-141">これらの値は <xref:System.Decimal> に変換できますが、基本的には異なる型であり、サーバーベースの関数や変換では異なる型として扱われます。</span><span class="sxs-lookup"><span data-stu-id="2deac-141">These types can be mapped to <xref:System.Decimal> but are basically different types and are treated as such by server-based functions and conversions.</span></span>

### <a name="multiple-mappings"></a><span data-ttu-id="2deac-142">複数のマッピング</span><span class="sxs-lookup"><span data-stu-id="2deac-142">Multiple Mappings</span></span>

<span data-ttu-id="2deac-143">SQL Server のデータ型には CLR の 1 つ以上のデータ型にマッピングできるものが多くあります。</span><span class="sxs-lookup"><span data-stu-id="2deac-143">There are many SQL Server data types that you can map to one or more CLR data types.</span></span> <span data-ttu-id="2deac-144">また、CLR のデータ型にも SQL Server の 1 つ以上のデータ型にマッピングできるものが多くあります。</span><span class="sxs-lookup"><span data-stu-id="2deac-144">There are also many CLR types that you can map to one or more SQL Server types.</span></span> <span data-ttu-id="2deac-145">マッピングは LINQ to SQL でサポートされている場合がありますが、CLR と SQL Server 間でマッピングされる 2 つの型が有効桁数、範囲、セマンティクスにおいて完全に一致するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="2deac-145">Although a mapping may be supported by LINQ to SQL, it does not mean that the two types mapped between the CLR and SQL Server are a perfect match in precision, range, and semantics.</span></span> <span data-ttu-id="2deac-146">これらの要素の一部または全部が異なるマッピングもあります。</span><span class="sxs-lookup"><span data-stu-id="2deac-146">Some mappings may include differences in any or all of these dimensions.</span></span> <span data-ttu-id="2deac-147">さまざまなマッピング パターンで生じる違いの詳細については、「[SQL と CLR の型マッピング](sql-clr-type-mapping.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2deac-147">You can find details about these potential differences for the various mapping possibilities at [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>

### <a name="user-defined-types"></a><span data-ttu-id="2deac-148">ユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="2deac-148">User-defined Types</span></span>

<span data-ttu-id="2deac-149">ユーザー定義の CLR 型は、型システムの差異を埋めるために設計されていますが、</span><span class="sxs-lookup"><span data-stu-id="2deac-149">User-defined CLR types are designed to help bridge the type system gap.</span></span> <span data-ttu-id="2deac-150">型のバージョン管理に関する興味深い問題が発生しています。</span><span class="sxs-lookup"><span data-stu-id="2deac-150">Nevertheless they surface interesting issues about type versioning.</span></span> <span data-ttu-id="2deac-151">クライアントで使用されるバージョンでの変更が、データベース サーバーに保存されている型での変更に一致しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="2deac-151">A change in the version on the client might not be matched by a change in the type stored on the database server.</span></span> <span data-ttu-id="2deac-152">このような変更が原因で別の型不一致が発生して型のセマンティクスが一致しなくなり、バージョンの差異が表面化する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2deac-152">Any such change causes another type mismatch where the type semantics might not match and the version gap is likely to become visible.</span></span> <span data-ttu-id="2deac-153">後続のバージョンで継承階層がリファクタリングされるにつれて、問題はさらに複雑化します。</span><span class="sxs-lookup"><span data-stu-id="2deac-153">Further complications occur as inheritance hierarchies are refactored in successive versions.</span></span>

## <a name="expression-semantics"></a><span data-ttu-id="2deac-154">式のセマンティクス</span><span class="sxs-lookup"><span data-stu-id="2deac-154">Expression Semantics</span></span>

<span data-ttu-id="2deac-155">CLR の型とデータベースの型が 1 対 1 で対応しないという不一致に加えて、式の変換がこの不一致をさらに複雑にしています。</span><span class="sxs-lookup"><span data-stu-id="2deac-155">In addition to the pairwise mismatch between CLR and database types, expressions add complexity to the mismatch.</span></span> <span data-ttu-id="2deac-156">演算子セマンティクス、関数セマンティクス、暗黙の型変換、および優先順位規則について不一致を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2deac-156">Mismatches in operator semantics, function semantics, implicit type conversion, and precedence rules must be considered.</span></span>

<span data-ttu-id="2deac-157">ここでは、よく似ている式で起こる不一致について具体的に説明します。</span><span class="sxs-lookup"><span data-stu-id="2deac-157">The following subsections illustrate the mismatch between apparently similar expressions.</span></span> <span data-ttu-id="2deac-158">特定の CLR 式にセマンティクス的に同等の SQL 式を生成することが可能な場合があります。</span><span class="sxs-lookup"><span data-stu-id="2deac-158">It might be possible to generate SQL expressions that are semantically equivalent to a given CLR expression.</span></span> <span data-ttu-id="2deac-159">ただし、よく似た 2 つの式のセマンティクスの相違が CLR ユーザーに明らかかどうかは不明なため、セマンティクスの同等性に必要な変更が意図されているかどうかはわかりません。</span><span class="sxs-lookup"><span data-stu-id="2deac-159">However, it is not clear whether the semantic differences between apparently similar expressions are evident to a CLR user, and therefore whether the changes that are required for semantic equivalence are intended or not.</span></span> <span data-ttu-id="2deac-160">これが特に重大な問題となるのは、式が一連の値に評価されるときです。</span><span class="sxs-lookup"><span data-stu-id="2deac-160">This is an especially critical issue when an expression is evaluated for a set of values.</span></span> <span data-ttu-id="2deac-161">差異が見えるかどうかはデータによっても左右され、コーディングとデバッグの段階で特定することは困難です。</span><span class="sxs-lookup"><span data-stu-id="2deac-161">The visibility of the difference might depend on data- and be hard to identify during coding and debugging.</span></span>

### <a name="null-semantics"></a><span data-ttu-id="2deac-162">null セマンティクス</span><span class="sxs-lookup"><span data-stu-id="2deac-162">Null Semantics</span></span>

<span data-ttu-id="2deac-163">SQL 式では、ブール式に 3 つの論理値を使用します。</span><span class="sxs-lookup"><span data-stu-id="2deac-163">SQL expressions provide three-valued logic for Boolean expressions.</span></span> <span data-ttu-id="2deac-164">式の結果は true、false、または null です。</span><span class="sxs-lookup"><span data-stu-id="2deac-164">The result can be true, false, or null.</span></span> <span data-ttu-id="2deac-165">これに対し、CLR は null 値に関する比較に、2 つの値によるブール型の結果を指定します。</span><span class="sxs-lookup"><span data-stu-id="2deac-165">By contrast, CLR specifies two-valued Boolean result for comparisons involving null values.</span></span> <span data-ttu-id="2deac-166">次のコードがあるとします。</span><span class="sxs-lookup"><span data-stu-id="2deac-166">Consider the following code:</span></span>

[!code-csharp[DLinqMismatch#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#2)]
[!code-vb[DLinqMismatch#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#2)]

```sql
-- Assume col1 and col2 are integer columns with null values.
-- Assume that ANSI null behavior has not been explicitly
--  turned off.
Select …
From …
Where col1 = col2
-- Evaluates to null, not true and the corresponding row is not
--   selected.
-- To obtain matching behavior (i -> col1, j -> col2) change
--   the query to the following:
Select …
From …
Where
    col1 = col2
or (col1 is null and col2 is null)
-- (Visual Basic 'Nothing'.)
```

<span data-ttu-id="2deac-167">同様の問題は、結果が 2 つの値のいずれかになることが前提とされているときにも起こります。</span><span class="sxs-lookup"><span data-stu-id="2deac-167">A similar problem occurs with the assumption about two-valued results.</span></span>

[!code-csharp[DLinqMismatch#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#3)]
[!code-vb[DLinqMismatch#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#3)]

```sql
-- Assume col1 and col2 are nullable columns.
-- Assume that ANSI null behavior has not been explicitly
--   turned off.
Select …
From …
Where
    col1 = col2
or col1 != col2
-- Visual Basic: col1 <> col2.

-- Excludes the case where the boolean expression evaluates
--   to null. Therefore the where clause does not always
--   evaluate to true.
```

<span data-ttu-id="2deac-168">この例では、生成される SQL の動作は同等ですが、意図したとおりに正確に変換されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2deac-168">In the previous case, you can get equivalent behavior in generating SQL, but the translation might not accurately reflect your intention.</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="2deac-169">では、C# の `null` または Visual Basic `nothing` の比較セマンティクスが SQL に強制されません。</span><span class="sxs-lookup"><span data-stu-id="2deac-169">does not impose C# `null` or Visual Basic `nothing` comparison semantics on SQL.</span></span> <span data-ttu-id="2deac-170">比較演算子は、対応する SQL の演算子に構文上は変換されます。</span><span class="sxs-lookup"><span data-stu-id="2deac-170">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="2deac-171">セマンティクスには、サーバーまたは接続の設定で定義された SQL セマンティクスが反映されます。</span><span class="sxs-lookup"><span data-stu-id="2deac-171">The semantics reflect SQL semantics as defined by server or connection settings.</span></span> <span data-ttu-id="2deac-172">既定の SQL Server 設定では、2 つの null 値は一致しないと見なされます (この設定を変更するとセマンティクスを変更できます)。</span><span class="sxs-lookup"><span data-stu-id="2deac-172">Two null values are considered unequal under default SQL Server settings (although you can change the settings to change the semantics).</span></span> <span data-ttu-id="2deac-173">いずれにしても、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ではクエリの変換時にサーバーの設定は考慮されません。</span><span class="sxs-lookup"><span data-stu-id="2deac-173">Regardless, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not consider server settings in query translation.</span></span>

<span data-ttu-id="2deac-174">リテラルの `null` (`nothing`) による比較は適切な SQL バージョンの (`is null` または `is not null`) に変換されます。</span><span class="sxs-lookup"><span data-stu-id="2deac-174">A comparison with the literal `null` (`nothing`) is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>

<span data-ttu-id="2deac-175">`null` (`nothing`) の値の照合順序は SQL Server で定義され、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では変更されません。</span><span class="sxs-lookup"><span data-stu-id="2deac-175">The value of `null` (`nothing`) in collation is defined by SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not change the collation.</span></span>

### <a name="type-conversion-and-promotion"></a><span data-ttu-id="2deac-176">型変換と上位変換</span><span class="sxs-lookup"><span data-stu-id="2deac-176">Type Conversion and Promotion</span></span>

<span data-ttu-id="2deac-177">SQL では、式における暗黙の型変換が豊富にサポートされています。</span><span class="sxs-lookup"><span data-stu-id="2deac-177">SQL supports a rich set of implicit conversions in expressions.</span></span> <span data-ttu-id="2deac-178">同じような式でも、C# では明示的なキャストが必要です。</span><span class="sxs-lookup"><span data-stu-id="2deac-178">Similar expressions in C# would require an explicit cast.</span></span> <span data-ttu-id="2deac-179">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="2deac-179">For example:</span></span>

- <span data-ttu-id="2deac-180">`Nvarchar` 型と `DateTime` 型は、SQL では明示的にキャストせずに比較できますが、C# では明示的に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2deac-180">`Nvarchar` and `DateTime` types can be compared in SQL without any explicit casts; C# requires explicit conversion.</span></span>

- <span data-ttu-id="2deac-181">`Decimal` は、SQL では暗黙に `DateTime` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="2deac-181">`Decimal` is implicitly converted to `DateTime` in SQL.</span></span> <span data-ttu-id="2deac-182">C# では、暗黙の変換は行われません。</span><span class="sxs-lookup"><span data-stu-id="2deac-182">C# does not allow for an implicit conversion.</span></span>

<span data-ttu-id="2deac-183">同様に、型の基本セットが異なるため、Transact-SQL の型の優先順位は C# の優先順位と異なります。</span><span class="sxs-lookup"><span data-stu-id="2deac-183">Likewise, type precedence in Transact-SQL differs from type precedence in C# because the underlying set of types is different.</span></span> <span data-ttu-id="2deac-184">実際に、両者の優先順位のリストには明白なサブセットやスーパーセットの関係は成り立ちません。</span><span class="sxs-lookup"><span data-stu-id="2deac-184">In fact, there is no clear subset/superset relationship between the precedence lists.</span></span> <span data-ttu-id="2deac-185">たとえば、`nvarchar` を `varchar` と比較すると、`varchar` 式が `nvarchar` に暗黙的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="2deac-185">For example, comparing an `nvarchar` with a `varchar` causes the implicit conversion of the `varchar` expression to `nvarchar`.</span></span> <span data-ttu-id="2deac-186">これに相当する上位変換は CLR にはありません。</span><span class="sxs-lookup"><span data-stu-id="2deac-186">The CLR provides no equivalent promotion.</span></span>

<span data-ttu-id="2deac-187">単純なケースでは、これらの違いによって、CLR 式には SQL 式では冗長となるキャストがあります。</span><span class="sxs-lookup"><span data-stu-id="2deac-187">In simple cases, these differences cause CLR expressions with casts to be redundant for a corresponding SQL expression.</span></span> <span data-ttu-id="2deac-188">さらに重要なことは、SQL 式が評価される過程で中間結果として、正確に対応するものが C# に存在しない型に上位変換される (またはその逆) 可能性があることです。</span><span class="sxs-lookup"><span data-stu-id="2deac-188">More importantly, the intermediate results of a SQL expression might be implicitly promoted to a type that has no accurate counterpart in C#, and vice versa.</span></span> <span data-ttu-id="2deac-189">このような式のテスト、デバッグ、および検証には多大な労力を要します。</span><span class="sxs-lookup"><span data-stu-id="2deac-189">Overall, the testing, debugging, and validation of such expressions adds significant burden on the user.</span></span>

### <a name="collation"></a><span data-ttu-id="2deac-190">照合順序</span><span class="sxs-lookup"><span data-stu-id="2deac-190">Collation</span></span>

<span data-ttu-id="2deac-191">Transact-SQL では、明示的な照合順序が文字列型の注釈としてサポートされます。</span><span class="sxs-lookup"><span data-stu-id="2deac-191">Transact-SQL supports explicit collations as annotations to character string types.</span></span> <span data-ttu-id="2deac-192">この照合順序に従って、特定の比較の有効性が決定されます。</span><span class="sxs-lookup"><span data-stu-id="2deac-192">These collations determine the validity of certain comparisons.</span></span> <span data-ttu-id="2deac-193">たとえば、明示的な照合順序の異なる 2 つの列を比較するとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="2deac-193">For example, comparing two columns with different explicit collations is an error.</span></span> <span data-ttu-id="2deac-194">CTS の文字列型はこれよりも単純なため、このようなエラーは起こりません。</span><span class="sxs-lookup"><span data-stu-id="2deac-194">The use of much simplified CTS string type does not cause such errors.</span></span> <span data-ttu-id="2deac-195">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="2deac-195">Consider the following example:</span></span>

```sql
create table T2 (
    Col1 nvarchar(10),
    Col2      nvarchar(10) collate Latin_general_ci_as
)
```

[!code-csharp[DLinqMismatch#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#4)]
[!code-vb[DLinqMismatch#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#4)]

```sql
Select …
From …
Where Col1 = Col2
-- Error, collation conflict.
```

<span data-ttu-id="2deac-196">ここでは、collation サブ句で、代用できない "*制限がある型*" を作成しています。</span><span class="sxs-lookup"><span data-stu-id="2deac-196">In effect, the collation subclause creates a *restricted type* that is not substitutable.</span></span>

<span data-ttu-id="2deac-197">同様に、並べ替え順序も型システムによって顕著に異なります。</span><span class="sxs-lookup"><span data-stu-id="2deac-197">Similarly, the sort order can be significantly different across the type systems.</span></span> <span data-ttu-id="2deac-198">この相違は、結果の並べ替えに影響します。</span><span class="sxs-lookup"><span data-stu-id="2deac-198">This difference affects the sorting of results.</span></span> <span data-ttu-id="2deac-199"><xref:System.Guid> は、すべての 16 バイトを辞書の編集順序 (`IComparable()`) で並べ替えますが、T-SQL は、node(10-15)、clock-seq(8-9)、time-high(6-7)、time-mid(4-5)、time-low(0-3) の順序で GUID を比較します。</span><span class="sxs-lookup"><span data-stu-id="2deac-199"><xref:System.Guid> is sorted on all 16 bytes by lexicographic order (`IComparable()`), whereas T-SQL compares GUIDs in the following order: node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3).</span></span> <span data-ttu-id="2deac-200">この順序は、NT 生成の GUID がこのようなオクテット順になった SQL 7.0 で採用されました。</span><span class="sxs-lookup"><span data-stu-id="2deac-200">This ordering was done in SQL 7.0 when NT-generated GUIDs had such an octet order.</span></span> <span data-ttu-id="2deac-201">この方法により、同じノード クラスターで生成された GUID がタイムスタンプに従って順番に並ぶことが保証されていました。</span><span class="sxs-lookup"><span data-stu-id="2deac-201">The approach ensured that GUIDs generated at the same node cluster came together in sequential order according to timestamp.</span></span> <span data-ttu-id="2deac-202">また、この方法はインデックスの作成にも便利でした (挿入時にランダムな入出力の代わりに追加が発生します)。</span><span class="sxs-lookup"><span data-stu-id="2deac-202">The approach was also useful for building indexes (inserts become appends instead of random IOs).</span></span> <span data-ttu-id="2deac-203">この順番はプライバシーを考慮して後に Windows で暗号化されましたが、SQL では互換性を維持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2deac-203">The order was scrambled later in Windows because of privacy concerns, but SQL must maintain compatibility.</span></span> <span data-ttu-id="2deac-204">この問題を回避するには、<xref:System.Guid> ではなく <xref:System.Data.SqlTypes.SqlGuid> を使用します。</span><span class="sxs-lookup"><span data-stu-id="2deac-204">A workaround is to use <xref:System.Data.SqlTypes.SqlGuid> instead of <xref:System.Guid>.</span></span>

### <a name="operator-and-function-differences"></a><span data-ttu-id="2deac-205">演算子と関数の相違</span><span class="sxs-lookup"><span data-stu-id="2deac-205">Operator and Function Differences</span></span>

<span data-ttu-id="2deac-206">基本的には対応する関係にある演算子と関数にも、若干のセマンティクスの違いがあります。</span><span class="sxs-lookup"><span data-stu-id="2deac-206">Operators and functions that are essentially comparable have subtly different semantics.</span></span> <span data-ttu-id="2deac-207">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="2deac-207">For example:</span></span>

- <span data-ttu-id="2deac-208">C# の論理演算子 `&&` と `||` については、オペランドの辞書編集上の順序に基づいてショート サーキットのセマンティクスが指定されます。</span><span class="sxs-lookup"><span data-stu-id="2deac-208">C# specifies short circuit semantics based on lexical order of operands for logical operators `&&` and `||`.</span></span> <span data-ttu-id="2deac-209">一方 SQL では、セットベースのクエリの対象となるため、実行の順序を決定する際の自由度が高くなります。</span><span class="sxs-lookup"><span data-stu-id="2deac-209">SQL on the other hand is targeted for set-based queries and therefore provides more freedom for the optimizer to decide the order of execution.</span></span> <span data-ttu-id="2deac-210">次に、これの具体例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="2deac-210">Some of the implications include the following:</span></span>

  - <span data-ttu-id="2deac-211">セマンティクスが等価になるように変換するには、SQL の "`CASE` …</span><span class="sxs-lookup"><span data-stu-id="2deac-211">Semantically equivalent translation would require "`CASE` …</span></span> <span data-ttu-id="2deac-212">`WHEN` …</span><span class="sxs-lookup"><span data-stu-id="2deac-212">`WHEN` …</span></span> <span data-ttu-id="2deac-213">`THEN`" 構造でオペランドの実行順序が変更されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2deac-213">`THEN`" construct in SQL to avoid reordering of operand execution.</span></span>

  - <span data-ttu-id="2deac-214">C# の式が最初のオペランドの評価結果に基づく 2 番目のオペランドの評価に依存している場合は、`AND`/`OR` 演算子へのルーズな変換によって予期しないエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2deac-214">A loose translation to `AND`/`OR` operators could cause unexpected errors if the C# expression relies on evaluation the second operand being based on the result of the evaluation of the first operand.</span></span>

- <span data-ttu-id="2deac-215">`Round()` 関数のセマンティクスは、.NET Framework と T-SQL で異なります。</span><span class="sxs-lookup"><span data-stu-id="2deac-215">`Round()` function has different semantics in .NET Framework and in T-SQL.</span></span>

- <span data-ttu-id="2deac-216">文字列のインデックスは、CLR では 0 から始まりますが、SQL では 1 から始まります。</span><span class="sxs-lookup"><span data-stu-id="2deac-216">Starting index for strings is 0 in the CLR but 1 in SQL.</span></span> <span data-ttu-id="2deac-217">したがって、インデックスのある関数にはインデックスの変換が必要です。</span><span class="sxs-lookup"><span data-stu-id="2deac-217">Therefore, any function that has index needs index translation.</span></span>

- <span data-ttu-id="2deac-218">CLR では、浮動小数点数に剰余演算子 (%) がサポートされていますが、SQL ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2deac-218">The CLR supports modulus (‘%’) operator for floating point numbers but SQL does not.</span></span>

- <span data-ttu-id="2deac-219">`Like` 演算子は、暗黙的な変換に基づいて自動的にオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="2deac-219">The `Like` operator effectively acquires automatic overloads based on implicit conversions.</span></span> <span data-ttu-id="2deac-220">`Like` は文字列型を操作するために定義された演算子ですが、数値型または `DateTime` 型に `Like` が使用される場合にはこれらの非文字列型からも暗黙の変換が許されます。</span><span class="sxs-lookup"><span data-stu-id="2deac-220">Although the `Like` operator is defined to operate on character string types, implicit conversion from numeric types or `DateTime` types allows for those non-string types to be used with `Like` just as well.</span></span> <span data-ttu-id="2deac-221">CTS には、これに相当する暗黙の変換はありません。</span><span class="sxs-lookup"><span data-stu-id="2deac-221">In CTS, comparable implicit conversions do not exist.</span></span> <span data-ttu-id="2deac-222">したがって、オーバーロードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2deac-222">Therefore, additional overloads are needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2deac-223">この `Like` 演算子の動作は C# のみに当てはまります。Visual Basic の `Like` キーワードは以前と変わりません。</span><span class="sxs-lookup"><span data-stu-id="2deac-223">This `Like` operator behavior applies to C# only; the Visual Basic `Like` keyword is unchanged.</span></span>

- <span data-ttu-id="2deac-224">SQL では常にオーバーフローがチェックされますが、C# ではこのチェックを明示的に指定して折り返しを回避する必要があります (Visual Basic では不要です)。</span><span class="sxs-lookup"><span data-stu-id="2deac-224">Overflow is always checked in SQL but it has to be explicitly specified in C# (not in Visual Basic) to avoid wraparound.</span></span> <span data-ttu-id="2deac-225">たとえば、整数の列 C1、C2、および C3 があり、C1+C2 が C3 (Update T Set C3 = C1 + C2) に保存されるとします。</span><span class="sxs-lookup"><span data-stu-id="2deac-225">Given integer columns C1, C2 and C3, if C1+C2 is stored in C3 (Update T Set C3 = C1 + C2).</span></span>

    ```sql
    create table T3 (
        Col1      integer,
        Col2      integer
    )
    insert into T3 (col1, col2) values (2147483647, 5)
    -- Valid values: max integer value and 5.
    select * from T3 where col1 + col2 < 0
    -- Produces arithmetic overflow error.
    ```

[!code-csharp[DLinqMismatch#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#5)]
[!code-vb[DLinqMismatch#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#5)]

- <span data-ttu-id="2deac-226">SQL では対称的な算術型丸めが実行されますが、.NET Framework では銀行型丸めが使用されます。</span><span class="sxs-lookup"><span data-stu-id="2deac-226">SQL performs symmetric arithmetic rounding while .NET Framework uses banker’s rounding.</span></span> <span data-ttu-id="2deac-227">詳細については、サポート技術情報の文書「丸めを行うカスタム プロシージャを実装する方法」(196652) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2deac-227">See Knowledgebase article 196652 for additional details.</span></span>

- <span data-ttu-id="2deac-228">既定で、共通ロケールの SQL で文字や文字列を比較する場合に大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="2deac-228">By default, for common locales, character-string comparisons are case-insensitive in SQL.</span></span> <span data-ttu-id="2deac-229">Visual Basic と C# では、大文字と小文字は区別されます。</span><span class="sxs-lookup"><span data-stu-id="2deac-229">In Visual Basic and in C#, they are case-sensitive.</span></span> <span data-ttu-id="2deac-230">たとえば、`s` が `food` の場合、`s == "Food"` (Visual Basic では `s = "Food"`) と `s == "Food"` の結果は異なります。</span><span class="sxs-lookup"><span data-stu-id="2deac-230">For example, `s == "Food"` (`s = "Food"` in Visual Basic) and `s == "Food"` can yield different results if `s` is `food`.</span></span>

    ```sql
    -- Assume default US-English locale (case insensitive).
    create table T4 (
        Col1      nvarchar (256)
    )
    insert into T4 values (‘Food’)
    insert into T4 values (‘FOOD’)
    select * from T4 where Col1 = ‘food’
    -- Both the rows are returned because of case-insensitive matching.
    ```

[!code-csharp[DLinqMismatch#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#6)]
[!code-vb[DLinqMismatch#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#6)]

- <span data-ttu-id="2deac-231">SQL で固定長の文字型引数に適用される演算子や関数と、CLR の <xref:System.String?displayProperty=nameWithType> に適用される同じ演算子や関数とでは、セマンティクスに顕著な違いがあります。</span><span class="sxs-lookup"><span data-stu-id="2deac-231">Operators/ functions applied to fixed length character type arguments in SQL have significantly different semantics than the same operators/functions applied to the CLR <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2deac-232">これも、型の説明で指摘したように、対応する型の欠落の問題が波及したものと解釈できます。</span><span class="sxs-lookup"><span data-stu-id="2deac-232">This could also be viewed as an extension of the missing counterpart problem discussed in the section about types.</span></span>

    ```sql
    create table T4 (
        Col1      nchar(4)
    )
    Insert into T5(Col1) values ('21');
    Insert into T5(Col1) values ('1021');
    Select * from T5 where Col1 like '%1'
    -- Only the second row with Col1 = '1021' is returned.
    -- Not the first row!
    ```

     [!code-csharp[DLinqMismatch#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#7)]
     [!code-vb[DLinqMismatch#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#7)]

     <span data-ttu-id="2deac-233">同様の問題は、文字列の連結でも見られます。</span><span class="sxs-lookup"><span data-stu-id="2deac-233">A similar problem occurs with string concatenation.</span></span>

    ```sql
    create table T6 (
        Col1      nchar(4)
        Col2       nchar(4)
    )
    Insert into T6 values ('a', 'b');
    Select Col1+Col2 from T6
    -- Returns concatenation of padded strings "a   b   " and not "ab".
    ```

<span data-ttu-id="2deac-234">概して、CLR 式には複雑な変換が必要になる場合があり、SQL 機能を表現するには演算子や関数の追加が必要になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2deac-234">In summary, a convoluted translation might be required for CLR expressions and additional operators/functions may be necessary to expose SQL functionality.</span></span>

### <a name="type-casting"></a><span data-ttu-id="2deac-235">型キャスト</span><span class="sxs-lookup"><span data-stu-id="2deac-235">Type Casting</span></span>

<span data-ttu-id="2deac-236">C# と SQL では、明示的な型キャスト (`Cast` および `Convert`) を使って、式の既定のセマンティクスをオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="2deac-236">In C# and in SQL, users can override the default semantics of expressions by using explicit type casts (`Cast` and `Convert`).</span></span> <span data-ttu-id="2deac-237">ただし、型システムの境界を越えてこの機能を提供するとジレンマが生じます。</span><span class="sxs-lookup"><span data-stu-id="2deac-237">However, exposing this capability across the type system boundary poses a dilemma.</span></span> <span data-ttu-id="2deac-238">特定のセマンティクスを提供する SQL のキャストは、それに相当する C# のキャストに簡単には変換できません。</span><span class="sxs-lookup"><span data-stu-id="2deac-238">A SQL cast that provides the desired semantics cannot be easily translated to a corresponding C# cast.</span></span> <span data-ttu-id="2deac-239">反対に、C# のキャストを SQL の同等のキャストに直接変換することはできません。型の不一致、対応する型の欠落、および型の優先順位の相違があるためです。</span><span class="sxs-lookup"><span data-stu-id="2deac-239">On the other hand, a C# cast cannot be directly translated into an equivalent SQL cast because of type mismatches, missing counterparts, and different type precedence hierarchies.</span></span> <span data-ttu-id="2deac-240">型システムの不一致の露出と式の有意性の喪失は、トレードオフの関係にあります。</span><span class="sxs-lookup"><span data-stu-id="2deac-240">There is a trade-off between exposing the type system mismatch and losing significant power of expression.</span></span>

<span data-ttu-id="2deac-241">また、型のキャストは、どちらのドメインでも式の検証には不要かもしれませんが、既定以外のマッピングを式に正しく適用するために必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2deac-241">In other cases, type casting might not be needed in either domain for validation of an expression but might be required to make sure that a non-default mapping is correctly applied to the expression.</span></span>

```sql
-- Example from "Non-default Mapping" section extended
create table T5 (
    Col1      nvarchar(10),
    Col2      nvarchar(10)
)
Insert into T5(col1, col2) values (‘3’, ‘2’);
```

[!code-csharp[DLinqMismatch#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#8)]
[!code-vb[DLinqMismatch#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#8)]

```sql
Select *
From T5
Where Col1 + Col2 > 4
-- "Col1 + Col2" expr evaluates to '32'
```

## <a name="performance-issues"></a><span data-ttu-id="2deac-242">パフォーマンスの問題</span><span class="sxs-lookup"><span data-stu-id="2deac-242">Performance Issues</span></span>

<span data-ttu-id="2deac-243">SQL Server と CLR の型の相違が原因となり、CLR と SQL Server の型システムの境界を越えるときにパフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2deac-243">Accounting for some SQL Server-CLR type differences may result in a decrease in performance when crossing between the CLR and SQL Server type systems.</span></span> <span data-ttu-id="2deac-244">次のような状況でパフォーマンスに影響が現れます。</span><span class="sxs-lookup"><span data-stu-id="2deac-244">Examples of scenarios impacting performance include the following:</span></span>

- <span data-ttu-id="2deac-245">論理積/和演算子の評価順序の強制</span><span class="sxs-lookup"><span data-stu-id="2deac-245">Forced order of evaluation for logical and/or operators</span></span>

- <span data-ttu-id="2deac-246">述語の評価順序を強制する SQL を生成すると、SQL オプティマイザーの機能が制限されます。</span><span class="sxs-lookup"><span data-stu-id="2deac-246">Generating SQL to enforce order of predicate evaluation restricts the SQL optimizer’s ability.</span></span>

- <span data-ttu-id="2deac-247">型変換は、CLR コンパイラで導入される場合も、オブジェクト リレーショナル クエリ実装で導入される場合も、インデックスの使用を抑制することがあります。</span><span class="sxs-lookup"><span data-stu-id="2deac-247">Type conversions, whether introduced by a CLR compiler or by an Object-Relational query implementation, may curtail index usage.</span></span>

     <span data-ttu-id="2deac-248">たとえば、オブジェクトに適用された</span><span class="sxs-lookup"><span data-stu-id="2deac-248">For example,</span></span>

    ```sql
    -- Table DDL
    create table T5 (
        Col1      varchar(100)
    )
    ```

     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]

     <span data-ttu-id="2deac-249">式 `(s = SOME_STRING_CONSTANT)` を変換するとします。</span><span class="sxs-lookup"><span data-stu-id="2deac-249">Consider the translation of expression `(s = SOME_STRING_CONSTANT)`.</span></span>

    ```sql
    -- Corresponding part of SQL where clause
    Where …
    Col1 = SOME_STRING_CONSTANT
    -- This expression is of the form <varchar> = <nvarchar>.
    -- Hence SQL introduces a conversion from varchar to nvarchar,
    --   resulting in
    Where …
    Convert(nvarchar(100), Col1) = SOME_STRING_CONSTANT
    -- Cannot use the index for column Col1 for some implementations.
    ```

<span data-ttu-id="2deac-250">SQL Server と CLR の型システムの境界を越えるときは、セマンティクスの相違に加えて、パフォーマンスへの影響も考慮することが重要です。</span><span class="sxs-lookup"><span data-stu-id="2deac-250">In addition to semantic differences, it is important to consider impacts to performance when crossing between the SQL Server and CLR type systems.</span></span> <span data-ttu-id="2deac-251">データセットが大きい場合、このようなパフォーマンスの問題が、アプリケーションの展開が可能かどうかを左右することがあります。</span><span class="sxs-lookup"><span data-stu-id="2deac-251">For large data sets, such performance issues can determine whether an application is deployable.</span></span>

## <a name="see-also"></a><span data-ttu-id="2deac-252">関連項目</span><span class="sxs-lookup"><span data-stu-id="2deac-252">See also</span></span>

- [<span data-ttu-id="2deac-253">背景情報</span><span class="sxs-lookup"><span data-stu-id="2deac-253">Background Information</span></span>](background-information.md)
