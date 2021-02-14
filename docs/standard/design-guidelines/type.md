---
description: '詳細情報: 型のデザインのガイドライン'
title: 型のデザインのガイドライン
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: d2c193d41dda118558cc5e7541f7e2dfbaf1a369
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641838"
---
# <a name="type-design-guidelines"></a><span data-ttu-id="3847b-103">型のデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="3847b-103">Type Design Guidelines</span></span>

<span data-ttu-id="3847b-104">CLR の観点から見ると、型には参照型と値型という 2 つのカテゴリしかありませんが、フレームワークの設計について説明するために、ここでは、それぞれに固有の設計規則がある多数の論理グループに型を分割しています。</span><span class="sxs-lookup"><span data-stu-id="3847b-104">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>

 <span data-ttu-id="3847b-105">クラスは、参照型の一般的なケースです。</span><span class="sxs-lookup"><span data-stu-id="3847b-105">Classes are the general case of reference types.</span></span> <span data-ttu-id="3847b-106">それらは、大半のフレームワークで型の大部分を構成します。</span><span class="sxs-lookup"><span data-stu-id="3847b-106">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="3847b-107">クラスは、それらがサポートしているオブジェクト指向の充実した機能セットと一般的な適用性によって、広く使用されています。</span><span class="sxs-lookup"><span data-stu-id="3847b-107">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="3847b-108">基底クラスと抽象クラスは、拡張性に関連する特殊な論理グループです。</span><span class="sxs-lookup"><span data-stu-id="3847b-108">Base classes and abstract classes are special logical groups related to extensibility.</span></span>

 <span data-ttu-id="3847b-109">インターフェイスは、参照型と値型の両方によって実装できる型です。</span><span class="sxs-lookup"><span data-stu-id="3847b-109">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="3847b-110">このため、参照型と値型の多様な形態の階層のルートとして機能できます。</span><span class="sxs-lookup"><span data-stu-id="3847b-110">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="3847b-111">さらに、インターフェイスを使用して、複数の継承をシミュレートできます。これは CLR ではネイティブにサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="3847b-111">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>

 <span data-ttu-id="3847b-112">構造体は値型の一般的なケースであり、言語プリミティブと同じように、小さく単純な型用に予約してください。</span><span class="sxs-lookup"><span data-stu-id="3847b-112">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>

 <span data-ttu-id="3847b-113">列挙型は、値型の特殊なケースであり、曜日やコンソールの色などの短い値のセットを定義するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="3847b-113">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>

 <span data-ttu-id="3847b-114">静的クラスは、静的メンバーのためのコンテナー用の型です。</span><span class="sxs-lookup"><span data-stu-id="3847b-114">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="3847b-115">通常は、他の操作へのショートカットを提供するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="3847b-115">They are commonly used to provide shortcuts to other operations.</span></span>

 <span data-ttu-id="3847b-116">デリゲート、例外、属性、配列、およびコレクションは、すべてが特定の用途のための参照型の特殊なケースであり、その設計と使用に関するガイドラインについては、本書の別の場所で説明します。</span><span class="sxs-lookup"><span data-stu-id="3847b-116">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>

 <span data-ttu-id="3847b-117">✔️ 各型は、関連性のない機能のランダムなコレクションではなく、必ず関連するメンバーの適切に定義されたセットであるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="3847b-117">✔️ DO ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="3847b-118">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3847b-118">In This Section</span></span>

 <span data-ttu-id="3847b-119">[クラスまたは構造体の選択](choosing-between-class-and-struct.md) [抽象クラスのデザイン](abstract-class.md) [静的クラスのデザイン](static-class.md) [インターフェイスのデザイン](interface.md) [構造体のデザイン](struct.md) [列挙型のデザイン](enum.md) [入れ子にされた型](nested-types.md) *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="3847b-119">[Choosing Between Class and Struct](choosing-between-class-and-struct.md) [Abstract Class Design](abstract-class.md) [Static Class Design](static-class.md) [Interface Design](interface.md) [Struct Design](struct.md) [Enum Design](enum.md) [Nested Types](nested-types.md) *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="3847b-120">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="3847b-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="3847b-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="3847b-121">See also</span></span>

- [<span data-ttu-id="3847b-122">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="3847b-122">Framework Design Guidelines</span></span>](index.md)
