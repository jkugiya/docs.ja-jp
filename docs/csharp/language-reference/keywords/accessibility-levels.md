---
description: アクセシビリティ レベル - C# リファレンス
title: アクセシビリティ レベル - C# リファレンス
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 509902e9998af421c0afd31070b1be36d64df0f8
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604594"
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="dabce-103">アクセシビリティ レベル (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="dabce-103">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="dabce-104">以下に示したのは、メンバーに適用されるアクセシビリティ レベルの宣言です。`public`、`protected`、`internal`、`private` の各アクセス修飾子を使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="dabce-104">Use the access modifiers, `public`, `protected`, `internal`, or `private`, to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="dabce-105">アクセシビリティの宣言</span><span class="sxs-lookup"><span data-stu-id="dabce-105">Declared accessibility</span></span>|<span data-ttu-id="dabce-106">説明</span><span class="sxs-lookup"><span data-stu-id="dabce-106">Meaning</span></span>|  
|----------------------------|-------------|  
|[`public`](public.md)|<span data-ttu-id="dabce-107">アクセスは無制限です。</span><span class="sxs-lookup"><span data-stu-id="dabce-107">Access is not restricted.</span></span>|  
|[`protected`](protected.md)|<span data-ttu-id="dabce-108">コンテナーであるクラスまたはそこから派生した型にアクセスが限定されます。</span><span class="sxs-lookup"><span data-stu-id="dabce-108">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|[`internal`](internal.md)|<span data-ttu-id="dabce-109">アクセスは現在のアセンブリに限定されます。</span><span class="sxs-lookup"><span data-stu-id="dabce-109">Access is limited to the current assembly.</span></span>|  
|[`protected internal`](protected-internal.md)|<span data-ttu-id="dabce-110">現在のアセンブリ、またはコンテナーであるクラスから派生した型にアクセスが限定されます。</span><span class="sxs-lookup"><span data-stu-id="dabce-110">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|[`private`](private.md)|<span data-ttu-id="dabce-111">コンテナーである型にアクセスが限定されます。</span><span class="sxs-lookup"><span data-stu-id="dabce-111">Access is limited to the containing type.</span></span>|  
|[`private protected`](private-protected.md)|<span data-ttu-id="dabce-112">現在のアセンブリ内の、コンテナーであるクラス、またはコンテナーであるクラスから派生した型にアクセスが制限されます。</span><span class="sxs-lookup"><span data-stu-id="dabce-112">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="dabce-113">C# 7.2 以降で使用可能です。</span><span class="sxs-lookup"><span data-stu-id="dabce-113">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="dabce-114">`protected internal` または `private protected` の組み合わせを使う場合を除き、1 つのメンバーまたは 1 つの型に指定できるアクセス修飾子は 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="dabce-114">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="dabce-115">アクセス修飾子を名前空間に適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="dabce-115">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="dabce-116">名前空間には、アクセス制限がありません。</span><span class="sxs-lookup"><span data-stu-id="dabce-116">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="dabce-117">メンバーが宣言されているコンテキストによっては、決まったアクセシビリティしか宣言できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="dabce-117">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="dabce-118">メンバーの宣言にアクセス修飾子が指定されていない場合は、既定のアクセシビリティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="dabce-118">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="dabce-119">トップレベルの型 (他の型に対して入れ子にされていない型) に指定できるアクセシビリティは `internal` と `public` だけです。</span><span class="sxs-lookup"><span data-stu-id="dabce-119">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="dabce-120">既定では、そのような型に `internal` のアクセシビリティが適用されます。</span><span class="sxs-lookup"><span data-stu-id="dabce-120">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="dabce-121">入れ子にされた型 (他の型のメンバーになっている型) には、次の表に示したアクセシビリティを宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="dabce-121">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="dabce-122">コンテナー</span><span class="sxs-lookup"><span data-stu-id="dabce-122">Members of</span></span>|<span data-ttu-id="dabce-123">メンバーの既定のアクセシビリティ</span><span class="sxs-lookup"><span data-stu-id="dabce-123">Default member accessibility</span></span>|<span data-ttu-id="dabce-124">メンバーに対して宣言できるアクセシビリティ</span><span class="sxs-lookup"><span data-stu-id="dabce-124">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="dabce-125">なし</span><span class="sxs-lookup"><span data-stu-id="dabce-125">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`\*<br /><br /> `protected internal` <br /><br />`private protected`|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  

<span data-ttu-id="dabce-126">\* `private` アクセシビリティを持つ `interface` メンバーには、既定の実装が必要です。</span><span class="sxs-lookup"><span data-stu-id="dabce-126">\* An `interface` member with `private` accessibility must have a default implementation.</span></span>

<span data-ttu-id="dabce-127">入れ子にされた型のアクセシビリティは、その型の[アクセシビリティ ドメイン](./accessibility-domain.md)によって決まります。このアクセシビリティ ドメインは、そのメンバーに対して宣言されているアクセシビリティと、そのメンバーの直接のコンテナーである型のアクセシビリティ ドメインの両方によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="dabce-127">The accessibility of a nested type depends on its [accessibility domain](./accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="dabce-128">ただし、入れ子にされた型のアクセシビリティ ドメインが、その型を含んでいる型のアクセシビリティ ドメインを上回ることはできません。</span><span class="sxs-lookup"><span data-stu-id="dabce-128">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="dabce-129">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="dabce-129">C# Language Specification</span></span>  

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dabce-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="dabce-130">See also</span></span>

- [<span data-ttu-id="dabce-131">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="dabce-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dabce-132">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="dabce-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dabce-133">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="dabce-133">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="dabce-134">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="dabce-134">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="dabce-135">アクセシビリティ ドメイン</span><span class="sxs-lookup"><span data-stu-id="dabce-135">Accessibility Domain</span></span>](./accessibility-domain.md)
- [<span data-ttu-id="dabce-136">アクセシビリティ レベルの使用に関する制限事項</span><span class="sxs-lookup"><span data-stu-id="dabce-136">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="dabce-137">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="dabce-137">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="dabce-138">public</span><span class="sxs-lookup"><span data-stu-id="dabce-138">public</span></span>](./public.md)
- [<span data-ttu-id="dabce-139">private</span><span class="sxs-lookup"><span data-stu-id="dabce-139">private</span></span>](./private.md)
- [<span data-ttu-id="dabce-140">protected</span><span class="sxs-lookup"><span data-stu-id="dabce-140">protected</span></span>](./protected.md)
- [<span data-ttu-id="dabce-141">internal</span><span class="sxs-lookup"><span data-stu-id="dabce-141">internal</span></span>](./internal.md)
