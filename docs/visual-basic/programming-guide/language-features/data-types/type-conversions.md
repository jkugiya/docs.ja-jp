---
description: '詳細情報: Visual Basic における型変換'
title: 型変換
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- changing data types [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 1cdacd21-ba31-4b62-b5be-395e41eeaa17
ms.openlocfilehash: 1f40951856710eb6f2892a7f7a4e04173ee3ee44
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100454483"
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="c7e57-103">Visual Basic における型変換</span><span class="sxs-lookup"><span data-stu-id="c7e57-103">Type Conversions in Visual Basic</span></span>

<span data-ttu-id="c7e57-104">あるデータ型から別の型に値を変更するプロセスは、"*変換*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="c7e57-104">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="c7e57-105">変換は、関連する型のデータ容量に応じて、"*拡大*" または "*縮小*" のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="c7e57-105">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="c7e57-106">また、ソース コードの構文に応じて、"*暗黙的*" または "*明示的*" があります。</span><span class="sxs-lookup"><span data-stu-id="c7e57-106">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7e57-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c7e57-107">In This Section</span></span>  

 [<span data-ttu-id="c7e57-108">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="c7e57-108">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)  
 <span data-ttu-id="c7e57-109">変換先の型がデータを保持できるかどうかによって分類される変換について説明します。</span><span class="sxs-lookup"><span data-stu-id="c7e57-109">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="c7e57-110">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="c7e57-110">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)  
 <span data-ttu-id="c7e57-111">Visual Basic によって自動的に実行されるかどうかによって分類される変換について説明します。</span><span class="sxs-lookup"><span data-stu-id="c7e57-111">Discusses conversions classified by whether Visual Basic performs them automatically.</span></span>  
  
 [<span data-ttu-id="c7e57-112">文字列とその他の型との変換</span><span class="sxs-lookup"><span data-stu-id="c7e57-112">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="c7e57-113">文字列と、数値、`Boolean`、または日付/時刻値の間での変換について説明します。</span><span class="sxs-lookup"><span data-stu-id="c7e57-113">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="c7e57-114">方法: Visual Basic でオブジェクトを別の型に変換する</span><span class="sxs-lookup"><span data-stu-id="c7e57-114">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="c7e57-115">`Object` 変数を他の任意のデータ型に変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c7e57-115">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="c7e57-116">配列変換</span><span class="sxs-lookup"><span data-stu-id="c7e57-116">Array Conversions</span></span>](array-conversions.md)  
 <span data-ttu-id="c7e57-117">さまざまなデータ型の配列間での変換を行う手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="c7e57-117">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c7e57-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7e57-118">Related Sections</span></span>  

 [<span data-ttu-id="c7e57-119">データの種類</span><span class="sxs-lookup"><span data-stu-id="c7e57-119">Data Types</span></span>](index.md)  
 <span data-ttu-id="c7e57-120">Visual Basic のデータ型の概要とそれらの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c7e57-120">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="c7e57-121">データの種類</span><span class="sxs-lookup"><span data-stu-id="c7e57-121">Data Types</span></span>](../../../language-reference/data-types/index.md)  
 <span data-ttu-id="c7e57-122">Visual Basic によって提供される基本データ型の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="c7e57-122">Lists the elementary data types supplied by Visual Basic.</span></span>  
  
 [<span data-ttu-id="c7e57-123">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="c7e57-123">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)  
 <span data-ttu-id="c7e57-124">データ型を使用しているときに発生する一般的な問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="c7e57-124">Discusses some common problems that can arise when working with data types.</span></span>
