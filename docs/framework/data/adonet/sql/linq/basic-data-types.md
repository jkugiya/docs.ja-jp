---
description: '詳細情報: 基本データ型'
title: 基本データ型
ms.date: 03/30/2017
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
ms.openlocfilehash: d0236bc315c884d9e70c3c4a75755c3b66b1f2e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712611"
---
# <a name="basic-data-types"></a><span data-ttu-id="160d1-103">基本データ型</span><span class="sxs-lookup"><span data-stu-id="160d1-103">Basic Data Types</span></span>

<span data-ttu-id="160d1-104">LINQ to SQL クエリは、Microsoft SQL Server で実行される前に Transact-SQL に変換されるため、</span><span class="sxs-lookup"><span data-stu-id="160d1-104">Because LINQ to SQL queries translate to Transact-SQL before they are executed on the Microsoft SQL Server.</span></span> <span data-ttu-id="160d1-105">LINQ to SQL は、SQL Server が基本データ型に対してサポートするのと同じ組み込み機能の多くをサポートします。</span><span class="sxs-lookup"><span data-stu-id="160d1-105">LINQ to SQL supports much of the same built-in functionality that SQL Server does for basic data types.</span></span>  
  
## <a name="casting"></a><span data-ttu-id="160d1-106">キャスト</span><span class="sxs-lookup"><span data-stu-id="160d1-106">Casting</span></span>  

 <span data-ttu-id="160d1-107">SQL Server 内に同様の有効な変換が存在する場合は、変換元の CLR 型から変換先の CLR 型への暗黙的または明示的なキャストが有効になります。</span><span class="sxs-lookup"><span data-stu-id="160d1-107">Implicit or explicit casts are enabled from a source CLR type to a target CLR type if there is a similar valid conversion within SQL Server.</span></span> <span data-ttu-id="160d1-108">CLR キャストの詳細については、「[CType 関数 (Visual Basic)](../../../../../visual-basic/language-reference/functions/ctype-function.md)」および[型のテストとキャストの演算子](../../../../../csharp/language-reference/operators/type-testing-and-cast.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="160d1-108">For more information about CLR casting, see [CType Function](../../../../../visual-basic/language-reference/functions/ctype-function.md) (Visual Basic) and [Type-testing and cast operators](../../../../../csharp/language-reference/operators/type-testing-and-cast.md).</span></span> <span data-ttu-id="160d1-109">変換後、CLR 式に対して実行される操作の動作は、変換先の型に通常割り当てられる他の CLR 式の動作と一致するように、キャストによって変更されます。</span><span class="sxs-lookup"><span data-stu-id="160d1-109">After conversion, casts change the behavior of operations performed on a CLR expression to match the behavior of other CLR expressions that naturally map to the destination type.</span></span> <span data-ttu-id="160d1-110">継承の割り当てのコンテキストにおいてもキャストは変換可能です。</span><span class="sxs-lookup"><span data-stu-id="160d1-110">Casts are also translatable in the context of inheritance mapping.</span></span> <span data-ttu-id="160d1-111">より厳密なエンティティ サブタイプにオブジェクトを変換して、そのサブタイプに固有のデータへのアクセスを可能にすることができます。</span><span class="sxs-lookup"><span data-stu-id="160d1-111">Objects can be cast to more specific entity subtypes so that their subtype-specific data can be accessed.</span></span>  
  
## <a name="equality-operators"></a><span data-ttu-id="160d1-112">等値演算子</span><span class="sxs-lookup"><span data-stu-id="160d1-112">Equality Operators</span></span>  

 <span data-ttu-id="160d1-113">LINQ to SQL は、LINQ to SQL クエリ内の基本データ型で次の等値演算子をサポートします。</span><span class="sxs-lookup"><span data-stu-id="160d1-113">LINQ to SQL supports the following equality operators on basic data types inside LINQ to SQL queries:</span></span>  
  
- <span data-ttu-id="160d1-114">等値演算子および非等値演算子:等値演算子および非等値演算子は、数値型、<xref:System.Boolean> 型、<xref:System.DateTime> 型、および <xref:System.TimeSpan> 型についてサポートされます。</span><span class="sxs-lookup"><span data-stu-id="160d1-114">Equal and Inequality Operator: Equality and inequality operators are supported for numeric, <xref:System.Boolean>, <xref:System.DateTime>, and <xref:System.TimeSpan> types.</span></span> <span data-ttu-id="160d1-115">Visual Basic 演算子 `=` と `<>` の詳細については、「[比較演算子](../../../../../visual-basic/language-reference/operators/comparison-operators.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="160d1-115">For more about Visual Basic operators `=` and `<>`, see [Comparison Operators](../../../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span> <span data-ttu-id="160d1-116">C# の比較演算子 `==` および `!=` の詳細については、「[等値演算子](../../../../../csharp/language-reference/operators/equality-operators.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="160d1-116">For more information about C# comparison operators `==` and `!=`, see [Equality operators](../../../../../csharp/language-reference/operators/equality-operators.md).</span></span>
  
- <span data-ttu-id="160d1-117">Is 演算子:`IS` 演算子には、継承の割り当ての使用時にサポートされる変換があります。</span><span class="sxs-lookup"><span data-stu-id="160d1-117">Is operator: The `IS` operator has a supported translation when inheritance mapping is being used.</span></span> <span data-ttu-id="160d1-118">これは、オブジェクトが特定の種類のエンティティであるかどうかを検査する場合に、判別列を直接調べる代わりとして使用でき、判別列のチェックに変換されます。</span><span class="sxs-lookup"><span data-stu-id="160d1-118">It can be used instead of directly testing the discriminator column to determine whether an object is of a specific entity type, and is translated to a check on the discriminator column.</span></span> <span data-ttu-id="160d1-119">Visual Basic と C# の Is 演算子の詳細については、「[Is 演算子](../../../../../visual-basic/language-reference/operators/is-operator.md)」および [is](../../../../../csharp/language-reference/operators/type-testing-and-cast.md#is-operator) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="160d1-119">For more information about the Visual Basic and C# Is operators, see [Is Operator](../../../../../visual-basic/language-reference/operators/is-operator.md) and [is](../../../../../csharp/language-reference/operators/type-testing-and-cast.md#is-operator).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="160d1-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="160d1-120">See also</span></span>

- [<span data-ttu-id="160d1-121">SQL と CLR の型マッピング</span><span class="sxs-lookup"><span data-stu-id="160d1-121">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
- [<span data-ttu-id="160d1-122">データ型と関数</span><span class="sxs-lookup"><span data-stu-id="160d1-122">Data Types and Functions</span></span>](data-types-and-functions.md)
