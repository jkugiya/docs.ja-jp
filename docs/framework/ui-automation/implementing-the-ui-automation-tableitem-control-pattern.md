---
title: UI オートメーション TableItem コントロール パターンの実装
description: UI オートメーションで TableItem コントロール パターンを実装するためのガイドラインと規則を確認します。 ITableItemProvider インターフェイスに必要なメンバーを確認します。
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 5e83f68772de3026fe8bcb265a11999e0b85a164
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265675"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a>UI オートメーション TableItem コントロール パターンの実装

> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックでは、イベントおよびプロパティに関する情報など、 <xref:System.Windows.Automation.Provider.ITableItemProvider>の実装のためのガイドラインと規則について説明します。 その他のリファレンスへのリンクは、概要の最後に記載します。  
  
 <xref:System.Windows.Automation.Provider.ITableProvider> を実装するコンテナーの子コントロールをサポートするために、<xref:System.Windows.Automation.TableItemPattern> コントロール パターンが使用されています。 個々のセル機能へのアクセスは、必要な <xref:System.Windows.Automation.Provider.IGridItemProvider> の同時実装によって提供されます。 このコントロール パターンは <xref:System.Windows.Automation.Provider.IGridItemProvider> と同様です。異なる点は、<xref:System.Windows.Automation.Provider.ITableItemProvider> を実装するコントロールは、個々のセルとその行および列情報の間の関係をプログラムによって公開しなければならないことです。 このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>実装のガイドラインと規則  
  
- 関連するグリッド項目の機能については、「[UI オートメーション GridItem コントロール パターンの実装](implementing-the-ui-automation-griditem-control-pattern.md)」を参照してください。  
  
<a name="Required_Members_for_ITableItemProvider"></a>

## <a name="required-members-for-itableitemprovider"></a>ITableItemProvider の必須メンバー  
  
|必須メンバー|メンバーの型|メモ|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|方法|なし|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|方法|なし|  
  
 このコントロール パターンに関連付けられるプロパティやイベントはありません。  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a>例外  

 このコントロール パターンに関連付けられた例外はありません。  
  
## <a name="see-also"></a>関連項目

- [UI オートメーション コントロール パターンの概要](ui-automation-control-patterns-overview.md)
- [UI オートメーション プロバイダーでのコントロール パターンのサポート](support-control-patterns-in-a-ui-automation-provider.md)
- [クライアントの UI オートメーション コントロール パターン](ui-automation-control-patterns-for-clients.md)
- [UI オートメーション Table コントロール パターンの実装](implementing-the-ui-automation-table-control-pattern.md)
- [UI オートメーション GridItem コントロール パターンの実装](implementing-the-ui-automation-griditem-control-pattern.md)
- [UI オートメーション ツリーの概要](ui-automation-tree-overview.md)
- [UI オートメーションにおけるキャッシュの使用](use-caching-in-ui-automation.md)
