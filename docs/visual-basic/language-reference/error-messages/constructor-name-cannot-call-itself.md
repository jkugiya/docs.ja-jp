---
description: "詳細情報: BC30298:コンストラクター '<name>' はそれ自体を呼び出すことはできません。"
title: コンストラクター '<name>' はそれ自体を呼び出すことはできません。
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 486495eb822e3e3008382232091fe3923851f97c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796718"
---
# <a name="bc30298-constructor-name-cannot-call-itself"></a><span data-ttu-id="b8a17-103">BC30298:コンストラクター '\<name>' はそれ自体を呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="b8a17-103">BC30298: Constructor '\<name>' cannot call itself</span></span>

<span data-ttu-id="b8a17-104">クラスまたは構造体の `Sub New` プロシージャはそれ自体を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b8a17-104">A `Sub New` procedure in a class or structure calls itself.</span></span>

 <span data-ttu-id="b8a17-105">コンストラクターの目的は、クラスまたは構造体が最初に作成されたときにそのインスタンスを初期化することです。</span><span class="sxs-lookup"><span data-stu-id="b8a17-105">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="b8a17-106">クラスまたは構造体には、すべてに異なるパラメーター リストが含まれていれば、複数のコンストラクターを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b8a17-106">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="b8a17-107">コンストラクターは、別のコンストラクターを呼び出して、独自の機能だけでなくその機能も実行することができます。</span><span class="sxs-lookup"><span data-stu-id="b8a17-107">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="b8a17-108">ただし、コンストラクターがそれ自体を呼び出す場合は意味がありません。許可されている場合、実際にはこれは無限再帰になります。</span><span class="sxs-lookup"><span data-stu-id="b8a17-108">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>

 <span data-ttu-id="b8a17-109">**エラー ID:** BC30298</span><span class="sxs-lookup"><span data-stu-id="b8a17-109">**Error ID:** BC30298</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b8a17-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="b8a17-110">To correct this error</span></span>

1. <span data-ttu-id="b8a17-111">呼び出されるコンストラクターのパラメーター リストを確認します。</span><span class="sxs-lookup"><span data-stu-id="b8a17-111">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="b8a17-112">これは、呼び出しを行うコンストラクターのものと異なる必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8a17-112">It should be different from that of the constructor making the call.</span></span>

2. <span data-ttu-id="b8a17-113">別のコンストラクターを呼び出さない場合は、`Sub New` 呼び出しを完全に削除します。</span><span class="sxs-lookup"><span data-stu-id="b8a17-113">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8a17-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8a17-114">See also</span></span>

- [<span data-ttu-id="b8a17-115">オブジェクトの有効期間:オブジェクトの作成と破棄</span><span class="sxs-lookup"><span data-stu-id="b8a17-115">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
