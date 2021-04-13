---
title: UI オートメーションを使用したテーブルの内容の公開
description: UI オートメーションを使用したテーブルの内容の公開方法をご覧ください。 表形式コントロール内の各セルのコンテンツおよび組み込みプロパティが公開されています。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables, exposing content of
- UI Automation, exposing content of tables
- exposing content of tables using UI Automation
ms.assetid: ac3c5eaa-49c7-4653-b83e-532e2a2604a2
ms.openlocfilehash: e089f1371dba476b1f75f9fffe7d224c840f8d80
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276517"
---
# <a name="expose-the-content-of-a-table-using-ui-automation"></a>UI オートメーションを使用したテーブルの内容の公開

> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックでは、[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] を使用して表形式コントロール内の各セルのコンテンツおよび組み込みプロパティを公開する方法を示します。  
  
## <a name="example"></a>例  

 次のコード例では、テーブル セルのコンテンツを表す <xref:System.Windows.Automation.AutomationElement> を取得する方法を示します。行および列インデックス、行と列の範囲、行と列のヘッダー情報などのセル プロパティも取得されます。 この例では、フォーカス変更イベント ハンドラーを使用して、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] を実装する表形式コントロールのキーボード トラバースをシミュレートします。 各テーブル項目の情報は、フォーカス変更イベントで公開されます。  
  
> [!NOTE]
> フォーカスの変更はグローバル デスクトップ イベントなので、テーブル外部のフォーカス変更イベントをフィルター処理する必要があります。 関連する実装については、「[TrackFocus のサンプル](/previous-versions/dotnet/netframework-3.5/ms771428(v=vs.90))」を参照してください。  
  
 [!code-csharp[UIATableItemPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#starttarget)]
 [!code-vb[UIATableItemPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#starttarget)]  
[!code-csharp[UIATableItemPattern_snip#GetTableElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#gettableelement)]
[!code-vb[UIATableItemPattern_snip#GetTableElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#gettableelement)]  
[!code-csharp[UIATableItemPattern_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#101)]
[!code-vb[UIATableItemPattern_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#101)]  
[!code-csharp[UIATableItemPattern_snip#1015](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#1015)]
[!code-vb[UIATableItemPattern_snip#1015](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#1015)]  
[!code-csharp[UIATableItemPattern_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#102)]
[!code-vb[UIATableItemPattern_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#102)]  
[!code-csharp[UIATableItemPattern_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#103)]
[!code-vb[UIATableItemPattern_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#103)]  
  
## <a name="see-also"></a>関連項目

- [UI オートメーション コントロール パターンの概要](ui-automation-control-patterns-overview.md)
- [クライアントの UI オートメーション コントロール パターン](ui-automation-control-patterns-for-clients.md)
- [UI オートメーション Table コントロール パターンの実装](implementing-the-ui-automation-table-control-pattern.md)
- [UI オートメーション TableItem コントロール パターンの実装](implementing-the-ui-automation-tableitem-control-pattern.md)
- [UI オートメーション Grid コントロール パターンの実装](implementing-the-ui-automation-grid-control-pattern.md)
- [UI オートメーション GridItem コントロール パターンの実装](implementing-the-ui-automation-griditem-control-pattern.md)
