---
description: '詳細情報: BC32005:If ステートメント行の外側でステートメント ブロックを終了することはできません。'
title: If ステートメント行の外側でステートメント ブロックを終了することはできません。
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: afe856b2c2ea3fa1db029d35c5b876f5d67da411
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731141"
---
# <a name="bc32005-statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="41e6c-103">BC32005:If ステートメント行の外側でステートメント ブロックを終了することはできません。</span><span class="sxs-lookup"><span data-stu-id="41e6c-103">BC32005: Statement cannot end a block outside of a line 'If' statement</span></span>

<span data-ttu-id="41e6c-104">単一行の `If` ステートメントにコロン (:) で区切られた複数のステートメントが含まれていて、そのうちの 1 つが、単一行の `If` の外側にある制御ブロックの `End` ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="41e6c-104">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="41e6c-105">単一行の `If` ステートメントで、`End If` ステートメントが使用されません。</span><span class="sxs-lookup"><span data-stu-id="41e6c-105">Single-line `If` statements do not use the `End If` statement.</span></span>

 <span data-ttu-id="41e6c-106">**エラー ID:** BC32005</span><span class="sxs-lookup"><span data-stu-id="41e6c-106">**Error ID:** BC32005</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="41e6c-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="41e6c-107">To correct this error</span></span>

- <span data-ttu-id="41e6c-108">単一行の `If` ステートメントを、`End If` ステートメントが含まれている制御ブロックの外側に移動します。</span><span class="sxs-lookup"><span data-stu-id="41e6c-108">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="41e6c-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="41e6c-109">See also</span></span>

- [<span data-ttu-id="41e6c-110">If...Then...Else ステートメント</span><span class="sxs-lookup"><span data-stu-id="41e6c-110">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
