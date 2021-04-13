---
title: UI オートメーションによる DataItem コントロール型のサポート
description: UI オートメーションによる DataItem コントロール型のサポートに関する情報を取得します。 必要なツリー構造、プロパティ、コントロール パターン、およびイベントについて説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Data Item control type
- Data Item control type
- control types, Data Item
ms.assetid: 181708fd-2595-4c43-9abd-75811627d64c
ms.openlocfilehash: be7e4afcbeb884f63d77fe9aa25342c7f9b49f52
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278090"
---
# <a name="ui-automation-support-for-the-dataitem-control-type"></a>UI オートメーションによる DataItem コントロール型のサポート

> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックでは、DataItem コントロール型に対する [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] のサポートについて説明します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] でのコントロール型とは、コントロールが <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> プロパティを使用するために満たす必要がある一連の条件のことです。 これらの条件には、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー構造、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のプロパティ値、およびコントロール パターンに関する特定のガイドラインが含まれます。  
  
 連絡先リストのエントリは、データ項目コントロールの一例です。 データ項目コントロールには、エンド ユーザーに必要な情報が格納されます。 これは、より豊富な情報が格納されるため、単純なリスト項目よりも複雑になります。  
  
 以下の各セクションで、DataItem コントロール型に必要な [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー構造、プロパティ、コントロール パターン、およびイベントを定義します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の要件は、[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]、Win32、Windows フォームのいずれの場合でも、すべてのデータ項目コントロールに適用されます。  
  
## <a name="required-ui-automation-tree-structure"></a>必須の UI オートメーション ツリー構造  

 次の表に、データ項目コントロールに関連する [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコントロール ビューとコンテンツ ビューを示し、それぞれのビューに含めることができる内容について説明します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーの詳細については、「[UI オートメーション ツリーの概要](ui-automation-tree-overview.md)」を参照してください。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー - コントロール ビュー|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー - コンテンツ ビュー|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataItem<br /><br /> -   多種多様 (0 以上。階層で構造化できます)|DataItem<br /><br /> -   多種多様 (0 以上。階層で構造化できます)|  
  
 データ グリッド内のデータ項目要素は、さまざまなオブジェクトをホストできます。たとえば、別のレイヤーのデータ項目や、テキスト、イメージ、エディット コントロールなどの特定のグリッド要素をホストできます。 データ項目要素に特定のオブジェクトの役割がある場合は、その要素を特定のコントロール型 (たとえば、グリッド内の選択可能なデータ項目の場合は ListItem コントロール型など) として公開する必要があります。  
  
## <a name="required-ui-automation-properties"></a>必須の UI オートメーション プロパティ  

 次の表に、データ項目コントロールに特に関連する値または定義を持つプロパティを示します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティの詳細については、「[クライアントの UI オートメーション プロパティ](ui-automation-properties-for-clients.md)」を参照してください。  
  
|プロパティ|[値]|Notes|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|「ノート」を参照してください。|このプロパティの値は、アプリケーション内のすべてのコントロールで一意である必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|「ノート」を参照してください。|コントロール全体を格納する最も外側の四角形。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|「ノート」を参照してください。|四角形領域が存在する場合にサポートされます。 四角形領域内にクリック不可能な点が存在し、特別なヒット テストを実行する場合は、オーバーライドしてクリック可能な点を提供します。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataItem|この値は、すべての UI フレームワークで同じです。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|○|データ項目コントロールは、常にコンテンツである必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|○|データ項目コントロールは、常にコントロールである必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|「ノート」を参照してください。|コントロールがキーボード フォーカスを受け取ることができる場合は、このプロパティをサポートする必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|「ノート」を参照してください。|コントロールに動的に更新される状態が含まれる場合、要素の状態が変化したときに支援技術が更新を受け取ることができるように、このプロパティをサポートする必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|「ノート」を参照してください。|これは、項目が表す基になるオブジェクトをエンド ユーザーに伝達する文字列値です。 例として "メディア ファイル" や "連絡先" があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|データ項目コントロールに静的なテキスト ラベルはありません。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"data item"|DataItem コントロール型に対応するローカライズされた文字列。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|「ノート」を参照してください。|データ項目コントロールには、主要なテキスト要素が常に含まれています。この要素は、その項目に対してユーザーが最も意味的な識別子として連想するものに関連しています。|  
  
## <a name="required-ui-automation-control-patterns"></a>必須の UI オートメーション コントロール パターン  

 次の表に、すべてのデータ項目コントロールでサポートされなければならない [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] コントロール パターンを示します。 コントロール パターンについて詳しくは、「 [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md)」をご覧ください。  
  
|コントロール パターン|サポート|Notes|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|依存|データ項目を展開したり折りたたんだりして、情報の表示/非表示を切り替える場合、Expand Collapse パターンをサポートする必要があります。|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|依存|データ項目の集合が、空間的に項目間を移動できるコンテナー内にある場合、データ項目は Grid Item パターンをサポートします。|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|依存|画面に収まる項目数を超える項目がデータ コンテナーにある場合、すべてのデータ項目は Scroll Item パターンを使用して、スクロールして表示する機能をサポートします。|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|はい|すべてのデータ項目は、項目が選択されたタイミングを示す Selection Item パターンをサポートする必要があります。|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|依存|データ項目が Data Grid コントロール型の中に含まれている場合、このパターンをサポートします。|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|依存|データ項目に循環する状態が含まれる場合。|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|依存|データ項目の主要なテキストが編集可能な場合は、Value パターンをサポートする必要があります。|  
  
## <a name="working-with-data-items-in-large-lists"></a>大きなリストでのデータ項目の操作  

 大きなリストでは、多くの場合、パフォーマンスを向上させるため、 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] フレームワーク内でデータが仮想化されます。 そのため、UI オートメーション クライアントは、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] クエリ機能を使用して、他の項目コンテナーと同じように完全なツリーからコンテンツを取得することができません。 クライアントは、データ項目の完全に揃った情報にアクセスする前に、項目をスクロールして表示する (またはコントロールを展開して重要なすべてのオプションを表示する) 必要があります。  
  
 データ項目の [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 要素で `SetFocus` を呼び出すと、Microsoft Windows エクスプローラーの場合は正常に値が返され、データ項目サブツリー内でフォーカスを編集に設定されます。  
  
## <a name="required-ui-automation-events"></a>必須の UI オートメーション イベント  

 次の表に、すべてのデータ項目コントロールでサポートされなければならない [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベントを示します。 イベントの詳細については、「 [UI Automation Events Overview](ui-automation-events-overview.md)」を参照してください。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベント|サポート|Notes|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必須|なし|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|依存|なし|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> プロパティ変更イベント。|依存|なし|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|必須|なし|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|必須|なし|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|必須|なし|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> プロパティ変更イベント。|依存|なし|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> プロパティ変更イベント。|依存|なし|  
  
## <a name="dataitem-control-type-example"></a>DataItem コントロール型の例  

 次の図は、列の豊富な情報をサポートするリスト ビュー コントロール内の DataItem コントロール型を示しています。  
  
 ![2 つのデータ項目を含むリスト ビュー コントロールのグラフィック](./media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 以下には、データ項目コントロールに関連する [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコントロール ビューとコンテンツ ビューが表示されています。 オートメーションの各要素のコントロール パターンが、かっこ内に示されています。 グループ "Contoso" は、データ グリッド ホスト コントロールのグリッドの一部でもあります。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー - コントロール ビュー|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー - コンテンツ ビュー|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|-   Group "Contoso" (Table、Grid)<br />-   DataItem "Accounts Receivable.doc" (TableItem、GridItem、SelectionItem、Invoke)<br />-   Image "Accounts Receivable.doc"<br />-   Edit "Name" (TableItem、GridItem、Value "Accounts Receivable.doc")<br />-   Edit "Date modified" (TableItem、GridItem、Value "8/25/2006 3:29 PM")<br />-   Edit "Size" (GridItem、TableItem、Value "11.0 KB)<br />-   DataItem "Accounts Payable.doc" (TableItem、GridItem、SelectionItem, Invoke)<br />-   ...|-   Group "Contoso" (Table、Grid)<br />-   DataItem "Accounts Receivable.doc" (TableItem、GridItem、SelectionItem、Invoke)<br />-   Image "Accounts Receivable.doc"<br />-   Edit "Name" (TableItem、GridItem、Value "Accounts Receivable.doc")<br />-   Edit "Date modified" (TableItem、GridItem、Value "8/25/2006 3:29 PM")<br />-   Edit "Size" (GridItem、TableItem、Value "11.0 KB)<br />-   DataItem "Accounts Payable.doc" (TableItem、GridItem、SelectionItem, Invoke)<br />-   …|  
  
 グリッドが選択可能な項目のリストを表している場合、DataItem コントロール型の代わりに、ListItem コントロール型で対応する UI 要素を公開できます。 前の例では、グループ ("Contoso") の下の DataItem 要素 ("Accounts Receivable.doc" および "Accounts Payable.doc") を ListItem コントロール型として公開することで、その型が既に SelectionItem コントロール パターンをサポートしているため、それらの要素を向上させることができます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Automation.ControlType.DataItem>
- [UI オートメーション コントロール型の概要](ui-automation-control-types-overview.md)
- [UI オートメーションの概要](ui-automation-overview.md)
