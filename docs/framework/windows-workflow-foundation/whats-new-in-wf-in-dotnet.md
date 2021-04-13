---
title: .NET Framework 4.5 での Windows Workflow Foundation の新機能
description: .NET Framework 4.5 の Windows Workflow Foundation には、新しいアクティビティ、デザイナー機能、ワークフロー開発モデルなど、多くの新機能が導入されています。
ms.date: 03/30/2017
ms.assetid: 195c43a8-e0a8-43d9-aead-d65a9e6751ec
ms.openlocfilehash: 0d7086fd5ff9bfa410568a74092be3e29f732e23
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697910"
---
# <a name="whats-new-in-windows-workflow-foundation-in-net-framework-45"></a>.NET Framework 4.5 での Windows Workflow Foundation の新機能

.NET Framework 4.5 の Windows Workflow Foundation (WF) には、新しいアクティビティ、デザイナー機能、ワークフロー開発モデルなど、多くの新機能が導入されています。 .NET Framework 4.5 で導入された新しいワークフロー機能の多く (ただし、すべてではありません) は、ホストを変更したワークフロー デザイナーでサポートされています。 サポートされる新機能の詳細については、「[再ホストされたワークフロー デザイナーにおける Workflow Foundation 4.5 の新機能のサポート](wf-features-in-the-rehosted-workflow-designer.md)」を参照してください。 .NET Framework 3.0 および .NET Framework 3.5 のワークフロー アプリケーションを移行して最新バージョンを使用する方法の詳細については、「[移行ガイダンス](migration-guidance.md)」を参照してください。 この記事では、.NET Framework 4.5 で導入された新しいワークフロー機能の概要について説明します。

> [!WARNING]
> .NET Framework 4.5 で導入された新しい Windows Workflow Foundation 機能は、以前のバージョンのフレームワークを対象とするプロジェクトには使用できません。 .NET Framework 4.5 を対象とするプロジェクトの対象を以前のバージョンのフレームワークに変更すると、いくつかの問題が発生する場合があります。
>
> - デザイナーでは、C# の式が「**値が XAML で設定されました**」というメッセージに置き換えられます。
> - 次のエラーを含む、多くのビルド エラーが発生します。
>
> **現在のターゲット フレームワークと互換性のないファイル形式です。ファイル形式を変換するにはファイルを明示的に保存してください。このエラー メッセージは、ファイルを保存してデザイナーを開き直すと表示されなくなります。**

## <a name="workflow-versioning"></a><a name="BKMK_Versioning"></a> ワークフローのバージョン管理

.NET Framework 4.5 では、新しい <xref:System.Activities.WorkflowIdentity> クラスに基づいて、いくつかの新しいバージョン管理機能が導入されました。 <xref:System.Activities.WorkflowIdentity> には、ワークフロー アプリケーションの作成者向けに、永続化されたワークフロー インスタンスをその定義でマップするメカニズムが備わっています。

- <xref:System.Activities.WorkflowApplication> ホスティングを使用する開発者は、<xref:System.Activities.WorkflowIdentity> を使用して、ワークフローの複数のバージョンを同時にホストできます。 永続化されたワークフロー インスタンスは新しい <xref:System.Activities.WorkflowApplicationInstance> クラスを使用して読み込むことができ、ホストは <xref:System.Activities.WorkflowApplicationInstance.DefinitionIdentity%2A> を使用して、<xref:System.Activities.WorkflowApplication> のインスタンス化時に適切なバージョンのワークフロー定義を提供できます。 詳細については、「[WorkflowIdentity と Versioning の使用](using-workflowidentity-and-versioning.md)」および「[方法: ワークフローの複数のバージョンを同時にホストする](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)」を参照してください。

- 現在、<xref:System.ServiceModel.WorkflowServiceHost> は複数のバージョンのホストです。 ワークフロー サービスの新しいバージョンを配置すると、新しいインスタンスが新しいサービスを使用して作成されますが、既存のインスタンスは以前のバージョンを使用して完了します。 詳細については、「[WorkflowServiceHost による side-by-side でのバージョン管理](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md)」を参照してください。

- 永続化されたワークフロー インスタンスの定義を更新するためのメカニズムを提供する動的更新が導入されました。 詳細については、「[動的な更新](dynamic-update.md)」および「[方法: 実行中のワークフロー インスタンスの定義を更新する](how-to-update-the-definition-of-a-running-workflow-instance.md)」を参照してください。

