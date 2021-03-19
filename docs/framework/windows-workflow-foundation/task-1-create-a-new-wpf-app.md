---
description: '詳細については、「タスク 1: 新しい Windows Presentation Foundation アプリケーションを作成する」を参照してください。'
title: タスク 1:新しい Windows Presentation Foundation アプリケーションの作成
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 7bbb49e3d663d1878b2b3e150a24f775eeca0135
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755240"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>タスク 1:新しい Windows Presentation Foundation アプリケーションの作成

このタスクでは、WPF Application Visual Studio テンプレートを使用して空の Windows Presentation Foundation (WPF) アプリケーションを作成し、適切なワークフローアセンブリに参照を追加し [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ます。  
  
## <a name="to-create-the-wpf-application-project"></a>WPF アプリケーション プロジェクトを作成するには

1. Visual Studio を開き、[ **ファイル** ] メニューの [ **新規作成**] をポイントし、[ **プロジェクト**] をクリックします。

2. [**新しいプロジェクト**] ダイアログボックスで、ボックスの左側にある [**インストールされたテンプレート**] ペインの [ **Visual C#** ] または [ **Visual Basic** ] を選択します。 選択した言語が表示されない場合は、[ **その他の言語**] を参照してください。

3. [**インストールさ** れたテンプレート] ペインで [ **Windows** ] を選択します。

4. 上部のウィンドウで、ドロップダウンリストボックスで (既定値) **.NET Framework 4** が選択されていることを確認し、[ **WPF アプリケーション**] を選択します。

5. ウィンドウの下部にあるプロジェクトの名前を **HostingApplication** に設定します。

6. ソリューション名を **RehostingTheDesigner** に設定します。

7. [ **OK]** をクリックして、アプリケーションプロジェクトを作成します。 Visual Studio では、アプリケーション用の基本的な WPF UI が作成され、適切な XAML と分離コードファイルが含まれます。

8. **Workflowmodel** アセンブリへの参照を追加します。 これを行うには、 **ソリューションエクスプローラー** で **HostingApplication** プロジェクトを右クリックし、[ **参照の追加**] を選択します。

9. [ **参照の追加** ] ダイアログボックスで、[ **.net** ] タブをクリックし、CTRL キーを押しながら次のアセンブリを選択し、[ **OK**] をクリックします。

    - System.Activities
    - System.Activities.Presentation
    - System.Activities.Core.Presentation

10. ワークフローデザイナーデザインキャンバスをホストする方法については [、「タスク 2: ワークフローデザイナーのホスト](task-2-host-the-workflow-designer.md) 」を参照してください。

## <a name="see-also"></a>関連項目

- [ワークフロー デザイナーのホスト変更](rehosting-the-workflow-designer.md)
- [タスク 2:ワークフロー デザイナーのホスティング](task-2-host-the-workflow-designer.md)
