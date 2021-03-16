---
description: '詳細情報: <oneWay>'
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: 8e3314dd14525b5f7585a7336c00b615da56d1c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683841"
---
# \<oneWay>

カスタム バインドのパケット ルーティングを有効にし、一方向メソッドを使用できるようにします。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oneWay>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`packetRoutable`|パケット ルーティングが有効かどうかを示すブール値。 既定では、 `false`です。|  
|`MaxAcceptedChannels`|許容できるチャネルの最大数を指定する整数。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<channelPoolSettings>](channelpoolsettings.md)|現在のチャネルのチャネル プールのプロパティを格納する <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> オブジェクト。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|カスタム バインドのすべてのバインド機能を定義します。|  
  
## <a name="remarks"></a>解説  

 パケット ルーティングを有効にするには、この要素が提供する "一方向の変換" 層が必要です。 カスタム バインドを作成し、このバインディングをセッション対応または要求応答のトランスポートの上に重ねて、パケット ルーティング可能にすることができます。 この要素は、一方向メソッドをよりネイティブな形式で公開するときにも役に立ちます。 複合二重や信頼できるメッセージ機能などのさらに大きい変換は、この層に対して適用できます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [バインド](../../../wcf/bindings.md)
- [バインディングの拡張](../../../wcf/extending/extending-bindings.md)
- [カスタム バインディング](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