- SqlWorkflowInstanceStoreSchemaUpgrade.sql データベース スクリプトは、.NET Framework 4 データベース スクリプトを使用して作成された永続性データベースをアップグレードするために用意されています。 このスクリプトにより、.NET Framework 4.5 で導入された新しいバージョン管理機能をサポートするように .NET Framework 4 永続性データベースが更新されます。 データベースで永続化されたワークフロー インスタンスは、既定のバージョン番号が付与されるため、side-by-side 実行および動的更新に参加できるようになります。 詳細については、「[ワークフローのバージョン管理をサポートする .NET Framework 4 永続性データベースのアップグレード](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)」を参照してください。

## <a name="activities"></a><a name="BKMK_NewActivities"></a> アクティビティ

組み込みのアクティビティ ライブラリには、既存のアクティビティ用の新しいアクティビティと新しい機能が含まれています。

### <a name="nopersist-scope"></a><a name="BKMK_NoPersistScope"></a>NoPersistScope

<xref:System.Activities.Statements.NoPersistScope> は、NoPersistScope の子アクティビティの実行時にワークフローが永続化されないようにする新しいコンテナー アクティビティです。 これは、ワークフローがファイル ハンドルなどのコンピューター固有のリソースを使用している場合、データベース トランザクション中など、ワークフローの永続化が適切でないシナリオで役立ちます。 以前のバージョンでは、アクティビティ実行中に永続化されないようにするために、<xref:System.Activities.NativeActivity> を使用したカスタム <xref:System.Activities.NoPersistHandle> が必要でした。

### <a name="new-flowchart-capabilities"></a><a name="BKMK_NewFlowchartCapabilities"></a> フローチャートの新機能

.NET Framework 4.5 用に更新されたフローチャートには、次の新機能があります。

- `DisplayName` アクティビティまたは <xref:System.Activities.Statements.FlowSwitch%601> アクティビティの <xref:System.Activities.Statements.FlowDecision> プロパティは編集できます。 これにより、アクティビティ デザイナーではアクティビティの目的に関する詳細な情報を表示できます。

- フローチャートには <xref:System.Activities.Statements.Flowchart.ValidateUnconnectedNodes%2A> という新しいプロパティがあります。このプロパティの既定値は `False` です。 このプロパティを `True` に設定すると、接続されていないフローチャート ノードでは検証エラーが発生します。

## <a name="support-for-partial-trust"></a>部分信頼のサポート

.NET Framework 4 のワークフローでは、完全に信頼されたアプリケーション ドメインが必要でした。 .NET Framework 4.5 では、ワークフローを部分信頼環境で動作させることができます。 部分信頼環境では、サード パーティのコンポーネントは、ホストのリソースに対するフル アクセスを許可しなくても使用できます。 部分信頼でのワークフローの実行に関する問題は次のとおりです。

1. 部分信頼環境では、<xref:System.Activities.Statements.Interop> アクティビティに含まれるレガシ コンポーネント (規則など) を使用することはできません。

2. <xref:System.ServiceModel.WorkflowServiceHost> において部分信頼でワークフローを実行することはできません。

3. 部分信頼シナリオで例外を永続化すると、セキュリティ上の脅威になる可能性があります。 例外の永続化を無効にするには、例外が永続化されないように <xref:System.Activities.ExceptionPersistenceExtension> 型の拡張機能をプロジェクトに追加する必要があります。 この型を実装する方法を示したコード例を次に示します。

    ```csharp
    public class ExceptionPersistenceExtension
    {
        public ExceptionPersistenceExtension()
        {
            this.PersistExceptions = false;
        }
        public bool PersistExceptions { get; set; }
    }
    ```

     例外がシリアル化されない場合は、例外が <xref:System.Activities.Statements.NoPersistScope> 内で使用されていることを確認してください。

4. アクティビティの作成者は、<xref:System.Activities.Activity.CacheMetadata%2A> をオーバーライドして、ワークフロー ランタイムが型に対してリフレクションを自動的に実行しないようにする必要があります。 引数と子アクティビティには null 以外を指定する必要があり、<xref:System.Activities.ActivityMetadata.Bind%2A> は明示的に呼び出す必要があります。 <xref:System.Activities.Activity.CacheMetadata%2A> のオーバーライドの詳細については、「[CacheMetadata を使用したデータの公開](exposing-data-with-cachemetadata.md)」を参照してください。 また、型が `internal` または **private** の引数のインスタンスは、リフレクションによって作成されないように、<xref:System.Activities.Activity.CacheMetadata%2A> で明示的に作成される必要があります。

