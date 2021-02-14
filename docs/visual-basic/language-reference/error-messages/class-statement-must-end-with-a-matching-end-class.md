---
description: "詳細情報: BC30481:'Class' ステートメントの終わりには、対応する 'End Class' を指定しなければなりません"
title: "'Class' ステートメントの終わりには、対応する 'End Class' を指定しなければなりません。"
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: b0d2d89e9e3549b24f9c923e271b15b3b02026b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796782"
---
# <a name="bc30481-class-statement-must-end-with-a-matching-end-class"></a><span data-ttu-id="d8410-103">BC30481:'Class' ステートメントの終わりには、対応する 'End Class' を指定しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="d8410-103">BC30481: 'Class' statement must end with a matching 'End Class'</span></span>

<span data-ttu-id="d8410-104">`Class` は `Class` ブロックを開始するために使用します。ブロックの先頭にのみ指定でき、対応する`End Class` ステートメントでブロックを終えます。</span><span class="sxs-lookup"><span data-stu-id="d8410-104">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="d8410-105">`Class` ステートメントが重複しているか、`Class` ブロックの最後に `End Class` が使用されませんでした。</span><span class="sxs-lookup"><span data-stu-id="d8410-105">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>

 <span data-ttu-id="d8410-106">**エラー ID:** BC30481</span><span class="sxs-lookup"><span data-stu-id="d8410-106">**Error ID:** BC30481</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d8410-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="d8410-107">To correct this error</span></span>

- <span data-ttu-id="d8410-108">不要な `Class` ステートメントを見つけて削除します。</span><span class="sxs-lookup"><span data-stu-id="d8410-108">Locate and remove the unnecessary `Class` statement.</span></span>

- <span data-ttu-id="d8410-109">一致する `End Class` で `Class` ブロックを終了します。</span><span class="sxs-lookup"><span data-stu-id="d8410-109">Conclude the `Class` block with a matching `End Class`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8410-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8410-110">See also</span></span>

- [<span data-ttu-id="d8410-111">End \<keyword> ステートメント</span><span class="sxs-lookup"><span data-stu-id="d8410-111">End \<keyword> Statement</span></span>](../statements/end-keyword-statement.md)
- [<span data-ttu-id="d8410-112">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="d8410-112">Class Statement</span></span>](../statements/class-statement.md)
