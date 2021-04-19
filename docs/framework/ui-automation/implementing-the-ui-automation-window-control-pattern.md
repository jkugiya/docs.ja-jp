---
title: UI オートメーション Window コントロール パターンの実装
description: UI オートメーションで Window コントロール パターンを実装するためのガイドラインと規則を確認します。 IWindowProvider インターフェイスに必要なメンバーを確認します。
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: b43884393974e6f2863da6a4a5ca8f305e5a160c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286098"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a><span data-ttu-id="2c2b8-104">UI オートメーション Window コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="2c2b8-104">Implementing the UI Automation Window Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="2c2b8-105">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="2c2b8-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2c2b8-106">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2c2b8-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="2c2b8-107">このトピックでは、 <xref:System.Windows.Automation.Provider.IWindowProvider>のプロパティ、メソッド、イベントに関する情報など、 <xref:System.Windows.Automation.WindowPattern> の実装のためのガイドラインと規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="2c2b8-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IWindowProvider>, including information about <xref:System.Windows.Automation.WindowPattern> properties, methods, and events.</span></span> <span data-ttu-id="2c2b8-108">その他のリファレンスへのリンクは、トピックの最後に記載します。</span><span class="sxs-lookup"><span data-stu-id="2c2b8-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="2c2b8-109"><xref:System.Windows.Automation.WindowPattern> コントロール パターンは、従来のグラフィカル ユーザー インターフェイス (GUI) 内で、ウィンドウベースの基本的な機能を提供するコントロールをサポートするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="2c2b8-109">The <xref:System.Windows.Automation.WindowPattern> control pattern is used to support controls that provide fundamental window-based functionality within a traditional graphical user interface (GUI).</span></span> <span data-ttu-id="2c2b8-110">このコントロール パターンを実装する必要があるコントロールの例として、最上位のアプリケーション ウィンドウ、マルチドキュメント インターフェイス (MDI) 子ウィンドウ、サイズ変更可能な分割ペイン コントロール、モーダル ダイアログ ボックス、バルーン ヘルプ ウィンドウがあります。</span><span class="sxs-lookup"><span data-stu-id="2c2b8-110">Examples of controls that must implement this control pattern include top-level application windows, multiple-document interface (MDI) child windows, resizable split pane controls, modal dialogs and balloon help windows.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="2c2b8-111">実装のガイドラインと規則</span><span class="sxs-lookup"><span data-stu-id="2c2b8-111">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="2c2b8-112">Window コントロール パターンを実装する場合は、次のガイドラインと規則に注意してください。</span><span class="sxs-lookup"><span data-stu-id="2c2b8-112">When implementing the Window control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="2c2b8-113">UI オートメーションを使用してウィンドウのサイズと位置の両方を変更する機能をサポートするには、コントロールが <xref:System.Windows.Automation.Provider.ITransformProvider> に加えて <xref:System.Windows.Automation.Provider.IWindowProvider>を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c2b8-113">To support the ability to modify both window size and screen position using UI Automation, a control must implement <xref:System.Windows.Automation.Provider.ITransformProvider> in addition to <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="2c2b8-114">コントロールを移動、サイズ変更、最大化、最小化、および閉じられるようにするタイトル バーの要素とタイトル バーを格納するコントロールは、通常 <xref:System.Windows.Automation.Provider.IWindowProvider>を実装することが求められます。</span><span class="sxs-lookup"><span data-stu-id="2c2b8-114">Controls that contain title bars and title bar elements that enable the control to be moved, resized, maximized, minimized, or closed are typically required to implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="2c2b8-115">ツールヒントのポップアップやコンボ ボックス、またはメニューのドロップダウンなどのコントロールは、通常 <xref:System.Windows.Automation.Provider.IWindowProvider>を実装しません。</span><span class="sxs-lookup"><span data-stu-id="2c2b8-115">Controls such as tooltip pop-ups and combo box or menu drop-downs do not typically implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="2c2b8-116">バルーン ヘルプ ウィンドウは、ウィンドウと同様の閉じるボタンを提供することで、基本的なツールヒント ポップアップから区別されます。</span><span class="sxs-lookup"><span data-stu-id="2c2b8-116">Balloon help windows are differentiated from basic tooltip pop-ups by the provision of a window-like Close button.</span></span>  
  
- <span data-ttu-id="2c2b8-117">全画面表示モードは、アプリケーション固有の機能であり、通常のウィンドウの動作ではないため、IWindowProvider によってサポートされません。</span><span class="sxs-lookup"><span data-stu-id="2c2b8-117">Full-screen mode is not supported by IWindowProvider as it is feature-specific to an application and is not typical window behavior.</span></span>  
  
<a name="Required_Members_for_IWindowProvider"></a>

## <a name="required-members-for-iwindowprovider"></a><span data-ttu-id="2c2b8-118">IWindowProvider の必須メンバー</span><span class="sxs-lookup"><span data-stu-id="2c2b8-118">Required Members for IWindowProvider</span></span>  

 <span data-ttu-id="2c2b8-119">IWindowProvider インターフェイスには、次のプロパティ、メソッド、イベントが必要です。</span><span class="sxs-lookup"><span data-stu-id="2c2b8-119">The following properties, methods, and events are required for the IWindowProvider interface.</span></span>  
  
