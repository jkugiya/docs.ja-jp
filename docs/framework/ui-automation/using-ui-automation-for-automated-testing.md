---
title: UI オートメーションによる自動テスト
description: 自動テストのシナリオでプログラムによってアクセスするためのフレームワークとして UI オートメーションを使用する方法についての概要説明をご覧ください。
ms.date: 03/30/2017
helpviewer_keywords:
- automated testing
- testing, UI Automation
- UI Automation, automated testing
ms.assetid: 3a0435c0-a791-4ad7-ba92-a4c1d1231fde
ms.openlocfilehash: 4b039fbbe636bd56afa25cb4b45605b09ab44662
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237340"
---
# <a name="using-ui-automation-for-automated-testing"></a>UI オートメーションによる自動テスト

> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 ここでは、自動テストのシナリオで、プログラムによるアクセスのためのフレームワークとして [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] がどのように役立つかについて説明します。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の統一されたオブジェクト モデルを使用すると、すべての [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] フレームワークにおいて、複雑で豊富な機能をアクセシビリティが高く自動化しやすい方法で公開できます。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] は、Microsoft Active Accessibility の後継として開発されました。 Active Accessibility は、コントロールとアプリケーションにアクセスできるようするソリューションを提供するために設計された既存のフレームワークです。 ユーザー補助と自動化の要件がよく似ているため、Active Accessibility はテストの自動化に使用されるようになりましたが、この役割を想定して設計されたものではありません。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]は、ユーザー補助のためのより洗練されたソリューションを提供するだけでなく、信頼性の高い自動テスト機能を提供するように設計されています。 たとえば、Active Accessibility では、UI に関する情報の公開と、AT 製品に必要な情報の収集の両方に、同じインターフェイスを使用します。これに対して [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では、2 つのモデルを分けています。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] を自動テスト ツールとして利用するには、プロバイダーとクライアントの両方にこれを実装する必要があります。 UI オートメーション プロバイダーは、Microsoft Word、Excel やその他のサードパーティ アプリケーションなどのアプリケーション、または Microsoft Windows オペレーティング システムに基づくコントロールです。 UI オートメーション クライアントは、自動テスト スクリプトや支援 (補助) 技術アプリケーションなどです。  
  
> [!NOTE]
> この概要の目的は、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の、自動テストに関する新機能と強化された機能について説明することです。 この概要はユーザー補助機能に関する情報の提供を目的とするものではなく、必要な場合以外、ユーザー補助については説明しません。  
  
## <a name="ui-automation-in-a-provider"></a>プロバイダーにおける UI オートメーション  

 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] を自動化するためにアプリケーションやコントロールの開発者が注意する必要があるのは、その [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] オブジェクトでキーボードとマウスの標準操作を使用して実行できるエンド ユーザーのアクションです。  
  
 これらの主要なアクションを特定したら、対応する [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] コントロール パターン (つまり、 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 要素の機能と動作をミラー化するコントロール パターン) をコントロール上に実装します。 たとえば、コンボ ボックス コントロール (実行用のダイアログなど) でのユーザー操作には、通常、項目の一覧を非表示にしたり表示したりするためのコンボ ボックスの展開と折りたたみ、一覧からの項目の選択、またはキーボード入力による新しい値の追加が含まれます。  
  
> [!NOTE]
> 他のユーザー補助モデルでは、開発者が直接、個々のボタン、メニューなどのコントロールから情報を収集する必要があります。 しかも、各コントロール型には、細部の異なるバリエーションが多数存在します。 つまり、あるプッシュボタンに 10 個のバリエーションが存在すると、それらすべての動作と機能が同じであっても、それぞれを別個のコントロールとして扱う必要があります。 これらのコントロールが機能的に同等であることを知る方法はありません。 コントロール パターンは、こうした共通のコントロール動作を表すために開発されました。 詳細については、「 [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md)」を参照してください。  
  
### <a name="implementing-ui-automation"></a>UI オートメーションの実装  

 既に述べたように、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の統一されたモデルを使用しない場合、フレームワーク内のコントロールのプロパティや動作を公開するためには、フレームワーク固有の情報をテスト ツールや開発者が知る必要があります。 Windows オペレーティング システム内には常に、Win32、Windows フォーム、Windows Presentation Foundation (WPF) などの複数の UI フレームワークが存在する可能性があるため、似たようなコントロールを持つ複数のアプリケーションをテストすることは困難な場合があります。 次の表では、例として、あるボタン コントロールに関連付けられた名前 (またはテキスト) を取得するために必要なフレームワーク固有のプロパティ名と、それと同等の単一 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティを示します。  
  
