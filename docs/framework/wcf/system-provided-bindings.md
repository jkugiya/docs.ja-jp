---
title: システム指定のバインド
description: すべてのシステム指定の Windows Communication Foundation (WCF) バインドについて説明します。
ms.date: 06/05/2018
helpviewer_keywords:
- bindings [WCF], system-provided
ms.assetid: 2c243746-45ce-4588-995e-c17126a579a6
ms.openlocfilehash: 3c6c6b628d208aede8c547dcfa66fc189a26ae01
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791509"
---
# <a name="system-provided-bindings"></a>システム指定のバインド

バインディングにより、エンドポイントとの通信で使用する通信メカニズムが指定され、エンドポイントへの接続方法が示されます。 バインディングには次の要素が含まれます。

- プロトコル スタックは、エンドポイントに送信されるメッセージで使用するセキュリティ、信頼性、およびコンテキスト フローの設定を決定します。

- トランスポートは、エンドポイントにメッセージを送信するときに使用する基礎トランスポート プロトコル (TCP または HTTP など) を決定します。

- エンコードでは、エンドポイントに送信されるメッセージに使用するネットワーク エンコードを決定します。 たとえば、テキスト/XML、バイナリ、Message Transmission Optimization Mechanism (MTOM) などです。

 この記事では、すべてのシステム指定の Windows Communication Foundation (WCF) バインドについて説明します。 このバインドがいずれもアプリケーションの条件に適合しない場合は、カスタム バインドを作成できます。 カスタム バインドを作成する方法の詳細については、「[カスタム バインディング](./extending/custom-bindings.md)」を参照してください。

 WS-Federation プロトコルをサポートする、セキュリティで保護された相互操作可能なバインディングを使用すると、フェデレーションに属す組織のユーザーを効率的に認証および承認できます。

> [!IMPORTANT]
> 常にセキュリティを備えたバインディングを選択します。 既定では、[\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) 要素以外のすべてのバインドでセキュリティが有効になっています。 セキュリティで保護されたバインディングを選択しない場合、またはセキュリティを無効にする場合は、セキュリティで保護されたデータ センターや隔離されたネットワークにデータを保存するなど、他の方法でデータを保護してください。

> [!IMPORTANT]
> 他の方法によってデータをセキュリティ保護している場合を除き、セキュリティをサポートしないバインディングやセキュリティが無効になっているバインディングでは、双方向コントラクトを使用しないでください。

次のバインドは WCF に付属します。

