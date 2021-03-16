---
description: '詳細情報: <peerTransport>'
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: babc4196c63d46b7515ac67812d5d584eb3ffcac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683620"
---
# \<peerTransport>

カスタム バインドのピア トランスポートを定義します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerTransport>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|listenIpAddress|ピア ノードが TCP メッセージをリッスンする IP アドレスを指定する文字列です。 既定では、 `null`です。|  
|maxBufferPoolSize|バッファー プールの最大サイズを指定する正の整数です。 既定値は 524288 です。<br /><br /> WCF の多くの部分でバッファーが使用されます。 使用するたびに毎回バッファーを作成および破壊すると負荷が高くなります。バッファーのガベージ コレクションも同様です。 バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。 これで、バッファーの作成と破棄のオーバーヘッドを回避できます。|  
|maxReceivedMessageSize|ヘッダーなどのメッセージの最大サイズ (バイト単位) を定義する正の整数。 受信側にとってメッセージが大きすぎると、メッセージの送信側は SOAP エラーを受け取ります。 メッセージは受信者によってドロップされ、トレース ログにこのイベントのエントリが作成されます。 既定値は 65536 です。|  
|port|このバインディングがピア チャネルの TCP メッセージを処理するネットワーク インターフェイス ポートを指定する整数です。 この値の有効値の範囲は <xref:System.Net.IPEndPoint.MinPort> ～ <xref:System.Net.IPEndPoint.MaxPort> です。 既定値は 0 です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|このトランスポートのセキュリティ設定を定義します。 この要素は <xref:System.ServiceModel.Configuration.PeerSecurityElement> 型です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|カスタム バインドのすべてのバインド機能を定義します。|  
  
## <a name="remarks"></a>解説  

 このトランスポートは、要求/応答操作を含むコントラクトと共に使用することはできません。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [トランスポート](../../../wcf/feature-details/transports.md)
- [トランスポートの選択](../../../wcf/feature-details/choosing-a-transport.md)
- [バインド](../../../wcf/bindings.md)
- [バインディングの拡張](../../../wcf/extending/extending-bindings.md)
- [カスタム バインディング](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
