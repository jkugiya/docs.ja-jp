---
description: '詳細情報: 宣言コンテキストと既定のアクセス レベル (Visual Basic)'
title: 宣言コンテキストと既定のアクセス レベル
ms.date: 07/20/2015
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
ms.openlocfilehash: c550db39862fbe9f69e5651b6e9fc7fdfcc88513
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700339"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a><span data-ttu-id="ce0e6-103">宣言コンテキストと既定のアクセス レベル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce0e6-103">Declaration Contexts and Default Access Levels (Visual Basic)</span></span>

<span data-ttu-id="ce0e6-104">このトピックでは、どの Visual Basic の型を他のどの型内に宣言できるか、およびそれらのアクセス レベルが指定されていない場合の既定値について説明します。</span><span class="sxs-lookup"><span data-stu-id="ce0e6-104">This topic describes which Visual Basic types can be declared within which other types, and what their access levels default to if not specified.</span></span>  
  
## <a name="declaration-context-levels"></a><span data-ttu-id="ce0e6-105">宣言コンテキスト レベル</span><span class="sxs-lookup"><span data-stu-id="ce0e6-105">Declaration Context Levels</span></span>  

 <span data-ttu-id="ce0e6-106">プログラミング要素の *宣言コンテキスト* は、それが宣言されているコードの領域です。</span><span class="sxs-lookup"><span data-stu-id="ce0e6-106">The *declaration context* of a programming element is the region of code in which it is declared.</span></span> <span data-ttu-id="ce0e6-107">これは、多くの場合、別のプログラミング要素であり、そのために *親要素* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ce0e6-107">This is often another programming element, which is then called the *containing element*.</span></span>  
  
 <span data-ttu-id="ce0e6-108">宣言コンテキストのレベルは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ce0e6-108">The levels for declaration contexts are the following:</span></span>  
  
- <span data-ttu-id="ce0e6-109">*名前空間レベル* - ソースファイルまたは名前空間内であり、クラス、構造体、モジュール、またはインターフェイス内ではありません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-109">*Namespace level* — within a source file or namespace but not within a class, structure, module, or interface</span></span>  
  
- <span data-ttu-id="ce0e6-110">*モジュール レベル* - クラス、構造体、モジュール、またはインターフェイス内であり、プロシージャまたはブロック内ではありません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-110">*Module level* — within a class, structure, module, or interface but not within a procedure or block</span></span>  
  
- <span data-ttu-id="ce0e6-111">*プロシージャ レベル* - プロシージャまたはブロック (`If` や `For` など) 内です</span><span class="sxs-lookup"><span data-stu-id="ce0e6-111">*Procedure level* — within a procedure or block (such as `If` or `For`)</span></span>  
  
 <span data-ttu-id="ce0e6-112">次の表に、宣言コンテキストに応じて、宣言されたさまざまなプログラミング要素の既定のアクセス レベルを示します。</span><span class="sxs-lookup"><span data-stu-id="ce0e6-112">The following table shows the default access levels for various declared programming elements, depending on their declaration contexts.</span></span>  
  
