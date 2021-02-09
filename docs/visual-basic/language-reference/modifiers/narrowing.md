---
description: '詳細情報: Narrowing (Visual Basic)'
title: Narrowing
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: 1dd9185ccf30fb6f9dc9360f75450c2533ab90e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795353"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="2c81b-103">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c81b-103">Narrowing (Visual Basic)</span></span>

<span data-ttu-id="2c81b-104">変換演算子 (`CType`) で、クラスまたは構造体を、元のクラスまたは構造体の一部の使用可能な値を保持できない可能性がある型に変換することを示します。</span><span class="sxs-lookup"><span data-stu-id="2c81b-104">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="2c81b-105">Narrowing キーワードを使用した変換</span><span class="sxs-lookup"><span data-stu-id="2c81b-105">Converting with the Narrowing Keyword</span></span>  

 <span data-ttu-id="2c81b-106">変換プロシージャでは、`Narrowing` に加えて `Public Shared` を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c81b-106">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="2c81b-107">縮小変換は実行時に必ず成功するとは限らず、失敗したり、データの損失が発生したりする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2c81b-107">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="2c81b-108">例として、`Long` から `Integer`、`String` から `Date`、および基本型から派生型があります。</span><span class="sxs-lookup"><span data-stu-id="2c81b-108">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="2c81b-109">基本型には派生型のすべてのメンバーが含まれていない場合があり、派生型のインスタンスではないため、この最後の変換は縮小変換になります。</span><span class="sxs-lookup"><span data-stu-id="2c81b-109">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="2c81b-110">`Option Strict` が `On` の場合、使用しているコードではすべての縮小変換に `CType` を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c81b-110">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="2c81b-111">`Narrowing` キーワードは次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="2c81b-111">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="2c81b-112">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="2c81b-112">Operator Statement</span></span>](../statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="2c81b-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c81b-113">See also</span></span>

- [<span data-ttu-id="2c81b-114">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="2c81b-114">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="2c81b-115">Widening</span><span class="sxs-lookup"><span data-stu-id="2c81b-115">Widening</span></span>](widening.md)
- [<span data-ttu-id="2c81b-116">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="2c81b-116">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="2c81b-117">方法: 演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="2c81b-117">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="2c81b-118">CType 関数</span><span class="sxs-lookup"><span data-stu-id="2c81b-118">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="2c81b-119">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="2c81b-119">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
