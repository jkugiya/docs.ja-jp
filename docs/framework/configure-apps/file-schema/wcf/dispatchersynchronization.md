---
description: '詳細情報: <dispatcherSynchronization>'
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 93664dec3648ed58df7e3e5c0760f1694c60ba7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749605"
---
# \<dispatcherSynchronization>
  
サービスが非同期に応答を返すことができるようにするエンドポイントの動作を指定します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dispatcherSynchronization>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a>種類  
  
`Type`  
  
## <a name="attributes-and-elements"></a>属性と要素  
  
以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性

| 属性               | 説明       |
| ----------------------- | ----------------- |
| asynchronousSendEnabled | 非同期の送信動作が有効かどうかを示すブール値。 |
| `maxPendingReceives`    | チャネルで発行可能な同時受信の数を指定する整数。<br /><br /> この値は、サービス調整の動作を適切に構成した後に構成する必要があります。 |

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

| 要素 | 説明 |  
| ------- | ----------- |  
| [\<behavior>](behavior-of-endpointbehaviors.md)|エンドポイントの動作を指定します。 |

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
