---
title: UI オートメーション要素のプロパティの取得
description: UI オートメーション要素の現在の、またはキャッシュされているプロパティを取得する方法について、手順と例をご覧ください。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: 34a42355acce0beafbb9658baf6032e4e7e19fcb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276426"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="8f8f2-103">UI オートメーション要素のプロパティの取得</span><span class="sxs-lookup"><span data-stu-id="8f8f2-103">Get UI Automation Element Properties</span></span>

> [!NOTE]
> <span data-ttu-id="8f8f2-104">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="8f8f2-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8f8f2-105">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8f8f2-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="8f8f2-106">このトピックでは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 要素のプロパティを取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8f8f2-106">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="8f8f2-107">現在のプロパティ値を取得する</span><span class="sxs-lookup"><span data-stu-id="8f8f2-107">Get a Current Property Value</span></span>  
  
1. <span data-ttu-id="8f8f2-108">取得するプロパティが含まれている <xref:System.Windows.Automation.AutomationElement> を取得します。</span><span class="sxs-lookup"><span data-stu-id="8f8f2-108">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2. <span data-ttu-id="8f8f2-109"><xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> を呼び出すか、<xref:System.Windows.Automation.AutomationElement.Current%2A> プロパティ構造体を取得し、そのメンバーの 1 つから値を取得します。</span><span class="sxs-lookup"><span data-stu-id="8f8f2-109">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="8f8f2-110">キャッシュされたプロパティ値を取得する</span><span class="sxs-lookup"><span data-stu-id="8f8f2-110">Get a Cached Property Value</span></span>  
  
1. <span data-ttu-id="8f8f2-111">取得するプロパティが含まれている <xref:System.Windows.Automation.AutomationElement> を取得します。</span><span class="sxs-lookup"><span data-stu-id="8f8f2-111">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="8f8f2-112">プロパティは、<xref:System.Windows.Automation.CacheRequest> で指定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8f8f2-112">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="8f8f2-113"><xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> を呼び出すか、<xref:System.Windows.Automation.AutomationElement.Cached%2A> プロパティ構造体を取得し、そのメンバーの 1 つから値を取得します。</span><span class="sxs-lookup"><span data-stu-id="8f8f2-113">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f8f2-114">例</span><span class="sxs-lookup"><span data-stu-id="8f8f2-114">Example</span></span>  

 <span data-ttu-id="8f8f2-115">次の例は、<xref:System.Windows.Automation.AutomationElement> の現在のプロパティを取得するさまざまな方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8f8f2-115">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="8f8f2-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f8f2-116">See also</span></span>

- [<span data-ttu-id="8f8f2-117">クライアントの UI オートメーション プロパティ</span><span class="sxs-lookup"><span data-stu-id="8f8f2-117">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="8f8f2-118">UI オートメーションにおけるキャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="8f8f2-118">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
- [<span data-ttu-id="8f8f2-119">UI オートメーション クライアントにおけるキャッシュ</span><span class="sxs-lookup"><span data-stu-id="8f8f2-119">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