5. 型は、シリアル化に <xref:System.Runtime.Serialization.ISerializable> または <xref:System.SerializableAttribute> を使用しません。シリアル化する型では、<xref:System.Runtime.Serialization.DataContractSerializer> をサポートする必要があります。

6. <xref:System.Activities.Expressions.LambdaValue%601> を使用する式は <xref:System.Security.Permissions.ReflectionPermissionAttribute.RestrictedMemberAccess%2A> を必要とするため、部分信頼では動作しません。 <xref:System.Activities.Expressions.LambdaValue%601> を使用するワークフローでは、これらの式を、<xref:System.Activities.CodeActivity%601> から派生するアクティビティと置き換える必要があります。 .

7. 部分信頼では、<xref:System.Activities.XamlIntegration.TextExpressionCompiler> または Visual Basic でホストされているコンパイラを使用して式をコンパイルすることはできませんが、以前コンパイルされた式を実行することはできます。

8. [レベル 2 の透過性](../misc/security-transparent-code-level-2.md)を使用する 1 つのアセンブリは、.NET Framework 4、[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] (完全な信頼)、および [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] (部分信頼) では使用できません。

## <a name="new-designer-capabilities"></a><a name="BKMK_NewDesignerCapabilites"></a> デザイナーの新機能

### <a name="designer-search"></a><a name="BKMK_DesignerSearch"></a> デザイナーでの検索

より大規模なワークフローを管理しやすくするために、キーワードでワークフローを検索できるようになりました。 この機能は Visual Studio でのみ使用できます。再ホストされたデザイナーではこの機能を使用できません。 利用できる検索機能には 2 種類あります。

- クイック検索 (**Ctrl+F** キーまたは **[編集]** 、 **[検索と置換]** 、 **[クイック検索]** で開始します)。

- フォルダーを指定して検索 (**Ctrl+Shift+F** キーまたは **[編集]** 、 **[検索と置換]** 、 **[フォルダーを指定して検索]** で開始します)。

置換はサポートされていません。

#### <a name="quick-find"></a><a name="BKMK_QuickFind"></a> クイック検索

ワークフロー内で検索されるキーワードは、次のデザイナー項目に一致します。

- <xref:System.Activities.Activity> オブジェクト、<xref:System.Activities.Statements.FlowNode> オブジェクト、<xref:System.Activities.Statements.State> オブジェクト、<xref:System.Activities.Statements.Transition> オブジェクト、およびその他のカスタム フロー制御項目のプロパティ。

- 変数

- 引数

- 式

クイック検索はデザイナーの <xref:System.Activities.Presentation.Model.ModelItem> ツリーで実行されます。 クイック検索は、ワークフロー定義にインポートされた名前空間を検索しません。

#### <a name="find-in-files"></a><a name="BKMK_FindInFiles"></a> フォルダーを指定して検索

ワークフロー内で検索されるキーワードは、ワークフロー ファイルの実際のコンテンツに一致します。 検索結果は Visual Studio の検索結果ビュー ペインに表示されます。 結果の項目をダブルクリックすると、ワークフロー デザイナーで一致を含むアクティビティに移動します。

### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a><a name="BKMK_VariableDeleteContextMenu"></a> 変数および引数デザイナーのコンテキスト メニュー項目の [削除]

.NET Framework 4 では、変数および引数を削除できるのは、デザイナーでキーボードを使用した場合だけでした。 .NET Framework 4.5 以降では、コンテキスト メニューを使用して変数および引数を削除できます。

変数デザイナーと引数デザイナーのコンテキスト メニューを次のスクリーンショットに示しています。

![変数/引数デザイナーのコンテキスト メニュー](./media/whats-new-in-wf-in-dotnet/designer-context-menu.png)

### <a name="auto-surround-with-sequence"></a><a name="BKMK_AutoSurround"></a> ブロックの自動挿入シーケンス

