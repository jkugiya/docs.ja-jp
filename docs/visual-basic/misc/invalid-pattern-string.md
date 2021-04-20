---
description: '詳細情報: 無効なパターン文字列'
title: 無効なパターン文字列
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 4fbf16dd43ac4ae44e1a99d85caae4a7baf99109
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462062"
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="b95d2-103">無効なパターン文字列</span><span class="sxs-lookup"><span data-stu-id="b95d2-103">Invalid pattern string</span></span>

<span data-ttu-id="b95d2-104">検索の `Like` 演算で指定されているパターン文字列が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="b95d2-104">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b95d2-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="b95d2-105">To correct this error</span></span>  
  
1. <span data-ttu-id="b95d2-106">リスト式に使用できる文字を確認します。</span><span class="sxs-lookup"><span data-stu-id="b95d2-106">Review the valid characters for list expressions.</span></span>  
  
2. <span data-ttu-id="b95d2-107">パターン範囲の指定で、 `[a-z]`のように、範囲の開始文字が終了文字より小さいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="b95d2-107">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3. <span data-ttu-id="b95d2-108">パターン範囲の指定で、 `[a--z]`のように、複数のハイフンが続けて指定されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="b95d2-108">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4. <span data-ttu-id="b95d2-109">パターン範囲を右角かっこで終了します。</span><span class="sxs-lookup"><span data-stu-id="b95d2-109">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b95d2-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="b95d2-110">See also</span></span>

- [<span data-ttu-id="b95d2-111">Like 演算子</span><span class="sxs-lookup"><span data-stu-id="b95d2-111">Like Operator</span></span>](../language-reference/operators/like-operator.md)
