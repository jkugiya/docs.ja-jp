---
description: '詳細情報: BC30812:省略可能な引数には、既定値を指定する必要があります。'
title: 省略可能な引数には、既定値を指定する必要があります。
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 1cbed1c0f1297ecacdae94d9234d18a3d268f487
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795535"
---
# <a name="bc30812-optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="b4ee5-103">BC30812:省略可能な引数には、既定値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4ee5-103">BC30812: Optional parameters must specify a default value</span></span>

<span data-ttu-id="b4ee5-104">省略可能なパラメーターには、呼び出し元のプロシージャによってパラメーターが指定されていない場合に使用できる既定値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4ee5-104">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>

<span data-ttu-id="b4ee5-105">**エラー ID:** BC30812</span><span class="sxs-lookup"><span data-stu-id="b4ee5-105">**Error ID:** BC30812</span></span>

## <a name="example"></a><span data-ttu-id="b4ee5-106">例</span><span class="sxs-lookup"><span data-stu-id="b4ee5-106">Example</span></span>

<span data-ttu-id="b4ee5-107">次の例では BC30812 が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b4ee5-107">The following example generates BC30812:</span></span>

```vb
Sub Proc1(x As Integer, Optional y As String)
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="to-correct-this-error"></a><span data-ttu-id="b4ee5-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="b4ee5-108">To correct this error</span></span>

<span data-ttu-id="b4ee5-109">省略可能なパラメーターの既定値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b4ee5-109">Specify default values for optional parameters:</span></span>

```vb
Sub Proc1(x As Integer, Optional y As String = "Default Value")
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="see-also"></a><span data-ttu-id="b4ee5-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4ee5-110">See also</span></span>

- [<span data-ttu-id="b4ee5-111">Optional</span><span class="sxs-lookup"><span data-stu-id="b4ee5-111">Optional</span></span>](../modifiers/optional.md)
