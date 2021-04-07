---
title: '.NET 5 の破壊的変更: DataGridView 関連の API が InvalidOperationException をスローする'
description: .NET 5 での破壊的変更について学習します。オブジェクトの DataGridViewCellAccessibleObject.Owner 値が null の場合に、DataGridView に関連する一部の API で例外がスローされます。
ms.date: 09/18/2020
ms.openlocfilehash: 57ff50d7bdc83286d4d452746e8f64bace187edb
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/31/2021
ms.locfileid: "106079597"
---
# <a name="datagridview-related-apis-throw-invalidoperationexception"></a><span data-ttu-id="28d7d-103">DataGridView 関連の API が InvalidOperationException をスローする</span><span class="sxs-lookup"><span data-stu-id="28d7d-103">DataGridView-related APIs throw InvalidOperationException</span></span>

<span data-ttu-id="28d7d-104"><xref:System.Windows.Forms.DataGridView> に関連する API の一部で、オブジェクトの <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> 値が `null` の場合、<xref:System.InvalidOperationException> をスローするようになりました。</span><span class="sxs-lookup"><span data-stu-id="28d7d-104">Some APIs related to <xref:System.Windows.Forms.DataGridView> now throw an <xref:System.InvalidOperationException> if the object's <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> value is `null`.</span></span>

## <a name="change-description"></a><span data-ttu-id="28d7d-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="28d7d-105">Change description</span></span>

<span data-ttu-id="28d7d-106">以前のバージョンの .NET では、影響を受ける API からは、呼び出し時、<xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> プロパティ値が `null` であれば、<xref:System.NullReferenceException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="28d7d-106">In previous .NET versions, the affected APIs throw a <xref:System.NullReferenceException> when they are invoked and the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property value is `null`.</span></span> <span data-ttu-id="28d7d-107">.NET 5 以降、これらの API では、呼び出し時、<xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> プロパティ値が `null` の場合、<xref:System.NullReferenceException> ではなく <xref:System.InvalidOperationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="28d7d-107">Starting in .NET 5, these APIs throw an <xref:System.InvalidOperationException> instead of a <xref:System.NullReferenceException> if the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property value is `null` when they're invoked.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="28d7d-108">変更理由</span><span class="sxs-lookup"><span data-stu-id="28d7d-108">Reason for change</span></span>

<span data-ttu-id="28d7d-109"><xref:System.InvalidOperationException> をスローすることは、.NET ランタイムの動作に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="28d7d-109">Throwing an <xref:System.InvalidOperationException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="28d7d-110">また、無効なプロパティが明確に伝えられることでデバッグ作業が快適になります。</span><span class="sxs-lookup"><span data-stu-id="28d7d-110">It also improves the debugging experience by clearly communicating the invalid property.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="28d7d-111">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="28d7d-111">Version introduced</span></span>

<span data-ttu-id="28d7d-112">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="28d7d-112">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="28d7d-113">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="28d7d-113">Recommended action</span></span>

<span data-ttu-id="28d7d-114">コードを見直し、必要であれば、影響を受ける型の <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> プロパティを `null` として構築しないよう、コードを変更します。</span><span class="sxs-lookup"><span data-stu-id="28d7d-114">Review your code and, if necessary, update it to prevent constructing the affected types with the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property as `null`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="28d7d-115">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="28d7d-115">Affected APIs</span></span>

<span data-ttu-id="28d7d-116">影響を受ける API は、次の表のとおりです。</span><span class="sxs-lookup"><span data-stu-id="28d7d-116">The following table lists the affected APIs:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="28d7d-117">影響を受けるメソッドまたはプロパティ</span><span class="sxs-lookup"><span data-stu-id="28d7d-117">Affected method or property</span></span> | <span data-ttu-id="28d7d-118">妥当性が確認されたプロパティ</span><span class="sxs-lookup"><span data-stu-id="28d7d-118">Validated property</span></span> | <span data-ttu-id="28d7d-119">追加されたバージョン</span><span class="sxs-lookup"><span data-stu-id="28d7d-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.DataGridViewButtonCell.DataGridViewButtonCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="28d7d-120">5.0</span><span class="sxs-lookup"><span data-stu-id="28d7d-120">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="28d7d-121">5.0</span><span class="sxs-lookup"><span data-stu-id="28d7d-121">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.State?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="28d7d-122">5.0</span><span class="sxs-lookup"><span data-stu-id="28d7d-122">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="28d7d-123">5.0</span><span class="sxs-lookup"><span data-stu-id="28d7d-123">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Bounds?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="28d7d-124">5.0</span><span class="sxs-lookup"><span data-stu-id="28d7d-124">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="28d7d-125">5.0</span><span class="sxs-lookup"><span data-stu-id="28d7d-125">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Name?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="28d7d-126">5.0</span><span class="sxs-lookup"><span data-stu-id="28d7d-126">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Parent?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="28d7d-127">5.0</span><span class="sxs-lookup"><span data-stu-id="28d7d-127">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="28d7d-128">5.0</span><span class="sxs-lookup"><span data-stu-id="28d7d-128">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="28d7d-129">5.0</span><span class="sxs-lookup"><span data-stu-id="28d7d-129">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewImageCell.DataGridViewImageCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="28d7d-130">5.0</span><span class="sxs-lookup"><span data-stu-id="28d7d-130">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="28d7d-131">5.0</span><span class="sxs-lookup"><span data-stu-id="28d7d-131">5.0</span></span> |

## <a name="see-also"></a><span data-ttu-id="28d7d-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="28d7d-132">See also</span></span>

- [<span data-ttu-id="28d7d-133">DataGridView 関連の API が InvalidOperationException をスローする (.NET 6)</span><span class="sxs-lookup"><span data-stu-id="28d7d-133">DataGridView-related APIs throw InvalidOperationException (.NET 6)</span></span>](../6.0/null-owner-causes-invalidoperationexception.md)

<!--

### Affected APIs

- `M:System.Windows.Forms.DataGridViewButtonCell.DataGridViewButtonCellAccessibleObject.DoDefaultAction`
- `P:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DefaultAction`
- `P:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.State`
- `M:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DoDefaultAction`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Bounds`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DefaultAction`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Name`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Parent`
- `M:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DoDefaultAction`
- `M:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)`
- `M:System.Windows.Forms.DataGridViewImageCell.DataGridViewImageCellAccessibleObject.DoDefaultAction`
- `M:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject.DoDefaultAction`

### Category

Windows Forms

-->
