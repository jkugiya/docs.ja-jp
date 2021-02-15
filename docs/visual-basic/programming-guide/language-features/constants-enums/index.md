---
description: '詳細情報: Visual Basic の定数と列挙体'
title: 定数と列挙体
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- Visual Basic code, constants
- constants [Visual Basic]
- object libraries, Object Browser
- Visual Basic code, enumerations
- declaring constants [Visual Basic], enumerations
- naming conventions [Visual Basic], constants
- Visual Basic code, improving readability with constants
ms.assetid: c8aba36e-fa47-4a33-8b68-cb2009218270
ms.openlocfilehash: 78436f1e00c95c33d547fb9819b21bbe8ebafc2c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468448"
---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="5d71f-103">Visual Basic の定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="5d71f-103">Constants and Enumerations in Visual Basic</span></span>

<span data-ttu-id="5d71f-104">定数は、変化しない値の代わりにわかりやすい名前を使用するための方法です。</span><span class="sxs-lookup"><span data-stu-id="5d71f-104">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="5d71f-105">定数に格納された値は、その名が示すとおり、アプリケーションの実行中に変わることはありません。</span><span class="sxs-lookup"><span data-stu-id="5d71f-105">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="5d71f-106">定数を使用すると、数値の代わりにわかりやすい名前を指定できるので、コードが読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="5d71f-106">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="5d71f-107">一連の関連する定数を操作する場合や、定数値に名前を関連付ける場合は、列挙型を使うと便利です。</span><span class="sxs-lookup"><span data-stu-id="5d71f-107">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="5d71f-108">たとえば、一連の整数型の定数を曜日に関連付けて列挙型として宣言すると、コードで整数値ではなく曜日名を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="5d71f-108">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5d71f-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5d71f-109">In This Section</span></span>  
  
|<span data-ttu-id="5d71f-110">用語</span><span class="sxs-lookup"><span data-stu-id="5d71f-110">Term</span></span>|<span data-ttu-id="5d71f-111">定義</span><span class="sxs-lookup"><span data-stu-id="5d71f-111">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="5d71f-112">定数の概要</span><span class="sxs-lookup"><span data-stu-id="5d71f-112">Constants Overview</span></span>](constants-overview.md)|<span data-ttu-id="5d71f-113">このセクションのトピックでは定数とその使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5d71f-113">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="5d71f-114">列挙型の概要</span><span class="sxs-lookup"><span data-stu-id="5d71f-114">Enumerations Overview</span></span>](enumerations-overview.md)|<span data-ttu-id="5d71f-115">このセクションのトピックでは列挙型とその使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5d71f-115">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="5d71f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d71f-116">Related Sections</span></span>  
  
|<span data-ttu-id="5d71f-117">用語</span><span class="sxs-lookup"><span data-stu-id="5d71f-117">Term</span></span>|<span data-ttu-id="5d71f-118">定義</span><span class="sxs-lookup"><span data-stu-id="5d71f-118">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="5d71f-119">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d71f-119">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)|<span data-ttu-id="5d71f-120">整数の宣言に使用される、`Const` ステートメントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5d71f-120">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="5d71f-121">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d71f-121">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)|<span data-ttu-id="5d71f-122">列挙型の作成に使用される、`Enum` ステートメントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5d71f-122">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="5d71f-123">Option Explicit ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d71f-123">Option Explicit Statement</span></span>](../../../language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="5d71f-124">`Option Explicit` ステートメントについて説明します。このステートメントはモジュール レベルで使用され、そのモジュール内のすべての変数の明示的な宣言を強制します。</span><span class="sxs-lookup"><span data-stu-id="5d71f-124">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="5d71f-125">Option Infer ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d71f-125">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)|<span data-ttu-id="5d71f-126">`Option Infer` ステートメントについて説明します。このステートメントは、変数の宣言でローカル型推論を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5d71f-126">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="5d71f-127">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d71f-127">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)|<span data-ttu-id="5d71f-128">`Object` ステートメントについて説明します。このステートメントは、暗黙的なデータ型変換を拡大変換のみに制限し、遅延バインディングを許可せず、`Option Strict` 型になる暗黙的な型指定も許可しません。</span><span class="sxs-lookup"><span data-stu-id="5d71f-128">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
