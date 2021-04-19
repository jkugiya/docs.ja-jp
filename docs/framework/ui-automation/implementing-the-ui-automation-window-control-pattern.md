---
title: UI オートメーション Window コントロール パターンの実装
description: UI オートメーションで Window コントロール パターンを実装するためのガイドラインと規則を確認します。 IWindowProvider インターフェイスに必要なメンバーを確認します。
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: b43884393974e6f2863da6a4a5ca8f305e5a160c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286098"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>UI オートメーション Window コントロール パターンの実装

> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックでは、 <xref:System.Windows.Automation.Provider.IWindowProvider>のプロパティ、メソッド、イベントに関する情報など、 <xref:System.Windows.Automation.WindowPattern> の実装のためのガイドラインと規則について説明します。 その他のリファレンスへのリンクは、トピックの最後に記載します。  
  
 <xref:System.Windows.Automation.WindowPattern> コントロール パターンは、従来のグラフィカル ユーザー インターフェイス (GUI) 内で、ウィンドウベースの基本的な機能を提供するコントロールをサポートするために使用されます。 このコントロール パターンを実装する必要があるコントロールの例として、最上位のアプリケーション ウィンドウ、マルチドキュメント インターフェイス (MDI) 子ウィンドウ、サイズ変更可能な分割ペイン コントロール、モーダル ダイアログ ボックス、バルーン ヘルプ ウィンドウがあります。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>実装のガイドラインと規則  

 Window コントロール パターンを実装する場合は、次のガイドラインと規則に注意してください。  
  
- UI オートメーションを使用してウィンドウのサイズと位置の両方を変更する機能をサポートするには、コントロールが <xref:System.Windows.Automation.Provider.ITransformProvider> に加えて <xref:System.Windows.Automation.Provider.IWindowProvider>を実装する必要があります。  
  
- コントロールを移動、サイズ変更、最大化、最小化、および閉じられるようにするタイトル バーの要素とタイトル バーを格納するコントロールは、通常 <xref:System.Windows.Automation.Provider.IWindowProvider>を実装することが求められます。  
  
- ツールヒントのポップアップやコンボ ボックス、またはメニューのドロップダウンなどのコントロールは、通常 <xref:System.Windows.Automation.Provider.IWindowProvider>を実装しません。  
  
- バルーン ヘルプ ウィンドウは、ウィンドウと同様の閉じるボタンを提供することで、基本的なツールヒント ポップアップから区別されます。  
  
- 全画面表示モードは、アプリケーション固有の機能であり、通常のウィンドウの動作ではないため、IWindowProvider によってサポートされません。  
  
<a name="Required_Members_for_IWindowProvider"></a>

## <a name="required-members-for-iwindowprovider"></a>IWindowProvider の必須メンバー  

 IWindowProvider インターフェイスには、次のプロパティ、メソッド、イベントが必要です。  
  
|必須メンバー|メンバーの型|メモ|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|方法|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|方法|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|方法|なし|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|イベント|なし|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|イベント|なし|  
|<xref:System.Windows.Automation.WindowInteractionState>|イベント|<xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a>例外  

 プロバイダーは、次の例外をスローする必要があります。  
  
|例外の種類|条件|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> -   要求された動作がコントロールによってサポートされない場合。|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> -   パラメーターが有効な数値ではない場合。|  
  
## <a name="see-also"></a>関連項目

- [UI オートメーション コントロール パターンの概要](ui-automation-control-patterns-overview.md)
- [UI オートメーション プロバイダーでのコントロール パターンのサポート](support-control-patterns-in-a-ui-automation-provider.md)
- [クライアントの UI オートメーション コントロール パターン](ui-automation-control-patterns-for-clients.md)
- [UI オートメーション ツリーの概要](ui-automation-tree-overview.md)
- [UI オートメーションにおけるキャッシュの使用](use-caching-in-ui-automation.md)
