---
description: '詳細情報: 方法:オブジェクトの現在のインスタンスを参照する (Visual Basic)'
title: '方法: オブジェクトの現在のインスタンスを参照する'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 84a52c9d0a8b1f588630b31d022490f37595850d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481741"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="d36dd-103">方法: オブジェクトの現在のインスタンスを参照する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d36dd-103">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>

<span data-ttu-id="d36dd-104">オブジェクトの "*現在のインスタンス*" は、コードが現在実行されているインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="d36dd-104">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="d36dd-105">現在のインスタンスを参照するには、`Me` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="d36dd-105">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="d36dd-106">現在のインスタンスを参照するには</span><span class="sxs-lookup"><span data-stu-id="d36dd-106">To refer to the current instance</span></span>  
  
- <span data-ttu-id="d36dd-107">オブジェクト変数の名前を通常使用する箇所で `Me` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="d36dd-107">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="d36dd-108">`Me` はオブジェクト変数と同様に動作しますが、宣言したり、何かを代入したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d36dd-108">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="d36dd-109">`Me` では常に現在のインスタンスが参照されます。</span><span class="sxs-lookup"><span data-stu-id="d36dd-109">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d36dd-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="d36dd-110">See also</span></span>

- [<span data-ttu-id="d36dd-111">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="d36dd-111">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="d36dd-112">オブジェクト変数の代入</span><span class="sxs-lookup"><span data-stu-id="d36dd-112">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="d36dd-113">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="d36dd-113">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
