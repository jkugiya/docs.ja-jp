---
description: '詳細情報: 静的クラスのデザイン'
title: 静的クラスのデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
ms.openlocfilehash: 16db470ab0975a5545617c9c5471d6ac157e688b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782469"
---
# <a name="static-class-design"></a><span data-ttu-id="d6d3f-103">静的クラスのデザイン</span><span class="sxs-lookup"><span data-stu-id="d6d3f-103">Static Class Design</span></span>

<span data-ttu-id="d6d3f-104">静的クラスは、静的メンバーのみが含まれるクラスとして定義されます (もちろん、<xref:System.Object?displayProperty=nameWithType> から継承されるインスタンス メンバーと、プライベート コンストラクターがある場合はそれを除きます)。</span><span class="sxs-lookup"><span data-stu-id="d6d3f-104">A static class is defined as a class that contains only static members (of course besides the instance members inherited from <xref:System.Object?displayProperty=nameWithType> and possibly a private constructor).</span></span> <span data-ttu-id="d6d3f-105">一部の言語には、静的クラスのサポートが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="d6d3f-105">Some languages provide built-in support for static classes.</span></span> <span data-ttu-id="d6d3f-106">C# 2.0 以降では、クラスが静的として宣言されている場合、それはシールドで抽象であり、インスタンス メンバーをオーバーライドまたは宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="d6d3f-106">In C# 2.0 and later, when a class is declared to be static, it is sealed, abstract, and no instance members can be overridden or declared.</span></span>

 <span data-ttu-id="d6d3f-107">静的クラスは、純粋なオブジェクト指向設計と単純さの間の妥協を表しています。</span><span class="sxs-lookup"><span data-stu-id="d6d3f-107">Static classes are a compromise between pure object-oriented design and simplicity.</span></span> <span data-ttu-id="d6d3f-108">一般に、それらは、他の操作 (<xref:System.IO.File?displayProperty=nameWithType> など)、拡張メソッドのホルダー、または完全なオブジェクト指向ラッパーが保証されていない機能 (<xref:System.Environment?displayProperty=nameWithType> など) へのショートカットを提供するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d6d3f-108">They are commonly used to provide shortcuts to other operations (such as <xref:System.IO.File?displayProperty=nameWithType>), holders of extension methods, or functionality for which a full object-oriented wrapper is unwarranted (such as <xref:System.Environment?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="d6d3f-109">✔️ 静的クラスは控えめに使用してください。</span><span class="sxs-lookup"><span data-stu-id="d6d3f-109">✔️ DO use static classes sparingly.</span></span>

 <span data-ttu-id="d6d3f-110">静的クラスは、フレームワークのオブジェクト指向コアのサポート クラスとしてのみ使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6d3f-110">Static classes should be used only as supporting classes for the object-oriented core of the framework.</span></span>

 <span data-ttu-id="d6d3f-111">❌ 静的クラスを雑多なもののバケットとして扱わないでください。</span><span class="sxs-lookup"><span data-stu-id="d6d3f-111">❌ DO NOT treat static classes as a miscellaneous bucket.</span></span>

 <span data-ttu-id="d6d3f-112">❌ 静的クラスのインスタンス メンバーを宣言またはオーバーライドしないでください。</span><span class="sxs-lookup"><span data-stu-id="d6d3f-112">❌ DO NOT declare or override instance members in static classes.</span></span>

 <span data-ttu-id="d6d3f-113">✔️ プログラミング言語に静的クラスの組み込みサポートがない場合は、静的クラスをシールドの抽象型として宣言し、プライベート インスタンス コンストラクターを追加します。</span><span class="sxs-lookup"><span data-stu-id="d6d3f-113">✔️ DO declare static classes as sealed, abstract, and add a private instance constructor if your programming language does not have built-in support for static classes.</span></span>

 <span data-ttu-id="d6d3f-114">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="d6d3f-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="d6d3f-115">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="d6d3f-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="d6d3f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6d3f-116">See also</span></span>

- [<span data-ttu-id="d6d3f-117">型デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="d6d3f-117">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="d6d3f-118">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="d6d3f-118">Framework Design Guidelines</span></span>](index.md)
