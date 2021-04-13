---
title: '方法: Net.TCP ポート共有サービスを有効にする'
description: 既定では無効になっている Net.TCP を有効にするために、MMC を使用して Net TCP ポート共有サービスを構成する方法について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 7200d82e4a45ce9e36b2a4cec3d0c08e1a5f00ab
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265467"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a>方法: Net.TCP ポート共有サービスを有効にする

Windows Communication Foundation (WCF) では Net.TCP ポート共有サービスと呼ばれる Windows サービスを使用し、複数のプロセス間での TCP ポート共有を実現します。 このサービスは WCF の一部としてインストールされますが、セキュリティ予防措置として既定では有効になっていません。したがって、初めて使用する前に手動で有効にする必要があります。 このトピックでは、Microsoft 管理コンソール (MMC) スナップインを使用して、Net TCP ポート共有サービスを設定する方法について説明します。  
  
 Net.TCP ポート共有サービスを有効にして手動で開始したら、「[方法: ポート共有を使用するように WCF サービスを構成する](how-to-configure-a-wcf-service-to-use-port-sharing.md)」を参照して、このサービスを使用できるようにユーザーのサービスを構成する方法を確認します。  
  
 net.tcp://ポート共有を使用するサンプルについては、「[Net.TCP ポート共有のサンプル](../samples/net-tcp-port-sharing-sample.md)」を参照してください。  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a>MMC を使用して Net.TCP ポート共有サービスを有効にするには  
  
1. [スタート] メニューから、コマンド プロンプト ウィンドウを開いて「`services.msc`」と入力するか、[ファイル名を指定して実行] を開いて [名前] ボックスに「`services.msc`」と入力し、サービス管理コンソールを開きます。  
  
2. サービス リストの **[名前]** 列の **[Net.Tcp ポート共有サービス]** を右クリックして、メニューの **[プロパティ]** をクリックします。  
  
3. サービスの手動起動を有効にするには、 **[プロパティ]** ウィンドウの **[全般]** タブをクリックし、 **[スタートアップの種類]** ボックスの [手動] を選択して、 **[適用]** をクリックします。  
  
4. サービスを開始するには、サービス状態領域の **[開始]** ボタンをクリックします。 これで、サービスの状態には "開始" が表示されます。  
  
5. **[OK]** をクリックしてサービス リストに戻り、MMC コンソールを終了します。  
  
## <a name="example"></a>例  
  
## <a name="see-also"></a>関連項目

- [Net.TCP ポート共有](net-tcp-port-sharing.md)
- [Net.TCP ポート共有サービスを構成する](configuring-the-net-tcp-port-sharing-service.md)
