---
description: '詳細情報: BC30024:メソッドや複数行のラムダの内部では有効でないステートメントです。'
title: メソッドや複数行のラムダの内部では有効でないステートメントです。
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: c70e5563ab8c161966cd9790ae1f192fa5d50b17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731176"
---
# <a name="bc30024-statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="bc602-103">BC30024:メソッドや複数行のラムダの内部では有効でないステートメントです。</span><span class="sxs-lookup"><span data-stu-id="bc602-103">BC30024: Statement is not valid inside a method/multiline lambda</span></span>

<span data-ttu-id="bc602-104">ステートメントは、`Sub`、`Function`、プロパティ `Get`、またはプロパティ `Set` プロシージャ内で無効です。</span><span class="sxs-lookup"><span data-stu-id="bc602-104">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="bc602-105">一部のステートメントは、モジュール レベルまたはクラス レベルで配置できます。</span><span class="sxs-lookup"><span data-stu-id="bc602-105">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="bc602-106">`Option Strict` などの他のものは、名前空間レベルで、他のすべての宣言の前に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc602-106">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>

 <span data-ttu-id="bc602-107">**エラー ID:** BC30024</span><span class="sxs-lookup"><span data-stu-id="bc602-107">**Error ID:** BC30024</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="bc602-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="bc602-108">To correct this error</span></span>

- <span data-ttu-id="bc602-109">プロシージャからステートメントを削除します。</span><span class="sxs-lookup"><span data-stu-id="bc602-109">Remove the statement from the procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc602-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc602-110">See also</span></span>

- [<span data-ttu-id="bc602-111">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="bc602-111">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="bc602-112">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="bc602-112">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="bc602-113">Get ステートメント</span><span class="sxs-lookup"><span data-stu-id="bc602-113">Get Statement</span></span>](../statements/get-statement.md)
- [<span data-ttu-id="bc602-114">Set ステートメント</span><span class="sxs-lookup"><span data-stu-id="bc602-114">Set Statement</span></span>](../statements/set-statement.md)