ワークフローまたは特定のコンテナー アクティビティ (<xref:System.Activities.Statements.NoPersistScope> など) には Body アクティビティを 1 つしか含めることができないため、2 つ目のアクティビティを追加するには、開発者が最初のアクティビティを削除し、<xref:System.Activities.Statements.Sequence> アクティビティを追加してから、シーケンス アクティビティに両方のアクティビティを追加する必要がありました。 .NET Framework 4.5 以降では、デザイナー画面に 2 つ目のアクティビティを追加すると、`Sequence` アクティビティが自動的に作成され、両方のアクティビティがラップされます。

次のスクリーンショットは、`WriteLine` の `Body` 内の `NoPersistScope` アクティビティを示しています。

![NoPersistScope アクティビティの Body 内の WriteLine アクティビティ。](./media/whats-new-in-wf-in-dotnet/auto-surround-write-line-activity.png)

次のスクリーンショットは、2 つ目の `WriteLine` を 1 つ目の下にドロップしたときに `Body` 内に自動的に作成された `Sequence` アクティビティを示しています。

![NoPersistScope の Body 内に自動的に作成された Sequence。](./media/whats-new-in-wf-in-dotnet/auto-surround-sequence-activity.png)

### <a name="pan-mode"></a><a name="BKMK_PanMode"></a> パン モード

デザイナーで大規模なワークフロー内をより簡単に移動するには、パン モードを有効にすると、開発者は、スクロール バーを使用する必要なく、ワークフローの表示される部分をクリックおよびドラッグして移動できるようになります。 パン モードをアクティブ化するボタンは、デザイナーの右下隅にあります。

次のスクリーンショットは、ワークフロー デザイナーの右下隅にあるパン ボタンを示しています。

![ワークフロー デザイナーで強調表示されているパン ボタン。](./media/whats-new-in-wf-in-dotnet/pan-button-workflow-designer.png)

マウスの中央ボタンまたは Space キーを使用して、ワークフロー デザイナーをパンすることもできます。

### <a name="multi-select"></a><a name="BKMK_MultiSelect"></a> 複数選択

複数のアクティビティを同時に選択できます。これを行うには、複数のアクティビティを囲むようにドラッグするか (パン モードが無効な場合)、Ctrl キーを押したまま目的のアクティビティを 1 つずつクリックします。

選択した複数のアクティビティは、デザイナー内でドラッグ アンド ドロップすることも、コンテキスト メニューを使用して操作することもできます。

### <a name="outline-view-of-workflow-items"></a><a name="BKMK_DocumentOutline"></a> ワークフロー項目のアウトライン表示

階層ワークフローを移動しやすくするため、ワークフローのコンポーネントはツリー スタイルのアウトライン表示で示されます。 アウトライン表示は、 **[ドキュメント アウトライン]** ビューに表示されます。 このビューを開くには、上部のメニューから **[表示]** 、 **[その他のウィンドウ]** 、 **[ドキュメント アウトライン]** の順に選択するか、Ctrl キーを押しながら W キーと U キーを押します。 アウトライン表示でノードをクリックすると、ワークフロー デザイナーの対応するアクティビティに移動し、アウトライン表示が更新されて、デザイナーで選択されているアクティビティが表示されます。

「[チュートリアル入門](getting-started-tutorial.md)」の完成したワークフローの次のスクリーンショットは、シーケンシャル ワークフローを含むアウトライン表示を示しています。

![Visual Studio のシーケンシャル ワークフローを含むアウトライン表示のスクリーンショット。](./media/whats-new-in-wf-in-dotnet/outline-view-in-workflow-designer.jpg)

### <a name="c-expressions"></a><a name="BKMK_CSharpExpressions"></a> C# の式

.NET Framework 4.5 より前では、ワークフロー内のすべての式を Visual Basic のみで記述できました。 .NET Framework 4.5 では、Visual Basic の式は Visual Basic を使用して作成されたプロジェクトでのみ使用されます。 Visual C# プロジェクトでは、式に C# が使用されるようになりました。 文法強調表示や Intellisense などの機能を備えた、フル機能の C# 式エディターが用意されています。 以前のバージョンで作成された、Visual Basic の式を使用する C# ワークフロー プロジェクトは引き続き動作します。

C# の式はデザイン時に検証されます。 C# 式のエラーは赤い波下線でマークされます。

C# 式の詳細については、「[C# の式](csharp-expressions.md)」を参照してください。

### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a><a name="BKMK_Visibility"></a> シェル バーおよびヘッダー項目の可視性の詳細な制御

