---
description: '詳細情報: 例外のデザインのガイドライン'
title: 例外のデザインのガイドライン
ms.date: 10/22/2008
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
ms.openlocfilehash: 0845f06dca0ee83d7315c3b0b4b6ae090b24a875
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642111"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="34ab5-103">例外のデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="34ab5-103">Design Guidelines for Exceptions</span></span>

<span data-ttu-id="34ab5-104">例外処理には、戻り値に基づくエラー報告よりも多くの利点があります。</span><span class="sxs-lookup"><span data-stu-id="34ab5-104">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="34ab5-105">優れたフレームワーク設計により、アプリケーション開発者は例外の利点を実感できます。</span><span class="sxs-lookup"><span data-stu-id="34ab5-105">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="34ab5-106">このセクションでは、例外の利点について説明し、それらを効果的に使用するためのガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="34ab5-106">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="34ab5-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="34ab5-107">In This Section</span></span>  

 [<span data-ttu-id="34ab5-108">例外のスロー</span><span class="sxs-lookup"><span data-stu-id="34ab5-108">Exception Throwing</span></span>](exception-throwing.md)  
 [<span data-ttu-id="34ab5-109">標準例外型の使用</span><span class="sxs-lookup"><span data-stu-id="34ab5-109">Using Standard Exception Types</span></span>](using-standard-exception-types.md)  
 [<span data-ttu-id="34ab5-110">例外とパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="34ab5-110">Exceptions and Performance</span></span>](exceptions-and-performance.md)  
 <span data-ttu-id="34ab5-111">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="34ab5-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="34ab5-112">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="34ab5-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34ab5-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="34ab5-113">See also</span></span>

- [<span data-ttu-id="34ab5-114">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="34ab5-114">Framework Design Guidelines</span></span>](index.md)