|UI オートメーション コントロール型|UI フレームワーク|フレームワーク固有のプロパティ|UI Automation のプロパティ|  
|--------------------------------|------------------|---------------------------------|----------------------------|  
|ボタン|Windows Presentation Foundation|Content|NameProperty|  
|ボタン|Win32|Caption|NameProperty|  
|Image|HTML|alt|NameProperty|  
  
 UI オートメーション プロバイダーは、そのコントロールのフレームワーク固有のプロパティから、同等の [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティへのマッピングを行います。  
  
 プロバイダーへの [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の実装については、「[マネージド コードの UI オートメーション プロバイダー](ui-automation-providers-for-managed-code.md)」を参照してください。 コントロール パターンを実装する方法については、「 [UI Automation Control Patterns](ui-automation-control-patterns.md) 」および「 [UI Automation Text Pattern](ui-automation-text-pattern.md)」を参照してください。  
  
## <a name="ui-automation-in-a-client"></a>クライアントにおける UI オートメーション  

 多くの自動テスト ツールやシナリオの目的は、一貫性があって再現可能なユーザー インターフェイス操作です。 これには、特定のコントロールの単体テストから、コントロールのグループに対する一連の一般的なアクションを反復処理するテスト スクリプトの記録と再生までが含まれます。  
  
 自動アプリケーションでの問題は、動的な対象にテストを合わせることが難しい点です。 たとえば、Windows タスク マネージャーに含まれているような、現在実行中のアプリケーションを一覧表示するリスト ボックス コントロールがあります。 リスト ボックス内の項目はテスト アプリケーションの制御範囲外で動的に更新されるため、リスト ボックスの特定の項目を一貫性を保って繰り返し選択することは不可能です。 テスト アプリケーションの制御範囲外の [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] でフォーカスの単純な変更を繰り返そうとした場合も、同様の問題が起きることがあります。  
  
### <a name="programmatic-access"></a>プログラムによるアクセス  

 プログラムによるアクセスでは、従来のマウス入力やキーボード入力によって公開される対話やエクスペリエンスをコードによって模倣する機能が提供されます。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] は、5 つのコンポーネントにより、プログラムによるアクセスを有効にします。  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーは、 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]の構造全体にわたってナビゲーションを容易にします。 ツリーは、hWnd のツリーのコレクションから構築されます。 詳細については、「 [UI Automation Tree Overview](ui-automation-tree-overview.md)」を参照してください。  
  
- オートメーション要素は、 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]の個々のコンポーネントです。 通常、これらは hWnd よりも細かい単位です。 詳細については、「 [UI Automation Control Types Overview](ui-automation-control-types-overview.md)」を参照してください。  
  
- オートメーション プロパティは、 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 要素に関する具体的な情報を提供します。 詳細については、「 [UI Automation Properties Overview](ui-automation-properties-overview.md)」を参照してください。  
  
- コントロール パターンは、コントロールが持つ機能の特定の側面を定義します。プロパティ、メソッド、イベント、および構造体の情報で構成することができます。 詳細については、「 [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md)」を参照してください。  
  
- オートメーション イベントは、イベント通知と情報を提供します。 詳細については、「 [UI Automation Events Overview](ui-automation-events-overview.md)」を参照してください。  
  
### <a name="key-properties-for-test-automation"></a>自動テストの主要なプロパティ  

 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 内の任意のコントロールを一意に識別して検索する機能は、自動テスト アプリケーションがその [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]を処理する基盤です。 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] プロパティの中にはこれを支援するものがいくつかあり、クライアントとプロバイダーによって使用されます。  
  
#### <a name="automationid"></a>AutomationID  

 オートメーション要素をその兄弟から一意に識別します。 製品が複数言語で出荷される場合に通常ローカライズされる<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> などのプロパティとは異なり、 <xref:System.Windows.Automation.AutomationElement.NameProperty> はローカライズされません。 「 [Use the AutomationID Property](use-the-automationid-property.md)」を参照してください。  
  
> [!NOTE]
> <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> では、オートメーション ツリー全体にわたって一意に識別できるとは限りません。 たとえば、アプリケーションには複数のトップレベルのメニュー項目を持つメニュー コントロールが含まれ、さらに、それらのメニュー項目に複数の子メニュー項目が含まれている場合があります。 これらの 2 次メニュー項目は、Item1、Item2、Item3 などの汎用スキームで識別され、トップレベルのメニュー項目間で子の識別子が重複することがあります。  
  
