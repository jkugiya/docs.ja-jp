---
description: '詳細情報: Widening (Visual Basic)'
title: Widening
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: de290296ba2b7716ba992c6bed46443053048282
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700703"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="15ce1-103">Widening (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15ce1-103">Widening (Visual Basic)</span></span>

<span data-ttu-id="15ce1-104">変換演算子 (`CType`) が、クラスまたは構造体を、元のクラスまたは構造体のすべての使用可能な値を保持できる型に変換することを示します。</span><span class="sxs-lookup"><span data-stu-id="15ce1-104">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="15ce1-105">Widening キーワードを使用した変換</span><span class="sxs-lookup"><span data-stu-id="15ce1-105">Converting with the Widening Keyword</span></span>  

 <span data-ttu-id="15ce1-106">変換プロシージャでは、`Widening` に加えて `Public Shared` を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15ce1-106">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="15ce1-107">拡大変換は実行時に必ず成功し、データの損失が発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="15ce1-107">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="15ce1-108">例として、`Single` から `Double`、`Char` から `String`、および派生型からその基本型があります。</span><span class="sxs-lookup"><span data-stu-id="15ce1-108">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="15ce1-109">この最後の変換は拡大変換です。これは、派生型に基本型のすべてのメンバーが含まれており、基本型のインスタンスであるためです。</span><span class="sxs-lookup"><span data-stu-id="15ce1-109">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="15ce1-110">`Option Strict` が `On` の場合でも、使用するコードが拡大変換に `CType` を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="15ce1-110">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="15ce1-111">`Widening` キーワードは次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="15ce1-111">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="15ce1-112">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="15ce1-112">Operator Statement</span></span>](../statements/operator-statement.md)  
  
 <span data-ttu-id="15ce1-113">拡大変換と縮小変換の演算子の定義の例については、「[方法: 変換演算子を定義する](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15ce1-113">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15ce1-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="15ce1-114">See also</span></span>

- [<span data-ttu-id="15ce1-115">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="15ce1-115">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="15ce1-116">Narrowing</span><span class="sxs-lookup"><span data-stu-id="15ce1-116">Narrowing</span></span>](narrowing.md)
- [<span data-ttu-id="15ce1-117">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="15ce1-117">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="15ce1-118">方法: 演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="15ce1-118">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="15ce1-119">CType 関数</span><span class="sxs-lookup"><span data-stu-id="15ce1-119">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="15ce1-120">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="15ce1-120">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
- [<span data-ttu-id="15ce1-121">方法: 変換演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="15ce1-121">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
