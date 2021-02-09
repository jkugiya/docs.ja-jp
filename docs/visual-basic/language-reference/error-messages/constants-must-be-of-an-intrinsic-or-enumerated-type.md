---
description: '詳細情報: BC30424:定数は、class、structure、または array 型ではなく、組み込み型または列挙型でなければなりません。'
title: 定数は、class、structure、または array 型ではなく、組み込み型または列挙型でなければなりません。
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: e9765d78ff671d6b99f47242509b1c3b4560c029
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796731"
---
# <a name="bc30424-constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="af829-103">BC30424:定数は、class、structure、または array 型ではなく、組み込み型または列挙型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="af829-103">BC30424: Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>

<span data-ttu-id="af829-104">定数をクラス、構造体、または配列型として宣言しようとしたか、格納先のジェネリック型によって定義された型パラメーターとして宣言しようとしました。</span><span class="sxs-lookup"><span data-stu-id="af829-104">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>

 <span data-ttu-id="af829-105">定数は、組み込み型 (`Boolean`、`Byte`、`Date`、`Decimal`、`Double`、`Integer`、`Long`、`Object`、`SByte`、`Short`、`Single`、`String`、`UInteger`、`ULong`、または `UShort`)、または整数型のいずれかに基づいた `Enum` 型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="af829-105">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>

 <span data-ttu-id="af829-106">**エラー ID:** BC30424</span><span class="sxs-lookup"><span data-stu-id="af829-106">**Error ID:** BC30424</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="af829-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="af829-107">To correct this error</span></span>

1. <span data-ttu-id="af829-108">定数を組み込み型または `Enum` 型として宣言します。</span><span class="sxs-lookup"><span data-stu-id="af829-108">Declare the constant as an intrinsic or `Enum` type.</span></span>

2. <span data-ttu-id="af829-109">定数は、`True`、`False`、`Nothing` などの特別な値でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="af829-109">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="af829-110">コンパイラは、これらの定義済みの値を適切な組み込み型と見なします。</span><span class="sxs-lookup"><span data-stu-id="af829-110">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>

## <a name="see-also"></a><span data-ttu-id="af829-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="af829-111">See also</span></span>

- [<span data-ttu-id="af829-112">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="af829-112">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
- [<span data-ttu-id="af829-113">データの種類</span><span class="sxs-lookup"><span data-stu-id="af829-113">Data Types</span></span>](../../programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="af829-114">データの種類</span><span class="sxs-lookup"><span data-stu-id="af829-114">Data Types</span></span>](../data-types/index.md)
