---
description: '詳細情報: 引数に Nothing を指定することはできません'
title: 引数には Nothing を使用できません
ms.date: 07/20/2015
f1_keywords:
- vbrGeneral_ArgumentNullException
ms.assetid: 2abd995b-36a5-45f0-b3c1-6e0c3b31a875
ms.openlocfilehash: 7a35d464b9e8cdbcfd0ee98a538eff653dca346c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472333"
---
# <a name="argument-cannot-be-nothing"></a><span data-ttu-id="3f8cf-103">引数には Nothing を使用できません</span><span class="sxs-lookup"><span data-stu-id="3f8cf-103">Argument cannot be Nothing</span></span>

<span data-ttu-id="3f8cf-104">値が必要な引数に null 値を指定しました。</span><span class="sxs-lookup"><span data-stu-id="3f8cf-104">A null value has been supplied for an argument that must have a value.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3f8cf-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="3f8cf-105">To correct this error</span></span>  
  
- <span data-ttu-id="3f8cf-106">オブジェクトのインスタンスを作成していない状態で、オブジェクトの使用を試みた可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3f8cf-106">You might have tried to use an object without providing an instance of the object.</span></span> <span data-ttu-id="3f8cf-107">そのような場合は、 `New` キーワードを使用してインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3f8cf-107">In such a case, use the `New` keyword to create the instance.</span></span>  
  
- <span data-ttu-id="3f8cf-108">値が正しく計算されることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3f8cf-108">Check that the value is calculated correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f8cf-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f8cf-109">See also</span></span>

- <xref:System.NullReferenceException>
