---
title: アクセス制御
description: F# プログラミング言語で、型、メソッド、関数などのプログラミング要素へのアクセスを制御する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: fe204a883a440794fdd033c54d6d8d4fb68e0ce2
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425112"
---
# <a name="access-control"></a><span data-ttu-id="b4fb7-103">アクセス制御</span><span class="sxs-lookup"><span data-stu-id="b4fb7-103">Access Control</span></span>

<span data-ttu-id="b4fb7-104">*アクセス制御* とは、特定のプログラム要素 (型、メソッド、関数など) を使用できるクライアントを宣言することを指します。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-104">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>

## <a name="basics-of-access-control"></a><span data-ttu-id="b4fb7-105">アクセス制御の基礎</span><span class="sxs-lookup"><span data-stu-id="b4fb7-105">Basics of Access Control</span></span>

<span data-ttu-id="b4fb7-106">F# では、アクセス制御指定子 `public`、`internal`、`private` を、モジュール、型、メソッド、値の定義、関数、プロパティ、明示的なフィールドに適用することができます。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-106">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>

- <span data-ttu-id="b4fb7-107">`public` は、そのエンティティにすべての呼び出し元からアクセスできることを示します。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-107">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="b4fb7-108">`internal` は、そのエンティティが同じアセンブリからのみアクセスできることを示します。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-108">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="b4fb7-109">`private` は、そのエンティティが、それを囲む型またはモジュールからのみアクセスできることを示します。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-109">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>

> [!NOTE]
> <span data-ttu-id="b4fb7-110">アクセス指定子 `protected` は F# では使用されませんが、`protected` アクセスをサポートする言語で作成された型を使用している場合は許容されます。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-110">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="b4fb7-111">したがって、保護されたメソッドをオーバーライドすると、そのメソッドはクラスとその子孫内でのみアクセス可能な状態になります。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-111">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="b4fb7-112">一般に、指定子は、エンティティの名前の前に置きます。ただし、`mutable` または `inline` 指定子を使用する場合は、それらをアクセス制御指定子の後に置きます。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-112">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="b4fb7-113">アクセス指定子を使用しない場合、既定値は `public` です。ただし、型の `let` バインドは例外で、型に対して常に `private` になります。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-113">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="b4fb7-114">F# のシグネチャは、F# プログラム要素へのアクセスを制御するための別の機構を提供します。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-114">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="b4fb7-115">アクセス制御にシグネチャは必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-115">Signatures are not required for access control.</span></span> <span data-ttu-id="b4fb7-116">詳細については、「[シグネチャ](signature-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-116">For more information, see [Signatures](signature-files.md).</span></span>

## <a name="rules-for-access-control"></a><span data-ttu-id="b4fb7-117">アクセス制御の規則</span><span class="sxs-lookup"><span data-stu-id="b4fb7-117">Rules for Access Control</span></span>

<span data-ttu-id="b4fb7-118">アクセス制御には、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-118">Access control is subject to the following rules:</span></span>

- <span data-ttu-id="b4fb7-119">継承宣言 (`inherit` を使用してクラスの基底クラスを指定)、インターフェイス宣言 (クラスがインターフェイスを実装することを指定)、抽象メンバーは、それを囲む型と同じアクセス可能性を常に持ちます。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-119">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="b4fb7-120">したがって、これらのコンストラクトではアクセス制御指定子を使用できません。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-120">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="b4fb7-121">判別共用体の個々のケースのアクセス可能性は、判別共用体そのもののアクセス可能性によって決まります。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-121">Accessibility for individual cases in a discriminated union is determined by the accessibility of the discriminated union itself.</span></span> <span data-ttu-id="b4fb7-122">つまり、特定の共用体ケースは、共用体そのもののアクセス可能性より低くはなりません。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-122">That is, a particular union case is no less accessible than the union itself.</span></span>

- <span data-ttu-id="b4fb7-123">レコード型の個々のフィールドのアクセス可能性は、レコードそのもののアクセス可能性によって決まります。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-123">Accessibility for individual fields of a record type is determined by the accessibility of the record itself.</span></span> <span data-ttu-id="b4fb7-124">つまり、特定のレコード ラベルは、レコードそのもののアクセス可能性より低くはなりません。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-124">That is, a particular record label is no less accessible than the record itself.</span></span>

## <a name="example"></a><span data-ttu-id="b4fb7-125">例</span><span class="sxs-lookup"><span data-stu-id="b4fb7-125">Example</span></span>

<span data-ttu-id="b4fb7-126">次のコードは、アクセス制御指定子の使用例を示しています。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-126">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="b4fb7-127">このプロジェクトには、2 つのファイル `Module1.fs` および `Module2.fs` があります。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-127">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="b4fb7-128">各ファイルは暗黙的にモジュールです。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-128">Each file is implicitly a module.</span></span> <span data-ttu-id="b4fb7-129">したがって、`Module1` と `Module2` という 2 つのモジュールがあります。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-129">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="b4fb7-130">`Module1` では、private 型と internal 型が定義されています。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-130">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="b4fb7-131">`Module2` から private 型にはアクセスできませんが、internal 型にはアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-131">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet1.fs)]

<span data-ttu-id="b4fb7-132">次のコードでは、`Module1.fs` で作成された型のアクセス可能性をテストします。</span><span class="sxs-lookup"><span data-stu-id="b4fb7-132">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a><span data-ttu-id="b4fb7-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4fb7-133">See also</span></span>

- [<span data-ttu-id="b4fb7-134">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="b4fb7-134">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="b4fb7-135">シグネチャ</span><span class="sxs-lookup"><span data-stu-id="b4fb7-135">Signatures</span></span>](signature-files.md)
