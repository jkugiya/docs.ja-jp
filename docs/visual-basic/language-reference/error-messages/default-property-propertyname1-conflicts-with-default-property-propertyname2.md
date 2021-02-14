---
description: "詳細情報: BC40007:既定プロパティ '<propertyname1>' は、'<propertyname2>' の既定プロパティ '<classname>' と競合しているため、'Shadows' と宣言できません"
title: 既定プロパティ '<propertyname1>' は、'<propertyname2>' の既定プロパティ '<classname>' と競合しているため、'Shadows' と宣言できません。
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 8ec7e36da18bbf8dda35e1a521d64268d14b7b26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796640"
---
# <a name="bc40007-default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a><span data-ttu-id="82ac1-103">BC40007:既定プロパティ '\<propertyname1>' は、'\<propertyname2>' の既定プロパティ '\<classname>' と競合しているため、'Shadows' と宣言できません。</span><span class="sxs-lookup"><span data-stu-id="82ac1-103">BC40007: Default property '\<propertyname1>' conflicts with default property '\<propertyname2>' in '\<classname>' and so should be declared 'Shadows'</span></span>

<span data-ttu-id="82ac1-104">プロパティが、基底クラスで定義されたプロパティと同じ名前で宣言されています。</span><span class="sxs-lookup"><span data-stu-id="82ac1-104">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="82ac1-105">この場合、このクラスのプロパティは、基底クラス プロパティをシャドウする必要があります。</span><span class="sxs-lookup"><span data-stu-id="82ac1-105">In this situation, the property in this class should shadow the base class property.</span></span>

 <span data-ttu-id="82ac1-106">このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="82ac1-106">This message is a warning.</span></span> <span data-ttu-id="82ac1-107">`Shadows` は、既定で指定されていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="82ac1-107">`Shadows` is assumed by default.</span></span> <span data-ttu-id="82ac1-108">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="82ac1-108">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="82ac1-109">**エラー ID:** BC40007</span><span class="sxs-lookup"><span data-stu-id="82ac1-109">**Error ID:** BC40007</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="82ac1-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="82ac1-110">To correct this error</span></span>

- <span data-ttu-id="82ac1-111">`Shadows` キーワードを宣言に追加するか、宣言されるプロパティの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="82ac1-111">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>

## <a name="see-also"></a><span data-ttu-id="82ac1-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="82ac1-112">See also</span></span>

- [<span data-ttu-id="82ac1-113">Shadows</span><span class="sxs-lookup"><span data-stu-id="82ac1-113">Shadows</span></span>](../modifiers/shadows.md)
- [<span data-ttu-id="82ac1-114">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="82ac1-114">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
