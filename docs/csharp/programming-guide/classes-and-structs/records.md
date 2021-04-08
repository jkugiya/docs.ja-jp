---
title: レコード - C# プログラミング ガイド
description: レコードの型と、その作成方法について説明します
ms.date: 02/26/2021
helpviewer_keywords:
- records [C#]
- C# language, records
ms.openlocfilehash: 99370e398d5e607def58334b33ae20aa59e21962
ms.sourcegitcommit: 872ca41d1c26f39d0aef57cc365d09503bac780d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2021
ms.locfileid: "106288031"
---
# <a name="records-c-programming-guide"></a><span data-ttu-id="1f82d-103">レコード (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="1f82d-103">Records (C# Programming Guide)</span></span>

<span data-ttu-id="1f82d-104">[レコード](../../language-reference/builtin-types/record.md)とは、データ モデルを操作するための特殊な構文と動作を提供する[クラス](../../language-reference/keywords/class.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f82d-104">A [record](../../language-reference/builtin-types/record.md) is a [class](../../language-reference/keywords/class.md) that provides special syntax and behavior for working with data models.</span></span> <span data-ttu-id="1f82d-105">クラスについては、「[クラス (C# プログラミング ガイド)](classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f82d-105">For information about classes, see [Classes (C# Programming Guide)](classes.md).</span></span>

## <a name="when-to-use-records"></a><span data-ttu-id="1f82d-106">レコードを使用する場面</span><span class="sxs-lookup"><span data-stu-id="1f82d-106">When to use records</span></span>

<span data-ttu-id="1f82d-107">次のシナリオでは、クラスの代わりにレコードを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="1f82d-107">Consider using a record in place of a class in the following scenarios:</span></span>

* <span data-ttu-id="1f82d-108">オブジェクトが不変となる参照型を定義する。</span><span class="sxs-lookup"><span data-stu-id="1f82d-108">You want to define a reference type for which objects are immutable.</span></span>
* <span data-ttu-id="1f82d-109">[値の等価性](../statements-expressions-operators/equality-comparisons.md#value-equality)に依存するデータ モデルを定義する。</span><span class="sxs-lookup"><span data-stu-id="1f82d-109">You want to define a data model that depends on [value equality](../statements-expressions-operators/equality-comparisons.md#value-equality).</span></span>

### <a name="immutability"></a><span data-ttu-id="1f82d-110">不変性</span><span class="sxs-lookup"><span data-stu-id="1f82d-110">Immutability</span></span>

<span data-ttu-id="1f82d-111">不変型とは、オブジェクトがインスタンス化された後にそのプロパティまたはフィールドの値を変更できないようにするためのものです。</span><span class="sxs-lookup"><span data-stu-id="1f82d-111">An immutable type is one that prevents you from changing any property or field values of an object after it's instantiated.</span></span> <span data-ttu-id="1f82d-112">不変性は、型をスレッドセーフにする必要がある場合またはハッシュ テーブル内で変化のないハッシュ コードに依存している場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1f82d-112">Immutability can be useful when you need a type to be thread-safe or you're depending on a hash code remaining the same in a hash table.</span></span> <span data-ttu-id="1f82d-113">レコードには、不変型を作成および操作するための簡潔な構文が用意されています。</span><span class="sxs-lookup"><span data-stu-id="1f82d-113">Records provide concise syntax for creating and working with immutable types.</span></span>

<span data-ttu-id="1f82d-114">不変性は、すべてのデータ シナリオに適しているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="1f82d-114">Immutability isn't appropriate for all data scenarios.</span></span> <span data-ttu-id="1f82d-115">たとえば、[Entity Framework Core](/ef/core/) では、不変のエンティティ型を使用した更新がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1f82d-115">[Entity Framework Core](/ef/core/), for example, doesn't support updating with immutable entity types.</span></span>

### <a name="value-equality"></a><span data-ttu-id="1f82d-116">値の等価性</span><span class="sxs-lookup"><span data-stu-id="1f82d-116">Value equality</span></span>

<span data-ttu-id="1f82d-117">レコードにおける値の等価性とは、型が一致し、かつプロパティおよびフィールドの値がすべて一致する場合にレコード型の 2 つの変数が等しいことを意味します。</span><span class="sxs-lookup"><span data-stu-id="1f82d-117">For records, value equality means that two variables of a record type are equal if the types match and all property and field values match.</span></span> <span data-ttu-id="1f82d-118">クラスなどの他の参照型における等価性とは、[参照の等価性](../statements-expressions-operators/equality-comparisons.md#reference-equality)を意味します。</span><span class="sxs-lookup"><span data-stu-id="1f82d-118">For other reference types such as classes, equality means [reference equality](../statements-expressions-operators/equality-comparisons.md#reference-equality).</span></span> <span data-ttu-id="1f82d-119">つまり、クラス型の 2 つの変数は、同じオブジェクトを参照する場合、等しいことになります。</span><span class="sxs-lookup"><span data-stu-id="1f82d-119">That is, two variables of a class type are equal if they refer to the same object.</span></span> <span data-ttu-id="1f82d-120">2 つのレコード インスタンスが等しいかどうかを判断するメソッドと演算子では、値の等価性が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1f82d-120">Methods and operators that determine equality of two record instances use value equality.</span></span>

<span data-ttu-id="1f82d-121">すべてのデータ モデルが値の等価性に適しているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="1f82d-121">Not all data models work well with value equality.</span></span> <span data-ttu-id="1f82d-122">たとえば、[Entity Framework Core](/ef/core/) では、概念的に 1 つのエンティティであるものに対して、エンティティ型の 1 つのインスタンスだけが確実に使用されるようにするために、参照の等価性に依存します。</span><span class="sxs-lookup"><span data-stu-id="1f82d-122">For example, [Entity Framework Core](/ef/core/) depends on reference equality to ensure that it uses only one instance of an entity type for what is conceptually one entity.</span></span> <span data-ttu-id="1f82d-123">このため、レコード型は Entity Framework Core でエンティティ型として使用するのに適していません。</span><span class="sxs-lookup"><span data-stu-id="1f82d-123">For this reason, record types aren't appropriate for use as entity types in Entity Framework Core.</span></span>

## <a name="how-records-differ-from-classes"></a><span data-ttu-id="1f82d-124">レコードとクラスの相違点</span><span class="sxs-lookup"><span data-stu-id="1f82d-124">How records differ from classes</span></span>

<span data-ttu-id="1f82d-125">クラスを[宣言](classes.md#declaring-classes)および[インスタンス化](classes.md#creating-objects)するのと同じ構文がレコードでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="1f82d-125">The same syntax that [declares](classes.md#declaring-classes) and [instantiates](classes.md#creating-objects) classes can be used with records.</span></span> <span data-ttu-id="1f82d-126">キーワード `class` をキーワード `record` に置き換えるだけです。</span><span class="sxs-lookup"><span data-stu-id="1f82d-126">Just substitute the `record` keyword for the `class` keyword.</span></span> <span data-ttu-id="1f82d-127">同様に、継承関係を表す場合も同じ構文がレコードによってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1f82d-127">Likewise, the same syntax for expressing inheritance relationships is supported by records.</span></span> <span data-ttu-id="1f82d-128">レコードは次の点がクラスとは異なります。</span><span class="sxs-lookup"><span data-stu-id="1f82d-128">Records differ from classes in the following ways:</span></span>

* <span data-ttu-id="1f82d-129">[位置指定パラメーター](../../language-reference/builtin-types/record.md#positional-syntax-for-property-definition)を使用して、不変プロパティを持つ型を作成してインスタンス化することができます。</span><span class="sxs-lookup"><span data-stu-id="1f82d-129">You can use [positional parameters](../../language-reference/builtin-types/record.md#positional-syntax-for-property-definition) to create and instantiate a type with immutable properties.</span></span>
* <span data-ttu-id="1f82d-130">クラスで参照の等価性または非等価性を示すメソッドと演算子 (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> や `==` など) は、レコードでは[値の等価性または非等価性](../../language-reference/builtin-types/record.md#value-equality)を示します。</span><span class="sxs-lookup"><span data-stu-id="1f82d-130">The same methods and operators that indicate reference equality or inequality in classes (such as <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> and `==`), indicate [value equality or inequality](../../language-reference/builtin-types/record.md#value-equality) in records.</span></span>
* <span data-ttu-id="1f82d-131">[`with` 式](../../language-reference/builtin-types/record.md#nondestructive-mutation)を使用すれば、選択したプロパティに新しい値を指定して、不変オブジェクトのコピーを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="1f82d-131">You can use a [`with` expression](../../language-reference/builtin-types/record.md#nondestructive-mutation) to create a copy of an immutable object with new values in selected properties.</span></span>
* <span data-ttu-id="1f82d-132">レコードの `ToString` メソッドを使用すると、オブジェクトの型名とそのすべてのパブリック プロパティの名前および値を示す書式設定された文字列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="1f82d-132">A record's `ToString` method creates a formatted string that shows an object's type name and the names and values of all its public properties.</span></span>
* <span data-ttu-id="1f82d-133">レコードは、[別のレコードから継承](../../language-reference/builtin-types/record.md#inheritance)できます。</span><span class="sxs-lookup"><span data-stu-id="1f82d-133">A record can [inherit from another record](../../language-reference/builtin-types/record.md#inheritance).</span></span> <span data-ttu-id="1f82d-134">レコードはクラスから継承できません。また、クラスはレコードから継承できません。</span><span class="sxs-lookup"><span data-stu-id="1f82d-134">A record can't inherit from a class, and a class can't inherit from a record.</span></span>

## <a name="examples"></a><span data-ttu-id="1f82d-135">例</span><span class="sxs-lookup"><span data-stu-id="1f82d-135">Examples</span></span>

<span data-ttu-id="1f82d-136">次の例では、位置指定パラメーターを使用してレコードを宣言およびインスタンス化するパブリック レコードを定義します。</span><span class="sxs-lookup"><span data-stu-id="1f82d-136">The following example defines a public record that uses positional parameters to declare and instantiate a record.</span></span> <span data-ttu-id="1f82d-137">次に、型名とプロパティ値を出力します。</span><span class="sxs-lookup"><span data-stu-id="1f82d-137">It then prints out the type name and property values:</span></span>

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="InstantiatePositional":::

<span data-ttu-id="1f82d-138">次の例では、レコードでの値の等価性を示します。</span><span class="sxs-lookup"><span data-stu-id="1f82d-138">The following example demonstrates value equality in records:</span></span>

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="Equality":::

<span data-ttu-id="1f82d-139">次の例では、`with` 式を使用して、不変オブジェクトをコピーし、プロパティの 1 つを変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1f82d-139">The following example demonstrates use of a `with` expression to copy an immutable object and change one of the properties:</span></span>

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="WithExpressions":::

<span data-ttu-id="1f82d-140">詳細については、「[レコード (C# リファレンス)](../../language-reference/builtin-types/record.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f82d-140">For more information, see [Records (C# reference)](../../language-reference/builtin-types/record.md).</span></span>
  
## <a name="c-language-specification"></a><span data-ttu-id="1f82d-141">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="1f82d-141">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1f82d-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f82d-142">See also</span></span>

- [<span data-ttu-id="1f82d-143">クラス (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="1f82d-143">Classes (C# Programming Guide)</span></span>](classes.md)
- [<span data-ttu-id="1f82d-144">レコード (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="1f82d-144">Records (C# reference)</span></span>](../../language-reference/builtin-types/record.md)
- [<span data-ttu-id="1f82d-145">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="1f82d-145">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1f82d-146">オブジェクト指向プログラミング</span><span class="sxs-lookup"><span data-stu-id="1f82d-146">Object-Oriented Programming</span></span>](../../tutorials/intro-to-csharp/object-oriented-programming.md)
- [<span data-ttu-id="1f82d-147">ポリモーフィズム</span><span class="sxs-lookup"><span data-stu-id="1f82d-147">Polymorphism</span></span>](polymorphism.md)
- [<span data-ttu-id="1f82d-148">識別子名</span><span class="sxs-lookup"><span data-stu-id="1f82d-148">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="1f82d-149">メンバー</span><span class="sxs-lookup"><span data-stu-id="1f82d-149">Members</span></span>](members.md)
- [<span data-ttu-id="1f82d-150">メソッド</span><span class="sxs-lookup"><span data-stu-id="1f82d-150">Methods</span></span>](methods.md)
- [<span data-ttu-id="1f82d-151">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="1f82d-151">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="1f82d-152">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="1f82d-152">Finalizers</span></span>](destructors.md)
- [<span data-ttu-id="1f82d-153">オブジェクト</span><span class="sxs-lookup"><span data-stu-id="1f82d-153">Objects</span></span>](objects.md)
