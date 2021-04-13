---
title: UI オートメーションを使用した、テキスト ボックスへのコンテンツの追加
description: .NET で Microsoft UI オートメーションを使用して、コンテンツを単一行のテキスト ボックスに追加する方法の例をご覧ください。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: 9108cb586700474f7f855751000944212a3cef29
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235728"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a><span data-ttu-id="97c08-103">UI オートメーションを使用した、テキスト ボックスへのコンテンツの追加</span><span class="sxs-lookup"><span data-stu-id="97c08-103">Add Content to a Text Box Using UI Automation</span></span>

> [!NOTE]
> <span data-ttu-id="97c08-104">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="97c08-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="97c08-105">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="97c08-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="97c08-106">このトピックには、[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]を使用して単一行のテキスト ボックスにテキストを挿入する方法を示すコード例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="97c08-106">This topic contains example code that demonstrates how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to insert text into a single-line text box.</span></span> <span data-ttu-id="97c08-107">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を適用できない複数行およびリッチ テキスト コントロールに対しては別の方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="97c08-107">An alternate method is provided for multi-line and rich text controls where [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is not applicable.</span></span> <span data-ttu-id="97c08-108">比較のために、この例では、Win32 メソッドを使用して同じ結果を実現する方法も示しています。</span><span class="sxs-lookup"><span data-stu-id="97c08-108">For comparison purposes, the example also demonstrates how to use Win32 methods to accomplish the same results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97c08-109">例</span><span class="sxs-lookup"><span data-stu-id="97c08-109">Example</span></span>  

 <span data-ttu-id="97c08-110">次の例では、対象アプリケーションのテキスト コントロールのシーケンスのステップを示します。</span><span class="sxs-lookup"><span data-stu-id="97c08-110">The following example steps through a sequence of text controls in a target application.</span></span> <span data-ttu-id="97c08-111">各テキスト コントロールでは、<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> メソッドを使用してそこから <xref:System.Windows.Automation.ValuePattern> オブジェクトを取得できるかどうかがテストされます。</span><span class="sxs-lookup"><span data-stu-id="97c08-111">Each text control is tested to see if a <xref:System.Windows.Automation.ValuePattern> object can be obtained from it using the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method.</span></span> <span data-ttu-id="97c08-112">テキスト コントロールで <xref:System.Windows.Automation.ValuePattern> がサポートされている場合は、<xref:System.Windows.Automation.ValuePattern.SetValue%2A> メソッドを使用して、ユーザー定義の文字列をテキスト コントロールに挿入します。</span><span class="sxs-lookup"><span data-stu-id="97c08-112">If the text control does support <xref:System.Windows.Automation.ValuePattern>, the <xref:System.Windows.Automation.ValuePattern.SetValue%2A> method is used to insert a user-defined string into the text control.</span></span> <span data-ttu-id="97c08-113">そうでない場合は、<xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> メソッドが使用されます。</span><span class="sxs-lookup"><span data-stu-id="97c08-113">Otherwise, the <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> method is used.</span></span>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a><span data-ttu-id="97c08-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="97c08-114">See also</span></span>

- <span data-ttu-id="97c08-115">[TextPattern 挿入テキストのサンプル](/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="97c08-115">[TextPattern Insert Text Sample](/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span></span>
