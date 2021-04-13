---
title: サポートされている UI オートメーション コントロール パターンの取得
description: サポートされているコントロール パターン オブジェクトを UI オートメーション要素から取得する方法を示す例をご覧ください。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: 68abe272e91c40932aba5bcf99394c4a8f815c53
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276452"
---
# <a name="get-supported-ui-automation-control-patterns"></a><span data-ttu-id="436b9-103">サポートされている UI オートメーション コントロール パターンの取得</span><span class="sxs-lookup"><span data-stu-id="436b9-103">Get Supported UI Automation Control Patterns</span></span>

> [!NOTE]
> <span data-ttu-id="436b9-104">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="436b9-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="436b9-105">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="436b9-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="436b9-106">このトピックでは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 要素からコントロール パターン オブジェクトを取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="436b9-106">This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.</span></span>  
  
### <a name="obtain-all-control-patterns"></a><span data-ttu-id="436b9-107">すべてのコントロール パターンの取得</span><span class="sxs-lookup"><span data-stu-id="436b9-107">Obtain All Control Patterns</span></span>  
  
1. <span data-ttu-id="436b9-108">対象とするコントロール パターンを持つ <xref:System.Windows.Automation.AutomationElement> を取得します。</span><span class="sxs-lookup"><span data-stu-id="436b9-108">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="436b9-109">要素からすべてのコントロール パターンを取得するために、<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="436b9-109">Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="436b9-110">クライアントでは <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> を使用しないことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="436b9-110">It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span></span> <span data-ttu-id="436b9-111">このメソッドは内部で既存のコントロール パターンごとに <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> を呼び出すため、パフォーマンスに重大な影響を及ぼす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="436b9-111">Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern.</span></span> <span data-ttu-id="436b9-112">可能であれば、クライアントでは主なパターンに対して <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> を呼び出してください。</span><span class="sxs-lookup"><span data-stu-id="436b9-112">If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.</span></span>  
  
### <a name="obtain-a-specific-control-pattern"></a><span data-ttu-id="436b9-113">特定のコントロール パターンの取得</span><span class="sxs-lookup"><span data-stu-id="436b9-113">Obtain a Specific Control Pattern</span></span>  
  
1. <span data-ttu-id="436b9-114">対象とするコントロール パターンを持つ <xref:System.Windows.Automation.AutomationElement> を取得します。</span><span class="sxs-lookup"><span data-stu-id="436b9-114">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="436b9-115">特定のパターンを照会するために、<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> または <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="436b9-115">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern.</span></span> <span data-ttu-id="436b9-116">これらのメソッドは同様ですが、パターンが見つからない場合、<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> では例外が発生し、<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> では `false` が返されます。</span><span class="sxs-lookup"><span data-stu-id="436b9-116">These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="436b9-117">例</span><span class="sxs-lookup"><span data-stu-id="436b9-117">Example</span></span>  

 <span data-ttu-id="436b9-118">次の例では、リスト項目の <xref:System.Windows.Automation.AutomationElement> を検索し、その要素から <xref:System.Windows.Automation.SelectionItemPattern> を取得します。</span><span class="sxs-lookup"><span data-stu-id="436b9-118">The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.</span></span>  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="436b9-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="436b9-119">See also</span></span>

- [<span data-ttu-id="436b9-120">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="436b9-120">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
