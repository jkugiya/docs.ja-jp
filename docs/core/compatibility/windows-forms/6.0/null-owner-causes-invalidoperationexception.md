---
title: '.NET 6 の破壊的変更: DataGridView 関連の API が InvalidOperationException をスローする'
description: .NET 6 での破壊的変更について学習します。オブジェクトの DataGridViewCellAccessibleObject.Owner 値が null の場合に、DataGridView に関連する一部の API で例外がスローされます。
ms.date: 03/29/2021
ms.openlocfilehash: 3726296bb93c88d438e45ea832bf9070ace69dd0
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/31/2021
ms.locfileid: "106080664"
---
# <a name="datagridview-related-apis-now-throw-invalidoperationexception"></a><span data-ttu-id="ec7c4-103">DataGridView 関連の API が InvalidOperationException をスローするようになった</span><span class="sxs-lookup"><span data-stu-id="ec7c4-103">DataGridView-related APIs now throw InvalidOperationException</span></span>

<span data-ttu-id="ec7c4-104"><xref:System.Windows.Forms.DataGridView> に関連する API の一部で、オブジェクトの <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> 値が `null` の場合、<xref:System.InvalidOperationException> をスローするようになりました。</span><span class="sxs-lookup"><span data-stu-id="ec7c4-104">Some APIs related to <xref:System.Windows.Forms.DataGridView> now throw an <xref:System.InvalidOperationException> if the object's <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> value is `null`.</span></span>

## <a name="change-description"></a><span data-ttu-id="ec7c4-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="ec7c4-105">Change description</span></span>

<span data-ttu-id="ec7c4-106">以前のバージョンの .NET では、影響を受ける API からは、呼び出し時、<xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> プロパティ値が `null` であれば、<xref:System.NullReferenceException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="ec7c4-106">In previous .NET versions, the affected APIs throw a <xref:System.NullReferenceException> when they are invoked and the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property value is `null`.</span></span> <span data-ttu-id="ec7c4-107">.NET 6 以降、これらの API では、呼び出し時、<xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> プロパティ値が `null` の場合、<xref:System.NullReferenceException> ではなく <xref:System.InvalidOperationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="ec7c4-107">Starting in .NET 6, these APIs throw an <xref:System.InvalidOperationException> instead of a <xref:System.NullReferenceException> if the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property value is `null` when they're invoked.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="ec7c4-108">変更理由</span><span class="sxs-lookup"><span data-stu-id="ec7c4-108">Reason for change</span></span>

<span data-ttu-id="ec7c4-109"><xref:System.InvalidOperationException> をスローすることは、.NET ランタイムの動作に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="ec7c4-109">Throwing an <xref:System.InvalidOperationException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="ec7c4-110">また、無効なプロパティが明確に伝えられることでデバッグ作業が快適になります。</span><span class="sxs-lookup"><span data-stu-id="ec7c4-110">It also improves the debugging experience by clearly communicating the invalid property.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="ec7c4-111">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="ec7c4-111">Version introduced</span></span>

<span data-ttu-id="ec7c4-112">.NET 6.0</span><span class="sxs-lookup"><span data-stu-id="ec7c4-112">.NET 6.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="ec7c4-113">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="ec7c4-113">Recommended action</span></span>

<span data-ttu-id="ec7c4-114">コードを見直し、必要であれば、影響を受ける型の <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> プロパティを `null` として構築しないよう、コードを変更します。</span><span class="sxs-lookup"><span data-stu-id="ec7c4-114">Review your code and, if necessary, update it to prevent constructing the affected types with the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property as `null`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="ec7c4-115">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="ec7c4-115">Affected APIs</span></span>

<span data-ttu-id="ec7c4-116">次の表に、影響を受けるプロパティとメソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="ec7c4-116">The following table lists the affected properties and methods:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="ec7c4-117">影響を受けるメソッドまたはプロパティ</span><span class="sxs-lookup"><span data-stu-id="ec7c4-117">Affected method or property</span></span> | <span data-ttu-id="ec7c4-118">追加されたバージョン</span><span class="sxs-lookup"><span data-stu-id="ec7c4-118">Version added</span></span> |
> |-|-|
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Bounds?displayProperty=fullName> | <span data-ttu-id="ec7c4-119">Preview 4</span><span class="sxs-lookup"><span data-stu-id="ec7c4-119">Preview 4</span></span> |
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.DefaultAction?displayProperty=fullName> | <span data-ttu-id="ec7c4-120">Preview 4</span><span class="sxs-lookup"><span data-stu-id="ec7c4-120">Preview 4</span></span> |
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Name?displayProperty=fullName> | <span data-ttu-id="ec7c4-121">Preview 4</span><span class="sxs-lookup"><span data-stu-id="ec7c4-121">Preview 4</span></span> |
>| <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)?displayProperty=fullName> | <span data-ttu-id="ec7c4-122">Preview 4</span><span class="sxs-lookup"><span data-stu-id="ec7c4-122">Preview 4</span></span> |
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.State?displayProperty=fullName> | <span data-ttu-id="ec7c4-123">Preview 4</span><span class="sxs-lookup"><span data-stu-id="ec7c4-123">Preview 4</span></span> |

## <a name="see-also"></a><span data-ttu-id="ec7c4-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec7c4-124">See also</span></span>

- [<span data-ttu-id="ec7c4-125">DataGridView 関連の API が InvalidOperationException をスローする (.NET 5)</span><span class="sxs-lookup"><span data-stu-id="ec7c4-125">DataGridView-related APIs throw InvalidOperationException (.NET 5)</span></span>](../5.0/null-owner-causes-invalidoperationexception.md)

<!--

### Affected APIs

- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Bounds`
- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.DefaultAction`
- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Name`
- `M:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)`
- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.State`

### Category

Windows Forms

-->
