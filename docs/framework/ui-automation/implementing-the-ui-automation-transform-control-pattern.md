---
title: UI オートメーション Transform コントロール パターンの実装
description: UI オートメーションで Transform コントロール パターンを実装するためのガイドラインと規則を確認します。 ITransformProvider インターフェイスに必要なメンバーを確認します。
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
ms.openlocfilehash: fc47170a08ff08f6cd8f67996ef8fbf19c40f819
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265649"
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a>UI オートメーション Transform コントロール パターンの実装

> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックでは、プロパティ、メソッド、イベントに関する情報など、 <xref:System.Windows.Automation.Provider.ITransformProvider>の実装のためのガイドラインと規則について説明します。 その他のリファレンスへのリンクは、トピックの最後に記載します。  
  
 <xref:System.Windows.Automation.TransformPattern> コントロール パターンは、2 次元空間で移動、サイズ変更、または回転できるコントロールをサポートするために使用されます。 このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>実装のガイドラインと規則  

 Transform コントロール パターンを実装する場合は、次のガイドラインと規則にご留意ください。  
  
- このコントロール パターンのサポートは、デスクトップ上のオブジェクトに制限されません。 コンテナーの境界内で子が自由に移動、サイズ変更、または回転できるようにする場合は、そのコンテナー オブジェクトの子もこのコントロール パターンをサポートしている必要があります。  
  
- 操作後の画面位置が完全にそのコンテナーの座標外となり、キーボードやマウスからアクセスできなくなる場合 (たとえば、トップレベルのウィンドウが画面外に移動したり、子オブジェクトがコンテナーのビューポートの境界外へ移動したりする場合) は、オブジェクトの移動、サイズ変更、および回転はできません。 このような場合、上辺または左辺の座標をコンテナーの境界内にオーバーライドして、要求された画面座標のできるだけ近くにオブジェクトが配置されます。  
  
- マルチモニター システムでは、結合したデスクトップ画面座標の完全に外へオブジェクトを移動、サイズ変更、または回転した場合、プライマリ モニター上の、要求された画面座標のできるだけ近くにオブジェクトが配置されます。  
  
- すべてのパラメーターとプロパティの値は絶対値で、ロケールには依存しません。  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-itransformprovider"></a>ITransformProvider の必須メンバー  

 <xref:System.Windows.Automation.Provider.ITransformProvider>の実装には、次のプロパティとメソッドが必要です。  
  
|必須メンバー|メンバーの型|メモ|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|方法|なし|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|方法|なし|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|方法|なし|  
  
 このコントロール パターンには、関連するイベントがありません。  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a>例外  

 プロバイダーは、次の例外をスローする必要があります。  
  
|例外の種類|条件|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> -   <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> が false の場合。|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> -   <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> が false の場合。|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> -   <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> が false の場合。|  
  
## <a name="see-also"></a>関連項目

- [UI オートメーション コントロール パターンの概要](ui-automation-control-patterns-overview.md)
- [UI オートメーション プロバイダーでのコントロール パターンのサポート](support-control-patterns-in-a-ui-automation-provider.md)
- [クライアントの UI オートメーション コントロール パターン](ui-automation-control-patterns-for-clients.md)
- [UI オートメーション ツリーの概要](ui-automation-tree-overview.md)
- [UI オートメーションにおけるキャッシュの使用](use-caching-in-ui-automation.md)
