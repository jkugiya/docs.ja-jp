---
title: UI オートメーション Value コントロール パターンの実装
description: UI オートメーションで Value コントロール パターンを実装するためのガイドラインと規則を確認します。 IValueProvider インターフェイスに必要なメンバーを確認します。
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: b4fea39088064751ff559bd236554255d43ba2a2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265662"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a><span data-ttu-id="71ee1-104">UI オートメーション Value コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="71ee1-104">Implementing the UI Automation Value Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="71ee1-105">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="71ee1-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="71ee1-106">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="71ee1-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="71ee1-107">このトピックでは、イベントおよびプロパティに関する情報など、 <xref:System.Windows.Automation.Provider.IValueProvider>の実装のためのガイドラインと規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="71ee1-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IValueProvider>, including information on events and properties.</span></span> <span data-ttu-id="71ee1-108">その他のリファレンスへのリンクは、トピックの最後に記載します。</span><span class="sxs-lookup"><span data-stu-id="71ee1-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="71ee1-109"><xref:System.Windows.Automation.ValuePattern> コントロール パターンは、範囲にまたがることのない組み込み値を持つコントロールや、文字列として表すことができるコントロールをサポートするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="71ee1-109">The <xref:System.Windows.Automation.ValuePattern> control pattern is used to support controls that have an intrinsic value not spanning a range and that can be represented as a string.</span></span> <span data-ttu-id="71ee1-110">この文字列は、コントロールとその設定によっては、編集できます。</span><span class="sxs-lookup"><span data-stu-id="71ee1-110">This string can be editable, depending on the control and its settings.</span></span> <span data-ttu-id="71ee1-111">このパターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71ee1-111">For examples of controls that implement this pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="71ee1-112">実装のガイドラインと規則</span><span class="sxs-lookup"><span data-stu-id="71ee1-112">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="71ee1-113">Value コントロール パターンを実装する場合は、次のガイドラインと規則に留意してください。</span><span class="sxs-lookup"><span data-stu-id="71ee1-113">When implementing the Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="71ee1-114"><xref:System.Windows.Automation.ControlType.ListItem> や <xref:System.Windows.Automation.ControlType.TreeItem> などのコントロールは、コントロールの現在の編集モードに関係なく、いずれかの項目の値が編集可能である場合は、 <xref:System.Windows.Automation.ValuePattern> をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="71ee1-114">Controls such as <xref:System.Windows.Automation.ControlType.ListItem> and <xref:System.Windows.Automation.ControlType.TreeItem> must support <xref:System.Windows.Automation.ValuePattern> if the value of any of the items is editable, regardless of the current edit mode of the control.</span></span> <span data-ttu-id="71ee1-115">子項目が編集可能である場合は、親コントロールも <xref:System.Windows.Automation.ValuePattern> をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="71ee1-115">The parent control must also support <xref:System.Windows.Automation.ValuePattern> if the child items are editable.</span></span>  
  
 <span data-ttu-id="71ee1-116">![編集可能なリスト項目。](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")</span><span class="sxs-lookup"><span data-stu-id="71ee1-116">![Editable list item.](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")</span></span>  
<span data-ttu-id="71ee1-117">編集可能なリスト項目の例</span><span class="sxs-lookup"><span data-stu-id="71ee1-117">Example of an Editable List Item</span></span>  
  
- <span data-ttu-id="71ee1-118">単一行のエディット コントロールは、そのコンテンツへのプログラムによるアクセスをサポートするために、 <xref:System.Windows.Automation.Provider.IValueProvider>を実装します。</span><span class="sxs-lookup"><span data-stu-id="71ee1-118">Single-line edit controls support programmatic access to their contents by implementing <xref:System.Windows.Automation.Provider.IValueProvider>.</span></span> <span data-ttu-id="71ee1-119">一方、複数行のエディット コントロールは <xref:System.Windows.Automation.Provider.IValueProvider>を実装しません。代わりに <xref:System.Windows.Automation.Provider.ITextProvider>を実装して、そのコンテンツへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="71ee1-119">However, multi-line edit controls do not implement <xref:System.Windows.Automation.Provider.IValueProvider>; instead they provide access to their content by implementing <xref:System.Windows.Automation.Provider.ITextProvider>.</span></span>  
  
- <span data-ttu-id="71ee1-120">複数行の編集コントロールのテキスト コンテンツを取得するには、コントロールが <xref:System.Windows.Automation.Provider.ITextProvider>を実装していなければなりません。</span><span class="sxs-lookup"><span data-stu-id="71ee1-120">To retrieve the textual contents of a multi-line edit control, the control must implement <xref:System.Windows.Automation.Provider.ITextProvider>.</span></span> <span data-ttu-id="71ee1-121">ただし、 <xref:System.Windows.Automation.Provider.ITextProvider> はコントロールの値の設定はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="71ee1-121">However, <xref:System.Windows.Automation.Provider.ITextProvider> does not support setting the value of a control.</span></span>  
  
- <span data-ttu-id="71ee1-122"><xref:System.Windows.Automation.Provider.IValueProvider> は、書式設定情報や部分文字列の値の取得をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="71ee1-122"><xref:System.Windows.Automation.Provider.IValueProvider> does not support the retrieval of formatting information or substring values.</span></span> <span data-ttu-id="71ee1-123">このようなシナリオでは <xref:System.Windows.Automation.Provider.ITextProvider> を実装します。</span><span class="sxs-lookup"><span data-stu-id="71ee1-123">Implement <xref:System.Windows.Automation.Provider.ITextProvider> in these scenarios.</span></span>  
  
