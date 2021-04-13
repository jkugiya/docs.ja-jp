---
title: プロパティ条件に基づく UI オートメーション要素の検索
description: プロパティ条件に基づいて UI オートメーション要素を検索します。 1 つまたは複数の特定のプロパティに基づいて、UI オートメーション ツリー内の要素を特定します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
ms.openlocfilehash: 603ecf5375af919a558168e14792035a16fb20f2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276491"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="fe329-104">プロパティ条件に基づく UI オートメーション要素の検索</span><span class="sxs-lookup"><span data-stu-id="fe329-104">Find a UI Automation Element Based on a Property Condition</span></span>

> [!NOTE]
> <span data-ttu-id="fe329-105">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="fe329-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="fe329-106">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fe329-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="fe329-107">このトピックには、1 つまたは複数の特定のプロパティに基づいて [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー内の要素を特定する方法を示すコード例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fe329-107">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe329-108">例</span><span class="sxs-lookup"><span data-stu-id="fe329-108">Example</span></span>  

 <span data-ttu-id="fe329-109">次の例では、一連のプロパティ条件を指定しています。これにより、<xref:System.Windows.Automation.AutomationElement> ツリー内の対象となる 1 つの特定の要素 (または複数の要素) を識別します。</span><span class="sxs-lookup"><span data-stu-id="fe329-109">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="fe329-110">次に、一致する要素の数を制限する一連の <xref:System.Windows.Automation.AndCondition> ブール演算を組み込んだ <xref:System.Windows.Automation.AutomationElement.FindAll%2A> メソッドを使用して、一致するすべての要素の検索が実行されます。</span><span class="sxs-lookup"><span data-stu-id="fe329-110">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe329-111"><xref:System.Windows.Automation.AutomationElement.RootElement%2A> から検索する場合は、直接の子のみを取得するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="fe329-111">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="fe329-112">子孫を検索すると、数百または数千もの要素が反復処理される場合があり、スタック オーバーフローを引き起こす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fe329-112">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="fe329-113">下位レベルの特定の要素を取得しようとする場合、アプリケーション ウィンドウから、または下位レベルのコンテナーから検索を開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe329-113">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="fe329-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe329-114">See also</span></span>

- <span data-ttu-id="fe329-115">[InvokePattern および ExpandCollapsePattern メニュー項目のサンプル](/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="fe329-115">[InvokePattern and ExpandCollapsePattern Menu Item Sample](/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span></span>
- [<span data-ttu-id="fe329-116">UI オートメーション要素の取得</span><span class="sxs-lookup"><span data-stu-id="fe329-116">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
- [<span data-ttu-id="fe329-117">AutomationID プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="fe329-117">Use the AutomationID Property</span></span>](use-the-automationid-property.md)