|バインド|Configuration 要素|説明|
|-------------|---------------------------|-----------------|
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md)|ASP.NET Web サービス (ASMX) ベースのサービスなど、WS-Basic Profile に適合する Web サービスとの通信に適したバインド。 このバインディングはトランスポートとして HTTP を、既定のメッセージ エンコーディングとして text/XML を使用します。|
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md)|二重のサービス コントラクト以外に適した、セキュリティで保護された相互操作可能なバインディング。|
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../configure-apps/file-schema/wcf/wsdualhttpbinding.md)|二重のサービス コントラクト、または SOAP 中継局を介しての通信に適した、セキュリティで保護された相互操作可能なバインディング。|
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|フェデレーションに属している組織のユーザーを効率的に認証および承認できる、WS-Federation プロトコルをサポートする、セキュリティで保護された相互操作可能なバインド。|
|<xref:System.ServiceModel.NetHttpBinding>|[\<netHttpBinding>](../configure-apps/file-schema/wcf/nethttpbinding.md)|HTTP や WebSocket のサービスを使用するように設計され、既定ではバイナリ エンコードを使用するバインディング。|
|<xref:System.ServiceModel.NetHttpsBinding>|[\<netHttpsBinding>](../configure-apps/file-schema/wcf/nethttpsbinding.md)|HTTP や WebSocket のサービスを使用するように設計され、既定ではバイナリ エンコードを使用するセキュリティで保護されたバインディング。|
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)|WCF アプリケーション間でのコンピューター間通信に適した、セキュリティで保護され、最適化されたバインド。|
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding>](../configure-apps/file-schema/wcf/netnamedpipebinding.md)|WCF アプリケーション間でのコンピューター上の通信に適した、セキュリティで保護され、信頼できる最適化されたバインド。|
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../configure-apps/file-schema/wcf/netmsmqbinding.md)|WCF アプリケーション間でのコンピューター間通信に適した、キューに置かれたバインド。|
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding>](../configure-apps/file-schema/wcf/netpeertcpbinding.md)|セキュリティで保護された、複数のコンピューター通信を可能にするバインディング。|
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding>](../configure-apps/file-schema/wcf/msmqintegrationbinding.md)|WCF アプリケーションと既存のメッセージ キュー アプリケーション間のコンピューター間通信に適したバインド。|
|<xref:System.ServiceModel.BasicHttpContextBinding>|[\<basicHttpContextBinding>](../configure-apps/file-schema/wcf/basichttpcontextbinding.md)|WS-Basic Profile に適合する Web サービスとの通信に適したバインド。HTTP Cookie を使用して、コンテキストをやり取りできるようにします。|
|<xref:System.ServiceModel.NetTcpContextBinding>|[\<netTcpContextBinding>](../configure-apps/file-schema/wcf/nettcpcontextbinding.md)|WCF アプリケーション間でのコンピューター間通信に適した、セキュリティで保護され、最適化されたバインド。SOAP ヘッダーを使用して、コンテキストを交換できるようにします。|
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding>](../configure-apps/file-schema/wcf/webhttpbinding.md)|SOAP メッセージではなく、HTTP 要求を介して公開される WCF Web サービスのエンドポイントを構成するために使用されるバインド。|
|<xref:System.ServiceModel.WSHttpContextBinding>|[\<wsHttpContextBinding>](../configure-apps/file-schema/wcf/wshttpcontextbinding.md)|非双方向サービス コントラクトに適した、セキュリティで保護された相互操作可能なバインド。SOAP ヘッダーを使用して、コンテキストを交換できるようにします。|
|<xref:System.ServiceModel.UdpBinding>|[\<udpBinding>](../configure-apps/file-schema/wcf/udpbinding.md)|単純なメッセージを複数のクライアントに同時に送信するために使用されるバインディング。|

 各システム指定のバインディングの機能を次の表に示します。 各バインディングをこの表の列に示します。機能とその説明は 2 番目の表の行に示します。 次の表に、使用されるバインディングの省略形のキーを示します。 バインディングを選択するには、必要な行の機能がすべて含まれる列を調べます。

|バインド|相互運用性|セキュリティ (既定)|Session<br />(既定値)。|トランザクション|二重|エンコード (かっこ内は既定値)|ストリーム<br />(既定値)。|
|-------------|----------------------|--------------------------|-----------------------------|------------------|------------|--------------------------|-------------------------------|
|<xref:System.ServiceModel.BasicHttpBinding>|Basic Profile 1.1|(なし)、トランスポート、メッセージ、混在|(なし)|(なし)|N/A|テキスト、(MTOM)|はい<br />(buffered)|
|<xref:System.ServiceModel.WSHttpBinding>|WS|トランスポート、(メッセージ)、混在|(なし)、信頼できるセッション、セキュリティ保護されたセッション|(なし)、あり|N/A|(テキスト)、MTOM|いいえ|
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|(メッセージ)、なし|(信頼できるセッション)、セキュリティ保護されたセッション|(なし)、あり|はい|(テキスト)、MTOM|いいえ|
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|(メッセージ)、混在、なし|(なし)、信頼できるセッション、セキュリティ保護されたセッション|(なし)、あり|いいえ|(テキスト)、MTOM|いいえ|
|<xref:System.ServiceModel.NetHttpBinding>|.NET|(なし)、トランスポート、メッセージ、TransportWithMessageCredential、TransportCredentialOnly|下記のメモを参照|なし|下記のメモを参照|(バイナリ)、テキスト、MTOM|〇 (バッファリング)|
|<xref:System.ServiceModel.NetHttpsBinding>|.NET|(トランスポート)、TransportWithMessageCredential|下記のメモを参照|なし|下記のメモを参照|(バイナリ)、テキスト、MTOM|はい<br />(buffered)|
|<xref:System.ServiceModel.NetTcpBinding>|.NET|(トランスポート)、メッセージ、なし、混在|(トランスポート)、信頼できるセッション、セキュリティ保護されたセッション|(なし)、あり|はい|Binary|はい<br />(buffered)|
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|(トランスポート)、なし|なし、(トランスポート)|(なし)、あり|はい|Binary|はい<br />(buffered)|
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|メッセージ、(トランスポート)、なし|(なし)、トランスポート|なし、(あり)|いいえ|Binary|いいえ|
|<xref:System.ServiceModel.NetPeerTcpBinding>|ピア|(トランスポート)|(なし)|(なし)|はい||いいえ|
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|(トランスポート)|(なし)|なし、(あり)|N/A|N/A|いいえ|
|<xref:System.ServiceModel.BasicHttpContextBinding>|Basic Profile 1.1|(なし)、トランスポート、メッセージ、混在|(なし)|(なし)|N/A|テキスト、(MTOM)|はい<br />(buffered)|
|<xref:System.ServiceModel.NetTcpContextBinding>|.NET|(トランスポート)、メッセージ、なし、混在|(トランスポート)、信頼できるセッション、セキュリティ保護されたセッション|(なし)、あり|はい|Binary|はい<br />(buffered)|
|<xref:System.ServiceModel.WSHttpContextBinding>|WS|トランスポート、(メッセージ)、混在|(なし)、信頼できるセッション、セキュリティ保護されたセッション|(なし)、あり|N/A|テキスト、(MTOM)|いいえ|
|<xref:System.ServiceModel.UdpBinding> <br /><br /> **注:** 相互運用性は、このバインドで実装される標準の UDP 上の SOAP 仕様を実装することによって実現できます。|.NET|(なし)|(なし)|(なし)|N/A|(テキスト)|いいえ|

