---
title: 基本的なプログラミング ライフサイクル
description: WCF アプリケーションを構築するためのタスクについて説明します。 WCF を使用すると、アプリは、同じコンピューター、ネットワーク経由、または異なるアプリケーション プラットフォーム上で通信できます。
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: f958bd06f617a5648b31332ebe9e7662d45cd241
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294847"
---
# <a name="basic-programming-lifecycle"></a>基本的なプログラミング ライフサイクル

Windows Communication Foundation (WCF) を使用すると、アプリケーションは、同一のコンピューター上、インターネット経由、異なるアプリケーション プラットフォーム上のいずれに存在していても通信できます。 ここでは、WCF アプリケーションを構築するために必要なタスクについて概説します。 実際のサンプル アプリケーションについては、「[チュートリアル入門](getting-started-tutorial.md)」参照してください。  
  
## <a name="the-basic-tasks"></a>基本的なタスク  

 基本的な作業は、次の順序で行います。  
  
1. サービス コントラクトを定義します。 サービス コントラクトでは、サービスの署名、交換するデータ、およびコントラクトに必要なその他のデータを指定します。 詳細については、「[サービス コントラクトの設計](designing-service-contracts.md)」を参照してください。  
  
2. コントラクトを実装します。 サービス コントラクトを実装するには、そのコントラクトを実装するクラスを作成し、ランタイムに必要なカスタム動作を指定します。 詳細については、「[サービス コントラクトの実装](implementing-service-contracts.md)」を参照してください。  
  
3. エンドポイントおよびその他の動作情報を指定して、サービスを構成します。 詳細については、「[サービスの構成](configuring-services.md)」を参照してください。  
  
4. サービスをホストします。 詳細については、「[ホスティング サービス](hosting-services.md)」を参照してください。  
  
5. クライアント アプリケーションを構築します。 詳細については、「[クライアントを構築する](building-clients.md)」を参照してください。  
  
 このセクションのトピックではこの順に従って説明しますが、手順を最初から実行しないシナリオもあります。 たとえば、既存のサービスを使用するクライアントを構築する場合は、手順 5. から開始します。 また、既存のクライアント アプリケーションが使用するサービスを構築する場合は、手順 5. を省略できます。  
  
 サービス コントラクトの開発について理解したら、「[拡張機能の概要](introduction-to-extensibility.md)」に目を通すこともできます。 サービスで問題が発生した場合は、「[WCF トラブルシューティング クイックスタート](wcf-troubleshooting-quickstart.md)」をチェックし、同様の問題が他で発生していないかどうかを確認してください。  
  
## <a name="see-also"></a>関連項目

- [サービス コントラクトの実装](implementing-service-contracts.md)
