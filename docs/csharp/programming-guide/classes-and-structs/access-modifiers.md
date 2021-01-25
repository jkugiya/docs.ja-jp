---
title: アクセス修飾子 - C# プログラミング ガイド
description: C# のすべての型とそのメンバーにアクセシビリティ レベルがあります。他のコードからそれらの型やそのメンバーを利用できるかどうかは、アクセシビリティ レベルによって制御されます。 このアクセス修飾子一覧を確認してください。
ms.date: 03/08/2020
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: d800116137e088a54edb221fb4f81ecd47b0278f
ms.sourcegitcommit: 2b878d7011306b215dbf3d5dc9c1e78355a6dcd5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2021
ms.locfileid: "98757864"
---
# <a name="access-modifiers-c-programming-guide"></a><span data-ttu-id="1f9eb-104">アクセス修飾子 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="1f9eb-104">Access Modifiers (C# Programming Guide)</span></span>

<span data-ttu-id="1f9eb-105">すべての型と型メンバーにアクセシビリティ レベルがあります。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-105">All types and type members have an accessibility level.</span></span> <span data-ttu-id="1f9eb-106">同じアセンブリまたは他のアセンブリに他のコードからそれらの型やそのメンバーを利用できるかどうかは、アクセシビリティ レベルによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-106">The accessibility level controls whether they can be used from other code in your assembly or other assemblies.</span></span> <span data-ttu-id="1f9eb-107">型またはメンバーにはその宣言時に、以下のアクセス修飾子を使ってアクセシビリティを指定します。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-107">Use the following access modifiers to specify the accessibility of a type or member when you declare it:</span></span>

- <span data-ttu-id="1f9eb-108">[public](../../language-reference/keywords/public.md):この型またはメンバーには、同じアセンブリ内の他のコードや、そのアセンブリを参照する別のアセンブリ内の任意のコードからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-108">[public](../../language-reference/keywords/public.md): The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>
- <span data-ttu-id="1f9eb-109">[private](../../language-reference/keywords/private.md):この型またはメンバーには、同じ `class` 内または同じ `struct` 内のコードからのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-109">[private](../../language-reference/keywords/private.md): The type or member can be accessed only by code in the same `class` or `struct`.</span></span>
- <span data-ttu-id="1f9eb-110">[protected](../../language-reference/keywords/protected.md):この型またはメンバーには、同じ `class` 内のコードか、その `class` から派生した `class` 内のコードからのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-110">[protected](../../language-reference/keywords/protected.md): The type or member can be accessed only by code in the same `class`, or in a `class` that is derived from that `class`.</span></span>
- <span data-ttu-id="1f9eb-111">[internal](../../language-reference/keywords/internal.md):この型またはメンバーには、同じアセンブリ内の任意のコードからアクセスできますが、別のアセンブリからはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-111">[internal](../../language-reference/keywords/internal.md): The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>
- <span data-ttu-id="1f9eb-112">[protected internal](../../language-reference/keywords/protected-internal.md):この型またはメンバーには、それが宣言されているアセンブリ内の任意のコードからアクセスできるほか、別のアセンブリの派生 `class` 内からアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-112">[protected internal](../../language-reference/keywords/protected-internal.md): The type or member can be accessed by any code in the assembly in which it's declared, or from within a derived `class` in another assembly.</span></span>
- <span data-ttu-id="1f9eb-113">[private protected](../../language-reference/keywords/private-protected.md):この型またはメンバーには、同じ `class` のコードか、その `class` から派生した型のコードによって、その宣言アセンブリ内でのみ、アクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-113">[private protected](../../language-reference/keywords/private-protected.md): The type or member can be accessed only within its declaring assembly, by code in the same `class` or in a type that is derived from that `class`.</span></span>

<span data-ttu-id="1f9eb-114">次の例は、型とメンバーにアクセス修飾子を指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-114">The following examples demonstrate how to specify access modifiers on a type and member:</span></span>

