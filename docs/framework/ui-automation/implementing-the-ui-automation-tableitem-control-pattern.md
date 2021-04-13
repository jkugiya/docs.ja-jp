---
title: UI オートメーション TableItem コントロール パターンの実装
description: UI オートメーションで TableItem コントロール パターンを実装するためのガイドラインと規則を確認します。 ITableItemProvider インターフェイスに必要なメンバーを確認します。
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 5e83f68772de3026fe8bcb265a11999e0b85a164
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265675"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="2608f-104">UI オートメーション TableItem コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="2608f-104">Implementing the UI Automation TableItem Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="2608f-105">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="2608f-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2608f-106">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2608f-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="2608f-107">このトピックでは、イベントおよびプロパティに関する情報など、 <xref:System.Windows.Automation.Provider.ITableItemProvider>の実装のためのガイドラインと規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="2608f-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="2608f-108">その他のリファレンスへのリンクは、概要の最後に記載します。</span><span class="sxs-lookup"><span data-stu-id="2608f-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="2608f-109"><xref:System.Windows.Automation.Provider.ITableProvider> を実装するコンテナーの子コントロールをサポートするために、<xref:System.Windows.Automation.TableItemPattern> コントロール パターンが使用されています。</span><span class="sxs-lookup"><span data-stu-id="2608f-109">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="2608f-110">個々のセル機能へのアクセスは、必要な <xref:System.Windows.Automation.Provider.IGridItemProvider> の同時実装によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="2608f-110">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="2608f-111">このコントロール パターンは <xref:System.Windows.Automation.Provider.IGridItemProvider> と同様です。異なる点は、<xref:System.Windows.Automation.Provider.ITableItemProvider> を実装するコントロールは、個々のセルとその行および列情報の間の関係をプログラムによって公開しなければならないことです。</span><span class="sxs-lookup"><span data-stu-id="2608f-111">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="2608f-112">このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2608f-112">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="2608f-113">実装のガイドラインと規則</span><span class="sxs-lookup"><span data-stu-id="2608f-113">Implementation Guidelines and Conventions</span></span>  
  
- <span data-ttu-id="2608f-114">関連するグリッド項目の機能については、「[UI オートメーション GridItem コントロール パターンの実装](implementing-the-ui-automation-griditem-control-pattern.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2608f-114">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>

## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="2608f-115">ITableItemProvider の必須メンバー</span><span class="sxs-lookup"><span data-stu-id="2608f-115">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="2608f-116">必須メンバー</span><span class="sxs-lookup"><span data-stu-id="2608f-116">Required member</span></span>|<span data-ttu-id="2608f-117">メンバーの型</span><span class="sxs-lookup"><span data-stu-id="2608f-117">Member type</span></span>|<span data-ttu-id="2608f-118">メモ</span><span class="sxs-lookup"><span data-stu-id="2608f-118">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="2608f-119">方法</span><span class="sxs-lookup"><span data-stu-id="2608f-119">Method</span></span>|<span data-ttu-id="2608f-120">なし</span><span class="sxs-lookup"><span data-stu-id="2608f-120">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="2608f-121">方法</span><span class="sxs-lookup"><span data-stu-id="2608f-121">Method</span></span>|<span data-ttu-id="2608f-122">なし</span><span class="sxs-lookup"><span data-stu-id="2608f-122">None</span></span>|  
  
 <span data-ttu-id="2608f-123">このコントロール パターンに関連付けられるプロパティやイベントはありません。</span><span class="sxs-lookup"><span data-stu-id="2608f-123">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="2608f-124">例外</span><span class="sxs-lookup"><span data-stu-id="2608f-124">Exceptions</span></span>  

 <span data-ttu-id="2608f-125">このコントロール パターンに関連付けられた例外はありません。</span><span class="sxs-lookup"><span data-stu-id="2608f-125">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2608f-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="2608f-126">See also</span></span>

- [<span data-ttu-id="2608f-127">UI オートメーション コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="2608f-127">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="2608f-128">UI オートメーション プロバイダーでのコントロール パターンのサポート</span><span class="sxs-lookup"><span data-stu-id="2608f-128">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="2608f-129">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="2608f-129">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="2608f-130">UI オートメーション Table コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="2608f-130">Implementing the UI Automation Table Control Pattern</span></span>](implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="2608f-131">UI オートメーション GridItem コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="2608f-131">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="2608f-132">UI オートメーション ツリーの概要</span><span class="sxs-lookup"><span data-stu-id="2608f-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="2608f-133">UI オートメーションにおけるキャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="2608f-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
