---
description: '詳細情報: <services>'
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 6e8c0c5ad5390c097db7bf1be1f0d489e1c0d624
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786708"
---
# \<services>

サービスは、設定ファイルの `services` セクションで定義されます。 各サービスには、独自の `service` 設定セクションがあります。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  

 なし  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<service>](service.md)|サービス コントラクト、動作、および特定のサービスのエンドポイントを定義します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|すべての Windows Communication Foundation (WCF) 構成要素のルート要素です。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.ServicesSection>
