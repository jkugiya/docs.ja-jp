---
title: UI オートメーション フラグメント プロバイダーでのナビゲーションの有効化
description: フラグメント内の要素に対して UI オートメーション プロバイダーでのナビゲーションを有効にする方法を示す例をご覧ください。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
ms.openlocfilehash: d8fb67a84b7cba84fe65cd2f87baa6549122d2a2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276504"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a><span data-ttu-id="a8446-103">UI オートメーション フラグメント プロバイダーでのナビゲーションの有効化</span><span class="sxs-lookup"><span data-stu-id="a8446-103">Enable Navigation in a UI Automation Fragment Provider</span></span>

> [!NOTE]
> <span data-ttu-id="a8446-104">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="a8446-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a8446-105">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a8446-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="a8446-106">このトピックのコード例では、フラグメント内の要素に対して UI オートメーション プロバイダーでのナビゲーションを有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a8446-106">This topic contains example code that shows how to enable navigation in a UI Automation provider for an element that is within a fragment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8446-107">例</span><span class="sxs-lookup"><span data-stu-id="a8446-107">Example</span></span>  

 <span data-ttu-id="a8446-108">次のコード例では、リスト内のリスト項目に対して <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> を実装しています。</span><span class="sxs-lookup"><span data-stu-id="a8446-108">The following example code implements <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> for a list item within a list.</span></span> <span data-ttu-id="a8446-109">親要素はリスト ボックス要素で、兄弟要素はそのリスト コレクション内の他の項目です。</span><span class="sxs-lookup"><span data-stu-id="a8446-109">The parent element is the list box element, and the sibling elements are other items in the list collection.</span></span> <span data-ttu-id="a8446-110">このメソッドは正しくない方向の場合に `null` (Visual Basic では`Nothing` ) を返します。このケースでは、 <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> と <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>がこれに相当します (要素に子がないため)。</span><span class="sxs-lookup"><span data-stu-id="a8446-110">The method returns `null` (`Nothing` in Visual Basic) for directions that are not valid; in this case, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> and <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, because the element has no children.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="a8446-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8446-111">See also</span></span>

- [<span data-ttu-id="a8446-112">UI オートメーション プロバイダーの概要</span><span class="sxs-lookup"><span data-stu-id="a8446-112">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="a8446-113">サーバー側 UI オートメーション プロバイダーの実装</span><span class="sxs-lookup"><span data-stu-id="a8446-113">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
