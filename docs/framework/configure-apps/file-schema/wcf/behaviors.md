---
description: '詳細情報: <behaviors>'
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 3cb8edea76f6e7af3c3b387e5b04b89e58a28305
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639511"
---
# \<behaviors>

この要素は、`endpointBehaviors` と`serviceBehaviors` という 2 つの子コレクションを定義します。  各コレクションは、エンドポイントとサービスによって使用されるそれぞれの動作要素を定義します。 各動作要素は、その一意の `name` 属性で識別されます。 .NET Framework 4 以降では、バインディングおよび動作に名前を付ける必要はありません。 既定の構成と、名前のないバインディングと動作については、「[簡略化された構成](../../../wcf/simplified-configuration.md)」と「[WCF サービスの簡略化された構成](../../../wcf/samples/simplified-configuration-for-wcf-services.md)」を参照してください。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  

 なし  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|この構成セクションは、特定のエンドポイントに対して定義されたすべての動作を表します。|  
|[\<serviceBehaviors>](servicebehaviors.md)|この構成セクションは、特定のサービスに対して定義されたすべての動作を表します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|すべての Windows Communication Foundation (WCF) 構成要素のルート要素です。|  
  
## <a name="remarks"></a>解説  

 `<remove>` 要素を使用して、コレクションから特定の動作を削除できます。 これを行うには、`name` 要素の `<remove>` 属性に、削除する動作の名前を指定します。  また、`<clear>` 要素を使用してコレクションの内容をすべて消去し、動作コレクションの初期値を確実に空にすることもできます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [動作を使用したランタイムの構成と拡張](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [クライアントの動作の構成](../../../wcf/configuring-client-behaviors.md)
- [クライアントのランタイム動作の指定](../../../wcf/specifying-client-run-time-behavior.md)
- [サービスのランタイム動作の指定](../../../wcf/specifying-service-run-time-behavior.md)
- [セキュリティ動作](../../../wcf/feature-details/security-behaviors-in-wcf.md)
