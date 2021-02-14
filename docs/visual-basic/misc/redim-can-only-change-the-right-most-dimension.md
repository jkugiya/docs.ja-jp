---
description: "詳細情報: ' ReDim ' は右端の次元のみを変更できます"
title: "'ReDim' では最も右にある次元のみ変更できます"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 6816e5b2e9c7c079b78ce53e168f46b337831512
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100454691"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="6e081-103">'ReDim' では最も右にある次元のみ変更できます</span><span class="sxs-lookup"><span data-stu-id="6e081-103">'ReDim' can only change the right-most dimension</span></span>

<span data-ttu-id="6e081-104">`ReDim` ステートメントが `Preserve` キーワードを使用して、最後のディメンションではない配列のディメンションを変更しようとしました。</span><span class="sxs-lookup"><span data-stu-id="6e081-104">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="6e081-105">`Preserve`を使用すると、配列の最後のディメンションについてのみ、サイズを変更できます。</span><span class="sxs-lookup"><span data-stu-id="6e081-105">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="6e081-106">他のすべてのディメンションに対しては、既存の配列と同じサイズを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e081-106">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6e081-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="6e081-107">To correct this error</span></span>  
  
- <span data-ttu-id="6e081-108">`Preserve` キーワードを削除します。</span><span class="sxs-lookup"><span data-stu-id="6e081-108">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e081-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="6e081-109">See also</span></span>

- [<span data-ttu-id="6e081-110">Visual Basic における配列</span><span class="sxs-lookup"><span data-stu-id="6e081-110">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="6e081-111">Visual Basic 内の配列の次元</span><span class="sxs-lookup"><span data-stu-id="6e081-111">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="6e081-112">ReDim ステートメント</span><span class="sxs-lookup"><span data-stu-id="6e081-112">ReDim Statement</span></span>](../language-reference/statements/redim-statement.md)
- [<span data-ttu-id="6e081-113">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="6e081-113">Dim Statement</span></span>](../language-reference/statements/dim-statement.md)
