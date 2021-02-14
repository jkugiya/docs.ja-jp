---
description: "詳細情報: BC36532:入れ子になった関数に、デリゲート '<delegatename>' と互換性のあるシグネチャがありません"
title: 入れ子になった関数に、デリゲート '<delegatename>' と互換性のあるシグネチャがありません。
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 2220faacdac065718a302ef7b086f99bf1e16cef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795665"
---
# <a name="bc36532-nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a><span data-ttu-id="d034f-103">BC36532:入れ子になった関数に、デリゲート '\<delegatename>' と互換性のあるシグネチャがありません。</span><span class="sxs-lookup"><span data-stu-id="d034f-103">BC36532: Nested function does not have a signature that is compatible with delegate '\<delegatename>'</span></span>

<span data-ttu-id="d034f-104">ラムダ式が、互換性のないシグネチャを含むデリゲートに割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="d034f-104">A lambda expression has been assigned to a delegate that has an incompatible signature.</span></span> <span data-ttu-id="d034f-105">たとえば、次のコードでは、デリゲート `Del` に 2 つの整数パラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="d034f-105">For example, in the following code, delegate `Del` has two integer parameters.</span></span>

```vb
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer
```

<span data-ttu-id="d034f-106">このエラーは、1 つの引数を含むラムダ式が `Del` 型として宣言されている場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="d034f-106">The error is raised if a lambda expression with one argument is declared as type `Del`:</span></span>

```vb
' Neither of these is valid.
' Dim lambda1 As Del = Function(n As Integer) n + 1
' Dim lambda2 As Del = Function(n) n + 1
```

<span data-ttu-id="d034f-107">**エラー ID:** BC36532</span><span class="sxs-lookup"><span data-stu-id="d034f-107">**Error ID:** BC36532</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d034f-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="d034f-108">To correct this error</span></span>

<span data-ttu-id="d034f-109">デリゲート定義または割り当てられているラムダ式を調整して、シグネチャに互換性を持たせるようにします。</span><span class="sxs-lookup"><span data-stu-id="d034f-109">Adjust either the delegate definition or the assigned lambda expression so that the signatures are compatible.</span></span>

## <a name="see-also"></a><span data-ttu-id="d034f-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="d034f-110">See also</span></span>

- [<span data-ttu-id="d034f-111">厳密でないデリゲート変換</span><span class="sxs-lookup"><span data-stu-id="d034f-111">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="d034f-112">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="d034f-112">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