- <span data-ttu-id="71ee1-124"><xref:System.Windows.Automation.Provider.IValueProvider> を実装する必要があるコントロールの一例は、Microsoft Word の **カラー ピッカー** 選択コントロールです (以下を参照)。これは、色の値 (たとえば「黄」) と同等の内部 RGB 構造の間の文字列マッピングをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="71ee1-124"><xref:System.Windows.Automation.Provider.IValueProvider> must be implemented by controls such as the **Color Picker** selection control from Microsoft Word (illustrated below), which supports string mapping between a color value (for example, "yellow") and an equivalent internal RGB structure.</span></span>  
  
 <span data-ttu-id="71ee1-125">![黄色が強調表示されたカラー ピッカー。](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")</span><span class="sxs-lookup"><span data-stu-id="71ee1-125">![Color picker with yellow highlighted.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")</span></span>  
<span data-ttu-id="71ee1-126">色見本の文字列マッピング例</span><span class="sxs-lookup"><span data-stu-id="71ee1-126">Example of Color Swatch String Mapping</span></span>  
  
- <span data-ttu-id="71ee1-127"><xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> を呼び出せるようにするには、コントロールの `true` を <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> に設定し、 `false` を <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71ee1-127">A control should have its <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> set to `true` and its <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> set to `false` before allowing a call to <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>.</span></span>  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-ivalueprovider"></a><span data-ttu-id="71ee1-128">IValueProvider の必須メンバー</span><span class="sxs-lookup"><span data-stu-id="71ee1-128">Required Members for IValueProvider</span></span>  

 <span data-ttu-id="71ee1-129"><xref:System.Windows.Automation.Provider.IValueProvider>の実装には、次のプロパティとメソッドが必要です。</span><span class="sxs-lookup"><span data-stu-id="71ee1-129">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IValueProvider>.</span></span>  
  
|<span data-ttu-id="71ee1-130">必須メンバー</span><span class="sxs-lookup"><span data-stu-id="71ee1-130">Required members</span></span>|<span data-ttu-id="71ee1-131">メンバーの型</span><span class="sxs-lookup"><span data-stu-id="71ee1-131">Member type</span></span>|<span data-ttu-id="71ee1-132">メモ</span><span class="sxs-lookup"><span data-stu-id="71ee1-132">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|<span data-ttu-id="71ee1-133">プロパティ</span><span class="sxs-lookup"><span data-stu-id="71ee1-133">Property</span></span>|<span data-ttu-id="71ee1-134">なし</span><span class="sxs-lookup"><span data-stu-id="71ee1-134">None</span></span>|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|<span data-ttu-id="71ee1-135">プロパティ</span><span class="sxs-lookup"><span data-stu-id="71ee1-135">Property</span></span>|<span data-ttu-id="71ee1-136">なし</span><span class="sxs-lookup"><span data-stu-id="71ee1-136">None</span></span>|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|<span data-ttu-id="71ee1-137">方法</span><span class="sxs-lookup"><span data-stu-id="71ee1-137">Method</span></span>|<span data-ttu-id="71ee1-138">なし</span><span class="sxs-lookup"><span data-stu-id="71ee1-138">None</span></span>|  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="71ee1-139">例外</span><span class="sxs-lookup"><span data-stu-id="71ee1-139">Exceptions</span></span>  

 <span data-ttu-id="71ee1-140">プロバイダーは、次の例外をスローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="71ee1-140">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="71ee1-141">例外の種類</span><span class="sxs-lookup"><span data-stu-id="71ee1-141">Exception type</span></span>|<span data-ttu-id="71ee1-142">条件</span><span class="sxs-lookup"><span data-stu-id="71ee1-142">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> <span data-ttu-id="71ee1-143">-   ロケールに固有の情報が、誤った形式でコントロールに渡された場合 (誤った日付形式など)。</span><span class="sxs-lookup"><span data-stu-id="71ee1-143">-   If locale-specific information is passed to a control in an incorrect format such as an incorrectly formatted date.</span></span>|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> <span data-ttu-id="71ee1-144">-   新しい値を、文字列からコントロールが認識する形式に変換できない場合。</span><span class="sxs-lookup"><span data-stu-id="71ee1-144">-   If a new value cannot be converted from a string to a format the control recognizes.</span></span>|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> <span data-ttu-id="71ee1-145">-   有効になっていないコントロールの操作が試行された場合。</span><span class="sxs-lookup"><span data-stu-id="71ee1-145">-   When an attempt is made to manipulate a control that is not enabled.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71ee1-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="71ee1-146">See also</span></span>

- [<span data-ttu-id="71ee1-147">UI オートメーション コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="71ee1-147">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="71ee1-148">UI オートメーション プロバイダーでのコントロール パターンのサポート</span><span class="sxs-lookup"><span data-stu-id="71ee1-148">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="71ee1-149">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="71ee1-149">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="71ee1-150">ValuePattern 挿入テキストのサンプル</span><span class="sxs-lookup"><span data-stu-id="71ee1-150">ValuePattern Insert Text Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [<span data-ttu-id="71ee1-151">UI オートメーション ツリーの概要</span><span class="sxs-lookup"><span data-stu-id="71ee1-151">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="71ee1-152">UI オートメーションにおけるキャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="71ee1-152">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
