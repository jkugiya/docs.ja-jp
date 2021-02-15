---
description: 詳細については、次の情報を参照してください。 <methodname> 縮小変換しないで、これらの引数を指定して呼び出すことができるアクセス可能なオーバーロードされた ' <list>
title: 縮小変換しないで、これらの引数と共に呼び出せるオーバーロードされたアクセス可能な '<methodname>' はありません <list>
ms.date: 07/20/2015
f1_keywords:
- vbrAmbiguousCall2
ms.assetid: 13b20ffa-9f02-4971-a3cb-e08b402fd971
ms.openlocfilehash: a802b420a01c1894feca2c61c0bfdbb7be5104f5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475709"
---
# <a name="no-accessible-overloaded-methodname-can-be-called-with-these-arguments-without-a-narrowing-conversion-list"></a><span data-ttu-id="3c9ba-103">縮小変換しないで、これらの引数と共に呼び出せるオーバーロードされたアクセス可能な '\<methodname>' はありません\<list></span><span class="sxs-lookup"><span data-stu-id="3c9ba-103">No accessible overloaded '\<methodname>' can be called with these arguments without a narrowing conversion: \<list></span></span>

<span data-ttu-id="3c9ba-104">オーバーロードされたメソッドが呼び出されましたが、メソッドは縮小変換せずに指定された引数のリストと一致しません。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-104">An overloaded method was called, but the method cannot be matched with the list of provided arguments without a narrowing conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3c9ba-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="3c9ba-105">To correct this error</span></span>  
  
1. <span data-ttu-id="3c9ba-106">`Option Strict Off`を指定します。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-106">Specify `Option Strict Off`.</span></span>
  
2. <span data-ttu-id="3c9ba-107">オーバーロードされたメソッドのシグネチャと一致するように、引数を変更します。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-107">Change the arguments to match a signature of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c9ba-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c9ba-108">See also</span></span>

- [<span data-ttu-id="3c9ba-109">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="3c9ba-109">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="3c9ba-110">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="3c9ba-110">Widening and Narrowing Conversions</span></span>](../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