|<span data-ttu-id="2c2b8-120">必須メンバー</span><span class="sxs-lookup"><span data-stu-id="2c2b8-120">Required member</span></span>|<span data-ttu-id="2c2b8-121">メンバーの型</span><span class="sxs-lookup"><span data-stu-id="2c2b8-121">Member type</span></span>|<span data-ttu-id="2c2b8-122">メモ</span><span class="sxs-lookup"><span data-stu-id="2c2b8-122">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|<span data-ttu-id="2c2b8-123">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2c2b8-123">Property</span></span>|<span data-ttu-id="2c2b8-124">なし</span><span class="sxs-lookup"><span data-stu-id="2c2b8-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|<span data-ttu-id="2c2b8-125">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2c2b8-125">Property</span></span>|<span data-ttu-id="2c2b8-126">なし</span><span class="sxs-lookup"><span data-stu-id="2c2b8-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|<span data-ttu-id="2c2b8-127">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2c2b8-127">Property</span></span>|<span data-ttu-id="2c2b8-128">なし</span><span class="sxs-lookup"><span data-stu-id="2c2b8-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|<span data-ttu-id="2c2b8-129">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2c2b8-129">Property</span></span>|<span data-ttu-id="2c2b8-130">なし</span><span class="sxs-lookup"><span data-stu-id="2c2b8-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|<span data-ttu-id="2c2b8-131">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2c2b8-131">Property</span></span>|<span data-ttu-id="2c2b8-132">なし</span><span class="sxs-lookup"><span data-stu-id="2c2b8-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|<span data-ttu-id="2c2b8-133">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2c2b8-133">Property</span></span>|<span data-ttu-id="2c2b8-134">なし</span><span class="sxs-lookup"><span data-stu-id="2c2b8-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|<span data-ttu-id="2c2b8-135">方法</span><span class="sxs-lookup"><span data-stu-id="2c2b8-135">Method</span></span>|<span data-ttu-id="2c2b8-136">なし</span><span class="sxs-lookup"><span data-stu-id="2c2b8-136">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|<span data-ttu-id="2c2b8-137">方法</span><span class="sxs-lookup"><span data-stu-id="2c2b8-137">Method</span></span>|<span data-ttu-id="2c2b8-138">なし</span><span class="sxs-lookup"><span data-stu-id="2c2b8-138">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|<span data-ttu-id="2c2b8-139">方法</span><span class="sxs-lookup"><span data-stu-id="2c2b8-139">Method</span></span>|<span data-ttu-id="2c2b8-140">なし</span><span class="sxs-lookup"><span data-stu-id="2c2b8-140">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|<span data-ttu-id="2c2b8-141">イベント</span><span class="sxs-lookup"><span data-stu-id="2c2b8-141">Event</span></span>|<span data-ttu-id="2c2b8-142">なし</span><span class="sxs-lookup"><span data-stu-id="2c2b8-142">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|<span data-ttu-id="2c2b8-143">イベント</span><span class="sxs-lookup"><span data-stu-id="2c2b8-143">Event</span></span>|<span data-ttu-id="2c2b8-144">なし</span><span class="sxs-lookup"><span data-stu-id="2c2b8-144">None</span></span>|  
|<xref:System.Windows.Automation.WindowInteractionState>|<span data-ttu-id="2c2b8-145">イベント</span><span class="sxs-lookup"><span data-stu-id="2c2b8-145">Event</span></span>|<span data-ttu-id="2c2b8-146"><xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span><span class="sxs-lookup"><span data-stu-id="2c2b8-146">Is not guaranteed to be <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span></span>|  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="2c2b8-147">例外</span><span class="sxs-lookup"><span data-stu-id="2c2b8-147">Exceptions</span></span>  

 <span data-ttu-id="2c2b8-148">プロバイダーは、次の例外をスローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c2b8-148">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="2c2b8-149">例外の種類</span><span class="sxs-lookup"><span data-stu-id="2c2b8-149">Exception type</span></span>|<span data-ttu-id="2c2b8-150">条件</span><span class="sxs-lookup"><span data-stu-id="2c2b8-150">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> <span data-ttu-id="2c2b8-151">-   要求された動作がコントロールによってサポートされない場合。</span><span class="sxs-lookup"><span data-stu-id="2c2b8-151">-   When a control does not support a requested behavior.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> <span data-ttu-id="2c2b8-152">-   パラメーターが有効な数値ではない場合。</span><span class="sxs-lookup"><span data-stu-id="2c2b8-152">-   When the parameter is not a valid number.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2c2b8-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c2b8-153">See also</span></span>

- [<span data-ttu-id="2c2b8-154">UI オートメーション コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="2c2b8-154">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="2c2b8-155">UI オートメーション プロバイダーでのコントロール パターンのサポート</span><span class="sxs-lookup"><span data-stu-id="2c2b8-155">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="2c2b8-156">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="2c2b8-156">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="2c2b8-157">UI オートメーション ツリーの概要</span><span class="sxs-lookup"><span data-stu-id="2c2b8-157">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="2c2b8-158">UI オートメーションにおけるキャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="2c2b8-158">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