再ホストされたデザイナーでは、標準 UI コントロールの中に、特定のワークフローにとって意味がないものもあれば、無効になっているものもあります。 .NET Framework 4 では、このカスタマイズがデザイナーの下部のシェル バーのみでサポートされています。 .NET Framework 4.5 では、デザイナーの上部にあるシェルのヘッダー項目の表示は、<xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> に適切な <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> 値を設定することにより調整できます。

### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a><a name="BKMK_AutoConnect"></a> フローチャートおよびステート マシンのワークフローの自動接続と自動挿入

.NET Framework 4 では、フローチャート ワークフロー内のノード間の接続は手動で追加する必要がありました。 .NET Framework 4.5 では、フローチャートおよびステート マシンのノードに、アクティビティをツールボックスからデザイナー画面上にドラッグすると表示される自動接続ポイントがあります。 アクティビティをこれらのポイントのうち 1 つにドロップすると、アクティビティが必要な接続と共に自動的に追加されます。

次のスクリーンショットは、アクティビティがツールボックスからドラッグされるときに表示されるアタッチ ポイントを示します。

![フローチャートの開始ノードに自動接続ポイントが示されている](./media/whats-new-in-wf-in-dotnet/auto-connect-points-start-node.png)

アクティビティは、フローチャート ノードと状態の間の接続にドラッグすることで、その他 2 つのノード間にノードを自動挿入することもできます。 次のスクリーンショットは、アクティビティをツールボックスからドラッグ アンド ドロップできる、強調表示された接続線を示しています。

![アクティビティをドロップするための自動挿入ハンドル](./media/whats-new-in-wf-in-dotnet/auto-insert-connecting-line.png)

### <a name="designer-annotations"></a><a name="BKMK_Annotations"></a> デザイナー注釈

より大規模なワークフローの開発を容易にするため、デザイン プロセスを追跡できるよう注釈の追加がサポートされるようになりました。 注釈は、アクティビティ、状態、フローチャート ノード、変数、および引数に追加できます。 次のスクリーンショットは、デザイナーに注釈を追加するためのコンテキスト メニューを示しています。

![注釈を追加するためのメニューを示すスクリーンショット。](./media/whats-new-in-wf-in-dotnet/designer-annotations-context-menu.png)

### <a name="debugging-states"></a>デバッグ状態

.NET Framework 4 では、アクティビティ以外の要素は、実行の単位ではないため、デバッグ ブレークポイントがサポートされていませんでした。 このリリースでは、<xref:System.Activities.Statements.State> オブジェクトにブレークポイントを追加する機能が用意されています。 ブレークポイントを <xref:System.Activities.Statements.State> に設定した場合、そのエントリ アクティビティまたはトリガーがスケジュールされる前に、状態が遷移すると実行が停止します。

### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a><a name="BKMK_ActivityDelegates"></a> デザイナーでの ActivityDelegate オブジェクトの定義と使用

.NET Framework 4 のアクティビティでは、<xref:System.Activities.ActivityDelegate> オブジェクトを使用して、ワークフローの他の部分がワークフローの実行と対話できる実行ポイントを公開していましたが、通常、これらの実行ポイントを使用するには相当な量のコードが必要でした。 このリリースでは、開発者はワークフロー デザイナーを使用してアクティビティ デリゲートを定義および使用できます。 詳細については、「[ワークフロー デザイナーでアクティビティ デリゲートを定義および使用する方法](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer)」を参照してください。

### <a name="build-time-validation"></a><a name="BKMK_BuildTimeValidation"></a> ビルド時の検証

.NET Framework 4 では、ワークフローの検証エラーが、ワークフロー プロジェクトのビルド中のビルド エラーとして数えられていませんでした。 つまり、ワークフローの検証エラーが発生した場合でも、ワークフロー プロジェクトのビルドは成功している可能性があります。 .NET Framework 4.5 では、ワークフローの検証エラーが発生するとビルドは失敗します。

### <a name="design-time-background-validation"></a><a name="BKMK_DesignTimeValidation"></a> デザイン時バックグラウンド検証

.NET Framework 4 では、ワークフローがフォアグラウンド プロセスとして検証されていました。これにより、複雑または時間のかかる検証プロセスでは UI がブロックされる可能性がありました。 現在、ワークフローの検証はバックグラウンド スレッドで実行されるため、UI がブロックされることはありません。

### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a><a name="BKMK_ViewState"></a> XAML ファイル内で別々の場所にあるビューステート

.NET Framework 4 では、ワークフローのビューステート情報は、多くの異なる場所にある XAML ファイルに保存されていました。 これは、XAML を直接読み取ったり、ビューステート情報を削除するコードを記述したりする開発者にとっては不便です。 .NET Framework 4.5 では、XAML ファイル内のビューステート情報は XAML ファイル内の個別の要素としてシリアル化されています。 開発者は、簡単に、アクティビティのビューステート情報を探して編集したり、ビューステートを完全に削除したりできます。

### <a name="expression-extensibility"></a><a name="BKMK_ExpressionExtensibility"></a> 式の拡張性

.NET Framework 4.5 では、開発者が、ワークフロー デザイナーにプラグインできる、独自の式および式作成操作を作成できるようになります。

### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a><a name="BKMK_BackwardCompatRehostedDesigner"></a> 再ホストされたデザイナーでの Workflow 4.5 機能のオプトイン

下位互換性を維持するために、再ホストされたデザイナーでは、.NET Framework 4.5 に含まれる新機能の一部が既定で有効になっていません。 これは、再ホストされたデザイナーを使用する既存のアプリケーションが、最新バージョンに更新することで壊れないようにするためです。 再ホストされたデザイナーで新機能を有効にするには、<xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> を ".NET Framework 4.5" に設定するか、<xref:System.Activities.Presentation.DesignerConfigurationService> の各メンバーを設定して各機能を有効にします。

## <a name="new-workflow-development-models"></a><a name="BKMK_NewWFModels"></a> 新しいワークフロー開発モデル

このリリースには、フローチャートおよびシーケンシャル ワークフロー開発モデルに加えて、ステート マシンのワークフロー、およびコントラクト優先ワークフロー サービスが含まれています。

### <a name="state-machine-workflows"></a><a name="BKMK_StateMachine"></a> ステート マシン ワークフロー

ステート マシン ワークフローは、.NET Framework 4、バージョン 4.0.1 の一部として [Microsoft .NET Framework 4 Platform Update 1](/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1) で導入されました。 この更新プログラムには、開発者がステート マシンのワークフローを作成できるようにする、いくつかの新しいクラスとアクティビティが含まれていました。 これらのクラスおよびアクティビティは .NET Framework 4.5 用に更新されました。 更新プログラムには次のものが含まれています。

1. 状態にブレークポイントを設定する機能。

2. ワークフロー デザイナーで遷移をコピーして貼り付ける機能。

3. トリガーを共有する遷移の作成に対するデザイナーのサポート。

4. ステート マシンのワークフロー作成に使用するアクティビティ (<xref:System.Activities.Statements.StateMachine><xref:System.Activities.Statements.State>、<xref:System.Activities.Statements.Transition> など)。

次のスクリーン ショットは、「[チュートリアル入門](getting-started-tutorial.md)」の「[方法: ステート マシン ワークフローを作成する](how-to-create-a-state-machine-workflow.md)」のステップで完成したステート マシン ワークフローを示しています。

![完成したステート マシン ワークフローを示す図。](./media/whats-new-in-wf-in-dotnet/complete-state-machine-workflow.jpg)

ステート マシン ワークフローの作成について詳しくは、「[ステート マシン ワークフロー](state-machine-workflows.md)」を参照してください。

### <a name="contract-first-workflow-development"></a><a name="BKMK_ContractFirst"></a> コントラクト優先ワークフローの開発

コントラクト優先ワークフローの開発ツールにより、開発者はコード優先のコントラクトを設計することができ、その後、Visual Studio で数回クリックするだけで、各操作を表すアクティビティ テンプレートをツールボックス内に自動的に生成できます。 これらのアクティビティは、コントラクトで定義された操作を実装するワークフローを作成するために使用されます。 ワークフロー デザイナーは、ワークフロー サービスを検証し、これらの操作が実装され、ワークフローの署名がコントラクトの署名と一致することを確認します。 また、開発者は、ワークフロー サービスを、実装済みコントラクトのコレクションと関連付けることもできます。 コントラクト優先ワークフロー サービスの開発について詳しくは、「[既存のサービス コントラクトを使用するワークフロー サービスを作成する方法](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)」を参照してください。
