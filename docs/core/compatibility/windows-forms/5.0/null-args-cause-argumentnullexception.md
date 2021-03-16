---
title: 破壊的変更:WinForms メソッドで ArgumentNullException がスローされるようになった
description: .NET 5 での破壊的変更について学習します。一部の Windows フォーム メソッドで、null 引数に対して ArgumentNullException がスローされるようになりました。
ms.date: 09/18/2020
ms.openlocfilehash: 9d72f8e3320430396132de20c252cd5e8759dce3
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256100"
---
# <a name="winforms-methods-now-throw-argumentnullexception"></a><span data-ttu-id="ffdc6-103">WinForms メソッドで ArgumentNullException がスローされるようになった</span><span class="sxs-lookup"><span data-stu-id="ffdc6-103">WinForms methods now throw ArgumentNullException</span></span>

<span data-ttu-id="ffdc6-104">一部の Windows フォーム メソッドで、null 引数について <xref:System.ArgumentNullException> がスローされるようになりました。以前は <xref:System.NullReferenceException> がスローされていました。</span><span class="sxs-lookup"><span data-stu-id="ffdc6-104">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

## <a name="change-description"></a><span data-ttu-id="ffdc6-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="ffdc6-105">Change description</span></span>

<span data-ttu-id="ffdc6-106">以前は、null の引数が渡された場合、特定の Windows フォーム メソッドでは <xref:System.NullReferenceException> がスローされていました。</span><span class="sxs-lookup"><span data-stu-id="ffdc6-106">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="ffdc6-107">.NET 5 以降、これらのメソッドでは、null 引数に対して <xref:System.ArgumentNullException> が代わりにスローされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ffdc6-107">Starting in .NET 5, these methods now throw an <xref:System.ArgumentNullException> for null arguments, instead.</span></span>

<span data-ttu-id="ffdc6-108"><xref:System.ArgumentNullException> をスローすることは、.NET ランタイムの動作に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="ffdc6-108">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="ffdc6-109">また、引数が null であることと、どの引数がそうであるのかが明確に伝えられることで、デバッグ エクスペリエンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="ffdc6-109">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="ffdc6-110">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="ffdc6-110">Version introduced</span></span>

<span data-ttu-id="ffdc6-111">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="ffdc6-111">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="ffdc6-112">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="ffdc6-112">Recommended action</span></span>

<span data-ttu-id="ffdc6-113">これらのメソッドのいずれかを呼び出す場合、コードでは現在 null 引数について <xref:System.NullReferenceException> をキャッチする場合は、代わりに <xref:System.ArgumentNullException> をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="ffdc6-113">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="ffdc6-114">さらに、リストされているメソッドに null 引数が渡されないようにコードを更新することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="ffdc6-114">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="ffdc6-115">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="ffdc6-115">Affected APIs</span></span>

