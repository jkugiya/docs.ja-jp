---
title: UI オートメーションおよび画面の拡大縮小
description: Windows と UI オートメーションによって画面の拡大縮小が処理される方法について説明します。 DWM では、UI オートメーション クライアント アプリで考慮する必要があるすべてのアプリケーションの既定の拡大縮小が実行されます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scaling, screens
- screens, scaling
- UI (user interface), automation
- UI Automation
ms.assetid: 4380cad7-e509-448f-b9a5-6de042605fd4
ms.openlocfilehash: cf8069f26b85318994aeeb47d42ad28a3a33834a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262529"
---
# <a name="ui-automation-and-screen-scaling"></a>UI オートメーションおよび画面の拡大縮小

> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
Windows Vista 以降の Windows では、ユーザーがドット/インチ (dpi) の設定を変更して、画面上のほとんどのユーザー インターフェイス (UI) 要素を拡大表示できます。 この機能は長い間、Windows で有効でしたが、以前のバージョンでは、アプリケーションによって拡大縮小を実装しなければなりませんでした。 Windows Vista 以降では、独自の拡大縮小処理を行わないアプリケーションのすべてについて、デスクトップ ウィンドウ マネージャーによって既定の拡大縮小が行われます。 UI オートメーション クライアント アプリケーションでは、この機能を考慮に入れる必要があります。  
  
<a name="Scaling_in_Windows_Vista"></a>

## <a name="scaling-in-windows-vista"></a>Windows Vista での拡大縮小  

 既定の dpi 設定は 96 です。つまり、幅または高さの概念上の 1 インチが 96 ピクセルで占められます。 「インチ」の正確な寸法は、モニターのサイズと物理的な解像度によって異なります。 たとえば、幅 12 インチで水平方向の解像度 1280 ピクセルのモニターでは、96 ピクセルの水平線は 1 インチの約 9/10 の長さになります。  
  
 dpi 設定を変更することは、画面の解像度を変更することと同じではありません。 dpi の拡大縮小では、画面上の物理的ピクセル数はそのまま変わりません。 拡大縮小が適用されるのは、 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 要素のサイズと位置です。 拡大縮小しないよう明示的に指定されていないデスクトップとアプリケーションに対し、デスクトップ ウィンドウ マネージャー (DWM) はこの拡大縮小を自動的に実行できます。  
  
 実際には、ユーザーがスケール ファクターを 120 dpi に設定すると、画面上の垂直または水平方向のインチが 25% 拡大されます。 すべての寸法は、それに応じて拡大されます。 画面の左上隅からのアプリケーション ウィンドウのオフセットは、25% 増加します。 アプリケーションの拡大縮小が有効であり、アプリケーションが dpi 対応でない場合、ウィンドウのサイズと、そこに含まれるすべての [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 要素のオフセットとサイズが同じ比率で大きくなります。  
  
> [!NOTE]
> 既定では、ユーザーが dpi を 120 に設定した場合、DWM では dpi 非対応のアプリケーションに対して拡大縮小が実行されませんが、dpi が 144 以上のカスタム値に設定されている場合には拡大縮小が実行されます。 ただし、この既定の動作は、ユーザーがオーバーライドできます。  
  
 画面の拡大縮小は、画面座標に何らかの関わりを持つアプリケーションに新しい課題をもたらします。 現在、画面には物理座標と論理座標という 2 つの座標系が含まれています。 あるポイントの物理座標は、原点の左上からの実際のオフセット (ピクセル数) です。 論理座標は、ピクセル自体が拡大縮小された場合のオフセットです。  
  
 たとえば、ダイアログ ボックスを設計し、座標 (100, 48) にボタンを配置するとします。 このダイアログ ボックスが既定の 96 dpi で表示される場合、ボタンは物理座標 (100, 48) に位置します。 120 dpi の場合は、物理座標 (125, 60) に位置します。 しかし、論理座標は dpi の設定に関係なく、(100, 48) のままです。  
  
 論理座標は、dpi の設定に関係なく、オペレーティング システムとアプリケーションの動作を一貫性のあるものとするので重要です。 たとえば、 <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> は通常、論理座標を返します。 カーソルをダイアログ ボックス内の要素に移動すると、dpi の設定に関係なく、同じ座標が返されます。 (100, 100) にコントロールを描画する場合、それはこの論理座標に描画され、dpi の設定に関係なく、同じ相対位置を占めることになります。  
  
<a name="Scaling_in_UI_Automation_Clients"></a>

## <a name="scaling-in-ui-automation-clients"></a>UI オートメーション クライアントにおける拡大縮小  

 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] API は論理座標を使用しません。 次のメソッドとプロパティが返す、あるいはパラメーターとして受け取るのは、物理座標です。  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 96 dpi ではない環境で実行されている UI オートメーション クライアント アプリケーションは、既定では、これらのメソッドとプロパティから正しい結果を取得できません。 たとえば、カーソルの位置は論理座標で表されるため、クライアントはそのカーソルの位置にある要素を取得するために、これらの座標をそのまま <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> に渡すことができません。 さらに、アプリケーションはクライアント領域外にウィンドウを正しく配置することもできません。  
  
 解決方法は 2 つの部分で構成されます。  
  
1. まず、クライアント アプリケーションを dpi 対応にします。 それには、起動時に Win32 関数 `SetProcessDPIAware` を呼び出します。 マネージド コードで、次の宣言によりこの関数を使用できるようになります。  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     この関数は、プロセス全体を dpi 対応にします。つまり、プロセスに属するすべてのウィンドウは拡大縮小されません。 [蛍光ペンのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)では、たとえば強調表示の四角形を構成する 4 つのウィンドウは、論理座標ではなく、UI オートメーションから取得した物理座標に位置します。 この例が dpi 非対応だったなら、強調表示はデスクトップ上の論理座標で描画されるため、96 dpi 以外の環境では誤った位置に配置されることになります。  
  
2. カーソルの座標を取得するには、 Win32 関数 `GetPhysicalCursorPos` を呼び出します。 次の例に、この関数を宣言して使用する方法を示します。  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
> <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>は使用しないでください。 拡大縮小される環境において、クライアント ウィンドウ外でのこのプロパティの動作は定義されていません。  
  
 アプリケーションが dpi 非対応のアプリケーションと直接プロセス間通信を行う場合は、Win32 関数 `PhysicalToLogicalPoint` および `LogicalToPhysicalPoint` を使用して、論理座標と物理座標を互いに変換できます。  
  
## <a name="see-also"></a>関連項目

- [Highlighter Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
