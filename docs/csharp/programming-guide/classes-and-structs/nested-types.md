---
title: 入れ子にされた型 - C# プログラミング ガイド
description: クラス、構造体、またはインターフェイスの中で定義された型は、C# では入れ子にされた型と呼ばれます。
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 853138beed6ad9ddffa789f0080ca1fd2ba9d700
ms.sourcegitcommit: 1d3af230ec30d8d061be7a887f6ba38a530c4ece
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2021
ms.locfileid: "102511919"
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="b55cf-103">入れ子にされた型 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="b55cf-103">Nested Types (C# Programming Guide)</span></span>

<span data-ttu-id="b55cf-104">[クラス](../../language-reference/keywords/class.md)、[構造体](../../language-reference/builtin-types/struct.md)、[インターフェイス](../../language-reference/keywords/interface.md)の中で定義された型は、入れ子にされた型と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="b55cf-104">A type defined within a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) is called a nested type.</span></span> <span data-ttu-id="b55cf-105">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b55cf-105">For example</span></span>

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

<span data-ttu-id="b55cf-106">外側の型がクラス、構造体、入れ子にされた型のいずれであっても、入れ子にされた型は既定で [private](../../language-reference/keywords/private.md) になり、それが含まれる型からのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b55cf-106">Regardless of whether the outer type is a class, interface, or struct, nested types default to [private](../../language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="b55cf-107">前の例では、`Nested` クラスは外部の型にアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="b55cf-107">In the previous example, the `Nested` class is inaccessible to external types.</span></span>

<span data-ttu-id="b55cf-108">次のように、[アクセス修飾子](../../language-reference/keywords/access-modifiers.md)を指定して、入れ子にされた型のアクセシビリティを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="b55cf-108">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="b55cf-109">**クラス** の入れ子にされた型は、[public](../../language-reference/keywords/public.md)、[protected](../../language-reference/keywords/protected.md)、[internal](../../language-reference/keywords/internal.md)、[protected internal](../../language-reference/keywords/protected-internal.md)、[private](../../language-reference/keywords/private.md)、[private protected](../../language-reference/keywords/private-protected.md) になります。</span><span class="sxs-lookup"><span data-stu-id="b55cf-109">Nested types of a **class** can be [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span>

   <span data-ttu-id="b55cf-110">ただし、[シール クラス](../../language-reference/keywords/sealed.md)内で `protected`、`protected internal`、`private protected` の入れ子にされたクラスを定義すると、コンパイラの警告 [CS0628](../../misc/cs0628.md)、"新規のプロテクト メンバーがシール クラスで宣言されました" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b55cf-110">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>

   <span data-ttu-id="b55cf-111">また、入れ子になった型を外部から参照できるようにすることは、コード品質ルール [CA1034](../../../fundamentals/code-analysis/quality-rules/ca1034.md) の "入れ子にされた型を参照可能にすることはできません" に違反することにもご注意ください。</span><span class="sxs-lookup"><span data-stu-id="b55cf-111">Also be aware that making a nested type externally visible violates the code quality rule [CA1034](../../../fundamentals/code-analysis/quality-rules/ca1034.md) "Nested types should not be visible".</span></span>

- <span data-ttu-id="b55cf-112">**構造体** の入れ子にされた型は、は、[public](../../language-reference/keywords/public.md)、[internal](../../language-reference/keywords/internal.md)、または [private](../../language-reference/keywords/private.md) のいずれかが可能です。</span><span class="sxs-lookup"><span data-stu-id="b55cf-112">Nested types of a **struct** can be [public](../../language-reference/keywords/public.md), [internal](../../language-reference/keywords/internal.md), or [private](../../language-reference/keywords/private.md).</span></span>

<span data-ttu-id="b55cf-113">次の例では、`Nested` クラスを public にします。</span><span class="sxs-lookup"><span data-stu-id="b55cf-113">The following example makes the `Nested` class public:</span></span>

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

<span data-ttu-id="b55cf-114">入れ子にされた型 (内側の型) は、包含する型 (外側の型) にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b55cf-114">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="b55cf-115">包含する型にアクセスするには、その型を引数として入れ子にされた型のコンストラクターに渡します。</span><span class="sxs-lookup"><span data-stu-id="b55cf-115">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="b55cf-116">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b55cf-116">For example:</span></span>

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

<span data-ttu-id="b55cf-117">入れ子にされた型は、包含する型にアクセス可能なすべてのメンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b55cf-117">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="b55cf-118">入れ子にされた型は、継承されたプロテクト メンバーを含む、包含する型のプライベート メンバーとプロテクト メンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b55cf-118">It can access private and protected members of the containing type, including any inherited protected members.</span></span>

<span data-ttu-id="b55cf-119">上記の宣言では、クラス `Nested` の完全名は `Container.Nested` です。</span><span class="sxs-lookup"><span data-stu-id="b55cf-119">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="b55cf-120">これは、次のように入れ子になったクラスの新しいインスタンスを作成するときに使用される名前です。</span><span class="sxs-lookup"><span data-stu-id="b55cf-120">This is the name used to create a new instance of the nested class, as follows:</span></span>

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a><span data-ttu-id="b55cf-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="b55cf-121">See also</span></span>

- [<span data-ttu-id="b55cf-122">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="b55cf-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b55cf-123">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="b55cf-123">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="b55cf-124">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="b55cf-124">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="b55cf-125">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="b55cf-125">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="b55cf-126">CA1034 ルール</span><span class="sxs-lookup"><span data-stu-id="b55cf-126">CA1034 rule</span></span>](../../../fundamentals/code-analysis/quality-rules/ca1034.md)
