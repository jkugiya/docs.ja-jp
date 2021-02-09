---
description: "詳細情報: BC30663:属性 '<attributename>' を複数回適用することはできません。"
title: 属性 '<attributename>' を複数回適用することはできません。
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 84b77111a7401eb6f30eb7cd167f4b5689f33e77
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797147"
---
# <a name="bc30663-attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="58e97-103">BC30663:属性 '\<attributename>' を複数回適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="58e97-103">BC30663: Attribute '\<attributename>' cannot be applied multiple times</span></span>

<span data-ttu-id="58e97-104">属性は、1 回のみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="58e97-104">The attribute can only be applied once.</span></span> <span data-ttu-id="58e97-105">`AttributeUsage` 属性は、属性を複数回適用できるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="58e97-105">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>

 <span data-ttu-id="58e97-106">**エラー ID:** BC30663</span><span class="sxs-lookup"><span data-stu-id="58e97-106">**Error ID:** BC30663</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="58e97-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="58e97-107">To correct this error</span></span>

1. <span data-ttu-id="58e97-108">属性が 1 回だけ適用されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="58e97-108">Make sure the attribute is only applied once.</span></span>

2. <span data-ttu-id="58e97-109">開発したカスタム属性を使用する場合は、次の例のように、複数の属性の使用を許可するように `AttributeUsage` 属性を変更することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="58e97-109">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>

```vb
<AttributeUsage(AllowMultiple := True)>
```

## <a name="see-also"></a><span data-ttu-id="58e97-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="58e97-110">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="58e97-111">カスタム属性の作成</span><span class="sxs-lookup"><span data-stu-id="58e97-111">Creating Custom Attributes</span></span>](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="58e97-112">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="58e97-112">AttributeUsage</span></span>](../../programming-guide/concepts/attributes/attributeusage.md)
