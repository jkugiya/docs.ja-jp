---
description: 詳細については、「定義クラスのインスタンスではないオブジェクトでフレンド関数を呼び出すことはできません」を参照してください。
title: 定義クラスのインスタンスではないオブジェクトのフレンド関数は呼び出せません
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: 612a169cf976881b82cb0bb0c44ac6c6e7f91755
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100478699"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="099cb-103">定義クラスのインスタンスではないオブジェクトのフレンド関数は呼び出せません</span><span class="sxs-lookup"><span data-stu-id="099cb-103">Cannot call friend function on object which is not an instance of defining class</span></span>

<span data-ttu-id="099cb-104">クラスの `Friend` プロシージャを呼び出そうとするか、プロセス間またはスレッド間で `Friend` プロパティまたはメソッドにアクセスしようとしました。</span><span class="sxs-lookup"><span data-stu-id="099cb-104">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="099cb-105">`Friend` 手順はクラスの外部のモジュールから呼び出せますが、クラスが定義されているプロジェクトの一部です。</span><span class="sxs-lookup"><span data-stu-id="099cb-105">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="099cb-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="099cb-106">To correct this error</span></span>  
  
- <span data-ttu-id="099cb-107">クラスが定義されているプロジェクトの一部であるモジュールからプロシージャを呼び出しているか、またはアクセスしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="099cb-107">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="099cb-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="099cb-108">See also</span></span>

- [<span data-ttu-id="099cb-109">Friend</span><span class="sxs-lookup"><span data-stu-id="099cb-109">Friend</span></span>](../language-reference/modifiers/friend.md)