|<span data-ttu-id="ce0e6-113">宣言された要素</span><span class="sxs-lookup"><span data-stu-id="ce0e6-113">Declared element</span></span>|<span data-ttu-id="ce0e6-114">名前空間レベル</span><span class="sxs-lookup"><span data-stu-id="ce0e6-114">Namespace level</span></span>|<span data-ttu-id="ce0e6-115">モジュール レベル</span><span class="sxs-lookup"><span data-stu-id="ce0e6-115">Module level</span></span>|<span data-ttu-id="ce0e6-116">プロシージャ レベル</span><span class="sxs-lookup"><span data-stu-id="ce0e6-116">Procedure level</span></span>|  
|----------------------|---------------------|------------------|---------------------|  
|<span data-ttu-id="ce0e6-117">変数 ([Dim ステートメント](dim-statement.md))</span><span class="sxs-lookup"><span data-stu-id="ce0e6-117">Variable ([Dim Statement](dim-statement.md))</span></span>|<span data-ttu-id="ce0e6-118">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-118">Not allowed</span></span>|<span data-ttu-id="ce0e6-119">`Private` (`Structure` 内の `Public`、`Interface` では使用できません)</span><span class="sxs-lookup"><span data-stu-id="ce0e6-119">`Private` (`Public` in `Structure`, not allowed in `Interface`)</span></span>|`Public`|  
|<span data-ttu-id="ce0e6-120">定数 ([Const ステートメント](const-statement.md))</span><span class="sxs-lookup"><span data-stu-id="ce0e6-120">Constant ([Const Statement](const-statement.md))</span></span>|<span data-ttu-id="ce0e6-121">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-121">Not allowed</span></span>|<span data-ttu-id="ce0e6-122">`Private` (`Structure` 内の `Public`、`Interface` では使用できません)</span><span class="sxs-lookup"><span data-stu-id="ce0e6-122">`Private` (`Public` in `Structure`, not allowed in `Interface`)</span></span>|`Public`|  
|<span data-ttu-id="ce0e6-123">列挙型 ([Enum ステートメント](enum-statement.md))</span><span class="sxs-lookup"><span data-stu-id="ce0e6-123">Enumeration ([Enum Statement](enum-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="ce0e6-124">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-124">Not allowed</span></span>|  
|<span data-ttu-id="ce0e6-125">クラス ([Class ステートメント](class-statement.md))</span><span class="sxs-lookup"><span data-stu-id="ce0e6-125">Class ([Class Statement](class-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="ce0e6-126">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-126">Not allowed</span></span>|  
|<span data-ttu-id="ce0e6-127">構造体 ([Structure ステートメント](structure-statement.md))</span><span class="sxs-lookup"><span data-stu-id="ce0e6-127">Structure ([Structure Statement](structure-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="ce0e6-128">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-128">Not allowed</span></span>|  
|<span data-ttu-id="ce0e6-129">モジュール ([Module ステートメント](module-statement.md))</span><span class="sxs-lookup"><span data-stu-id="ce0e6-129">Module ([Module Statement](module-statement.md))</span></span>|`Friend`|<span data-ttu-id="ce0e6-130">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-130">Not allowed</span></span>|<span data-ttu-id="ce0e6-131">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-131">Not allowed</span></span>|  
|<span data-ttu-id="ce0e6-132">インターフェイス ([Interface ステートメント](interface-statement.md))</span><span class="sxs-lookup"><span data-stu-id="ce0e6-132">Interface ([Interface Statement](interface-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="ce0e6-133">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-133">Not allowed</span></span>|  
|<span data-ttu-id="ce0e6-134">プロシージャ ([Function ステートメント](function-statement.md)、[Sub ステートメント](sub-statement.md))</span><span class="sxs-lookup"><span data-stu-id="ce0e6-134">Procedure ([Function Statement](function-statement.md), [Sub Statement](sub-statement.md))</span></span>|<span data-ttu-id="ce0e6-135">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-135">Not allowed</span></span>|`Public`|<span data-ttu-id="ce0e6-136">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-136">Not allowed</span></span>|  
|<span data-ttu-id="ce0e6-137">外部参照 ([Declare ステートメント](declare-statement.md))</span><span class="sxs-lookup"><span data-stu-id="ce0e6-137">External reference ([Declare Statement](declare-statement.md))</span></span>|<span data-ttu-id="ce0e6-138">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-138">Not allowed</span></span>|<span data-ttu-id="ce0e6-139">`Public` (`Interface` では使用できません)</span><span class="sxs-lookup"><span data-stu-id="ce0e6-139">`Public` (not allowed in `Interface`)</span></span>|<span data-ttu-id="ce0e6-140">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-140">Not allowed</span></span>|  
|<span data-ttu-id="ce0e6-141">演算子 ([Operator ステートメント](operator-statement.md))</span><span class="sxs-lookup"><span data-stu-id="ce0e6-141">Operator ([Operator Statement](operator-statement.md))</span></span>|<span data-ttu-id="ce0e6-142">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-142">Not allowed</span></span>|<span data-ttu-id="ce0e6-143">`Public` (`Interface` または `Module` では使用できません)</span><span class="sxs-lookup"><span data-stu-id="ce0e6-143">`Public` (not allowed in `Interface` or `Module`)</span></span>|<span data-ttu-id="ce0e6-144">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-144">Not allowed</span></span>|  
|<span data-ttu-id="ce0e6-145">プロパティ ([Property ステートメント](property-statement.md))</span><span class="sxs-lookup"><span data-stu-id="ce0e6-145">Property ([Property Statement](property-statement.md))</span></span>|<span data-ttu-id="ce0e6-146">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-146">Not allowed</span></span>|`Public`|<span data-ttu-id="ce0e6-147">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-147">Not allowed</span></span>|  
|<span data-ttu-id="ce0e6-148">既定のプロパティ ([Default](../modifiers/default.md))</span><span class="sxs-lookup"><span data-stu-id="ce0e6-148">Default property ([Default](../modifiers/default.md))</span></span>|<span data-ttu-id="ce0e6-149">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-149">Not allowed</span></span>|<span data-ttu-id="ce0e6-150">`Public` (`Module` では使用できません)</span><span class="sxs-lookup"><span data-stu-id="ce0e6-150">`Public` (not allowed in `Module`)</span></span>|<span data-ttu-id="ce0e6-151">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-151">Not allowed</span></span>|  
|<span data-ttu-id="ce0e6-152">イベント ([Event ステートメント](event-statement.md))</span><span class="sxs-lookup"><span data-stu-id="ce0e6-152">Event ([Event Statement](event-statement.md))</span></span>|<span data-ttu-id="ce0e6-153">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-153">Not allowed</span></span>|`Public`|<span data-ttu-id="ce0e6-154">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-154">Not allowed</span></span>|  
|<span data-ttu-id="ce0e6-155">委任 ([Delegate ステートメント](delegate-statement.md))</span><span class="sxs-lookup"><span data-stu-id="ce0e6-155">Delegate ([Delegate Statement](delegate-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="ce0e6-156">使用できません</span><span class="sxs-lookup"><span data-stu-id="ce0e6-156">Not allowed</span></span>|  
  
 <span data-ttu-id="ce0e6-157">詳しくは、「[Visual Basic でのアクセス レベル](../../programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce0e6-157">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce0e6-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="ce0e6-158">See also</span></span>

- [<span data-ttu-id="ce0e6-159">Friend</span><span class="sxs-lookup"><span data-stu-id="ce0e6-159">Friend</span></span>](../modifiers/friend.md)
- [<span data-ttu-id="ce0e6-160">Private</span><span class="sxs-lookup"><span data-stu-id="ce0e6-160">Private</span></span>](../modifiers/private.md)
- [<span data-ttu-id="ce0e6-161">Public</span><span class="sxs-lookup"><span data-stu-id="ce0e6-161">Public</span></span>](../modifiers/public.md)
