---
title: クラス内の do 束縛
description: クラス定義の F# 'do' バインドを使用する方法について説明します。これにより、オブジェクトが構築されたとき、または型が最初に使用されたときにアクションが実行されます。
ms.date: 05/16/2016
ms.openlocfilehash: ced4f1bb17d9e23bf51cc79b5a275cc334cca013
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627580"
---
# <a name="do-bindings-in-classes"></a><span data-ttu-id="a2f26-103">クラス内の do 束縛</span><span class="sxs-lookup"><span data-stu-id="a2f26-103">do Bindings in Classes</span></span>

<span data-ttu-id="a2f26-104">クラス定義の `do` バインドではオブジェクトが構築されたとき、静的 `do` バインドでは型が最初に使用されたときにアクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="a2f26-104">A `do` binding in a class definition performs actions when the object is constructed or, for a static `do` binding, when the type is first used.</span></span>

## <a name="syntax"></a><span data-ttu-id="a2f26-105">構文</span><span class="sxs-lookup"><span data-stu-id="a2f26-105">Syntax</span></span>

```fsharp
[static] do expression
```

## <a name="remarks"></a><span data-ttu-id="a2f26-106">解説</span><span class="sxs-lookup"><span data-stu-id="a2f26-106">Remarks</span></span>

<span data-ttu-id="a2f26-107">`do` バインドは、クラス定義の中で、`let` バインドと一緒かその後、ただしメンバー定義よりも前に現れます。</span><span class="sxs-lookup"><span data-stu-id="a2f26-107">A `do` binding appears together with or after `let` bindings but before member definitions in a class definition.</span></span> <span data-ttu-id="a2f26-108">`do` キーワードは、モジュール レベルの `do` バインドに対しては省略可能ですが、クラス定義の `do` バインドでは省略可能ではありません。</span><span class="sxs-lookup"><span data-stu-id="a2f26-108">Although the `do` keyword is optional for `do` bindings at the module level, it is not optional for `do` bindings in a class definition.</span></span>

<span data-ttu-id="a2f26-109">所定の型の各オブジェクトを構築する際、非静的 `do` バインドと非静的 `let` バインドは、クラス定義に表示される順序で実行されます。</span><span class="sxs-lookup"><span data-stu-id="a2f26-109">For the construction of every object of any given type, non-static `do` bindings and non-static `let` bindings are executed in the order in which they appear in the class definition.</span></span> <span data-ttu-id="a2f26-110">1 つの型で複数の `do` バインドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="a2f26-110">Multiple `do` bindings can occur in one type.</span></span> <span data-ttu-id="a2f26-111">非静的 `let` バインドと非静的 `do` バインドは、プライマリ コンストラクターの本体になります。</span><span class="sxs-lookup"><span data-stu-id="a2f26-111">The non-static `let` bindings and the non-static `do` bindings become the body of the primary constructor.</span></span> <span data-ttu-id="a2f26-112">非静的 `do` バインド セクションのコードは、プライマリ コンストラクターのパラメーターと、`let` バインド セクションで定義されている任意の値または関数を参照できます。</span><span class="sxs-lookup"><span data-stu-id="a2f26-112">The code in the non-static `do` bindings section can reference the primary constructor parameters and any values or functions that are defined in the `let` bindings section.</span></span>

<span data-ttu-id="a2f26-113">非静的 `do` バインドでは、クラスのメンバーにアクセスできます。ただし、そのクラスに、クラスの見出しで `as` キーワードによって定義されている自己識別子があり、かつそれらのメンバーの使用がすべて、そのクラスの自己識別子で修飾されている場合に限ります。</span><span class="sxs-lookup"><span data-stu-id="a2f26-113">Non-static `do` bindings can access members of the class as long as the class has a self identifier that is defined by an `as` keyword in the class heading, and as long as all uses of those members are qualified with the self identifier for the class.</span></span>

