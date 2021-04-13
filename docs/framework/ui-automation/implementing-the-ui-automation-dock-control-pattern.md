---
title: UI オートメーション Dock コントロール パターンの実装
description: UI オートメーション Dock コントロール パターンの実装について説明します。 コントロールのドッキング プロパティを公開するには、DockPattern コントロール パターンを使用します。 IDockProvider を実装します。
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
ms.openlocfilehash: 769808b190ade33ae52c53e03e1b4f77d4439df1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269627"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a><span data-ttu-id="b84d3-105">UI オートメーション Dock コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="b84d3-105">Implementing the UI Automation Dock Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="b84d3-106">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="b84d3-106">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b84d3-107">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b84d3-107">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="b84d3-108">ここでは、プロパティに関する情報など、 <xref:System.Windows.Automation.Provider.IDockProvider>を実装するガイドラインと規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="b84d3-108">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IDockProvider>, including information about properties.</span></span> <span data-ttu-id="b84d3-109">その他のリファレンスへのリンクは、トピックの最後に記載します。</span><span class="sxs-lookup"><span data-stu-id="b84d3-109">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="b84d3-110"><xref:System.Windows.Automation.DockPattern> コントロール パターンは、ドッキング コンテナー内のコントロールのドッキング プロパティを公開するために使用します。</span><span class="sxs-lookup"><span data-stu-id="b84d3-110">The <xref:System.Windows.Automation.DockPattern> control pattern is used to expose the dock properties of a control within a docking container.</span></span> <span data-ttu-id="b84d3-111">ドッキング コンテナーは、子要素を互いに水平方向または垂直方向に整列できるコントロールです。</span><span class="sxs-lookup"><span data-stu-id="b84d3-111">A docking container is a control that allows you to arrange child elements horizontally and vertically, relative to each other.</span></span> <span data-ttu-id="b84d3-112">このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b84d3-112">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
 <span data-ttu-id="b84d3-113">![ドッキングされた 2 つの子を持つドッキング コンテナー。](./media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span><span class="sxs-lookup"><span data-stu-id="b84d3-113">![Docking container with two docked children.](./media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span></span>  
<span data-ttu-id="b84d3-114">"Class View" ウィンドウが DockPosition.Right に "Error List" ウィンドウが DockPosition.Bottom にそれぞれ配置された Visual Studio のドッキングの例</span><span class="sxs-lookup"><span data-stu-id="b84d3-114">Docking Example from Visual Studio Where "Class View" Window Is DockPosition.Right and "Error List" Window Is DockPosition.Bottom</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="b84d3-115">実装のガイドラインと規則</span><span class="sxs-lookup"><span data-stu-id="b84d3-115">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="b84d3-116">Dock コントロール パターンを実装する場合は、次のガイドラインと規則に注意してください。</span><span class="sxs-lookup"><span data-stu-id="b84d3-116">When implementing the Dock control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="b84d3-117"><xref:System.Windows.Automation.Provider.IDockProvider> は、ドッキング コンテナーのプロパティや、ドッキング コンテナー内の現在のコントロールに隣接してドッキングされるコントロールのプロパティは公開しません。</span><span class="sxs-lookup"><span data-stu-id="b84d3-117"><xref:System.Windows.Automation.Provider.IDockProvider> does not expose any properties of the docking container or any properties of controls that are docked adjacent to the current control within the docking container.</span></span>  
  
- <span data-ttu-id="b84d3-118">コントロールは、現在の重ね順に基づき、互いを基準としてドッキングされます。重ね順が上位であるほど、指定されたドッキング コンテナーの端から離れた位置に配置されます。</span><span class="sxs-lookup"><span data-stu-id="b84d3-118">Controls are docked relative to each other based on their current z-order; the higher their z-order placement, the farther they are placed from the specified edge of the docking container.</span></span>  
  
- <span data-ttu-id="b84d3-119">ドッキング コンテナーのサイズを変更すると、コンテナー内にドッキングされているコントロールは、もともとドッキングされていたのと同じ端に合わせて再配置されます。</span><span class="sxs-lookup"><span data-stu-id="b84d3-119">If the docking container is resized, any docked controls within the container will be repositioned flush to the same edge to which they were originally docked.</span></span> <span data-ttu-id="b84d3-120">また、ドッキングされているコントロールは、 <xref:System.Windows.Automation.DockPosition>のドッキング動作に従って、コンテナー内のスペースを埋めるようにサイズ変更されます。</span><span class="sxs-lookup"><span data-stu-id="b84d3-120">The docked controls will also resize to fill any space within the container according to the docking behavior of their <xref:System.Windows.Automation.DockPosition>.</span></span> <span data-ttu-id="b84d3-121">たとえば、 <xref:System.Windows.Automation.DockPosition.Top> が指定されている場合は、コントロールの左側と右側が広がって、使用できるスペースを埋めます。</span><span class="sxs-lookup"><span data-stu-id="b84d3-121">For example, if <xref:System.Windows.Automation.DockPosition.Top> is specified, the left and right sides of the control will expand to fill any available space.</span></span> <span data-ttu-id="b84d3-122"><xref:System.Windows.Automation.DockPosition.Fill> が指定されている場合は、コントロールの 4 つの側面すべてが広がって、使用できるスペースを埋めます。</span><span class="sxs-lookup"><span data-stu-id="b84d3-122">If <xref:System.Windows.Automation.DockPosition.Fill> is specified, all four sides of the control will expand to fill any available space.</span></span>  
  
- <span data-ttu-id="b84d3-123">マルチモニター システムでは、コントロールは現在のモニターの左側または右側にドッキングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b84d3-123">On a multi-monitor system, controls should dock to the left or right side of the current monitor.</span></span> <span data-ttu-id="b84d3-124">それが不可能な場合は、左端のモニターの左側、または右端のモニターの右側にドッキングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b84d3-124">If that is not possible, they should dock to the left side of the leftmost monitor or the right side of the rightmost monitor.</span></span>  
  
<a name="Required_Members_for_IDockProvider"></a>

## <a name="required-members-for-idockprovider"></a><span data-ttu-id="b84d3-125">IDockProvider の必須メンバー</span><span class="sxs-lookup"><span data-stu-id="b84d3-125">Required Members for IDockProvider</span></span>  

 <span data-ttu-id="b84d3-126">次のプロパティとメソッドは、IDockProvider インターフェイスの実装時に必要です。</span><span class="sxs-lookup"><span data-stu-id="b84d3-126">The following properties and methods are required for implementing the IDockProvider interface.</span></span>  
  
|<span data-ttu-id="b84d3-127">必須メンバー</span><span class="sxs-lookup"><span data-stu-id="b84d3-127">Required members</span></span>|<span data-ttu-id="b84d3-128">メンバーの型</span><span class="sxs-lookup"><span data-stu-id="b84d3-128">Member type</span></span>|<span data-ttu-id="b84d3-129">メモ</span><span class="sxs-lookup"><span data-stu-id="b84d3-129">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|<span data-ttu-id="b84d3-130">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b84d3-130">Property</span></span>|<span data-ttu-id="b84d3-131">なし</span><span class="sxs-lookup"><span data-stu-id="b84d3-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|<span data-ttu-id="b84d3-132">方法</span><span class="sxs-lookup"><span data-stu-id="b84d3-132">Method</span></span>|<span data-ttu-id="b84d3-133">なし</span><span class="sxs-lookup"><span data-stu-id="b84d3-133">None</span></span>|  
  
 <span data-ttu-id="b84d3-134">このコントロール パターンには、関連するイベントがありません。</span><span class="sxs-lookup"><span data-stu-id="b84d3-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="b84d3-135">例外</span><span class="sxs-lookup"><span data-stu-id="b84d3-135">Exceptions</span></span>  

 <span data-ttu-id="b84d3-136">プロバイダーは、次の例外をスローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b84d3-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="b84d3-137">例外の種類</span><span class="sxs-lookup"><span data-stu-id="b84d3-137">Exception type</span></span>|<span data-ttu-id="b84d3-138">条件</span><span class="sxs-lookup"><span data-stu-id="b84d3-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> <span data-ttu-id="b84d3-139">-   要求されたドッキング スタイルをコントロールによって実行することができない場合。</span><span class="sxs-lookup"><span data-stu-id="b84d3-139">-   When a control is not able to execute the requested dock style.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b84d3-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="b84d3-140">See also</span></span>

- [<span data-ttu-id="b84d3-141">UI オートメーション コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="b84d3-141">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="b84d3-142">UI オートメーション プロバイダーでのコントロール パターンのサポート</span><span class="sxs-lookup"><span data-stu-id="b84d3-142">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="b84d3-143">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="b84d3-143">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="b84d3-144">UI オートメーション ツリーの概要</span><span class="sxs-lookup"><span data-stu-id="b84d3-144">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="b84d3-145">UI オートメーションにおけるキャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="b84d3-145">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
