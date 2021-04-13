---
title: UI オートメーションを使用した、テキストの検索と強調表示
description: UI オートメーションを使用して、テキストを検索および強調表示します。 例では、テキスト コントロールのコンテンツ内で文字列の各出現箇所を順次検索し、強調表示します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text, highlighting
- finding text
- text, finding
- UI automation, highlighting text
- UI automation, finding text
- highlighting text
ms.assetid: b77693f5-87bb-4b29-a297-05ff882e2044
ms.openlocfilehash: 7ae933bdf12c81e48371fa89ba5fc5cf5dd4731e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276465"
---
# <a name="find-and-highlight-text-using-ui-automation"></a>UI オートメーションを使用した、テキストの検索と強調表示

> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックでは、[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]を使用して、テキスト コントロールのコンテンツ内の文字列の各出現箇所を順次検索し、強調表示する方法を示します。  
  
## <a name="example"></a>例  

 次の例では、テキスト コントロールから <xref:System.Windows.Automation.TextPattern> オブジェクトを取得します。 その後、ドキュメント全体のテキスト コンテンツを表す <xref:System.Windows.Automation.Text.TextPatternRange> オブジェクトが、この <xref:System.Windows.Automation.TextPattern> の <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> プロパティを使用して作成されます。 その後、順次検索と強調表示の機能に対して、2 つの <xref:System.Windows.Automation.Text.TextPatternRange> オブジェクトが追加で作成されます。  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#SearchTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#searchtarget)]
[!code-vb[FindText#SearchTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#searchtarget)]  
  
## <a name="see-also"></a>関連項目

- [UI オートメーションを使用した、テキストの検索と強調表示](find-and-highlight-text-using-ui-automation.md)
