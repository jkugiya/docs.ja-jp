---
title: UI オートメーションを使用してテキスト属性を取得する
description: UI オートメーションを使用してテキスト属性を取得する方法について説明します。 テキスト範囲からテキスト属性を取得するコード例を参照してください。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting, text attributes
- UI Automation, getting text attributes
- text attributes, getting
ms.assetid: fdefc6c3-b836-4cfe-8dec-1484bfdc5551
ms.openlocfilehash: 2c59c42e2ba6b67381ab9f70da51bd51ad4330c9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96282328"
---
# <a name="obtain-text-attributes-using-ui-automation"></a><span data-ttu-id="6a7bb-104">UI オートメーションを使用してテキスト属性を取得する</span><span class="sxs-lookup"><span data-stu-id="6a7bb-104">Obtain Text Attributes Using UI Automation</span></span>

> [!NOTE]
> <span data-ttu-id="6a7bb-105">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="6a7bb-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6a7bb-106">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6a7bb-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="6a7bb-107">このトピックでは、 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] を使用して、テキスト範囲からテキスト属性を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6a7bb-107">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attributes from a text range.</span></span> <span data-ttu-id="6a7bb-108">テキスト範囲は、ドキュメント内でのキャレット (^) の現在位置 (つまり低次元の選択範囲)、連続したテキストを選択したもの、個別に選択したテキストの集合、またはドキュメントに含まれるテキスト全体のいずれかに対応します。</span><span class="sxs-lookup"><span data-stu-id="6a7bb-108">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a7bb-109">例</span><span class="sxs-lookup"><span data-stu-id="6a7bb-109">Example</span></span>  

 <span data-ttu-id="6a7bb-110">次のコード例は、テキスト範囲から <xref:System.Windows.Automation.TextPattern.FontNameAttribute> を取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6a7bb-110">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#starttarget)]
 [!code-vb[UIATextPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#starttarget)]  
[!code-csharp[UIATextPattern_snip#GetTextElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#gettextelement)]
[!code-vb[UIATextPattern_snip#GetTextElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#gettextelement)]  
[!code-csharp[UIATextPattern_snip#FontName](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#fontname)]
[!code-vb[UIATextPattern_snip#FontName](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#fontname)]  
  
 <span data-ttu-id="6a7bb-111"><xref:System.Windows.Automation.TextPattern> コントロール パターンは <xref:System.Windows.Automation.Text.TextPatternRange> クラスと連携して、基本のテキスト属性、プロパティ、メソッドをサポートします。</span><span class="sxs-lookup"><span data-stu-id="6a7bb-111">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="6a7bb-112"><xref:System.Windows.Automation.TextPattern> または <xref:System.Windows.Automation.Text.TextPatternRange> によってサポートされないコントロール固有の機能の場合、 <xref:System.Windows.Automation.AutomationElement>クラスは対応するネイティブ オブジェクト モデルにアクセスするための UI オートメーション クライアントのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="6a7bb-112">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange> the <xref:System.Windows.Automation.AutomationElement>, class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a7bb-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="6a7bb-113">See also</span></span>

- [<span data-ttu-id="6a7bb-114">UI オートメーション TextPattern の概要</span><span class="sxs-lookup"><span data-stu-id="6a7bb-114">UI Automation TextPattern Overview</span></span>](ui-automation-textpattern-overview.md)
- [<span data-ttu-id="6a7bb-115">UI オートメーションを使用した、テキスト ボックスへのコンテンツの追加</span><span class="sxs-lookup"><span data-stu-id="6a7bb-115">Add Content to a Text Box Using UI Automation</span></span>](add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="6a7bb-116">UI オートメーションを使用した、テキストの検索と強調表示</span><span class="sxs-lookup"><span data-stu-id="6a7bb-116">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="6a7bb-117">UI オートメーション コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="6a7bb-117">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="6a7bb-118">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="6a7bb-118">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="6a7bb-119">UI オートメーションを使用して混合テキスト属性の詳細を取得する</span><span class="sxs-lookup"><span data-stu-id="6a7bb-119">Obtain Mixed Text Attribute Details Using UI Automation</span></span>](obtain-mixed-text-attribute-details-using-ui-automation.md)
