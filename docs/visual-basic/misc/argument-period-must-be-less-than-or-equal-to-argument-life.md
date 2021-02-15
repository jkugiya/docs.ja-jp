---
description: 詳細については、引数 ' Period ' は ' Life ' 引数以下でなければなりません
title: 引数 'Period' は 'Life' 引数以下でなければなりません
ms.date: 07/20/2015
f1_keywords:
- vbrFinancial_PeriodLELife
ms.assetid: dc575d41-b376-4b05-bbbe-6de1e98385f1
ms.openlocfilehash: 451defc2e9015b12bd6b340c3c32782ea4d4774f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100458630"
---
# <a name="argument-period-must-be-less-than-or-equal-to-argument-life"></a><span data-ttu-id="a283d-103">引数 'Period' は 'Life' 引数以下でなければなりません</span><span class="sxs-lookup"><span data-stu-id="a283d-103">Argument 'Period' must be less than or equal to argument 'Life'</span></span>

<span data-ttu-id="a283d-104">資産の減価償却費計算の対象期間を指定する `Period` 引数の値が `Life` 引数の値より大きくなっています。</span><span class="sxs-lookup"><span data-stu-id="a283d-104">The value of the `Period` argument, which specifies the period for which asset depreciation is calculated, is greater than the value of the `Life` argument.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a283d-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="a283d-105">To correct this error</span></span>  
  
- <span data-ttu-id="a283d-106">`Life` 引数と `Period` 引数の両方が同じ単位で指定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a283d-106">Ensure that the `Life` and `Period` arguments are expressed in the same units.</span></span> <span data-ttu-id="a283d-107">たとえば、 `Life` を月単位で指定する場合は、 `Period` も月単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="a283d-107">For example, if `Life` is measured in months, `Period` should be as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a283d-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="a283d-108">See also</span></span>

- [<span data-ttu-id="a283d-109">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="a283d-109">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
