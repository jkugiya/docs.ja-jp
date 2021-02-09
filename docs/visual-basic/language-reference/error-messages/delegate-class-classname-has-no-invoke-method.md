---
description: "詳細情報: BC30220:Delegate クラス '<classname>' には Invoke メソッドが含まれていないため、この型の式をメソッド呼び出しのターゲットに設定することはできません。"
title: Delegate クラス '<classname>' には Invoke メソッドが含まれていないため、この型の式をメソッド呼び出しのターゲットに設定することはできません。
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: c0d3f6e352a98e194b2c2ddca04bfa7254ec37a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796627"
---
# <a name="bc30220-delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="4ac31-103">BC30220:Delegate クラス '\<classname>' には Invoke メソッドが含まれていないため、この型の式をメソッド呼び出しのターゲットに設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="4ac31-103">BC30220: Delegate class '\<classname>' has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>

<span data-ttu-id="4ac31-104">デリゲート クラスに `Invoke` が実装されていないため、デリゲートを使用して `Invoke` を呼び出すことができませんでした。</span><span class="sxs-lookup"><span data-stu-id="4ac31-104">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>

 <span data-ttu-id="4ac31-105">**エラー ID:** BC30220</span><span class="sxs-lookup"><span data-stu-id="4ac31-105">**Error ID:** BC30220</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="4ac31-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="4ac31-106">To correct this error</span></span>

1. <span data-ttu-id="4ac31-107">デリゲート クラスのインスタンスが `Dim` ステートメントを使用して作成されていること、およびプロシージャが `AddressOf` 演算子を使用してデリゲート インスタンスに割り当てられていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4ac31-107">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>

2. <span data-ttu-id="4ac31-108">デリゲート クラスを実装するコードを見つけ、それによって `Invoke` プロシージャが実装されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4ac31-108">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ac31-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ac31-109">See also</span></span>

- [<span data-ttu-id="4ac31-110">デリゲート</span><span class="sxs-lookup"><span data-stu-id="4ac31-110">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="4ac31-111">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="4ac31-111">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="4ac31-112">AddressOf 演算子</span><span class="sxs-lookup"><span data-stu-id="4ac31-112">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="4ac31-113">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="4ac31-113">Dim Statement</span></span>](../statements/dim-statement.md)
