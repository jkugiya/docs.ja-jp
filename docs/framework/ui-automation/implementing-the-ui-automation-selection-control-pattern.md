---
title: UI オートメーション Selection コントロール パターンの実装
description: UI オートメーションで Selection コントロール パターンを実装するためのガイドラインと規則を確認します。 ISelectionProvider インターフェイスに必要なメンバーをご覧ください。
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
ms.openlocfilehash: 7ce6b9765dfd15be320f01151ca0b91393508e55
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237509"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>UI オートメーション Selection コントロール パターンの実装

> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックでは、イベントおよびプロパティに関する情報など、 <xref:System.Windows.Automation.Provider.ISelectionProvider>の実装のためのガイドラインと規則について説明します。 その他のリファレンスへのリンクは、トピックの最後に記載します。  
  
 <xref:System.Windows.Automation.SelectionPattern> コントロール パターンは、選択可能な子項目のコレクションのコンテナーとして機能するコントロールをサポートするために使用します。 この要素の子は <xref:System.Windows.Automation.Provider.ISelectionItemProvider>を実装する必要があります。 このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>実装のガイドラインと規則  

 Selection コントロール パターンを実装する場合は、次のガイドラインと規則にご留意ください。  
  
- <xref:System.Windows.Automation.Provider.ISelectionProvider> を実装するコントロールでは、単一の子または複数の子項目を選択できます。 たとえば、リスト ボックス、リスト ビュー、ツリー ビューでは複数の項目を選択できる一方、コンボ ボックス、スライダー、ラジオ ボタン グループでは 1 つの項目だけを選択できます。  
  
- **音量** スライダー コントロールなど、最小値、最大値、連続した値の範囲を持つコントロールは、 <xref:System.Windows.Automation.Provider.IRangeValueProvider> ではなく <xref:System.Windows.Automation.Provider.ISelectionProvider>を実装する必要があります。  
  
- **[画面のプロパティ]** ダイアログ ボックスの **[画面解像度]** スライダーや、Microsoft Word の **カラー ピッカー** 選択コントロールなど (以下を参照)、<xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot> を実装する子コントロールを管理する単一選択コントロールは <xref:System.Windows.Automation.Provider.ISelectionProvider> を実装する必要があり、その子は <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> と <xref:System.Windows.Automation.Provider.ISelectionItemProvider> の両方を実装する必要があります。  
  
 ![黄色が強調表示されたカラー ピッカー。](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
色見本の文字列マッピング例  
  
- メニューは <xref:System.Windows.Automation.SelectionPattern>をサポートしていません。 グラフィックスとテキストの両方を含むメニュー項目 (Microsoft Outlook の **[表示]** メニューにある **[プレビュー ウィンドウ]** 項目など) を処理していて、状態を伝える必要がある場合は、<xref:System.Windows.Automation.Provider.IToggleProvider> を実装する必要があります。  
  
<a name="Required_Members_for_ISelectionProvider"></a>

## <a name="required-members-for-iselectionprovider"></a>ISelectionProvider の必須メンバー  

 <xref:System.Windows.Automation.Provider.ISelectionProvider> インターフェイスには、次のプロパティ、メソッド、イベントが必要です。  
  
|必須メンバー|種類|Notes|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|プロパティ|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> と <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>を使用してプロパティ変更イベントをサポートする必要があります。|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|プロパティ|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> と <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>を使用してプロパティ変更イベントをサポートする必要があります。|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|方法|なし|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|イベント|コンテナー内の選択が大幅に変更され、 <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> 定数で許可されるよりも多くの追加イベントと削除イベントを送信する必要がある場合に発生します。|  
  
 <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> プロパティと <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> プロパティは、動的に設定できます。 たとえば、既定で初期状態では何も項目が選択されていないコントロールがあるとします。これは、 <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> が `false`であるということです。 しかし、項目が 1 つ選択されると、このコントロールは、項目が常に 1 つ以上選択された状態を保持する必要があります。 同様に、まれなケースとして、初期設定では複数の項目の選択を許可し、以降は 1 項目の選択だけを許可するようにコントロールが設定される場合があります。  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a>例外  

 プロバイダーは、次の例外をスローする必要があります。  
  
|例外の種類|条件|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|コントロールが有効でない場合。|  
|<xref:System.InvalidOperationException>|コントロールが非表示の場合。|  
  
## <a name="see-also"></a>関連項目

- [UI オートメーション コントロール パターンの概要](ui-automation-control-patterns-overview.md)
- [UI オートメーション プロバイダーでのコントロール パターンのサポート](support-control-patterns-in-a-ui-automation-provider.md)
- [クライアントの UI オートメーション コントロール パターン](ui-automation-control-patterns-for-clients.md)
- [UI オートメーション SelectionItem コントロール パターンの実装](implementing-the-ui-automation-selectionitem-control-pattern.md)
- [UI オートメーション ツリーの概要](ui-automation-tree-overview.md)
- [UI オートメーションにおけるキャッシュの使用](use-caching-in-ui-automation.md)
