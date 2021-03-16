---
description: '詳細情報: <timeOuts>'
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: 097569d1742f6486ddfb5fb3c3d98ba106424f45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786591"
---
# \<timeOuts>

サービス ホストを開くまたは閉じるまでに待機できる期間を指定する構成要素を表します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`closeTimeout`|サービス ホストを閉じるまでに待機できる期間を指定する <xref:System.TimeSpan> 値。|  
|`openTimeout`|サービス ホストを開くまでに待機できる期間を指定する <xref:System.TimeSpan> 値。|  
  
### <a name="child-elements"></a>子要素  

 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<host>](host.md)|サービス ホストの設定を指定する構成要素です。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [ホスティング](../../../wcf/feature-details/hosting.md)
