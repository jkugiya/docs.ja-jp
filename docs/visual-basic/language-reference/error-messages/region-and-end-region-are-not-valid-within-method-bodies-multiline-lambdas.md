---
description: "詳細情報: BC32025: '#Region' および '#End Region' ステートメントは、メソッド本体や複数行ラムダの内部では有効ではありません"
title: "'#Region' および '#End Region' ステートメントは、メソッド本体や複数行ラムダの内部では有効ではありません。"
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: 0746b9caf677699d6fbbf0c5a7063b1b33d86f3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792025"
---
# <a name="bc32025-region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="6e6ef-103">BC32025: '#Region' および '#End Region' ステートメントは、メソッド本体や複数行ラムダの内部では有効ではありません</span><span class="sxs-lookup"><span data-stu-id="6e6ef-103">BC32025: '#Region' and '#End Region' statements are not valid within method bodies/multiline lambdas</span></span>

<span data-ttu-id="6e6ef-104">`#Region` ブロックは、クラス、モジュール、または名前空間レベルで宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e6ef-104">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="6e6ef-105">折りたたみ可能な領域には 1 つ以上のプロシージャを含めることができますが、プロシージャの内部で開始または終了することはできません。</span><span class="sxs-lookup"><span data-stu-id="6e6ef-105">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>

 <span data-ttu-id="6e6ef-106">**エラー ID:** BC32025</span><span class="sxs-lookup"><span data-stu-id="6e6ef-106">**Error ID:** BC32025</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="6e6ef-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="6e6ef-107">To correct this error</span></span>

1. <span data-ttu-id="6e6ef-108">前の手順が `End Function` または `End Sub` ステートメントで適切に終了していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6e6ef-108">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>

2. <span data-ttu-id="6e6ef-109">`#Region` ディレクティブと `#End Region` ディレクティブが同じコード ブロック内にあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6e6ef-109">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e6ef-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="6e6ef-110">See also</span></span>

- [<span data-ttu-id="6e6ef-111">#Region ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="6e6ef-111">#Region Directive</span></span>](../directives/region-directive.md)
