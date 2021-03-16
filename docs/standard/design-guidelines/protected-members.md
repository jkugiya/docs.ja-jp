---
description: '詳細情報: プロテクト メンバー'
title: プロテクト メンバー
ms.date: 10/22/2008
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
ms.openlocfilehash: 5860828a5a469c77fbee001d01460a488fda4edf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731761"
---
# <a name="protected-members"></a><span data-ttu-id="f04d3-103">プロテクト メンバー</span><span class="sxs-lookup"><span data-stu-id="f04d3-103">Protected Members</span></span>

<span data-ttu-id="f04d3-104">プロテクト メンバー自体では拡張機能は提供されませんが、サブクラス化による拡張性をいっそう強力にすることができます。</span><span class="sxs-lookup"><span data-stu-id="f04d3-104">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="f04d3-105">それらを使用すると、メインのパブリック インターフェイスを不必要に複雑にすることなく、高度なカスタマイズ オプションを公開できます。</span><span class="sxs-lookup"><span data-stu-id="f04d3-105">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>

 <span data-ttu-id="f04d3-106">フレームワーク デザイナーは、"プロテクト" という名前からセキュリティに関して誤った認識を持つ可能性があるため、プロテクト メンバーには注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f04d3-106">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="f04d3-107">だれでも、アンシールド クラスをサブクラス化し、プロテクト メンバーにアクセスできるので、パブリック メンバーに使用されるものと同じ防御的なコーディング方法がすべてプロテクト メンバーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="f04d3-107">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>

 <span data-ttu-id="f04d3-108">✔️ 高度なカスタマイズには、プロテクト メンバーの使用を検討します。</span><span class="sxs-lookup"><span data-stu-id="f04d3-108">✔️ CONSIDER using protected members for advanced customization.</span></span>

 <span data-ttu-id="f04d3-109">✔️ セキュリティ、ドキュメント、互換性分析の目的では、アンシールド クラスのプロテクト メンバーをパブリックとして扱います。</span><span class="sxs-lookup"><span data-stu-id="f04d3-109">✔️ DO treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>

 <span data-ttu-id="f04d3-110">だれでもクラスを継承し、プロテクト メンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f04d3-110">Anyone can inherit from a class and access the protected members.</span></span>

 <span data-ttu-id="f04d3-111">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="f04d3-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="f04d3-112">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="f04d3-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="f04d3-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f04d3-113">See also</span></span>

- [<span data-ttu-id="f04d3-114">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="f04d3-114">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="f04d3-115">機能拡張のデザイン</span><span class="sxs-lookup"><span data-stu-id="f04d3-115">Designing for Extensibility</span></span>](designing-for-extensibility.md)