> [!IMPORTANT]
> <xref:System.ServiceModel.NetHttpBinding> は、HTTP や WebSocket のサービスを使用するために設計されたバインドで、既定ではバイナリ エンコードを使用します。 <xref:System.ServiceModel.NetHttpBinding> は、要求/応答コントラクトと二重コントラクトのどちらで使用されているかを検出し、一致するように動作を変更します。要求/応答には HTTP、二重には WebSocket を使用します。 この動作は、次の <xref:System.ServiceModel.Channels.WebSocketTransportUsage> バインド設定を使用してオーバーライドできます。WhenDuplex - これが既定値であり、上述のように動作します。 Never - Websocket が使用されないようにします。 この設定で二重コントラクトを使用しようとすると、例外が発生します。 Always - 要求-応答コントラクトでも Websocket が使用されるようにします。 NetHttpBinding では、HTTP モードと WebSocket モードの両方で信頼できるセッションがサポートされます。 WebSocket モードでは、セッションがトランスポートによって提供されます。

 次の表では、前の表に示された機能について説明します。

|機能|説明|
|-------------|-----------------|
|相互運用性の種類|バインディングによる相互操作を可能にするプロトコルまたはテクノロジに名前を付けます。|
|セキュリティ|チャネルをセキュリティで保護する方法を指定します。<br />- なし: SOAP メッセージはセキュリティで保護されず、クライアントは認証されません。<br />- トランスポート: セキュリティ要件はトランスポート層で満たされます。<br />- メッセージ: セキュリティ要件はメッセージ層で満たされます。<br />- 混在: クレームはメッセージに含まれ、整合性と機密性の要件がトランスポート層で満たされます。|
|Session|このバインディングでセッション コントラクトをサポートするかどうかを指定します。|
|トランザクション|トランザクションが有効かどうかを指定します。|
|二重|二重のコントラクトがサポートされているかどうかを指定します。 この機能はバインディングでセッションをサポートする必要があることに注意してください。|
|Encoding|メッセージのネットワーク上での形式を指定します。 次の値を使用できます。<br />- テキスト: UTF-8 など。<br />- バイナリ<br />- Message Transmission Optimization Mechanism (MTOM): SOAP エンベロープのコンテキスト内でバイナリ XML 要素を効率的にエンコードするためのメソッドです。|
|ストリーム|受信メッセージおよび送信メッセージに対してストリーミングをサポートするかどうかを指定します。 バインディングで `TransferMode` プロパティを使用して値を設定します。 次の値を使用できます。<br />- <xref:System.ServiceModel.TransferMode.Buffered>: 要求メッセージと応答メッセージの両方がバッファリングされます。<br />- <xref:System.ServiceModel.TransferMode.Streamed>: 要求メッセージと応答メッセージの両方がストリーミングされます。<br />- <xref:System.ServiceModel.TransferMode.StreamedRequest>: 要求メッセージがストリーミングされ、応答メッセージがバッファリングされます。<br />- <xref:System.ServiceModel.TransferMode.StreamedResponse>: 要求メッセージがバッファリングされ、応答メッセージがストリーミングされます。|

## <a name="see-also"></a>関連項目

- [エンドポイントの作成の概要](endpoint-creation-overview.md)
- [サービスとクライアントを構成するためのバインディングの使用](using-bindings-to-configure-services-and-clients.md)
- [基本的な WCF プログラミング](basic-wcf-programming.md)
