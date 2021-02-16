---
description: "詳細情報: BC30154: <type1>'<typename>' はインターフェイス '<interfacename>' に対して '<membername>' を実装しなければなりません"
title: <type1>'<typename>' は、インターフェイス '<interfacename>' に対して '<membername>' を実装しなければなりません。
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: fc0cf8544984ddf41f1f91cb0bca90b630d9614d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100473564"
---
# <a name="bc30154-type1typename-must-implement-membername-for-interface-interfacename"></a><span data-ttu-id="1c422-103">BC30154: \<type1>'\<typename>' はインターフェイス '\<interfacename>' に対して '\<membername>' を実装しなければなりません</span><span class="sxs-lookup"><span data-stu-id="1c422-103">BC30154: \<type1>'\<typename>' must implement '\<membername>' for interface '\<interfacename>'</span></span>

<span data-ttu-id="1c422-104">'\<typename>' は、インターフェイス '\<interfacename>' に対して '\<membername>' を実装しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="1c422-104">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="1c422-105">プロパティの実装には、一致する 'ReadOnly'/'WriteOnly' 指定子が必要です。</span><span class="sxs-lookup"><span data-stu-id="1c422-105">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>

 <span data-ttu-id="1c422-106">クラスまたは構造体では、インターフェイスを実装することが要求されますが、インターフェイスによって定義されるプロシージャ、プロパティ、またはイベントは実装しません。</span><span class="sxs-lookup"><span data-stu-id="1c422-106">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="1c422-107">インターフェイスのすべてのメンバーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c422-107">Every member of the interface must be implemented.</span></span>

 <span data-ttu-id="1c422-108">**エラー ID:** BC30154</span><span class="sxs-lookup"><span data-stu-id="1c422-108">**Error ID:** BC30154</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="1c422-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="1c422-109">To correct this error</span></span>

1. <span data-ttu-id="1c422-110">インターフェイスで定義されているものと同じ名前およびシグネチャのメンバーを宣言します。</span><span class="sxs-lookup"><span data-stu-id="1c422-110">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="1c422-111">少なくとも `End Function`、`End Sub`、または `End Property` ステートメントを含めてください。</span><span class="sxs-lookup"><span data-stu-id="1c422-111">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>

2. <span data-ttu-id="1c422-112">`Function`、`Sub`、`Property`、または `Event` ステートメントの末尾に `Implements` 句を追加します。</span><span class="sxs-lookup"><span data-stu-id="1c422-112">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="1c422-113">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1c422-113">For example:</span></span>

    ```vb
    Public Event ItHappened() Implements IBaseInterface.ItHappened
    ```

3. <span data-ttu-id="1c422-114">プロパティを実装するときは、インターフェイス定義と同じ方法で `ReadOnly` または `WriteOnly` が使用されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1c422-114">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>

4. <span data-ttu-id="1c422-115">プロパティを実装する場合は、必要に応じて `Get` および `Set` プロシージャを宣言します。</span><span class="sxs-lookup"><span data-stu-id="1c422-115">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c422-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="1c422-116">See also</span></span>

- [<span data-ttu-id="1c422-117">Implements ステートメント</span><span class="sxs-lookup"><span data-stu-id="1c422-117">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="1c422-118">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1c422-118">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
