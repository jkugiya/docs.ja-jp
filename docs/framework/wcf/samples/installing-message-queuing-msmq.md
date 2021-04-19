---
title: メッセージ キュー (MSMQ) のインストール
description: 1 回限りのセットアップ手順の一部として、WFC サンプルで使用するメッセージ キュー 4.0 とメッセージ キュー 3.0 をインストールする方法について説明します。
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: bf33a5cd899bf2d7ef4947c51ac1723c8eb80c29
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281873"
---
# <a name="installing-message-queuing-msmq"></a>メッセージ キュー (MSMQ) のインストール

メッセージ キュー 4.0 およびメッセージ キュー 3.0 をインストールする方法を次の手順に示します。  
  
> [!NOTE]
> Windows XP および Windows Server 2003 では、メッセージ キュー 4.0 は使用できません。  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a>Windows Server 2008 または Windows Server 2008 R2 にメッセージ キュー 4.0 をインストールするには  
  
1. サーバー マネージャーで **[機能]** をクリックします。  
  
2. **[機能の概要]** の右側のペインで、 **[機能の追加]** をクリックします。  
  
3. 表示されたウィンドウで **[メッセージ キュー]** を展開します。  
  
4. **[メッセージ キュー サービス]** を展開します。  
  
5. **[ディレクトリ サービス統合]** をクリックし (ドメインに参加するコンピューターの場合)、 **[HTTP サポート]** をクリックします。  
  
6. **[次へ]** をクリックし、 **[インストール]** をクリックします。  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a>Windows 7 または Windows Vista にメッセージ キュー 4.0 をインストールするには  
  
1. **[コントロール パネル]** を開きます。  
  
2. **[プログラム]** をクリックし、 **[プログラムと機能]** の **[Windows の機能の有効化または無効化]** をクリックします。  
  
3. [Microsoft Message Queue (MSMQ) Server]、[Microsoft Message Queue (MSMQ) Server Core] の順に展開して、インストールする次のメッセージ キュー機能のチェック ボックスをオンにします。  
  
    - [MSMQ Active Directory Domain Services Integration] (ドメインに参加するコンピューターの場合)  
  
    - [MSMQ HTTP サポート]  
  
4. **[OK]** をクリックします。  
  
5. コンピューターを再起動するよう求められた場合は、 **[OK]** をクリックしてインストールを完了します。  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a>Windows XP および Windows Server 2003 にメッセージ キュー 3.0 をインストールするには  
  
1. **[コントロール パネル]** を開きます。  
  
2. **[プログラムの追加と削除]** 、 **[Windows コンポーネントの追加と削除]** の順にクリックします。  
  
3. メッセージ キューを選択し、 **[詳細]** をクリックします。  
  
    > [!NOTE]
    > Windows Server 2003 を実行している場合は、メッセージ キューにアクセスするアプリケーション サーバーを選択します。  
  
4. 詳細ページで、[MSMQ HTTP サポート] オプションが選択されていることを確認します。  
  
5. **[OK]** をクリックして詳細ページを閉じ、 **[次へ]** をクリックします。 インストールを完了します。  
  
6. コンピューターを再起動するよう求められた場合は、 **[OK]** をクリックしてインストールを完了します。  
  
## <a name="see-also"></a>関連項目

- [セットアップ手順](set-up-instructions.md)
