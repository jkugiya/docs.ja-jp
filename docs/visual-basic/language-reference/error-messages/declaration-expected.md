---
description: '詳細情報: BC30188:宣言が必要です。'
title: 宣言が必要です。
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: b86c182fb9dc8ab7d624833136f0e87b072aed92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796666"
---
# <a name="bc30188-declaration-expected"></a><span data-ttu-id="7b212-103">BC30188:宣言が必要です。</span><span class="sxs-lookup"><span data-stu-id="7b212-103">BC30188: Declaration expected</span></span>

<span data-ttu-id="7b212-104">代入ステートメントやループ ステートメントなどの非宣言ステートメントが、プロシージャの外側に記述されています。</span><span class="sxs-lookup"><span data-stu-id="7b212-104">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="7b212-105">プロシージャの外側で許可されるのは宣言のみです。</span><span class="sxs-lookup"><span data-stu-id="7b212-105">Only declarations are allowed outside procedures.</span></span>

 <span data-ttu-id="7b212-106">または、プログラミング要素が、`Dim` や `Const` などの宣言キーワードを使用せずに宣言されています。</span><span class="sxs-lookup"><span data-stu-id="7b212-106">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>

 <span data-ttu-id="7b212-107">**エラー ID:** BC30188</span><span class="sxs-lookup"><span data-stu-id="7b212-107">**Error ID:** BC30188</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="7b212-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="7b212-108">To correct this error</span></span>

- <span data-ttu-id="7b212-109">非宣言ステートメントをプロシージャの本体に移動します。</span><span class="sxs-lookup"><span data-stu-id="7b212-109">Move the nondeclarative statement to the body of a procedure.</span></span>

- <span data-ttu-id="7b212-110">適切な宣言キーワードを使用して、宣言を開始します。</span><span class="sxs-lookup"><span data-stu-id="7b212-110">Begin the declaration with an appropriate declaration keyword.</span></span>

- <span data-ttu-id="7b212-111">宣言キーワードのスペルが間違っていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="7b212-111">Ensure that a declaration keyword is not misspelled.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b212-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b212-112">See also</span></span>

- [<span data-ttu-id="7b212-113">手順</span><span class="sxs-lookup"><span data-stu-id="7b212-113">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="7b212-114">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="7b212-114">Dim Statement</span></span>](../statements/dim-statement.md)
