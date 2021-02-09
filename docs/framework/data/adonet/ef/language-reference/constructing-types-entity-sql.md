---
description: '詳細情報: コンストラクター (Entity SQL)'
title: コンストラクター (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 5963c34ffd8e9273d400cc16ba93f72ded2ede46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724844"
---
# <a name="constructing-types-entity-sql"></a><span data-ttu-id="831be-103">コンストラクター (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="831be-103">Constructing Types (Entity SQL)</span></span>

<!-- markdownlint-disable DOCSMD001 -->
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="831be-104">には、行コンストラクター、名前付きの型コンストラクター、およびコレクション コンストラクターの 3 種類のコンストラクターが用意されています。</span><span class="sxs-lookup"><span data-stu-id="831be-104">provides three kinds of constructors: row constructors, named type constructors, and collection constructors.</span></span>

## <a name="row-constructors"></a><span data-ttu-id="831be-105">行コンストラクター</span><span class="sxs-lookup"><span data-stu-id="831be-105">Row Constructors</span></span>

<span data-ttu-id="831be-106">1 つまたは複数の値から構造的に型付けされた匿名レコードを構築するには、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の行コンストラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="831be-106">You use row constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="831be-107">行コンストラクターの結果の型は、行の構築に使用された値の型に対応するフィールド型を持つ行型です。</span><span class="sxs-lookup"><span data-stu-id="831be-107">The result type of a row constructor is a row type whose field types correspond to the types of the values used to construct the row.</span></span> <span data-ttu-id="831be-108">たとえば、次の式では `Record(a int, b string, c int)`型の値が構築されます。</span><span class="sxs-lookup"><span data-stu-id="831be-108">For example, the following expression constructs a value of type `Record(a int, b string, c int)`:</span></span>

`ROW(1 AS a, "abc" AS b, a + 34 AS c)`

<span data-ttu-id="831be-109">行コンストラクターで式の別名が指定されていなければ、Entity Framework は別名の生成を試みます。</span><span class="sxs-lookup"><span data-stu-id="831be-109">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="831be-110">詳細については、「[識別子](identifiers-entity-sql.md)」の「別名の規則」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="831be-110">For more information, see the "Aliasing Rules" section in [Identifiers](identifiers-entity-sql.md).</span></span>

<span data-ttu-id="831be-111">次の規則は、行コンストラクターで別名を定義する式に適用されます。</span><span class="sxs-lookup"><span data-stu-id="831be-111">The following rules apply to expression aliasing in a row constructor:</span></span>

- <span data-ttu-id="831be-112">行コンストラクターの式で同じコンストラクターの他の別名を参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="831be-112">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>
- <span data-ttu-id="831be-113">同じ行コンストラクター内の 2 つの式に同じ別名を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="831be-113">Two expressions in the same row constructor cannot have the same alias.</span></span>

<span data-ttu-id="831be-114">行コンストラクターの詳細については、「[ROW](row-entity-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="831be-114">For more information about row constructors, see [ROW](row-entity-sql.md).</span></span>

## <a name="collection-constructors"></a><span data-ttu-id="831be-115">コレクション コンストラクター</span><span class="sxs-lookup"><span data-stu-id="831be-115">Collection Constructors</span></span>

<span data-ttu-id="831be-116">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のコレクション コンストラクターを使用して、値のリストからマルチセットのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="831be-116">You use collection constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="831be-117">コンストラクターのすべての値は、相互に互換性のある型 `T` でなければなりません。また、コンストラクターは `Multiset<T>` 型のコレクションを生成します。</span><span class="sxs-lookup"><span data-stu-id="831be-117">All the values in the constructor must be of mutually compatible type `T`, and the constructor produces a collection of type `Multiset<T>`.</span></span> <span data-ttu-id="831be-118">たとえば、次の式は整数のコレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="831be-118">For example, the following expression creates a collection of integers:</span></span>

`Multiset(1, 2, 3)`

`{1, 2, 3}`

<span data-ttu-id="831be-119">要素の型が確認できないため、空のマルチセット コンストラクターは使用できません。</span><span class="sxs-lookup"><span data-stu-id="831be-119">Empty multiset constructors are not allowed because the type of the elements cannot be determined.</span></span> <span data-ttu-id="831be-120">次の式は無効です。</span><span class="sxs-lookup"><span data-stu-id="831be-120">The following is not valid:</span></span>

`multiset() {}`

<span data-ttu-id="831be-121">詳細については、「[MULTISET](multiset-entity-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="831be-121">For more information, see [MULTISET](multiset-entity-sql.md).</span></span>

## <a name="named-type-constructors-namedtype-initializers"></a><span data-ttu-id="831be-122">名前付きの型コンストラクター (NamedType 初期化子)</span><span class="sxs-lookup"><span data-stu-id="831be-122">Named Type Constructors (NamedType Initializers)</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="831be-123">では、型コンストラクター (初期化子) を使用して、名前付きの複合型およびエンティティ型のインスタンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="831be-123">allows type constructors (initializers) to create instances of named complex types and entity types.</span></span> <span data-ttu-id="831be-124">たとえば、次の式は `Person` 型のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="831be-124">For example, the following expression creates an instance of a `Person` type.</span></span>

`Person("abc", 12)`

<span data-ttu-id="831be-125">次の式は、複合型のインスタンスを作成する式です。</span><span class="sxs-lookup"><span data-stu-id="831be-125">The following expression creates an instance of a complex type.</span></span>

`MyModel.ZipCode(‘98118’, ‘4567’)`

<span data-ttu-id="831be-126">次の式は、入れ子になった複合型のインスタンスを作成する式です。</span><span class="sxs-lookup"><span data-stu-id="831be-126">The following expression creates an instance of a nested complex type.</span></span>

`MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`

<span data-ttu-id="831be-127">次の式は、入れ子になった複合型を持つエンティティのインスタンスを作成する式です。</span><span class="sxs-lookup"><span data-stu-id="831be-127">The following expression creates an instance of an entity with a nested complex type.</span></span>

`MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`

<span data-ttu-id="831be-128">次の例は、複合型のプロパティを null に初期化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="831be-128">The following example shows how to initialize a property of a complex type to null.</span></span> `MyModel.ZipCode(‘98118’, null)`

<span data-ttu-id="831be-129">コンストラクターに対する引数は、型の属性の宣言と同じ順序であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="831be-129">The arguments to the constructor are assumed to be in the same order as the declaration of the attributes of the type.</span></span>

<span data-ttu-id="831be-130">詳細については、「[名前付きの型コンストラクター](named-type-constructor-entity-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="831be-130">For more information, see [Named Type Constructor](named-type-constructor-entity-sql.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="831be-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="831be-131">See also</span></span>

- [<span data-ttu-id="831be-132">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="831be-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="831be-133">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="831be-133">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="831be-134">型システム</span><span class="sxs-lookup"><span data-stu-id="831be-134">Type System</span></span>](type-system-entity-sql.md)
