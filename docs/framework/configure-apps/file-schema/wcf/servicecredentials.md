---
description: '詳細情報: <serviceCredentials>'
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: c6fd39226ca2235d8f8253a7d2f2e363522870e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682866"
---
# \<serviceCredentials>

サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCredentials>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<serviceCredentials type="String">
  <clientCertificate>
  </clientCertificate>
  <issuedTokenAuthentication>
  </issuedTokenAuthentication>
  <peer>
  </peer>
  <secureConversationAuthentication>
  </secureConversationAuthentication>
  <serviceCertificate>
  </serviceCertificate>
  <userNameAuthentication>
  </userNameAuthentication>
  <windowsAuthentication>
  </windowsAuthentication>
</serviceCredentials>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`type`|この設定要素の種類を指定する文字列です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|クライアント証明書を帯域外で使用できるときに使用される証明書を指定します。 この要素は、クライアント証明書の検証設定も指定します。 この要素は <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement> 型です。|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|このサービス用に現在発行されているトークンを指定します。 この要素は <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement> 型です。|  
|[\<peer>](peer-of-servicecredentials.md)|ピア ノードの現在の資格情報を指定します。 この要素は <xref:System.ServiceModel.Configuration.PeerCredentialElement> 型です。|  
|[\<secureConversationAuthentication>](secureconversationauthentication-of-servicecredential.md)|セキュリティで保護されたメッセージ交換の現在の資格情報を指定します。 この要素は <xref:System.ServiceModel.Configuration.SecureConversationServiceElement> 型です。|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|サービスが自身を識別するために使用する証明書を指定します。 この要素は <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement> 型です。|  
|[\<userNameAuthentication>](usernameauthentication.md)|ユーザー名とパスワードの検証の設定を指定します。 この要素は <xref:System.ServiceModel.Configuration.UserNameServiceElement> 型です。|  
|[\<windowsAuthentication>](windowsauthentication-of-servicecredentials.md)|Windows 資格情報の検証の設定を指定します。 この要素は <xref:System.ServiceModel.Configuration.WindowsServiceElement> 型です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|動作の要素を指定します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [セキュリティ動作](../../../wcf/feature-details/security-behaviors-in-wcf.md)
