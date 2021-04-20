---
description: '詳細情報: レコード番号が正しくありません'
title: レコード番号が正しくありません
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: a250419c131f75381426705d52563732322631cb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460996"
---
# <a name="bad-record-number"></a><span data-ttu-id="9c946-103">レコード番号が正しくありません</span><span class="sxs-lookup"><span data-stu-id="9c946-103">Bad record number</span></span>

<span data-ttu-id="9c946-104">`a FileGet`、 `FilePut`、 `FileGetObject`、または `FilePutObject` ステートメント内のレコード番号が 0 以下です。</span><span class="sxs-lookup"><span data-stu-id="9c946-104">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9c946-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="9c946-105">To correct this error</span></span>  
  
1. <span data-ttu-id="9c946-106">レコード番号の生成で使用される計算を確認します。</span><span class="sxs-lookup"><span data-stu-id="9c946-106">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="9c946-107">レコード番号が含まれている変数、またはレコード番号の計算で使用される変数のスペルを確認します。</span><span class="sxs-lookup"><span data-stu-id="9c946-107">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="9c946-108">モジュールで `Option Explicit On` を使用しない限り、スペル ミスの変数名は暗黙的に宣言され、0 に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="9c946-108">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c946-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c946-109">See also</span></span>

- [<span data-ttu-id="9c946-110">Option Explicit ステートメント</span><span class="sxs-lookup"><span data-stu-id="9c946-110">Option Explicit Statement</span></span>](../language-reference/statements/option-explicit-statement.md)
