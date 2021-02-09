---
description: '詳細情報: BC30996:初期化子が必要です'
title: 初期化子が必要です
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: a9859dc319ec53cb42785d71b21447a097ce30f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796055"
---
# <a name="bc30996-initializer-expected"></a><span data-ttu-id="eee7e-103">BC30996:初期化子が必要です</span><span class="sxs-lookup"><span data-stu-id="eee7e-103">BC30996: Initializer expected</span></span>

<span data-ttu-id="eee7e-104">次の例に示すように、初期化リストが空のオブジェクト初期化子を使用して、クラスのインスタンスを宣言しようとしました。</span><span class="sxs-lookup"><span data-stu-id="eee7e-104">You have tried to declare an instance of a class by using an object initializer in which the initialization list is empty, as shown in the following example.</span></span>

 `' Not valid.`

 `' Dim aStudent As New Student With {}`

 <span data-ttu-id="eee7e-105">次の例に示すように、初期化子リストの少なくとも 1 つのフィールドまたはプロパティを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eee7e-105">At least one field or property must be initialized in the initializer list, as shown in the following example.</span></span>

 `Dim aStudent As New Student With {.year = "Senior"}`

 <span data-ttu-id="eee7e-106">**エラー ID:** BC30996</span><span class="sxs-lookup"><span data-stu-id="eee7e-106">**Error ID:** BC30996</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="eee7e-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="eee7e-107">To correct this error</span></span>

- <span data-ttu-id="eee7e-108">初期化子の少なくとも 1 つのフィールドまたはプロパティを初期化するか、オブジェクト初期化子を使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="eee7e-108">Initialize at least one field or property in the initializer, or do not use an object initializer.</span></span>

## <a name="see-also"></a><span data-ttu-id="eee7e-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="eee7e-109">See also</span></span>

- [<span data-ttu-id="eee7e-110">オブジェクト初期化子: 名前付きの型と匿名型</span><span class="sxs-lookup"><span data-stu-id="eee7e-110">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="eee7e-111">方法: オブジェクト初期化子を使用してオブジェクトを宣言する</span><span class="sxs-lookup"><span data-stu-id="eee7e-111">How to: Declare an Object by Using an Object Initializer</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
