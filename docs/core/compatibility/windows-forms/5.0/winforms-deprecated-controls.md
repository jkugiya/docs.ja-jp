---
title: 破壊的変更:削除されたステータス バー コントロール
description: .NET 5 での破壊的変更について学習します。一部の Windows フォーム コントロールは利用できなくなりました。
ms.date: 07/18/2020
ms.openlocfilehash: c93b16047896b263248858e807b74c547cfa6d9d
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256192"
---
# <a name="removed-status-bar-controls"></a><span data-ttu-id="b2190-103">削除されたステータス バー コントロール</span><span class="sxs-lookup"><span data-stu-id="b2190-103">Removed status bar controls</span></span>

<span data-ttu-id="b2190-104">.NET 5 より、一部の Windows フォーム コントロールが利用できません。</span><span class="sxs-lookup"><span data-stu-id="b2190-104">Starting in .NET 5, some Windows Forms controls are no longer available.</span></span>

## <a name="change-description"></a><span data-ttu-id="b2190-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="b2190-105">Change description</span></span>

<span data-ttu-id="b2190-106">.NET 5 以降では、Windows フォームのステータス バー関連のコントロールの一部が利用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="b2190-106">Starting with .NET 5, some of the status bar-related Windows Forms controls are no longer available.</span></span> <span data-ttu-id="b2190-107">デザインとサポートが改善された代替コントロールは .NET Framework 2.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="b2190-107">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="b2190-108">非推奨コントロールは前にデザイナー ツールボックスから削除されましたが、引き続き利用できました。</span><span class="sxs-lookup"><span data-stu-id="b2190-108">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span> <span data-ttu-id="b2190-109">現在は、完全に削除されています。</span><span class="sxs-lookup"><span data-stu-id="b2190-109">Now, they have been completely removed.</span></span>

<span data-ttu-id="b2190-110">次の型は現在なくなっています。</span><span class="sxs-lookup"><span data-stu-id="b2190-110">The following types are no longer available:</span></span>

* `StatusBar`
* `StatusBarDrawItemEventArgs`
* `StatusBarDrawItemEventHandler`
* `StatusBarPanel`
* `StatusBarPanelAutoSize`
* `StatusBarPanelBorderStyle`
* `StatusBarPanelClickEventArgs`
* `StatusBarPanelClickEventHandler`
* `StatusBarPanelStyle`

## <a name="version-introduced"></a><span data-ttu-id="b2190-111">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b2190-111">Version introduced</span></span>

<span data-ttu-id="b2190-112">5.0</span><span class="sxs-lookup"><span data-stu-id="b2190-112">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="b2190-113">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="b2190-113">Recommended action</span></span>

<span data-ttu-id="b2190-114">これらのコントロールに対する代わりの API とそのシナリオに移行します。</span><span class="sxs-lookup"><span data-stu-id="b2190-114">Move to the replacement APIs for these controls and their scenarios:</span></span>

| <span data-ttu-id="b2190-115">古いコントロール (API)</span><span class="sxs-lookup"><span data-stu-id="b2190-115">Old Control (API)</span></span> | <span data-ttu-id="b2190-116">推奨される代替機能</span><span class="sxs-lookup"><span data-stu-id="b2190-116">Recommended Replacement</span></span>                          |
|-------------------|--------------------------------------------------|
| <span data-ttu-id="b2190-117">StatusBar</span><span class="sxs-lookup"><span data-stu-id="b2190-117">StatusBar</span></span>         | <xref:System.Windows.Forms.StatusStrip>          |
| <span data-ttu-id="b2190-118">StatusBarPanel</span><span class="sxs-lookup"><span data-stu-id="b2190-118">StatusBarPanel</span></span>    | <xref:System.Windows.Forms.ToolStripStatusLabel> |

## <a name="affected-apis"></a><span data-ttu-id="b2190-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="b2190-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.StatusBar?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanel?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelAutoSize?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelBorderStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelStyle?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Windows.Forms.StatusBar`
- `T:System.Windows.Forms.StatusBarDrawItemEventArgs`
- `T:System.Windows.Forms.StatusBarDrawItemEventHandler`
- `T:System.Windows.Forms.StatusBarPanel`
- `T:System.Windows.Forms.StatusBarPanelAutoSize`
- `T:System.Windows.Forms.StatusBarPanelBorderStyle`
- `T:System.Windows.Forms.StatusBarPanelClickEventArgs`
- `T:System.Windows.Forms.StatusBarPanelClickEventHandler`
- `T:System.Windows.Forms.StatusBarPanelStyle`

### Category

Windows Forms

-->
