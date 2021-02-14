---
description: "詳細情報: BC30439:定数式は、型 '<typename>' では表現できません"
title: 定数式は、型 '<typename>' では表現できません。
ms.date: 07/20/2015
f1_keywords:
- bc30439
- vbc30439
helpviewer_keywords:
- BC30439
ms.assetid: 0a842906-3bc5-4946-8a37-3e3da883ef63
ms.openlocfilehash: 763ed8a414d8dda3e950ae85a4b1152a459518a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796744"
---
# <a name="bc30439-constant-expression-not-representable-in-type-typename"></a><span data-ttu-id="02384-103">BC30439:定数式は、型 '\<typename>' では表現できません。</span><span class="sxs-lookup"><span data-stu-id="02384-103">BC30439: Constant expression not representable in type '\<typename>'</span></span>

<span data-ttu-id="02384-104">通常は範囲をオーバーフローしているため、ターゲットの型に収まらない定数を評価しようとしています。</span><span class="sxs-lookup"><span data-stu-id="02384-104">You are trying to evaluate a constant that will not fit into the target type, usually because it is overflowing the range.</span></span>

 <span data-ttu-id="02384-105">**エラー ID:** BC30439</span><span class="sxs-lookup"><span data-stu-id="02384-105">**Error ID:** BC30439</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="02384-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="02384-106">To correct this error</span></span>

1. <span data-ttu-id="02384-107">ターゲットの型を、定数を処理できるものに変更します。</span><span class="sxs-lookup"><span data-stu-id="02384-107">Change the target type to one that can handle the constant.</span></span>

## <a name="see-also"></a><span data-ttu-id="02384-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="02384-108">See also</span></span>

- [<span data-ttu-id="02384-109">定数の概要</span><span class="sxs-lookup"><span data-stu-id="02384-109">Constants Overview</span></span>](../../programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="02384-110">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="02384-110">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
