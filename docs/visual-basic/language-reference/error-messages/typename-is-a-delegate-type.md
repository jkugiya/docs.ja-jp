---
description: "詳細情報: BC32008: '<typename>' はデリゲート型です"
title: "'<typename>' はデリゲート型です。"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 72aac48038c433b7938c54e7f1138a5b91bf7689
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675027"
---
# <a name="bc32008-typename-is-a-delegate-type"></a><span data-ttu-id="16a45-103">BC32008: '\<typename>' はデリゲート型です</span><span class="sxs-lookup"><span data-stu-id="16a45-103">BC32008: '\<typename>' is a delegate type</span></span>

<span data-ttu-id="16a45-104">'\<typename>' はデリゲート型です。</span><span class="sxs-lookup"><span data-stu-id="16a45-104">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="16a45-105">デリゲート コンストラクションでは、引数リストとして 1 つの AddressOf 式のみが許可されます。</span><span class="sxs-lookup"><span data-stu-id="16a45-105">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="16a45-106">多くの場合、デリゲート コンストラクションの代わりに AddressOf 式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="16a45-106">Often an AddressOf expression can be used instead of a delegate construction.</span></span>

 <span data-ttu-id="16a45-107">デリゲート クラスのインスタンスを作成する `New` 句は、デリゲート コンストラクターに無効な引数リストを指定します。</span><span class="sxs-lookup"><span data-stu-id="16a45-107">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>

 <span data-ttu-id="16a45-108">新しいデリゲート インスタンスを作成するときは、1 つの `AddressOf` 式のみを指定できます。</span><span class="sxs-lookup"><span data-stu-id="16a45-108">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>

 <span data-ttu-id="16a45-109">このエラーは、デリゲート コンストラクターに引数を渡さない場合、複数の引数を渡した場合、または有効な `AddressOf` 式ではない 1 つの引数を渡した場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="16a45-109">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>

 <span data-ttu-id="16a45-110">**エラー ID:** BC32008</span><span class="sxs-lookup"><span data-stu-id="16a45-110">**Error ID:** BC32008</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="16a45-111">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="16a45-111">To correct this error</span></span>

- <span data-ttu-id="16a45-112">`New` 句で、デリゲート クラスの引数リストに含まれる 1 つの `AddressOf` 式を使用します。</span><span class="sxs-lookup"><span data-stu-id="16a45-112">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>

## <a name="see-also"></a><span data-ttu-id="16a45-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="16a45-113">See also</span></span>

- [<span data-ttu-id="16a45-114">New 演算子</span><span class="sxs-lookup"><span data-stu-id="16a45-114">New Operator</span></span>](../operators/new-operator.md)
- [<span data-ttu-id="16a45-115">AddressOf 演算子</span><span class="sxs-lookup"><span data-stu-id="16a45-115">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="16a45-116">デリゲート</span><span class="sxs-lookup"><span data-stu-id="16a45-116">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="16a45-117">方法: デリゲート メソッドを呼び出す</span><span class="sxs-lookup"><span data-stu-id="16a45-117">How to: Invoke a Delegate Method</span></span>](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