[!code-csharp[PublicAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#PublicAccess)]

<span data-ttu-id="1f9eb-115">一部のコンテキスト、型、メンバーでは、アクセス修飾子が無効になります。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-115">Not all access modifiers are valid for all types or members in all contexts.</span></span> <span data-ttu-id="1f9eb-116">場合によっては、ある型のメンバーのアクセシビリティが、それが含まれる型のアクセシビリティによって制約されることがあります。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-116">In some cases, the accessibility of a type member is constrained by the accessibility of its containing type.</span></span>

## <a name="class-and-struct-accessibility"></a><span data-ttu-id="1f9eb-117">クラスと構造体のアクセシビリティ</span><span class="sxs-lookup"><span data-stu-id="1f9eb-117">Class and struct accessibility</span></span>  

<span data-ttu-id="1f9eb-118">名前空間に直接宣言されている (つまり、他のクラスや構造体の入れ子にされていない) クラスと構造体には、`public` または `internal` を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-118">Classes and structs declared directly within a namespace (in other words, that aren't nested within other classes or structs) can be either `public` or `internal`.</span></span> <span data-ttu-id="1f9eb-119">アクセス修飾子が指定されなかった場合は、既定で `internal` が適用されます。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-119">`internal` is the default if no access modifier is specified.</span></span>

<span data-ttu-id="1f9eb-120">構造体のメンバー (入れ子にされているクラスや構造体も含む) は `public`、`internal`、`private` のいずれかとして宣言できます。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-120">Struct members, including nested classes and structs, can be declared `public`, `internal`, or `private`.</span></span> <span data-ttu-id="1f9eb-121">クラスのメンバー (入れ子にされているクラスや構造体も含む) は `public`、`protected internal`、`protected`、`internal`、`private protected`、`private` のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-121">Class members, including nested classes and structs, can be `public`, `protected internal`, `protected`, `internal`, `private protected`, or `private`.</span></span> <span data-ttu-id="1f9eb-122">クラスのメンバーと構造体のメンバー (入れ子にされているクラスや構造体も含む) には、既定で `private` のアクセスが与えられます。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-122">Class and struct members,  including nested classes and structs, have `private` access by default.</span></span> <span data-ttu-id="1f9eb-123">入れ子にされた型のうち、private が指定されているものには、それを含んでいる型の外部からはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-123">Private nested types aren't accessible from outside the containing type.</span></span>

<span data-ttu-id="1f9eb-124">派生クラスに、その基本型を超えるアクセシビリティを割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-124">Derived classes can't have greater accessibility than their base types.</span></span> <span data-ttu-id="1f9eb-125">内部クラス `A` から派生した public クラス `B` を宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-125">You can't declare a public class `B` that derives from an internal class `A`.</span></span> <span data-ttu-id="1f9eb-126">許可される場合は、`A` を public にする効果が与えられるでしょう。`A` のすべての `protected` または `internal` メンバーに派生クラスからアクセスできるためです。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-126">If allowed, it would have the effect of making `A` public, because all `protected` or `internal` members of `A` are accessible from the derived class.</span></span>

<span data-ttu-id="1f9eb-127">`InternalsVisibleToAttribute` を使用すると、internal 型へのアクセスを他の特定のアセンブリに許可できます。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-127">You can enable specific other assemblies to access your internal types by using the `InternalsVisibleToAttribute`.</span></span> <span data-ttu-id="1f9eb-128">詳細については、[Friend アセンブリ](../../../standard/assembly/friend.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-128">For more information, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>

## <a name="class-and-struct-member-accessibility"></a><span data-ttu-id="1f9eb-129">クラスと構造体のメンバーのアクセシビリティ</span><span class="sxs-lookup"><span data-stu-id="1f9eb-129">Class and struct member accessibility</span></span>  

<span data-ttu-id="1f9eb-130">クラスのメンバー (入れ子にされているクラスや構造体も含む) は、6 種類あるアクセス修飾子をどれでも使って宣言できます。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-130">Class members (including nested classes and structs) can be declared with any of the six types of access.</span></span> <span data-ttu-id="1f9eb-131">構造体のメンバーを `protected`、`protected internal`、`private protected` として宣言することはできません。構造体は継承をサポートしていないためです。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-131">Struct members can't be declared as `protected`, `protected internal`, or `private protected` because structs don't support inheritance.</span></span>

<span data-ttu-id="1f9eb-132">通常、メンバーのアクセシビリティが、それを含んでいる型のアクセシビリティを超えることはありません。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-132">Normally, the accessibility of a member isn't greater than the accessibility of the type that contains it.</span></span> <span data-ttu-id="1f9eb-133">ただし、internal クラスの `public` メンバーには、そのアセンブリの外部からアクセスできる場合もあります。そのメンバーがインターフェイスのメソッドを実装している場合や public な基本クラスに定義されている仮想メソッドをオーバーライドしている場合がそれに該当します。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-133">However, a `public` member of an internal class might be accessible from outside the assembly if the member implements interface methods or overrides virtual methods that are defined in a public base class.</span></span>

<span data-ttu-id="1f9eb-134">あらゆるメンバー フィールド、プロパティ、イベントの型には、メンバー自体と同じかそれ以上のアクセシビリティが必要です。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-134">The type of any member field, property, or event must be at least as accessible as the member itself.</span></span> <span data-ttu-id="1f9eb-135">同様に、あらゆるメソッド、インデクサー、デリゲートの戻り値の型とパラメーターの型には、メンバー自体と同じかそれ以上のアクセシビリティが必要です。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-135">Similarly, the return type and the parameter types of any method, indexer, or delegate must be at least as accessible as the member itself.</span></span> <span data-ttu-id="1f9eb-136">たとえば、`public` メソッド `M` でクラス `C` を返すには、`C` が `public` にもなっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-136">For example, you can't have a `public` method `M` that returns a class `C` unless `C` is also `public`.</span></span> <span data-ttu-id="1f9eb-137">同様に、`A` が `private` として宣言されている場合、`A` 型のプロパティを `protected` にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-137">Likewise, you can't have a `protected` property of type `A` if `A` is declared as `private`.</span></span>

<span data-ttu-id="1f9eb-138">ユーザー定義の演算子は、必ず `public` と `static` として宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-138">User-defined operators must always be declared as `public` and `static`.</span></span> <span data-ttu-id="1f9eb-139">詳細については、「[演算子のオーバーロード](../../language-reference/operators/operator-overloading.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-139">For more information, see [Operator overloading](../../language-reference/operators/operator-overloading.md).</span></span>

<span data-ttu-id="1f9eb-140">アクセシビリティ修飾子をファイナライザーに割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-140">Finalizers can't have accessibility modifiers.</span></span>

<span data-ttu-id="1f9eb-141">`class` または `struct` のメンバーにアクセス レベルを設定するには、該当するキーワードをメンバーの宣言に追加します。その例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-141">To set the access level for a `class` or `struct` member, add the appropriate keyword to the member declaration, as shown in the following example.</span></span>

[!code-csharp[MethodAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#MethodAccess)]

## <a name="other-types"></a><span data-ttu-id="1f9eb-142">その他の型</span><span class="sxs-lookup"><span data-stu-id="1f9eb-142">Other types</span></span>

<span data-ttu-id="1f9eb-143">名前空間内に直接宣言されたインターフェイスは、`public` または `internal` にすることができます。クラスや構造体と同様、インターフェイスの既定のアクセス レベルは `internal` になります。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-143">Interfaces declared directly within a namespace can be `public` or `internal` and, just like classes and structs, interfaces default to `internal` access.</span></span> <span data-ttu-id="1f9eb-144">インターフェイスのメンバーは既定で `public` です。他の型がクラスや構造体にアクセスできるようにすることがインターフェイスの目的であるためです。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-144">Interface members are `public` by default because the purpose of an interface is to enable other types to access a class or struct.</span></span> <span data-ttu-id="1f9eb-145">インターフェイス メンバー宣言には、あらゆるアクセス修飾子を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-145">Interface member declarations may include any access modifier.</span></span> <span data-ttu-id="1f9eb-146">そのことは、クラスを実装するあらゆるもので必要になる共通実装を静的メソッドから与えるときに最も役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-146">This is most useful for static methods to provide common implementations needed by all implementors of a class.</span></span>

<span data-ttu-id="1f9eb-147">列挙型のメンバーは常に `public` となり、アクセス修飾子を適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-147">Enumeration members are always `public`, and no access modifiers can be applied.</span></span>

<span data-ttu-id="1f9eb-148">デリゲートの振る舞いは、クラスおよび構造体と似ています。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-148">Delegates behave like classes and structs.</span></span> <span data-ttu-id="1f9eb-149">既定では、名前空間内に直接宣言されているときには `internal` アクセスが、入れ子にされているときは `private` アクセスが適用されます。</span><span class="sxs-lookup"><span data-stu-id="1f9eb-149">By default, they have `internal` access when declared directly within a namespace, and `private` access when nested.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1f9eb-150">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="1f9eb-150">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="1f9eb-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f9eb-151">See also</span></span>

- [<span data-ttu-id="1f9eb-152">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="1f9eb-152">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1f9eb-153">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="1f9eb-153">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="1f9eb-154">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f9eb-154">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="1f9eb-155">private</span><span class="sxs-lookup"><span data-stu-id="1f9eb-155">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="1f9eb-156">public</span><span class="sxs-lookup"><span data-stu-id="1f9eb-156">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="1f9eb-157">internal</span><span class="sxs-lookup"><span data-stu-id="1f9eb-157">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="1f9eb-158">protected</span><span class="sxs-lookup"><span data-stu-id="1f9eb-158">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="1f9eb-159">protected internal</span><span class="sxs-lookup"><span data-stu-id="1f9eb-159">protected internal</span></span>](../../language-reference/keywords/protected-internal.md)
- [<span data-ttu-id="1f9eb-160">private protected</span><span class="sxs-lookup"><span data-stu-id="1f9eb-160">private protected</span></span>](../../language-reference/keywords/private-protected.md)
- [<span data-ttu-id="1f9eb-161">class</span><span class="sxs-lookup"><span data-stu-id="1f9eb-161">class</span></span>](../../language-reference/keywords/class.md)
- [<span data-ttu-id="1f9eb-162">struct</span><span class="sxs-lookup"><span data-stu-id="1f9eb-162">struct</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="1f9eb-163">interface</span><span class="sxs-lookup"><span data-stu-id="1f9eb-163">interface</span></span>](../../language-reference/keywords/interface.md)
