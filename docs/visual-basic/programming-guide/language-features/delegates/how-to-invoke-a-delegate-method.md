---
description: '詳細情報: 方法:デリゲート メソッドを呼び出す (Visual Basic)'
title: '方法: デリゲート メソッドを呼び出す'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: c5c20048969f2fef16b8b7f65e84a094a3f1cf9f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434473"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="fb969-103">方法: デリゲート メソッドを呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb969-103">How to: Invoke a Delegate Method (Visual Basic)</span></span>

<span data-ttu-id="fb969-104">この例では、メソッドをデリゲートに関連付け、デリゲートからそのメソッドを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fb969-104">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>

### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="fb969-105">デリゲートおよび一致するプロシージャを作成する</span><span class="sxs-lookup"><span data-stu-id="fb969-105">Create the delegate and matching procedures</span></span>

1. <span data-ttu-id="fb969-106">`MySubDelegate` という名前のデリゲートを作成します。</span><span class="sxs-lookup"><span data-stu-id="fb969-106">Create a delegate named `MySubDelegate`.</span></span>

    ```vb
    Delegate Sub MySubDelegate(ByVal x As Integer)
    ```

2. <span data-ttu-id="fb969-107">デリゲートと同じシグネチャのメソッドを含むクラスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="fb969-107">Declare a class that contains a method with the same signature as the delegate.</span></span>

    ```vb
    Class class1
        Sub Sub1(ByVal x As Integer)
            MsgBox("The value of x is: " & CStr(x))
        End Sub
    End Class
    ```

3. <span data-ttu-id="fb969-108">デリゲートのインスタンスを作成して、デリゲートに関連付けられているメソッドを、組み込みの `Invoke` メソッドを呼び出すことで起動するメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="fb969-108">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>

    ```vb
    Protected Sub DelegateTest()
        Dim c1 As New class1
        ' Create an instance of the delegate.
        Dim msd As MySubDelegate = AddressOf c1.Sub1
        ' Call the method.
        msd.Invoke(10)
    End Sub
    ```

## <a name="see-also"></a><span data-ttu-id="fb969-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb969-109">See also</span></span>

- [<span data-ttu-id="fb969-110">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="fb969-110">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="fb969-111">デリゲート</span><span class="sxs-lookup"><span data-stu-id="fb969-111">Delegates</span></span>](index.md)
- [<span data-ttu-id="fb969-112">イベント</span><span class="sxs-lookup"><span data-stu-id="fb969-112">Events</span></span>](../events/index.md)
- [<span data-ttu-id="fb969-113">マルチスレッド アプリケーション</span><span class="sxs-lookup"><span data-stu-id="fb969-113">Multithreaded Applications</span></span>](../../../../standard/threading/using-threads-and-threading.md)
