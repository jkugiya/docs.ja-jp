---
title: UI オートメーション Transform コントロール パターンの実装
description: UI オートメーションで Transform コントロール パターンを実装するためのガイドラインと規則を確認します。 ITransformProvider インターフェイスに必要なメンバーを確認します。
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
ms.openlocfilehash: fc47170a08ff08f6cd8f67996ef8fbf19c40f819
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265649"
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a><span data-ttu-id="33708-104">UI オートメーション Transform コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="33708-104">Implementing the UI Automation Transform Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="33708-105">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="33708-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="33708-106">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="33708-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="33708-107">このトピックでは、プロパティ、メソッド、イベントに関する情報など、 <xref:System.Windows.Automation.Provider.ITransformProvider>の実装のためのガイドラインと規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="33708-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITransformProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="33708-108">その他のリファレンスへのリンクは、トピックの最後に記載します。</span><span class="sxs-lookup"><span data-stu-id="33708-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="33708-109"><xref:System.Windows.Automation.TransformPattern> コントロール パターンは、2 次元空間で移動、サイズ変更、または回転できるコントロールをサポートするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="33708-109">The <xref:System.Windows.Automation.TransformPattern> control pattern is used to support controls that can be moved, resized, or rotated within a two-dimensional space.</span></span> <span data-ttu-id="33708-110">このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="33708-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="33708-111">実装のガイドラインと規則</span><span class="sxs-lookup"><span data-stu-id="33708-111">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="33708-112">Transform コントロール パターンを実装する場合は、次のガイドラインと規則にご留意ください。</span><span class="sxs-lookup"><span data-stu-id="33708-112">When implementing the Transform control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="33708-113">このコントロール パターンのサポートは、デスクトップ上のオブジェクトに制限されません。</span><span class="sxs-lookup"><span data-stu-id="33708-113">Support for this control pattern is not limited to objects on the desktop.</span></span> <span data-ttu-id="33708-114">コンテナーの境界内で子が自由に移動、サイズ変更、または回転できるようにする場合は、そのコンテナー オブジェクトの子もこのコントロール パターンをサポートしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="33708-114">This control pattern must also be supported by the children of a container object if the children can be moved, resized, or rotated freely within the boundaries of the container.</span></span>  
  
