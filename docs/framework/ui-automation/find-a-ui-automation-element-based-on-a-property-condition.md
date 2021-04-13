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
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a>プロパティ条件に基づく UI オートメーション要素の検索

> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックには、1 つまたは複数の特定のプロパティに基づいて [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー内の要素を特定する方法を示すコード例が含まれています。  
  
## <a name="example"></a>例  

 次の例では、一連のプロパティ条件を指定しています。これにより、<xref:System.Windows.Automation.AutomationElement> ツリー内の対象となる 1 つの特定の要素 (または複数の要素) を識別します。 次に、一致する要素の数を制限する一連の <xref:System.Windows.Automation.AndCondition> ブール演算を組み込んだ <xref:System.Windows.Automation.AutomationElement.FindAll%2A> メソッドを使用して、一致するすべての要素の検索が実行されます。  
  
> [!NOTE]
> <xref:System.Windows.Automation.AutomationElement.RootElement%2A> から検索する場合は、直接の子のみを取得するようにしてください。 子孫を検索すると、数百または数千もの要素が反復処理される場合があり、スタック オーバーフローを引き起こす可能性があります。 下位レベルの特定の要素を取得しようとする場合、アプリケーション ウィンドウから、または下位レベルのコンテナーから検索を開始する必要があります。  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a>関連項目

- [InvokePattern および ExpandCollapsePattern メニュー項目のサンプル](/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))
- [UI オートメーション要素の取得](obtaining-ui-automation-elements.md)
- [AutomationID プロパティの使用](use-the-automationid-property.md)
