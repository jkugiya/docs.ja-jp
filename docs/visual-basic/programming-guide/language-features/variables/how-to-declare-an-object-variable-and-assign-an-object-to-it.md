---
description: '詳細情報: 方法:Visual Basic でオブジェクト変数を宣言してオブジェクトを代入する'
title: '方法: Visual Basic でオブジェクト変数を宣言し、オブジェクト変数にオブジェクトを代入する'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: f79cda4507a3dbf2a6946dee7d909b6d1b10802d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481949"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="548a0-103">方法: Visual Basic でオブジェクト変数を宣言してオブジェクトを代入する</span><span class="sxs-lookup"><span data-stu-id="548a0-103">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>

<span data-ttu-id="548a0-104">[Object データ型](../../../language-reference/data-types/object-data-type.md)の変数は、[Dim ステートメント](../../../language-reference/statements/dim-statement.md)で `As Object` を指定して宣言します。</span><span class="sxs-lookup"><span data-stu-id="548a0-104">You declare a variable of the [Object Data Type](../../../language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="548a0-105">このような変数にオブジェクトを代入するには、代入ステートメントまたは初期化句で等号 (`=`) の後にオブジェクトを配置します。</span><span class="sxs-lookup"><span data-stu-id="548a0-105">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>

## <a name="example"></a><span data-ttu-id="548a0-106">例</span><span class="sxs-lookup"><span data-stu-id="548a0-106">Example</span></span>

<span data-ttu-id="548a0-107">次の例では、`Object` 変数を宣言して、現在のインスタンスをこれに代入します。</span><span class="sxs-lookup"><span data-stu-id="548a0-107">The following example declares an `Object` variable and assigns the current instance to it.</span></span>

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

<span data-ttu-id="548a0-108">宣言に変数の初期化を含めると、宣言と代入を同時に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="548a0-108">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="548a0-109">次の例は、前の例と同じです。</span><span class="sxs-lookup"><span data-stu-id="548a0-109">The following example is equivalent to the preceding example.</span></span>

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compile-the-code"></a><span data-ttu-id="548a0-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="548a0-110">Compile the code</span></span>

<span data-ttu-id="548a0-111">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="548a0-111">This example requires:</span></span>

- <span data-ttu-id="548a0-112"><xref:System> 名前空間への参照</span><span class="sxs-lookup"><span data-stu-id="548a0-112">A reference to the <xref:System> namespace.</span></span>

- <span data-ttu-id="548a0-113">`Dim` ステートメントを入れるクラス、構造体、またはモジュール。</span><span class="sxs-lookup"><span data-stu-id="548a0-113">A class, structure, or module in which to put the `Dim` statement.</span></span>

- <span data-ttu-id="548a0-114">代入ステートメントを入れるプロシージャ。</span><span class="sxs-lookup"><span data-stu-id="548a0-114">A procedure in which to put the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="548a0-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="548a0-115">See also</span></span>

- [<span data-ttu-id="548a0-116">変数宣言</span><span class="sxs-lookup"><span data-stu-id="548a0-116">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="548a0-117">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="548a0-117">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="548a0-118">オブジェクト変数の宣言</span><span class="sxs-lookup"><span data-stu-id="548a0-118">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="548a0-119">Object 型</span><span class="sxs-lookup"><span data-stu-id="548a0-119">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="548a0-120">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="548a0-120">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="548a0-121">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="548a0-121">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="548a0-122">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="548a0-122">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
