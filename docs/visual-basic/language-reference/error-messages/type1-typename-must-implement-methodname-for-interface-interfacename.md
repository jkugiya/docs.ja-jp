---
description: "詳細情報: BC30149: <type1>'<typename>' はインターフェイス '<interfacename>' に対して '<methodname>' を実装しなければなりません"
title: <type1>'<typename>' は、インターフェイス '<interfacename>' に対して '<methodname>' を実装しなければなりません。
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 34635cbe5b8736d273d5972a1bb83aa3d975490b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675014"
---
# <a name="bc30149-type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="87331-103">BC30149: \<type1>'\<typename>' はインターフェイス '\<interfacename>' に対して '\<methodname>' を実装しなければなりません</span><span class="sxs-lookup"><span data-stu-id="87331-103">BC30149: \<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>

<span data-ttu-id="87331-104">クラスまたは構造体では、インターフェイスを実装することが要求されますが、インターフェイスによって定義されるプロシージャは実装しません。</span><span class="sxs-lookup"><span data-stu-id="87331-104">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="87331-105">インターフェイスのすべてのメンバーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87331-105">Every member of the interface must be implemented.</span></span>

 <span data-ttu-id="87331-106">**エラー ID:** BC30149</span><span class="sxs-lookup"><span data-stu-id="87331-106">**Error ID:** BC30149</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="87331-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="87331-107">To correct this error</span></span>

1. <span data-ttu-id="87331-108">インターフェイスで定義されているものと同じ名前およびシグネチャを持つプロシージャを宣言します。</span><span class="sxs-lookup"><span data-stu-id="87331-108">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="87331-109">少なくとも `End Function` または `End Sub` ステートメントを含めてください。</span><span class="sxs-lookup"><span data-stu-id="87331-109">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>

2. <span data-ttu-id="87331-110">`Function` または `Sub` ステートメントの末尾に `Implements` 句を追加します。</span><span class="sxs-lookup"><span data-stu-id="87331-110">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="87331-111">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="87331-111">For example:</span></span>

    ```vb
    Public Sub DoSomething() Implements IBaseInterface.DoSomething
    ```

## <a name="see-also"></a><span data-ttu-id="87331-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="87331-112">See also</span></span>

- [<span data-ttu-id="87331-113">Implements ステートメント</span><span class="sxs-lookup"><span data-stu-id="87331-113">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="87331-114">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87331-114">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
