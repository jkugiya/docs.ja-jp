---
description: 詳細については <methodname> 、拡大変換せずに、これらの引数を指定して呼び出すことができるアクセス可能なオーバーロードされた ' ' はありません。 <list>
title: "上位変換しないで、これらの引数と共に呼び出せるオーバーロードされたアクセス可能な '<methodname>' はありません:  <list>"
ms.date: 07/20/2015
f1_keywords:
- vbrAmbiguousCall_WideningConversion2
ms.assetid: 5e74f5cf-80bd-4b48-b58a-465f981ec694
ms.openlocfilehash: 68e3ecf16aac19ef644b0060b49b2b316f72e22e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100479154"
---
# <a name="no-accessible-overloaded-methodname-can-be-called-with-these-arguments-without-a-widening-conversion-list"></a><span data-ttu-id="21d7b-103">上位変換しないで、これらの引数と共に呼び出せるオーバーロードされたアクセス可能な '\<methodname>' はありません: \<list></span><span class="sxs-lookup"><span data-stu-id="21d7b-103">No accessible overloaded '\<methodname>' can be called with these arguments without a widening conversion: \<list></span></span>

<span data-ttu-id="21d7b-104">オーバーロードされたメソッドが呼び出されましたが、拡大変換せずに指定された引数のリストと一致するメソッドはありませんでした。</span><span class="sxs-lookup"><span data-stu-id="21d7b-104">An overloaded method was called, but no method could be matched with the list of provided arguments without a widening conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="21d7b-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="21d7b-105">To correct this error</span></span>  
  
- <span data-ttu-id="21d7b-106">`Option Strict Off`を指定します。</span><span class="sxs-lookup"><span data-stu-id="21d7b-106">Specify `Option Strict Off`.</span></span>  
  
- <span data-ttu-id="21d7b-107">オーバーロードされたメソッドのシグネチャのいずれかと一致するように、引数を変更します。</span><span class="sxs-lookup"><span data-stu-id="21d7b-107">Change the arguments to match one of the signatures of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21d7b-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="21d7b-108">See also</span></span>

- [<span data-ttu-id="21d7b-109">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="21d7b-109">Widening and Narrowing Conversions</span></span>](../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="21d7b-110">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="21d7b-110">Option Strict Statement</span></span>](../language-reference/statements/option-strict-statement.md)
