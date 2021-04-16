---
description: '詳細情報: <identity> の <certificateReference>'
title: <identity> の <certificateReference>
ms.date: 03/30/2017
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
ms.openlocfilehash: 2c30e7ad035b560d766f3b5592af18210df53aad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639043"
---
# <a name="certificatereference-for-identity"></a>\<identity> の \<certificateReference>

X.509 証明書検証の設定を指定します。 この ID を持つエンドポイントに接続するセキュリティで保護された Windows Communication Foundation (WCF) クライアントは、サーバーによって提示されるクレームに、この ID を構築するために使用された ID クレームが含まれていることを検証します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<certificateReference findValue="String"
                      isChainIncluded="Boolean"
                      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                      storeLocation="LocalMachine/CurrentUser"
                      X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier">
</certificateReference>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|findValue|X.509 証明書ストアで検索する値を指定します。 この属性に格納されている型は、指定された `X509FindType` 値の要件を満たす必要があります。 既定値は空の文字列です。|  
|isChainIncluded|証明書チェーンを使用して検証を行うかどうかを指定するブール値です。|  
|storeLocation|クライアントがサーバーの証明書の検証に使用できる証明書ストアの場所を指定します。<br /><br /> 有効な値は次のとおりです。<br /><br /> -   LocalMachine: ローカル マシンに割り当てられた証明書ストア。<br />-   CurrentUser: 現在のユーザーに割り当てられた証明書ストア。<br /><br /> 既定値は LocalMachine です。<br /><br /> この属性は <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 型です。|  
|storeName|開く X.509 証明書ストアの名前を指定します。<br /><br /> 有効な値は次のとおりです。<br /><br /> -   AddressBook: 他のユーザー用の証明書ストア。<br />-   AuthRoot: サードパーティ証明機関 (CA) の証明書ストア。<br />-   CertificateAuthority: 中間証明機関 (CA) の証明書ストア。<br />-   Disallowed: 失効した証明書の証明書ストア。<br />-   My: 個人用証明書の証明書ストア。<br />-   Root: 信頼されたルート CA の証明書ストア。<br />-   TrustedPeople: 直接信頼されたユーザーやリソースの証明書ストア。<br />-   TrustedPublisher: 直接信頼された発行者の証明書ストア。<br /><br /> 既定値は、My です。<br /><br /> この属性は <xref:System.Security.Cryptography.X509Certificates.StoreName> 型です。|  
|X509FindType|実行する X.509 検索の種類を指定します。 `findValue` 属性に含まれている型は、指定された X509FindType の要件を満たしている必要があります。<br /><br /> 有効な値は次のとおりです。<br /><br /> -   FindByThumbPrint<br />-   FindBySubjectName<br />-   FindBySubjectDistinguishedName<br />-   FindByIssuerName<br />-   FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-   FindByTemplateName<br />-   FindByApplicationPolicy<br />-   FindByCertificatePolicy<br />-   FindByExtension<br />-   FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> 既定値は FindBySubjectDistinguishedName です。<br /><br /> この属性は <xref:System.Security.Cryptography.X509Certificates.X509FindType> 型です。|  
  
### <a name="child-elements"></a>子要素  

 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<identity>](identity.md)|メッセージを交換する他のエンドポイントによるエンドポイントの認証を可能にする設定を指定します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.CertificateReferenceElement>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
