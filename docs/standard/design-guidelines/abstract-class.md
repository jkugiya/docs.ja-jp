---
description: '詳細情報: 抽象クラスのデザイン'
title: 抽象クラスのデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
ms.openlocfilehash: 5b1cd833bf43e5bf5731176243809393187e84d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642462"
---
# <a name="abstract-class-design"></a><span data-ttu-id="95937-103">抽象クラスのデザイン</span><span class="sxs-lookup"><span data-stu-id="95937-103">Abstract Class Design</span></span>

<span data-ttu-id="95937-104">❌ 抽象型では、パブリックの、または保護された内部コンストラクターを定義しないでください。</span><span class="sxs-lookup"><span data-stu-id="95937-104">❌ DO NOT define public or protected internal constructors in abstract types.</span></span>

 <span data-ttu-id="95937-105">ユーザーがその型のインスタンスを作成する必要がある場合にのみ、コンストラクターをパブリックにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="95937-105">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="95937-106">抽象型のインスタンスは作成できないため、パブリック コンストラクターのある抽象型は不適切な設計になり、ユーザーの誤解を招きます。</span><span class="sxs-lookup"><span data-stu-id="95937-106">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>

 <span data-ttu-id="95937-107">✔️ 抽象クラスでは、保護されたコンストラクターまたは内部コンストラクターを定義します。</span><span class="sxs-lookup"><span data-stu-id="95937-107">✔️ DO define a protected or an internal constructor in abstract classes.</span></span>

 <span data-ttu-id="95937-108">保護されたコンストラクターの方が一般的であり、サブタイプの作成時に基底クラスによる独自の初期化の実行を許可するだけです。</span><span class="sxs-lookup"><span data-stu-id="95937-108">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>

 <span data-ttu-id="95937-109">内部コンストラクターを使用すると、抽象クラスの具象実装を、クラスを定義するアセンブリに制限できます。</span><span class="sxs-lookup"><span data-stu-id="95937-109">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>

 <span data-ttu-id="95937-110">✔️ 出荷する各抽象クラスから継承される具象型を少なくとも 1 つ提供します。</span><span class="sxs-lookup"><span data-stu-id="95937-110">✔️ DO provide at least one concrete type that inherits from each abstract class that you ship.</span></span>

 <span data-ttu-id="95937-111">これにより、抽象クラスの設計を検証できます。</span><span class="sxs-lookup"><span data-stu-id="95937-111">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="95937-112">たとえば、<xref:System.IO.FileStream?displayProperty=nameWithType> は <xref:System.IO.Stream?displayProperty=nameWithType> 抽象クラスの実装です。</span><span class="sxs-lookup"><span data-stu-id="95937-112">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>

 <span data-ttu-id="95937-113">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="95937-113">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="95937-114">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="95937-114">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="95937-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="95937-115">See also</span></span>

- [<span data-ttu-id="95937-116">型デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="95937-116">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="95937-117">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="95937-117">Framework Design Guidelines</span></span>](index.md)
