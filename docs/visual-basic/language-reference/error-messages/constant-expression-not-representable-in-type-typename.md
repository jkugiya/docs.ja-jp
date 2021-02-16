---
description: "詳細情報: BC30439:定数式は、型 '<typename>' では表現できません。"
title: 定数式は、型 '<typename>' では表現できません。
ms.date: 07/20/2015
f1_keywords:
- bc30439
- vbc30439
helpviewer_keywords:
- BC30439
ms.assetid: 0a842906-3bc5-4946-8a37-3e3da883ef63
ms.openlocfilehash: 034278523fc25cea2e8bb6c749d4c6d412620372
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471371"
---
# <a name="bc30439-constant-expression-not-representable-in-type-typename"></a><span data-ttu-id="39fb1-103">BC30439:定数式は、型 '\<typename>' では表現できません。</span><span class="sxs-lookup"><span data-stu-id="39fb1-103">BC30439: Constant expression not representable in type '\<typename>'</span></span>

<span data-ttu-id="39fb1-104">通常は範囲をオーバーフローしているため、ターゲットの型に収まらない定数を評価しようとしています。</span><span class="sxs-lookup"><span data-stu-id="39fb1-104">You are trying to evaluate a constant that will not fit into the target type, usually because it is overflowing the range.</span></span>

 <span data-ttu-id="39fb1-105">**エラー ID:** BC30439</span><span class="sxs-lookup"><span data-stu-id="39fb1-105">**Error ID:** BC30439</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="39fb1-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="39fb1-106">To correct this error</span></span>

1. <span data-ttu-id="39fb1-107">ターゲットの型を、定数を処理できるものに変更します。</span><span class="sxs-lookup"><span data-stu-id="39fb1-107">Change the target type to one that can handle the constant.</span></span>

## <a name="see-also"></a><span data-ttu-id="39fb1-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="39fb1-108">See also</span></span>

- [<span data-ttu-id="39fb1-109">定数の概要</span><span class="sxs-lookup"><span data-stu-id="39fb1-109">Constants Overview</span></span>](../../programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="39fb1-110">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="39fb1-110">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
