---
description: '詳細情報: 入れ子にされた型'
title: 入れ子にされた型
ms.date: 10/22/2008
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
ms.openlocfilehash: 07d81827d67e50351f442ec15ca6cb18a63160fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713378"
---
# <a name="nested-types"></a><span data-ttu-id="c95e1-103">入れ子にされた型</span><span class="sxs-lookup"><span data-stu-id="c95e1-103">Nested Types</span></span>

<span data-ttu-id="c95e1-104">入れ子にされた型は、外側の型と呼ばれる別の型のスコープ内で定義された型です。</span><span class="sxs-lookup"><span data-stu-id="c95e1-104">A nested type is a type defined within the scope of another type, which is called the enclosing type.</span></span> <span data-ttu-id="c95e1-105">入れ子にされた型は、それを囲む型のすべてのメンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c95e1-105">A nested type has access to all members of its enclosing type.</span></span> <span data-ttu-id="c95e1-106">たとえば、外側の型で定義されているプライベート フィールドや、囲む型のすべての先祖で定義されている保護されたフィールドにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c95e1-106">For example, it has access to private fields defined in the enclosing type and to protected fields defined in all ascendants of the enclosing type.</span></span>

 <span data-ttu-id="c95e1-107">一般に、入れ子にされた型は控えめに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c95e1-107">In general, nested types should be used sparingly.</span></span> <span data-ttu-id="c95e1-108">直接呼び出すべきではないいくつかの理由があります。</span><span class="sxs-lookup"><span data-stu-id="c95e1-108">There are several reasons for this.</span></span> <span data-ttu-id="c95e1-109">一部の開発者は、この概念について完全には理解していません。</span><span class="sxs-lookup"><span data-stu-id="c95e1-109">Some developers are not fully familiar with the concept.</span></span> <span data-ttu-id="c95e1-110">たとえば、そのような開発者は、入れ子にされた型の変数を宣言する構文で問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c95e1-110">These developers might, for example, have problems with the syntax of declaring variables of nested types.</span></span> <span data-ttu-id="c95e1-111">入れ子にされた型はそれを囲む型と密接に結び付けられているため、汎用的な型には適していません。</span><span class="sxs-lookup"><span data-stu-id="c95e1-111">Nested types are also very tightly coupled with their enclosing types, and as such are not suited to be general-purpose types.</span></span>

 <span data-ttu-id="c95e1-112">入れ子にされた型は、それを囲む型の実装の詳細をモデル化する場合に最適です。</span><span class="sxs-lookup"><span data-stu-id="c95e1-112">Nested types are best suited for modeling implementation details of their enclosing types.</span></span> <span data-ttu-id="c95e1-113">エンド ユーザーは、入れ子にされた型の変数を宣言する必要はあまりなく、入れ子にされた型を明示的にインスタンス化する必要はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="c95e1-113">The end user should rarely have to declare variables of a nested type and almost never should have to explicitly instantiate nested types.</span></span> <span data-ttu-id="c95e1-114">たとえば、コレクションの列挙子は、そのコレクションの入れ子にされた型にすることができます。</span><span class="sxs-lookup"><span data-stu-id="c95e1-114">For example, the enumerator of a collection can be a nested type of that collection.</span></span> <span data-ttu-id="c95e1-115">通常、列挙子はそれを囲む型によってインスタンス化され、多くの言語では foreach ステートメントがサポートされているため、エンド ユーザーが列挙子変数を宣言する必要はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="c95e1-115">Enumerators are usually instantiated by their enclosing type, and because many languages support the foreach statement, enumerator variables rarely have to be declared by the end user.</span></span>

 <span data-ttu-id="c95e1-116">✔️ 入れ子にされた型とその外側の型の関係が、メンバーのアクセシビリティ セマンティクスが望ましいものである場合は、入れ子にされた型を使用ます。</span><span class="sxs-lookup"><span data-stu-id="c95e1-116">✔️ DO use nested types when the relationship between the nested type and its outer type is such that member-accessibility semantics are desirable.</span></span>

 <span data-ttu-id="c95e1-117">❌ 入れ子にされたパブリック型を論理グループ化構成体として使用しないでください。この場合は名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="c95e1-117">❌ DO NOT use public nested types as a logical grouping construct; use namespaces for this.</span></span>

 <span data-ttu-id="c95e1-118">❌ 入れ子にされた型をパブリックに公開しないでください。</span><span class="sxs-lookup"><span data-stu-id="c95e1-118">❌ AVOID publicly exposed nested types.</span></span> <span data-ttu-id="c95e1-119">唯一の例外は、サブクラス化のようなまれなシナリオや、その他の高度なカスタマイズ シナリオで、入れ子にされた型の変数を宣言する必要がある場合だけです。</span><span class="sxs-lookup"><span data-stu-id="c95e1-119">The only exception to this is if variables of the nested type need to be declared only in rare scenarios such as subclassing or other advanced customization scenarios.</span></span>

 <span data-ttu-id="c95e1-120">❌ 含んでいる型の外側で型が参照される可能性が高い場合は、入れ子にされた型を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="c95e1-120">❌ DO NOT use nested types if the type is likely to be referenced outside of the containing type.</span></span>

 <span data-ttu-id="c95e1-121">たとえば、クラスで定義されたメソッドに渡される列挙型を、入れ子にされた型としてクラスで定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="c95e1-121">For example, an enum passed to a method defined on a class should not be defined as a nested type in the class.</span></span>

 <span data-ttu-id="c95e1-122">❌ クライアントのコードでインスタンス化する必要がある場合は、入れ子にされた型を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="c95e1-122">❌ DO NOT use nested types if they need to be instantiated by client code.</span></span>  <span data-ttu-id="c95e1-123">型にパブリック コンストラクターがある場合は、入れ子にしてはならない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c95e1-123">If a type has a public constructor, it should probably not be nested.</span></span>

 <span data-ttu-id="c95e1-124">型をインスタンス化できる場合、フレームワーク内にその型独自の場所があることを示している可能性があり (外側の型を使用しないで作成、操作、破棄できます)、入れ子にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c95e1-124">If a type can be instantiated, that seems to indicate the type has a place in the framework on its own (you can create it, work with it, and destroy it without ever using the outer type), and thus should not be nested.</span></span> <span data-ttu-id="c95e1-125">外側の型への何らかの関係なしに、外側の型の外部で内側の型を広く再利用することはできません。</span><span class="sxs-lookup"><span data-stu-id="c95e1-125">Inner types should not be widely reused outside of the outer type without any relationship whatsoever to the outer type.</span></span>

 <span data-ttu-id="c95e1-126">❌ インターフェイスのメンバーとして、入れ子にされた型を定義しないでください。</span><span class="sxs-lookup"><span data-stu-id="c95e1-126">❌ DO NOT define a nested type as a member of an interface.</span></span> <span data-ttu-id="c95e1-127">多くの言語では、そのようなコンストラクトはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c95e1-127">Many languages do not support such a construct.</span></span>

 <span data-ttu-id="c95e1-128">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="c95e1-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="c95e1-129">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="c95e1-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="c95e1-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="c95e1-130">See also</span></span>

- [<span data-ttu-id="c95e1-131">型デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="c95e1-131">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="c95e1-132">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="c95e1-132">Framework Design Guidelines</span></span>](index.md)