<span data-ttu-id="ffdc6-116">次の表では、影響を受けるメソッドとパラメーターを示します。</span><span class="sxs-lookup"><span data-stu-id="ffdc6-116">The following table lists the affected methods and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="ffdc6-117">メソッド</span><span class="sxs-lookup"><span data-stu-id="ffdc6-117">Method</span></span> | <span data-ttu-id="ffdc6-118">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="ffdc6-118">Parameter name</span></span> | <span data-ttu-id="ffdc6-119">追加されたバージョン</span><span class="sxs-lookup"><span data-stu-id="ffdc6-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)> | `owner` | <span data-ttu-id="ffdc6-120">Preview 1</span><span class="sxs-lookup"><span data-stu-id="ffdc6-120">Preview 1</span></span> |
> | <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType> | `item` | <span data-ttu-id="ffdc6-121">Preview 1</span><span class="sxs-lookup"><span data-stu-id="ffdc6-121">Preview 1</span></span> |
> | <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)> | `container` | <span data-ttu-id="ffdc6-122">Preview 1</span><span class="sxs-lookup"><span data-stu-id="ffdc6-122">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="ffdc6-123">Preview 1</span><span class="sxs-lookup"><span data-stu-id="ffdc6-123">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="ffdc6-124">Preview 1</span><span class="sxs-lookup"><span data-stu-id="ffdc6-124">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="ffdc6-125">Preview 1</span><span class="sxs-lookup"><span data-stu-id="ffdc6-125">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="ffdc6-126">Preview 1</span><span class="sxs-lookup"><span data-stu-id="ffdc6-126">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType> > | `e` | <span data-ttu-id="ffdc6-127">Preview 1</span><span class="sxs-lookup"><span data-stu-id="ffdc6-127">Preview 1</span></span> |
> | <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType> | `dataGridViewCellStyle` | <span data-ttu-id="ffdc6-128">Preview 2</span><span class="sxs-lookup"><span data-stu-id="ffdc6-128">Preview 2</span></span> |
> | <xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> | `data` | <span data-ttu-id="ffdc6-129">Preview 2</span><span class="sxs-lookup"><span data-stu-id="ffdc6-129">Preview 2</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="ffdc6-130">Preview 5</span><span class="sxs-lookup"><span data-stu-id="ffdc6-130">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="ffdc6-131">Preview 5</span><span class="sxs-lookup"><span data-stu-id="ffdc6-131">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListViewGroup.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | <span data-ttu-id="ffdc6-132">Preview 5</span><span class="sxs-lookup"><span data-stu-id="ffdc6-132">Preview 5</span></span> |
> | <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor(System.String,System.Int32,System.Int32)> | `className` | <span data-ttu-id="ffdc6-133">Preview 5</span><span class="sxs-lookup"><span data-stu-id="ffdc6-133">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="ffdc6-134">Preview 6</span><span class="sxs-lookup"><span data-stu-id="ffdc6-134">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Object[])> | <span data-ttu-id="ffdc6-135">`owner`, `value`</span><span class="sxs-lookup"><span data-stu-id="ffdc6-135">`owner`, `value`</span></span> | <span data-ttu-id="ffdc6-136">Preview 6</span><span class="sxs-lookup"><span data-stu-id="ffdc6-136">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)> | <span data-ttu-id="ffdc6-137">`owner`, `value`</span><span class="sxs-lookup"><span data-stu-id="ffdc6-137">`owner`, `value`</span></span> | <span data-ttu-id="ffdc6-138">Preview 6</span><span class="sxs-lookup"><span data-stu-id="ffdc6-138">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])?displayProperty=nameWithType> | `items` | <span data-ttu-id="ffdc6-139">Preview 6</span><span class="sxs-lookup"><span data-stu-id="ffdc6-139">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)?displayProperty=nameWithType> | `value` | <span data-ttu-id="ffdc6-140">Preview 6</span><span class="sxs-lookup"><span data-stu-id="ffdc6-140">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="ffdc6-141">Preview 6</span><span class="sxs-lookup"><span data-stu-id="ffdc6-141">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.System%23Collections%23ICollection%23CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="ffdc6-142">Preview 6</span><span class="sxs-lookup"><span data-stu-id="ffdc6-142">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListView.SelectedIndexCollection.%23ctor(System.Windows.Forms.ListView)> | `owner` | <span data-ttu-id="ffdc6-143">Preview 7</span><span class="sxs-lookup"><span data-stu-id="ffdc6-143">Preview 7</span></span> |
> | <xref:System.Windows.Forms.TreeNodeCollection.Find(System.String,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="ffdc6-144">`key` が `null` または空です</span><span class="sxs-lookup"><span data-stu-id="ffdc6-144">`key` is `null` or empty</span></span> | <span data-ttu-id="ffdc6-145">Preview 8</span><span class="sxs-lookup"><span data-stu-id="ffdc6-145">Preview 8</span></span> |
> | <xref:System.Windows.Forms.ListView.ListViewItemCollection.Find(System.String,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="ffdc6-146">`key` が `null` または空です</span><span class="sxs-lookup"><span data-stu-id="ffdc6-146">`key` is `null` or empty</span></span> | <span data-ttu-id="ffdc6-147">RC1</span><span class="sxs-lookup"><span data-stu-id="ffdc6-147">RC1</span></span> |
> | <xref:System.Windows.Forms.ScrollableControl.OnPaintBackground(System.Windows.Forms.PaintEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="ffdc6-148">RC1</span><span class="sxs-lookup"><span data-stu-id="ffdc6-148">RC1</span></span> |

<!--

### Affected APIs

- `M:System.Windows.Forms.Control.ControlCollection.#ctor(System.Windows.Forms.Control)`
- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.TableLayoutControlCollection.#ctor(System.Windows.Forms.TableLayoutPanel)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)`
- `M:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)`
- `M:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)`
- `M:System.Windows.Forms.ListViewGroup.System#Runtime#Serialization#ISerializable#GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)`
- `M:System.Windows.Forms.VisualStyles.VisualStyleRenderer.#ctor(System.String,System.Int32,System.Int32)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.#ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox,System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.System#Collections#ICollection#CopyTo(System.Array,System.Int32)`
- `M:System.Windows.Forms.ListView.SelectedIndexCollection.#ctor(System.Windows.Forms.ListView)`
- `M:System.Windows.Forms.TreeNodeCollection.Find(System.String,System.Boolean)`
- `M:System.Windows.Forms.ListView.ListViewItemCollection.Find(System.String,System.Boolean)`
- `M:System.Windows.Forms.ScrollableControl.OnPaintBackground(System.Windows.Forms.PaintEventArgs)`

### Category

Windows Forms

-->
