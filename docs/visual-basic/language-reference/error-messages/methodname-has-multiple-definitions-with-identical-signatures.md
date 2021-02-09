---
description: '詳細情報: BC30269: メソッド "<methodname>" には、同じシグネチャを持つ複数の定義が含まれています。'
title: メソッド '<methodname>' には、同じシグネチャを持つ複数の定義が含まれています。
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 7364ee7a308fab96afce268ff0c92cd45717f1bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795808"
---
# <a name="bc30269-methodname-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="802f7-103">BC30269: メソッド "\<methodname>" には、同じシグネチャを持つ複数の定義が含まれています。</span><span class="sxs-lookup"><span data-stu-id="802f7-103">BC30269: '\<methodname>' has multiple definitions with identical signatures</span></span>

<span data-ttu-id="802f7-104">`Function` または `Sub` プロシージャ宣言で、前の宣言と同じプロシージャ名と引数リストを使用しています。</span><span class="sxs-lookup"><span data-stu-id="802f7-104">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="802f7-105">考えられる原因の 1 つは、元のプロシージャをオーバーロードしようとしたことです。</span><span class="sxs-lookup"><span data-stu-id="802f7-105">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="802f7-106">オーバーロードされたプロシージャには、異なる引数リストが必要です。</span><span class="sxs-lookup"><span data-stu-id="802f7-106">Overloaded procedures must have different argument lists.</span></span>

 <span data-ttu-id="802f7-107">**エラー ID:** BC30269</span><span class="sxs-lookup"><span data-stu-id="802f7-107">**Error ID:** BC30269</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="802f7-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="802f7-108">To correct this error</span></span>

- <span data-ttu-id="802f7-109">プロシージャ名または引数リストを変更するか、または重複する宣言を削除します。</span><span class="sxs-lookup"><span data-stu-id="802f7-109">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="802f7-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="802f7-110">See also</span></span>

- [<span data-ttu-id="802f7-111">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="802f7-111">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="802f7-112">プロシージャのオーバーロードに関する注意事項</span><span class="sxs-lookup"><span data-stu-id="802f7-112">Considerations in Overloading Procedures</span></span>](../../programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
