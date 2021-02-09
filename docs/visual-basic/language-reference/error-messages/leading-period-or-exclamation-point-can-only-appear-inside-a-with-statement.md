---
description: "詳細情報: BC30157:先頭の '.' または '!' は、'With' ステートメント内でのみ使用できます。"
title: 先頭の '.' または '!' は、'With' ステートメント内でのみ使用できます。
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: e0325ac3c54046718d71df37edaac1edaf12f43e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795899"
---
# <a name="bc30157-leading--or--can-only-appear-inside-a-with-statement"></a><span data-ttu-id="0c29d-103">BC30157:先頭の '.' または '!' は、'With' ステートメント内でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="0c29d-103">BC30157: Leading '.' or '!' can only appear inside a 'With' statement</span></span>

<span data-ttu-id="0c29d-104">`With` ブロック内にないピリオド (.) または感嘆符 (!) が、左側に式がない状態で指定されています。</span><span class="sxs-lookup"><span data-stu-id="0c29d-104">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="0c29d-105">メンバー アクセス (`.`) とディクショナリ メンバー アクセス (`!`) には、メンバーが含まれている要素を指定した式が必要になります。</span><span class="sxs-lookup"><span data-stu-id="0c29d-105">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="0c29d-106">これは、アクセサーのすぐ左側、またはメンバー アクセスを含む `With` ブロックのターゲットとして指定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c29d-106">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>

 <span data-ttu-id="0c29d-107">**エラー ID:** BC30157</span><span class="sxs-lookup"><span data-stu-id="0c29d-107">**Error ID:** BC30157</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="0c29d-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="0c29d-108">To correct this error</span></span>

1. <span data-ttu-id="0c29d-109">`With` ブロックが正しく書式設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0c29d-109">Ensure that the `With` block is correctly formatted.</span></span>

2. <span data-ttu-id="0c29d-110">`With` ブロックがない場合は、アクセサーの左側に、メンバーを含む定義済みの要素に評価される式を追加します。</span><span class="sxs-lookup"><span data-stu-id="0c29d-110">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c29d-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c29d-111">See also</span></span>

- [<span data-ttu-id="0c29d-112">コード内の特殊文字</span><span class="sxs-lookup"><span data-stu-id="0c29d-112">Special Characters in Code</span></span>](../../programming-guide/program-structure/special-characters-in-code.md)
- [<span data-ttu-id="0c29d-113">With...End With ステートメント</span><span class="sxs-lookup"><span data-stu-id="0c29d-113">With...End With Statement</span></span>](../statements/with-end-with-statement.md)
