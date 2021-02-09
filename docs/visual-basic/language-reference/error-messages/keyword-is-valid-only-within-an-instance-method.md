---
description: "詳細情報: BC30043: '<keyword>' はインスタンス メソッド内でのみ有効です"
title: "'<keyword>' は、インスタンス メソッド内でのみ有効です。"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 0bca2df44e096da016c9cb0c2031a8ef6faeb2b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795977"
---
# <a name="bc30043-keyword-is-valid-only-within-an-instance-method"></a><span data-ttu-id="2314e-103">BC30043: '\<keyword>' はインスタンス メソッド内でのみ有効です</span><span class="sxs-lookup"><span data-stu-id="2314e-103">BC30043: '\<keyword>' is valid only within an instance method</span></span>

<span data-ttu-id="2314e-104">`Me`、`MyClass`、および `MyBase` キーワードは、特定のクラス インスタンスを参照します。</span><span class="sxs-lookup"><span data-stu-id="2314e-104">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="2314e-105">それらを共有の `Function` または `Sub` プロシージャ内で使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="2314e-105">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>

<span data-ttu-id="2314e-106">"*エラー ID:* " \* BC30043</span><span class="sxs-lookup"><span data-stu-id="2314e-106">*Error ID:*\* BC30043</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2314e-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="2314e-107">To correct this error</span></span>

- <span data-ttu-id="2314e-108">プロシージャからキーワードを削除するか、プロシージャ宣言から `Shared` キーワードを削除します。</span><span class="sxs-lookup"><span data-stu-id="2314e-108">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="2314e-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="2314e-109">See also</span></span>

- [<span data-ttu-id="2314e-110">オブジェクト変数の代入</span><span class="sxs-lookup"><span data-stu-id="2314e-110">Object Variable Assignment</span></span>](../../programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="2314e-111">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="2314e-111">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="2314e-112">継承の基本</span><span class="sxs-lookup"><span data-stu-id="2314e-112">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
