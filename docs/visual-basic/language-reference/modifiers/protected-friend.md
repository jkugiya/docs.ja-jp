---
description: '詳細情報: Protected Friend (Visual Basic)'
title: Protected Friend
ms.date: 05/10/2018
f1_keywords:
- vb.ProtectedFriend
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: dcc8fd2b1aa99f910f002ac05178d379532fb73d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700976"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="e100f-103">Protected Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e100f-103">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="e100f-104">キーワード組み合わせ `Protected Friend` はメンバー アクセス修飾子です。</span><span class="sxs-lookup"><span data-stu-id="e100f-104">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="e100f-105">宣言された要素に対して、[Friend](friend.md) アクセスと [Protected](protected.md) アクセスの両方が許可されるため、同じアセンブリ内の任意の場所から、それらの独自のクラスから、および派生クラスから、それらにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e100f-105">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="e100f-106">`Protected Friend` は、クラスのメンバーに対してのみ指定できます。構造体は継承できないため、構造体のメンバーに `Protected Friend` を適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="e100f-106">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="e100f-107">Visual Studio で、`protected friend` に対して F1 ヘルプを選択すると、[protected](protected.md) または [friend](friend.md) のヘルプが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e100f-107">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="e100f-108">IDE では、複合語ではなくカーソルの下にある 1 つのトークンが選択されます。</span><span class="sxs-lookup"><span data-stu-id="e100f-108">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="e100f-109">ルール</span><span class="sxs-lookup"><span data-stu-id="e100f-109">Rules</span></span>

<span data-ttu-id="e100f-110">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="e100f-110">**Declaration Context.**</span></span> <span data-ttu-id="e100f-111">`Protected Friend` は、クラス レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e100f-111">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="e100f-112">つまり、`Protected` 要素の宣言コンテキストはクラスにする必要があり、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e100f-112">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="e100f-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="e100f-113">See also</span></span>

- [<span data-ttu-id="e100f-114">Public</span><span class="sxs-lookup"><span data-stu-id="e100f-114">Public</span></span>](public.md)
- [<span data-ttu-id="e100f-115">Protected</span><span class="sxs-lookup"><span data-stu-id="e100f-115">Protected</span></span>](protected.md)
- [<span data-ttu-id="e100f-116">Friend</span><span class="sxs-lookup"><span data-stu-id="e100f-116">Friend</span></span>](friend.md)
- [<span data-ttu-id="e100f-117">Private</span><span class="sxs-lookup"><span data-stu-id="e100f-117">Private</span></span>](private.md)
- [<span data-ttu-id="e100f-118">Private Protected</span><span class="sxs-lookup"><span data-stu-id="e100f-118">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="e100f-119">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="e100f-119">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="e100f-120">手順</span><span class="sxs-lookup"><span data-stu-id="e100f-120">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="e100f-121">構造体</span><span class="sxs-lookup"><span data-stu-id="e100f-121">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="e100f-122">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="e100f-122">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
