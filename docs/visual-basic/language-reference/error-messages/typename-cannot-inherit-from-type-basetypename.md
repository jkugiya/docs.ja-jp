---
description: "詳細情報: BC30910: ベース <type> のアクセスをアセンブリの外側に展開しているため、'<typename>' は <type> '<basetypename>' から継承できません"
title: ベース <typename> のアクセスをアセンブリの外側に展開しているため、'<type>' は <basetypename> '<type>' から継承できません。
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: 332bfcbe9345f03605d6e1d6ded4a3e931ed491f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641097"
---
# <a name="bc30910-typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a><span data-ttu-id="e5163-103">BC30910: ベース \<type> のアクセスをアセンブリの外側に展開しているため、'\<typename>' は \<type> '\<basetypename>' から継承できません</span><span class="sxs-lookup"><span data-stu-id="e5163-103">BC30910: '\<typename>' cannot inherit from \<type> '\<basetypename>' because it expands the access of the base \<type> outside the assembly</span></span>

<span data-ttu-id="e5163-104">クラスまたはインターフェイスは、基底クラスまたはインターフェイスから継承されますが、アクセス レベルの制限が緩くなります。</span><span class="sxs-lookup"><span data-stu-id="e5163-104">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>

 <span data-ttu-id="e5163-105">たとえば、`Public` インターフェイスは `Friend` インターフェイスから継承し、または `Protected` クラスは、`Private` クラスから継承します。</span><span class="sxs-lookup"><span data-stu-id="e5163-105">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="e5163-106">これにより、目的のレベルを超えてアクセスする基底クラスまたはインターフェイスが公開されます。</span><span class="sxs-lookup"><span data-stu-id="e5163-106">This exposes the base class or interface to access beyond the intended level.</span></span>

 <span data-ttu-id="e5163-107">**エラー ID:** BC30910</span><span class="sxs-lookup"><span data-stu-id="e5163-107">**Error ID:** BC30910</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e5163-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="e5163-108">To correct this error</span></span>

- <span data-ttu-id="e5163-109">派生クラスまたはインターフェイスのアクセス レベルを、少なくとも基底クラスまたはインターフェイスのアクセス レベルの制限になるように変更します。</span><span class="sxs-lookup"><span data-stu-id="e5163-109">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>

     <span data-ttu-id="e5163-110">\- または -</span><span class="sxs-lookup"><span data-stu-id="e5163-110">-or-</span></span>

- <span data-ttu-id="e5163-111">制限の緩いアクセス レベルが必要な場合は、`Inherits` ステートメントを削除します。</span><span class="sxs-lookup"><span data-stu-id="e5163-111">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="e5163-112">より制限の厳しい基底クラスまたはインターフェイスから継承することはできません。</span><span class="sxs-lookup"><span data-stu-id="e5163-112">You cannot inherit from a more restricted base class or interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5163-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5163-113">See also</span></span>

- [<span data-ttu-id="e5163-114">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="e5163-114">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="e5163-115">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="e5163-115">Interface Statement</span></span>](../statements/interface-statement.md)
- [<span data-ttu-id="e5163-116">Inherits ステートメント</span><span class="sxs-lookup"><span data-stu-id="e5163-116">Inherits Statement</span></span>](../statements/inherits-statement.md)
- [<span data-ttu-id="e5163-117">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="e5163-117">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