#### <a name="controltype"></a>ControlType  

 オートメーション要素によって表されるコントロール型を識別します。 コントロール型がわかると、そこから多くの情報を推測できます。 「 [UI Automation Control Types Overview](ui-automation-control-types-overview.md)」を参照してください。  
  
#### <a name="nameproperty"></a>NameProperty  

 これは、コントロールを識別または説明するテキスト文字列です。 <xref:System.Windows.Automation.AutomationElement.NameProperty> はローカライズされる可能性があるため、注意して使用する必要があります。 「 [UI Automation Properties Overview](ui-automation-properties-overview.md)」を参照してください。  
  
### <a name="implementing-ui-automation-in-a-test-application"></a>テスト アプリケーションへの UI オートメーションの実装  
  
|||  
|-|-|  
|UI オートメーション参照を追加します。|UI オートメーション クライアントに必要な [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の dll を次に示します。<br /><br /> -   UIAutomationClient.dll では、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]のクライアント側 API へのアクセスが提供されます。<br />-   UIAutomationClientSideProvider.dll では、Win32 コントロールを自動化する機能が提供されます。 「 [UI Automation Support for Standard Controls](ui-automation-support-for-standard-controls.md)」を参照してください。<br />-   UIAutomationTypes.dll では、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]で定義された特定の型へのアクセスが提供されます。|  
|<xref:System.Windows.Automation> 名前空間を追加します。|この名前空間には、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のテキスト処理以外の機能を使用するために UI オートメーション クライアントが必要とするすべてのものが含まれています。|  
|<xref:System.Windows.Automation.Text> 名前空間を追加します。|この名前空間には、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のテキスト処理機能を使用するために UI オートメーション クライアントが必要とするすべてのものが含まれています。|  
|目的のコントロールを検索します。|自動テスト スクリプトは、目的のコントロールを表す UI オートメーション要素をオートメーション ツリー内で検索します。<br /><br /> コードで UI オートメーション要素を取得する方法は複数あります。<br /><br /> -   <xref:System.Windows.Automation.Condition> ステートメントを使用して [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] を照会します。 この場合は、通常、言語に依存しない <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> を使用します。 **注意:**  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> は、コントロールの [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティを項目別に示すことができる Inspect.exe などのツールを使用して取得できます。 <br /><br /> -   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー全体またはそのサブセットを検索するには、<xref:System.Windows.Automation.TreeWalker> クラスを使用します。<br />-   フォーカスを追跡します。<br />-   コントロールの hWnd を使用します。<br />-   マウス カーソルの位置など、画面位置を使用します。<br /><br /> 「 [Obtaining UI Automation Elements](obtaining-ui-automation-elements.md)」を参照してください。|  
|コントロール パターンを取得します。|コントロール パターンは、機能的によく似た複数のコントロールにおける共通の動作を公開します。<br /><br /> 自動テスト スクリプトは、テストする必要があるコントロールを特定すると、それらの UI オートメーション要素から目的のコントロール パターンを取得します。 たとえば、一般的なボタン機能には <xref:System.Windows.Automation.InvokePattern> コントロール パターンを、ウィンドウ機能には <xref:System.Windows.Automation.WindowPattern> コントロール パターンを使用します。<br /><br /> 「 [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md)」を参照してください。|  
|UI を自動化します。|自動テスト スクリプトで、 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] フレームワークの任意の [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] を、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] コントロール パターンによって公開された情報や機能を使用して制御できるようになりました。|  
  
## <a name="related-tools-and-technologies"></a>関連ツールと関連技術  

 複数の関連ツールや関連技術で、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を使用した自動テストがサポートされています。  
  
- Inspect.exe は、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の情報を収集してプロバイダーとクライアントを開発およびデバッグするために使用できる グラフィカル ユーザー インターフェイス (GUI) アプリケーションです。 Inspect.exe は Windows SDK に含まれています。  
  
- MSAABridge では、Active Accessibility クライアントに対して [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]情報が公開されます。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] と Active Accessibility の間に継続性を持たせる主な目的は、既存の Active Accessibility クライアントが [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を実装済みの任意のフレームワークと対話できるようにすることです。  
  
## <a name="security"></a>セキュリティ  

 セキュリティについては、「 [UI Automation Security Overview](ui-automation-security-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [UI オートメーションの基礎](index.md)
