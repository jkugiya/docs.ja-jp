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
# <a name="get-ui-automation-element-properties"></a>UI オートメーション要素のプロパティの取得

> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックでは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 要素のプロパティを取得する方法を示します。  
  
### <a name="get-a-current-property-value"></a>現在のプロパティ値を取得する  
  
1. 取得するプロパティが含まれている <xref:System.Windows.Automation.AutomationElement> を取得します。  
  
2. <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> を呼び出すか、<xref:System.Windows.Automation.AutomationElement.Current%2A> プロパティ構造体を取得し、そのメンバーの 1 つから値を取得します。  
  
### <a name="get-a-cached-property-value"></a>キャッシュされたプロパティ値を取得する  
  
1. 取得するプロパティが含まれている <xref:System.Windows.Automation.AutomationElement> を取得します。 プロパティは、<xref:System.Windows.Automation.CacheRequest> で指定されている必要があります。  
  
2. <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> を呼び出すか、<xref:System.Windows.Automation.AutomationElement.Cached%2A> プロパティ構造体を取得し、そのメンバーの 1 つから値を取得します。  
  
## <a name="example"></a>例  

 次の例は、<xref:System.Windows.Automation.AutomationElement> の現在のプロパティを取得するさまざまな方法を示しています。  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>関連項目

- [クライアントの UI オートメーション プロパティ](ui-automation-properties-for-clients.md)
- [UI オートメーションにおけるキャッシュの使用](use-caching-in-ui-automation.md)
- [UI オートメーション クライアントにおけるキャッシュ](caching-in-ui-automation-clients.md)
