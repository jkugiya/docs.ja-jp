---
description: "詳細情報: 'Dir' 関数は、'PathName' 引数で最初に呼び出されなければなりません"
title: "'Dir' 関数は、'Pathname' 引数で最初に呼び出されなければなりません。"
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: ee492a269d41e8c9fe1fddbd59210b59fbe8618c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796588"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="91d8c-103">'Dir' 関数は、'Pathname' 引数で最初に呼び出されなければなりません。</span><span class="sxs-lookup"><span data-stu-id="91d8c-103">'Dir' function must first be called with a 'PathName' argument</span></span>

<span data-ttu-id="91d8c-104">`Dir` 関数の最初の呼び出しには、`PathName` 引数は含まれていません。</span><span class="sxs-lookup"><span data-stu-id="91d8c-104">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="91d8c-105">`Dir` の最初の呼び出しには `PathName` を含める必要がありますが、後続の `Dir` の呼び出しには、次の項目を取得するためのパラメーターを含める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="91d8c-105">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="91d8c-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="91d8c-106">To correct this error</span></span>

- <span data-ttu-id="91d8c-107">関数呼び出しに `PathName` 引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="91d8c-107">Supply a `PathName` argument in the function call.</span></span>

## <a name="see-also"></a><span data-ttu-id="91d8c-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="91d8c-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
