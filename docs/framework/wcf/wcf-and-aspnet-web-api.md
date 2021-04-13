---
title: WCF と ASP.NET Web API
description: 各テクノロジの主な機能を比較することにより、WCF と ASP.NET Web API のどちらがニーズに適しているかを説明します。
ms.date: 03/30/2017
ms.assetid: 08ceded3-fd9a-4467-9715-c4cbd9c7228e
ms.openlocfilehash: b3a905f890b4dfa9f60c906c3a242be60921e5c8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273595"
---
# <a name="wcf-and-aspnet-web-api"></a>WCF と ASP.NET Web API

WCF は、サービス指向のアプリケーションを構築するための Microsoft の統一プログラミング モデルです。 これを使用して開発者は、プラットフォーム間を統合し、既存のコンポーネントと相互運用する、セキュリティで保護された信頼性の高いトランザクション型のソリューションを構築できます。 [ASP.NET Web API](https://www.asp.net/web-api) は、ブラウザーやモバイル デバイスなどを含む多様なクライアントに提供できる HTTP サービスの構築が容易になるフレームワークです。 ASP.NET Web API は、.NET Framework に基づいて RESTful アプリケーションを構築するのに最適なプラットフォームです。 このトピックでは、ニーズに最適なテクノロジを決定するのに役立つガイドラインを示します。  
  
## <a name="choosing-which-technology-to-use"></a>使用するテクノロジの選択  

 各テクノロジの主な機能を次の表に示します。  
  
|WCF|ASP.NET Web API|  
|---------|---------------------|  
|複数のトランスポート プロトコル (HTTP、TCP、UDP、およびカスタム トランスポート) をサポートするサービスを構築し、構築したサービスを切り替えることができます。|HTTP のみ。 HTTP 用のファーストクラスのプログラミング モデルです。 広範囲のアクセスを実現できるさまざまなブラウザーやモバイル デバイスなどからのアクセスにより適しています。|  
|メッセージの種類が同じ複数のエンコーディング (テキスト、MTOM、およびバイナリ) をサポートするサービスを構築し、構築したサービスを切り替えることができます。|XML や JSON などのさまざまなメディアの種類をサポートする Web API を構築できます。|  
|Reliable Messaging、Transactions、Message Security などの WS-* 標準を使用してサービスを構築できます。|HTTP、WebSocket、SSL、JSON、XML など、基本的なプロトコルと形式を使用します。 Reliable Messaging や Transactions などの高レベルのプロトコルはサポートされません。|  
|要求/応答、一方向、および双方向の各メッセージ交換パターンをサポートしています。|HTTP は要求/応答ですが、[SignalR](https://github.com/SignalR/SignalR) と WebSocket の統合を通じて追加のパターンをサポートできます。|  
|WCF SOAP サービスは WSDL で記述でき、スキーマが複雑なサービスの場合でも自動化ツールを使用してクライアント プロキシを生成できます。|スニペットを記述する自動生成された HTML ヘルプ ページから OData で統合された API 用に構造化されたメタデータまで、Web API を記述するためのさまざまな方法があります。|  
|.NET Framework に付属しています。|.NET Framework に付属していますが、オープンソースであるため、個別のダウンロードとして帯域外でも使用できます。|  
  
 WCF を使用すると、さまざまなトランスポートを経由してアクセスできる、信頼性が高くセキュリティで保護された Web サービスを作成できます。 ASP.NET Web API を使用すると、さまざまなクライアントからアクセスできる HTTP ベースのサービスを作成できます。 ASP.NET Web API は、新しい REST スタイルのサービスを作成および設計する場合に使用します。 WCF では REST スタイルのサービスの作成を一部サポートしていますが、ASP.NET Web API の REST のサポートはより詳細で、以降の REST 機能の強化は ASP.NET Web API で行われる予定です。 既存の WCF サービスがあり、追加の REST エンドポイントを公開する場合は、WCF および <xref:System.ServiceModel.WebHttpBinding> を使用してください。  
  
## <a name="see-also"></a>関連項目

- [Windows Communication Foundation とは](whats-wcf.md)
- [Windows Communication Foundation の基本概念](fundamental-concepts.md)
