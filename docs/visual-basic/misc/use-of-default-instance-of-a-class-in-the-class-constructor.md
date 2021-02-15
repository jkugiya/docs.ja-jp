---
description: '詳細情報: クラスコンストラクターでクラスの既定のインスタンスを使用すると、無限の再帰呼び出しが発生する可能性がある'
title: クラス コンストラクター内のクラスの既定のインスタンスを使用すると、無限の再帰呼び出しを引き起こす能性があります。
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: f65956c92f7d391aa77734d7afd5adf3bea1f906
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475683"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="62406-103">クラス コンストラクター内のクラスの既定のインスタンスを使用すると、無限の再帰呼び出しを引き起こす能性があります。</span><span class="sxs-lookup"><span data-stu-id="62406-103">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>

<span data-ttu-id="62406-104">クラスの既定のインスタンスは、クラス コンストラクターで使用されています。</span><span class="sxs-lookup"><span data-stu-id="62406-104">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="62406-105">これは、無限ループとも呼ばれる、無限の再帰呼び出しを引き起こす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="62406-105">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="62406-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="62406-106">To correct this error</span></span>  
  
- <span data-ttu-id="62406-107">クラス コンストラクターから、既定のインスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="62406-107">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62406-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="62406-108">See also</span></span>

- [<span data-ttu-id="62406-109">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="62406-109">Constructors</span></span>](../programming-guide/concepts/object-oriented-programming.md#constructors)
