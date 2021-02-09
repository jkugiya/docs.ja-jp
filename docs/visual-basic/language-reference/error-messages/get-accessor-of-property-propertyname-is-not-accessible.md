---
description: "詳細情報: BC31103:プロパティ '<propertyname>' の 'Get' アクセサーにアクセスできません。"
title: プロパティ '<propertyname>' の 'Get' アクセサーにアクセスできません。
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 3517bc7ec512ec99909539eb4d7cf3fafe9016fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796133"
---
# <a name="bc31103-get-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="5e28f-103">BC31103:プロパティ '\<propertyname>' の 'Get' アクセサーにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="5e28f-103">BC31103: 'Get' accessor of property '\<propertyname>' is not accessible</span></span>

<span data-ttu-id="5e28f-104">ステートメントは、プロパティの `Get` プロシージャにアクセスできない場合に、プロパティの値を取得しようとします。</span><span class="sxs-lookup"><span data-stu-id="5e28f-104">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>

 <span data-ttu-id="5e28f-105">[Get ステートメント](../statements/get-statement.md)がその [Property ステートメント](../statements/property-statement.md)よりも制限の厳しいアクセス レベルでマークされている場合は、プロパティ値を読み取ろうとすると、次のような場合は失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5e28f-105">If the [Get Statement](../statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>

- <span data-ttu-id="5e28f-106">`Get` ステートメントが [Private](../modifiers/private.md) とマークされていて、呼び出し元のコードが、プロパティが定義されているクラスまたは構造体の外側にある。</span><span class="sxs-lookup"><span data-stu-id="5e28f-106">The `Get` statement is marked [Private](../modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>

- <span data-ttu-id="5e28f-107">`Get` ステートメントが [Protected](../modifiers/protected.md) とマークされていて、呼び出し元のコードが、プロパティが定義されているクラスまたは構造体内にも、派生クラス内にもない。</span><span class="sxs-lookup"><span data-stu-id="5e28f-107">The `Get` statement is marked [Protected](../modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>

- <span data-ttu-id="5e28f-108">`Get` ステートメントが [Friend](../modifiers/friend.md) とマークされていて、呼び出し元のコードが、プロパティが定義されているアセンブリと同じアセンブリ内にない。</span><span class="sxs-lookup"><span data-stu-id="5e28f-108">The `Get` statement is marked [Friend](../modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>

 <span data-ttu-id="5e28f-109">**エラー ID:** BC31103</span><span class="sxs-lookup"><span data-stu-id="5e28f-109">**Error ID:** BC31103</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="5e28f-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="5e28f-110">To correct this error</span></span>

- <span data-ttu-id="5e28f-111">プロパティを定義するソース コードを制御できる場合は、プロパティ自体と同じアクセス レベルで `Get` プロシージャを宣言することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="5e28f-111">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>

- <span data-ttu-id="5e28f-112">プロパティを定義するソース コードを制御できない場合、またはプロパティ自体よりも `Get` プロシージャのアクセス レベルを制限する必要がある場合は、プロパティ値を読み取るステートメントを、プロパティによりアクセスしやすいコードの領域に移動してみてください。</span><span class="sxs-lookup"><span data-stu-id="5e28f-112">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e28f-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e28f-113">See also</span></span>

- [<span data-ttu-id="5e28f-114">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="5e28f-114">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="5e28f-115">方法: 複数のアクセス レベルを持つプロパティを宣言する</span><span class="sxs-lookup"><span data-stu-id="5e28f-115">How to: Declare a Property with Mixed Access Levels</span></span>](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
