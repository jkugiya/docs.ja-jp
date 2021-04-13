---
title: UI オートメーション GridItem コントロール パターンの実装
description: UI オートメーションでグリッド項目の GridItemPattern コントロール パターンを実装するためのガイドラインと規則について説明します。 IGridItemProvider の必須メンバーをご覧ください。
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: 30932e630c663aabb7d26302174785d44dc1c385
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267885"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="366d1-104">UI オートメーション GridItem コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="366d1-104">Implementing the UI Automation GridItem Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="366d1-105">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="366d1-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="366d1-106">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="366d1-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="366d1-107">ここでは、プロパティに関する情報など、 <xref:System.Windows.Automation.Provider.IGridItemProvider>を実装するガイドラインと規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="366d1-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="366d1-108">その他のリファレンスへのリンクは、概要の最後に記載します。</span><span class="sxs-lookup"><span data-stu-id="366d1-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="366d1-109"><xref:System.Windows.Automation.GridItemPattern> コントロール パターンは、<xref:System.Windows.Automation.Provider.IGridProvider> を実装するコンテナーの個々の子コントロールをサポートするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="366d1-109">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="366d1-110">このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="366d1-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="366d1-111">実装のガイドラインと規則</span><span class="sxs-lookup"><span data-stu-id="366d1-111">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="366d1-112"><xref:System.Windows.Automation.Provider.IGridProvider> を実装する場合は、次のガイドラインと規則に留意してください。</span><span class="sxs-lookup"><span data-stu-id="366d1-112">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="366d1-113">グリッドの座標は 0 から始まり、左上のセルの座標が (0, 0) です。</span><span class="sxs-lookup"><span data-stu-id="366d1-113">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="366d1-114">結合されたセルが報告する <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> および <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> プロパティは、UI オートメーション プロバイダーによって定義された、基になるアンカー セルに基づきます。</span><span class="sxs-lookup"><span data-stu-id="366d1-114">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="366d1-115">通常、これは、最上位の左端の行または列です。</span><span class="sxs-lookup"><span data-stu-id="366d1-115">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="366d1-116"><xref:System.Windows.Automation.Provider.IGridItemProvider> は、セルの結合や分割などのアクティブなグリッド操作を提供しません。</span><span class="sxs-lookup"><span data-stu-id="366d1-116"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="366d1-117"><xref:System.Windows.Automation.Provider.IGridItemProvider> を実装するコントロールは、一般にキーボードを使用して横断できます (つまり、UI オートメーション クライアントが隣接するコントロールに移動できます)。</span><span class="sxs-lookup"><span data-stu-id="366d1-117">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>

## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="366d1-118">IGridItemProvider の必須メンバー</span><span class="sxs-lookup"><span data-stu-id="366d1-118">Required Members for IGridItemProvider</span></span>  

 <span data-ttu-id="366d1-119"><xref:System.Windows.Automation.Provider.IGridItemProvider>の実装には、次のプロパティとメソッドが必要です。</span><span class="sxs-lookup"><span data-stu-id="366d1-119">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="366d1-120">必須メンバー</span><span class="sxs-lookup"><span data-stu-id="366d1-120">Required members</span></span>|<span data-ttu-id="366d1-121">メンバーの型</span><span class="sxs-lookup"><span data-stu-id="366d1-121">Member type</span></span>|<span data-ttu-id="366d1-122">メモ</span><span class="sxs-lookup"><span data-stu-id="366d1-122">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="366d1-123">プロパティ</span><span class="sxs-lookup"><span data-stu-id="366d1-123">Property</span></span>|<span data-ttu-id="366d1-124">なし</span><span class="sxs-lookup"><span data-stu-id="366d1-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="366d1-125">プロパティ</span><span class="sxs-lookup"><span data-stu-id="366d1-125">Property</span></span>|<span data-ttu-id="366d1-126">なし</span><span class="sxs-lookup"><span data-stu-id="366d1-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="366d1-127">プロパティ</span><span class="sxs-lookup"><span data-stu-id="366d1-127">Property</span></span>|<span data-ttu-id="366d1-128">なし</span><span class="sxs-lookup"><span data-stu-id="366d1-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="366d1-129">プロパティ</span><span class="sxs-lookup"><span data-stu-id="366d1-129">Property</span></span>|<span data-ttu-id="366d1-130">なし</span><span class="sxs-lookup"><span data-stu-id="366d1-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="366d1-131">プロパティ</span><span class="sxs-lookup"><span data-stu-id="366d1-131">Property</span></span>|<span data-ttu-id="366d1-132">なし</span><span class="sxs-lookup"><span data-stu-id="366d1-132">None</span></span>|  
  
 <span data-ttu-id="366d1-133">このコントロール パターンに関連するメソッドまたはイベントはありません。</span><span class="sxs-lookup"><span data-stu-id="366d1-133">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="366d1-134">例外</span><span class="sxs-lookup"><span data-stu-id="366d1-134">Exceptions</span></span>  

 <span data-ttu-id="366d1-135">このコントロール パターンに関連付けられた例外はありません。</span><span class="sxs-lookup"><span data-stu-id="366d1-135">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="366d1-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="366d1-136">See also</span></span>

- [<span data-ttu-id="366d1-137">UI オートメーション コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="366d1-137">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="366d1-138">UI オートメーション プロバイダーでのコントロール パターンのサポート</span><span class="sxs-lookup"><span data-stu-id="366d1-138">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="366d1-139">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="366d1-139">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="366d1-140">UI オートメーション Grid コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="366d1-140">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="366d1-141">UI オートメーション ツリーの概要</span><span class="sxs-lookup"><span data-stu-id="366d1-141">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="366d1-142">UI オートメーションにおけるキャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="366d1-142">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
