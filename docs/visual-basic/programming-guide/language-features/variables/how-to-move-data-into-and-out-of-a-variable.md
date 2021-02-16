---
description: '詳細情報: 方法:変数に値を格納する、および変数から値を取得する (Visual Basic)'
title: '方法: 変数に値を格納する、および変数から値を取得する'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: e75be83f82a3e1418099375eb52a2d2cc4fdbd18
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481819"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a><span data-ttu-id="dbbfc-103">方法: 変数に値を格納する、および変数から値を取得する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbbfc-103">How to: Move Data Into and Out of a Variable (Visual Basic)</span></span>

<span data-ttu-id="dbbfc-104">変数に値を格納するには、代入ステートメントの左辺に変数名を指定します。</span><span class="sxs-lookup"><span data-stu-id="dbbfc-104">You store a value in a variable by putting the variable name on the left side of an assignment statement.</span></span>

## <a name="putting-data-in-a-variable"></a><span data-ttu-id="dbbfc-105">変数にデータを格納する</span><span class="sxs-lookup"><span data-stu-id="dbbfc-105">Putting Data in a Variable</span></span>

#### <a name="to-store-a-value-in-a-variable"></a><span data-ttu-id="dbbfc-106">変数に値を格納するには</span><span class="sxs-lookup"><span data-stu-id="dbbfc-106">To store a value in a variable</span></span>

- <span data-ttu-id="dbbfc-107">代入ステートメントの左辺に変数名を使用します。</span><span class="sxs-lookup"><span data-stu-id="dbbfc-107">Use the variable name on the left side of an assignment statement.</span></span>

    <span data-ttu-id="dbbfc-108">次の例では、変数 `alpha` の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="dbbfc-108">The following example sets the value of the variable `alpha`.</span></span>

    ```vb
    alpha = (beta * 6.27) / (gamma + 2.1)
    ```

    <span data-ttu-id="dbbfc-109">代入ステートメントの右辺で生成された値がその変数に格納されます。</span><span class="sxs-lookup"><span data-stu-id="dbbfc-109">The value generated on the right side of the assignment statement is stored in the variable.</span></span>

## <a name="getting-data-from-a-variable"></a><span data-ttu-id="dbbfc-110">変数からのデータの取得</span><span class="sxs-lookup"><span data-stu-id="dbbfc-110">Getting Data from a Variable</span></span>

<span data-ttu-id="dbbfc-111">変数の値を取得するには、式に変数名を含めます。</span><span class="sxs-lookup"><span data-stu-id="dbbfc-111">You retrieve a variable's value by including the variable name in an expression.</span></span>

#### <a name="to-retrieve-a-value-from-a-variable"></a><span data-ttu-id="dbbfc-112">変数から値を取得するには</span><span class="sxs-lookup"><span data-stu-id="dbbfc-112">To retrieve a value from a variable</span></span>

- <span data-ttu-id="dbbfc-113">式内に変数名を使用します。</span><span class="sxs-lookup"><span data-stu-id="dbbfc-113">Use the variable name in an expression.</span></span> <span data-ttu-id="dbbfc-114">定数またはリテラルを使用できる場所であればどこでも変数を使用できます。ただし、定数の値を定義する式内は例外です。</span><span class="sxs-lookup"><span data-stu-id="dbbfc-114">You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.</span></span>

  <span data-ttu-id="dbbfc-115">\- または -</span><span class="sxs-lookup"><span data-stu-id="dbbfc-115">\-or-</span></span>

- <span data-ttu-id="dbbfc-116">代入ステートメント内で等号 (`=`) の後に変数名を使用します。</span><span class="sxs-lookup"><span data-stu-id="dbbfc-116">Use the variable name following the equal (`=`) sign in an assignment statement.</span></span>

  <span data-ttu-id="dbbfc-117">次の例では、変数 `startValue` の値を読み取ってから、式内で変数 `counter` の値を使用しています。</span><span class="sxs-lookup"><span data-stu-id="dbbfc-117">The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.</span></span>

  ```vb
  counter = startValue
  cellValue = (counter + 5) ^ 2
  ```

  <span data-ttu-id="dbbfc-118">変数の値は定数の場合と同様に式に含められ、そして代入ステートメントの左辺にある変数またはプロパティに格納されます。</span><span class="sxs-lookup"><span data-stu-id="dbbfc-118">The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="dbbfc-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="dbbfc-119">See also</span></span>

- [<span data-ttu-id="dbbfc-120">変数</span><span class="sxs-lookup"><span data-stu-id="dbbfc-120">Variables</span></span>](index.md)
- [<span data-ttu-id="dbbfc-121">変数宣言</span><span class="sxs-lookup"><span data-stu-id="dbbfc-121">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="dbbfc-122">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="dbbfc-122">Object Variables</span></span>](object-variables.md)
