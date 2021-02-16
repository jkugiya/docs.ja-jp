---
description: '詳細情報: 方法:長い修飾パスを持つオブジェクトに対するアクセス時間を短縮する (Visual Basic)'
title: '方法: 長い修飾パスを持つオブジェクトへのアクセス時間を短縮する'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: 8e0b5dc2ab6c23d57a4e9d905cfd711a79843185
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100467044"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="2467d-103">方法: 長い修飾パスを持つオブジェクトに対するアクセス時間を短縮する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2467d-103">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>

<span data-ttu-id="2467d-104">複数のメソッドおよびプロパティの修飾パスを必要とするオブジェクトに頻繁にアクセスする場合は、修飾パスを繰り返さないことでコードを高速化することができます。</span><span class="sxs-lookup"><span data-stu-id="2467d-104">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>

<span data-ttu-id="2467d-105">修飾パスの繰り返しを回避するには、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="2467d-105">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="2467d-106">オブジェクトを変数に割り当てることも、`With`...`End With` ブロック内で使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="2467d-106">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="2467d-107">頻繁に使用する修飾オブジェクトへのアクセスを変数への代入によって高速化するには</span><span class="sxs-lookup"><span data-stu-id="2467d-107">To speed up access to a heavily qualified object by assigning it to a variable</span></span>

1. <span data-ttu-id="2467d-108">頻繁にアクセスするオブジェクトの型の変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="2467d-108">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="2467d-109">宣言の初期化部分に修飾パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="2467d-109">Specify the qualification path in the initialization part of the declaration.</span></span>

    ```vb
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="2467d-110">オブジェクトのメンバーにアクセスするには、変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="2467d-110">Use the variable to access the object's members.</span></span>

    ```vb
    ctrlActv.Text = "Test"
    ctrlActv.Location = New Point(100, 100)
    ctrlActv.Show()
    ```

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="2467d-111">頻繁に使用する修飾オブジェクトへのアクセスを With...End の With ブロックを使用して高速化するには</span><span class="sxs-lookup"><span data-stu-id="2467d-111">To speed up access to a heavily qualified object by using a With...End With block</span></span>

1. <span data-ttu-id="2467d-112">`With` ステートメントに修飾パスを配置します。</span><span class="sxs-lookup"><span data-stu-id="2467d-112">Put the qualification path in a `With` statement.</span></span>

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="2467d-113">`End With` ステートメントの前に、`With` ブロック内でオブジェクトのメンバーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2467d-113">Access the object's members inside the `With` block, before the `End With` statement.</span></span>

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a><span data-ttu-id="2467d-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="2467d-114">See also</span></span>

- [<span data-ttu-id="2467d-115">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="2467d-115">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="2467d-116">With...End With ステートメント</span><span class="sxs-lookup"><span data-stu-id="2467d-116">With...End With Statement</span></span>](../../../language-reference/statements/with-end-with-statement.md)
