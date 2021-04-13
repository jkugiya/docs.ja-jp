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
# <a name="add-content-to-a-text-box-using-ui-automation"></a>UI オートメーションを使用した、テキスト ボックスへのコンテンツの追加

> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックには、[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]を使用して単一行のテキスト ボックスにテキストを挿入する方法を示すコード例が含まれています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を適用できない複数行およびリッチ テキスト コントロールに対しては別の方法が用意されています。 比較のために、この例では、Win32 メソッドを使用して同じ結果を実現する方法も示しています。  
  
## <a name="example"></a>例  

 次の例では、対象アプリケーションのテキスト コントロールのシーケンスのステップを示します。 各テキスト コントロールでは、<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> メソッドを使用してそこから <xref:System.Windows.Automation.ValuePattern> オブジェクトを取得できるかどうかがテストされます。 テキスト コントロールで <xref:System.Windows.Automation.ValuePattern> がサポートされている場合は、<xref:System.Windows.Automation.ValuePattern.SetValue%2A> メソッドを使用して、ユーザー定義の文字列をテキスト コントロールに挿入します。 そうでない場合は、<xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> メソッドが使用されます。  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>関連項目

- [TextPattern 挿入テキストのサンプル](/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))
