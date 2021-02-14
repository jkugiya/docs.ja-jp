---
description: "詳細情報: ' ReDim ' で次元数を変更することはできません"
title: "'ReDim' で次元数を変更することはできません"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: 4552dd6b1cce54813b57e5b8c76a3580b81b8def
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100454639"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="8ef41-103">'ReDim' で次元数を変更することはできません</span><span class="sxs-lookup"><span data-stu-id="8ef41-103">'ReDim' cannot change the number of dimensions</span></span>

<span data-ttu-id="8ef41-104">`ReDim` ステートメントを使用して、配列のランク (次元の数) を変更する操作が行われました。</span><span class="sxs-lookup"><span data-stu-id="8ef41-104">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="8ef41-105">`ReDim` は既に宣言された配列の 1 つ以上の次元のサイズを変更するために使用できますが、配列のランクを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="8ef41-105">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8ef41-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="8ef41-106">To correct this error</span></span>  
  
- <span data-ttu-id="8ef41-107">次元のサイズではなく、配列のランクを変更しようとしていることを確認します。可能な場合は、 `Dim` を使用して、希望のランクを持つ配列を新規に宣言します。</span><span class="sxs-lookup"><span data-stu-id="8ef41-107">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef41-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ef41-108">See also</span></span>

- [<span data-ttu-id="8ef41-109">Visual Basic における配列</span><span class="sxs-lookup"><span data-stu-id="8ef41-109">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="8ef41-110">Visual Basic 内の配列の次元</span><span class="sxs-lookup"><span data-stu-id="8ef41-110">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="8ef41-111">ReDim ステートメント</span><span class="sxs-lookup"><span data-stu-id="8ef41-111">ReDim Statement</span></span>](../language-reference/statements/redim-statement.md)
- [<span data-ttu-id="8ef41-112">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="8ef41-112">Dim Statement</span></span>](../language-reference/statements/dim-statement.md)