<span data-ttu-id="a2f26-114">`let` バインドによってクラスのプライベート フィールドが初期化されるため (これは、メンバーが想定どおりに動作することを保証するためにしばしば必要となる)、通常は `do` バインドの後に `let` バインドが配置されます。これにより、`do` バインド内のコードが完全に初期化されたオブジェクトで実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a2f26-114">Because `let` bindings initialize the private fields of a class, which is often necessary to guarantee that members behave as expected, `do` bindings are usually put after `let` bindings so that code in the `do` binding can execute with a fully initialized object.</span></span> <span data-ttu-id="a2f26-115">初期化が完了する前にコードによってメンバーの使用が試行されると、InvalidOperationException が発生します。</span><span class="sxs-lookup"><span data-stu-id="a2f26-115">If your code attempts to use a member before the initialization is complete, an InvalidOperationException is raised.</span></span>

<span data-ttu-id="a2f26-116">静的 `do` バインドでは、外部クラスの静的メンバーまたはフィールドを参照できますが、インスタンスのメンバーやフィールドを参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="a2f26-116">Static `do` bindings can reference static members or fields of the enclosing class but not instance members or fields.</span></span> <span data-ttu-id="a2f26-117">静的 `do` バインドはクラスの静的初期化子の一部となり、クラスが最初に使用される前に確実に実行されます。</span><span class="sxs-lookup"><span data-stu-id="a2f26-117">Static `do` bindings become part of the static initializer for the class, which is guaranteed to execute before the class is first used.</span></span>

<span data-ttu-id="a2f26-118">型の `do` バインドでは、属性は無視されます。</span><span class="sxs-lookup"><span data-stu-id="a2f26-118">Attributes are ignored for `do` bindings in types.</span></span> <span data-ttu-id="a2f26-119">`do` バインドで実行されるコードに属性が必要な場合は、プライマリ コンストラクターに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2f26-119">If an attribute is required for code that executes in a `do` binding, it must be applied to the primary constructor.</span></span>

<span data-ttu-id="a2f26-120">次のコードでは、クラスに静的 `do` バインドと非静的 `do` バインドがあります。</span><span class="sxs-lookup"><span data-stu-id="a2f26-120">In the following code, a class has a static `do` binding and a non-static `do` binding.</span></span> <span data-ttu-id="a2f26-121">オブジェクトには、`a` と `b` という 2 つのパラメーターを持つコンストラクターがあり、2 つのプライベート フィールドがクラスの `let` バインドで定義されています。</span><span class="sxs-lookup"><span data-stu-id="a2f26-121">The object has a constructor that has two parameters, `a` and `b`, and two private fields are defined in the `let` bindings for the class.</span></span> <span data-ttu-id="a2f26-122">2 つのプロパティも定義されています。</span><span class="sxs-lookup"><span data-stu-id="a2f26-122">Two properties are also defined.</span></span> <span data-ttu-id="a2f26-123">これらはすべては、それらの値をすべて出力する行で示されているように、非静的 `do` バインド セクションのスコープ内にあります。</span><span class="sxs-lookup"><span data-stu-id="a2f26-123">All of these are in scope in the non-static `do` bindings section, as is illustrated by the line that prints all those values.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

<span data-ttu-id="a2f26-124">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a2f26-124">The output is as follows.</span></span>

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a><span data-ttu-id="a2f26-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2f26-125">See also</span></span>

- <span data-ttu-id="a2f26-126">[[メンバー]](index.md)</span><span class="sxs-lookup"><span data-stu-id="a2f26-126">[Members](index.md)</span></span>
- [<span data-ttu-id="a2f26-127">クラス</span><span class="sxs-lookup"><span data-stu-id="a2f26-127">Classes</span></span>](../classes.md)
- [<span data-ttu-id="a2f26-128">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="a2f26-128">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="a2f26-129">クラス内の `let` バインド</span><span class="sxs-lookup"><span data-stu-id="a2f26-129">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
- [<span data-ttu-id="a2f26-130">`do` バインド</span><span class="sxs-lookup"><span data-stu-id="a2f26-130">`do` Bindings</span></span>](../functions/do-Bindings.md)