- <span data-ttu-id="33708-115">操作後の画面位置が完全にそのコンテナーの座標外となり、キーボードやマウスからアクセスできなくなる場合 (たとえば、トップレベルのウィンドウが画面外に移動したり、子オブジェクトがコンテナーのビューポートの境界外へ移動したりする場合) は、オブジェクトの移動、サイズ変更、および回転はできません。</span><span class="sxs-lookup"><span data-stu-id="33708-115">An object cannot be moved, resized, or rotated such that its resulting screen location would be completely outside the coordinates of its container and therefore inaccessible to the keyboard or mouse (for example, when a top-level window is moved off-screen or a child object is moved outside the boundaries of the container's viewport).</span></span> <span data-ttu-id="33708-116">このような場合、上辺または左辺の座標をコンテナーの境界内にオーバーライドして、要求された画面座標のできるだけ近くにオブジェクトが配置されます。</span><span class="sxs-lookup"><span data-stu-id="33708-116">In these cases, the object is placed as close to the requested screen coordinates as possible with the top or left coordinates overridden to be within the container boundaries.</span></span>  
  
- <span data-ttu-id="33708-117">マルチモニター システムでは、結合したデスクトップ画面座標の完全に外へオブジェクトを移動、サイズ変更、または回転した場合、プライマリ モニター上の、要求された画面座標のできるだけ近くにオブジェクトが配置されます。</span><span class="sxs-lookup"><span data-stu-id="33708-117">For multi-monitor systems, if an object is moved, resized, or rotated completely outside the combined desktop screen coordinates, the object is placed on the primary monitor as close to the requested coordinates as possible.</span></span>  
  
- <span data-ttu-id="33708-118">すべてのパラメーターとプロパティの値は絶対値で、ロケールには依存しません。</span><span class="sxs-lookup"><span data-stu-id="33708-118">All parameters and property values are absolute and independent of locale.</span></span>  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-itransformprovider"></a><span data-ttu-id="33708-119">ITransformProvider の必須メンバー</span><span class="sxs-lookup"><span data-stu-id="33708-119">Required Members for ITransformProvider</span></span>  

 <span data-ttu-id="33708-120"><xref:System.Windows.Automation.Provider.ITransformProvider>の実装には、次のプロパティとメソッドが必要です。</span><span class="sxs-lookup"><span data-stu-id="33708-120">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.ITransformProvider>.</span></span>  
  
|<span data-ttu-id="33708-121">必須メンバー</span><span class="sxs-lookup"><span data-stu-id="33708-121">Required members</span></span>|<span data-ttu-id="33708-122">メンバーの型</span><span class="sxs-lookup"><span data-stu-id="33708-122">Member type</span></span>|<span data-ttu-id="33708-123">メモ</span><span class="sxs-lookup"><span data-stu-id="33708-123">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|<span data-ttu-id="33708-124">プロパティ</span><span class="sxs-lookup"><span data-stu-id="33708-124">Property</span></span>|<span data-ttu-id="33708-125">なし</span><span class="sxs-lookup"><span data-stu-id="33708-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|<span data-ttu-id="33708-126">プロパティ</span><span class="sxs-lookup"><span data-stu-id="33708-126">Property</span></span>|<span data-ttu-id="33708-127">なし</span><span class="sxs-lookup"><span data-stu-id="33708-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|<span data-ttu-id="33708-128">プロパティ</span><span class="sxs-lookup"><span data-stu-id="33708-128">Property</span></span>|<span data-ttu-id="33708-129">なし</span><span class="sxs-lookup"><span data-stu-id="33708-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|<span data-ttu-id="33708-130">方法</span><span class="sxs-lookup"><span data-stu-id="33708-130">Method</span></span>|<span data-ttu-id="33708-131">なし</span><span class="sxs-lookup"><span data-stu-id="33708-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|<span data-ttu-id="33708-132">方法</span><span class="sxs-lookup"><span data-stu-id="33708-132">Method</span></span>|<span data-ttu-id="33708-133">なし</span><span class="sxs-lookup"><span data-stu-id="33708-133">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|<span data-ttu-id="33708-134">方法</span><span class="sxs-lookup"><span data-stu-id="33708-134">Method</span></span>|<span data-ttu-id="33708-135">なし</span><span class="sxs-lookup"><span data-stu-id="33708-135">None</span></span>|  
  
 <span data-ttu-id="33708-136">このコントロール パターンには、関連するイベントがありません。</span><span class="sxs-lookup"><span data-stu-id="33708-136">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="33708-137">例外</span><span class="sxs-lookup"><span data-stu-id="33708-137">Exceptions</span></span>  

 <span data-ttu-id="33708-138">プロバイダーは、次の例外をスローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="33708-138">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="33708-139">例外の種類</span><span class="sxs-lookup"><span data-stu-id="33708-139">Exception Type</span></span>|<span data-ttu-id="33708-140">条件</span><span class="sxs-lookup"><span data-stu-id="33708-140">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> <span data-ttu-id="33708-141">-   <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> が false の場合。</span><span class="sxs-lookup"><span data-stu-id="33708-141">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> is false.</span></span>|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> <span data-ttu-id="33708-142">-   <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> が false の場合。</span><span class="sxs-lookup"><span data-stu-id="33708-142">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> is false.</span></span>|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> <span data-ttu-id="33708-143">-   <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> が false の場合。</span><span class="sxs-lookup"><span data-stu-id="33708-143">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> is false.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="33708-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="33708-144">See also</span></span>

- [<span data-ttu-id="33708-145">UI オートメーション コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="33708-145">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="33708-146">UI オートメーション プロバイダーでのコントロール パターンのサポート</span><span class="sxs-lookup"><span data-stu-id="33708-146">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="33708-147">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="33708-147">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="33708-148">UI オートメーション ツリーの概要</span><span class="sxs-lookup"><span data-stu-id="33708-148">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="33708-149">UI オートメーションにおけるキャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="33708-149">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
