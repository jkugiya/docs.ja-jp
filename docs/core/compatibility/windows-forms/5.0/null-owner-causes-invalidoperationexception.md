---
title: 破壊的変更:DataGridView 関連の API が InvalidOperationException をスローする
description: .NET 5 での破壊的変更について学習します。オブジェクトの DataGridViewCellAccessibleObject.Owner 値が null の場合に、DataGridView に関連する一部の API で例外がスローされます。
ms.date: 09/18/2020
ms.openlocfilehash: e49ce0ebecb5a9ab4ed7f0e0d70d994ab751bc58
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256115"
---
# <a name="datagridview-related-apis-now-throw-invalidoperationexception"></a><span data-ttu-id="6cf80-103">DataGridView 関連の API が InvalidOperationException をスローするようになった</span><span class="sxs-lookup"><span data-stu-id="6cf80-103">DataGridView-related APIs now throw InvalidOperationException</span></span>

<span data-ttu-id="6cf80-104"><xref:System.Windows.Forms.DataGridView> に関連する API の一部で、オブジェクトの <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> 値が `null` の場合、<xref:System.InvalidOperationException> をスローするようになりました。</span><span class="sxs-lookup"><span data-stu-id="6cf80-104">Some APIs related to <xref:System.Windows.Forms.DataGridView> now throw an <xref:System.InvalidOperationException> if the object's <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> value is `null`.</span></span>

## <a name="change-description"></a><span data-ttu-id="6cf80-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="6cf80-105">Change description</span></span>

<span data-ttu-id="6cf80-106">以前のバージョンの .NET では、影響を受ける API からは、呼び出し時、<xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> 値が <xref:System.NullReferenceException> であれば、`null` がスローされます。</span><span class="sxs-lookup"><span data-stu-id="6cf80-106">In previous .NET versions, the affected APIs throw a <xref:System.NullReferenceException> when they are invoked and the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> value is `null`.</span></span> <span data-ttu-id="6cf80-107">.NET 5 以降、これらの API では、呼び出し時、<xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> 値が `null` の場合、<xref:System.NullReferenceException> ではなく <xref:System.InvalidOperationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="6cf80-107">Starting in .NET 5, these APIs throw an <xref:System.InvalidOperationException> instead of a <xref:System.NullReferenceException> if the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> value is `null` when they are invoked.</span></span>

<span data-ttu-id="6cf80-108"><xref:System.InvalidOperationException> をスローすることは、.NET ランタイムの動作に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="6cf80-108">Throwing an <xref:System.InvalidOperationException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="6cf80-109">また、無効なプロパティが明確に伝えられることでデバッグ作業が快適になります。</span><span class="sxs-lookup"><span data-stu-id="6cf80-109">It also improves the debugging experience by clearly communicating the invalid property.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="6cf80-110">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="6cf80-110">Version introduced</span></span>

<span data-ttu-id="6cf80-111">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="6cf80-111">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="6cf80-112">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="6cf80-112">Recommended action</span></span>

<span data-ttu-id="6cf80-113">コードを見直し、必要であれば、影響を受ける型の <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> プロパティを `null` として構築しないよう、コードを変更します。</span><span class="sxs-lookup"><span data-stu-id="6cf80-113">Review your code and, if necessary, update it to prevent constructing the affected types with the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property as `null`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="6cf80-114">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="6cf80-114">Affected APIs</span></span>

<span data-ttu-id="6cf80-115">次の表に、影響を受けるプロパティとパラメーターの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="6cf80-115">The following table lists the affected properties and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="6cf80-116">影響を受けるメソッドまたはプロパティ</span><span class="sxs-lookup"><span data-stu-id="6cf80-116">Affected method or property</span></span> | <span data-ttu-id="6cf80-117">妥当性が確認されたプロパティ</span><span class="sxs-lookup"><span data-stu-id="6cf80-117">Validated property</span></span> | <span data-ttu-id="6cf80-118">追加されたバージョン</span><span class="sxs-lookup"><span data-stu-id="6cf80-118">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.DataGridViewButtonCell.DataGridViewButtonCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="6cf80-119">5.0</span><span class="sxs-lookup"><span data-stu-id="6cf80-119">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="6cf80-120">5.0</span><span class="sxs-lookup"><span data-stu-id="6cf80-120">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.State?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="6cf80-121">5.0</span><span class="sxs-lookup"><span data-stu-id="6cf80-121">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="6cf80-122">5.0</span><span class="sxs-lookup"><span data-stu-id="6cf80-122">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Bounds?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="6cf80-123">5.0</span><span class="sxs-lookup"><span data-stu-id="6cf80-123">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="6cf80-124">5.0</span><span class="sxs-lookup"><span data-stu-id="6cf80-124">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Name?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="6cf80-125">5.0</span><span class="sxs-lookup"><span data-stu-id="6cf80-125">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Parent?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="6cf80-126">5.0</span><span class="sxs-lookup"><span data-stu-id="6cf80-126">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="6cf80-127">5.0</span><span class="sxs-lookup"><span data-stu-id="6cf80-127">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="6cf80-128">5.0</span><span class="sxs-lookup"><span data-stu-id="6cf80-128">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewImageCell.DataGridViewImageCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="6cf80-129">5.0</span><span class="sxs-lookup"><span data-stu-id="6cf80-129">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="6cf80-130">5.0</span><span class="sxs-lookup"><span data-stu-id="6cf80-130">5.0</span></span> |

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
