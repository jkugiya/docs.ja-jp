---
description: '詳細情報: BC30106:インデックス番号がインデックス付き配列の次元を超えています。'
title: インデックス番号がインデックス付き配列の次元を超えています。
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: 35ec1ea106e67022046179412b142cd92712c822
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795612"
---
# <a name="bc30106-number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a><span data-ttu-id="1b350-103">BC30106:インデックス番号がインデックス付き配列の次元を超えています。</span><span class="sxs-lookup"><span data-stu-id="1b350-103">BC30106: Number of indices exceeds the number of dimensions of the indexed array</span></span>

<span data-ttu-id="1b350-104">配列要素にアクセスするために使用されるインデックスの数は、配列のランク、つまり配列に宣言した次元の数とまったく同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b350-104">The number of indices used to access an array element must be exactly the same as the rank of the array, that is, the number of dimensions declared for it.</span></span>

 <span data-ttu-id="1b350-105">**エラー ID:** BC30106</span><span class="sxs-lookup"><span data-stu-id="1b350-105">**Error ID:** BC30106</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="1b350-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="1b350-106">To correct this error</span></span>

- <span data-ttu-id="1b350-107">添字の合計数が配列のランクと同じになるまで、配列参照から添字を削除します。</span><span class="sxs-lookup"><span data-stu-id="1b350-107">Remove subscripts from the array reference until the total number of subscripts equals the rank of the array.</span></span> <span data-ttu-id="1b350-108">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1b350-108">For example:</span></span>

    ```vb
    Dim gameBoard(3, 3) As String

    ' Incorrect code. The array has two dimensions.
    gameBoard(1, 1, 1) = "X"
    gameBoard(2, 1, 1) = "O"

    ' Correct code.
    gameBoard(0, 0) = "X"
    gameBoard(1, 0) = "O"
    ```

## <a name="see-also"></a><span data-ttu-id="1b350-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b350-109">See also</span></span>

- [<span data-ttu-id="1b350-110">配列</span><span class="sxs-lookup"><span data-stu-id="1b350-110">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
