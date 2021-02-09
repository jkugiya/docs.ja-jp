---
description: '詳細情報: Property Let プロシージャが定義されておらず、Property Get プロシージャからオブジェクトが返されませんでした。'
title: Property Let プロシージャが定義されておらず、Property Get プロシージャからオブジェクトが返されませんでした。
ms.date: 07/20/2015
f1_keywords:
- vbrID451
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
ms.openlocfilehash: 8376a30abb476abb1d45973e36eb086cadad0054
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795366"
---
# <a name="property-let-procedure-not-defined-and-property-get-procedure-did-not-return-an-object"></a><span data-ttu-id="ebbb9-103">Property Let プロシージャが定義されておらず、Property Get プロシージャからオブジェクトが返されませんでした。</span><span class="sxs-lookup"><span data-stu-id="ebbb9-103">Property let procedure not defined and property get procedure did not return an object</span></span>

<span data-ttu-id="ebbb9-104">特定のプロパティ、メソッド、および操作は、`Collection` オブジェクトにのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="ebbb9-104">Certain properties, methods, and operations can only apply to `Collection` objects.</span></span> <span data-ttu-id="ebbb9-105">コレクション専用の操作またはプロパティを指定しましたが、このオブジェクトはコレクションではありません。</span><span class="sxs-lookup"><span data-stu-id="ebbb9-105">You specified an operation or property that is exclusive to collections, but the object is not a collection.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ebbb9-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="ebbb9-106">To correct this error</span></span>  
  
1. <span data-ttu-id="ebbb9-107">オブジェクトまたはプロパティ名のスペルを確認するか、オブジェクトが `Collection` オブジェクトであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ebbb9-107">Check the spelling of the object or property name, or verify that the object is a `Collection` object.</span></span>  
  
2. <span data-ttu-id="ebbb9-108">オブジェクトをコレクションに追加するために使用する `Add` メソッドを確認して、構文が正しいことと、識別子のスペルが正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ebbb9-108">Look at the `Add` method used to add the object to the collection to be sure the syntax is correct and that any identifiers were spelled correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebbb9-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="ebbb9-109">See also</span></span>

- <xref:Microsoft.VisualBasic.Collection>
