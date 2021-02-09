---
description: '詳細情報: オーバーフローしました。(Visual Basic ランタイム エラー)'
title: オーバーフローしました。(Visual Basic ランタイム エラー)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: a01a8916e09f9278dbdf6d594c5ef84d63b04c51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795457"
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="2f9de-103">オーバーフローしました。(Visual Basic ランタイム エラー)</span><span class="sxs-lookup"><span data-stu-id="2f9de-103">Overflow (Visual Basic Run-Time Error)</span></span>

<span data-ttu-id="2f9de-104">代入の対象の制限を超える代入を試みると、オーバーフローが発生します。</span><span class="sxs-lookup"><span data-stu-id="2f9de-104">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2f9de-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="2f9de-105">To correct this error</span></span>  
  
1. <span data-ttu-id="2f9de-106">代入、計算、およびデータ型の変換の結果が、その型の値に対して許可されている変数の範囲内で表すには大きすぎないことを確認し、必要に応じて、より大きな値の範囲を保持できる型の変数に値を代入します。</span><span class="sxs-lookup"><span data-stu-id="2f9de-106">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2. <span data-ttu-id="2f9de-107">プロパティへの代入が、代入先のプロパティの範囲に適合することを確認します。</span><span class="sxs-lookup"><span data-stu-id="2f9de-107">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3. <span data-ttu-id="2f9de-108">整数に強制的に変換される計算で使用される数値に、整数よりも大きな結果がないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="2f9de-108">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f9de-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f9de-109">See also</span></span>

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [<span data-ttu-id="2f9de-110">データの種類</span><span class="sxs-lookup"><span data-stu-id="2f9de-110">Data Types</span></span>](../data-types/index.md)
- [<span data-ttu-id="2f9de-111">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="2f9de-111">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
