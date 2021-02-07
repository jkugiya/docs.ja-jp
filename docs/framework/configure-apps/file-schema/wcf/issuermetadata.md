---
description: '詳細情報: <issuerMetadata>'
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 86671b6b704f5753cf4bd45c2dfd90a368070b22
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725533"
---
# \<issuerMetadata>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="eee7e-102">構文</span><span class="sxs-lookup"><span data-stu-id="eee7e-102">Syntax</span></span>  
  
```xml  
<issuerMetadata address="String">
  <headers>
    <add name="String"
         namespace="String" />
  </headers>
  <identity>
    <certificate encodedValue="String" />
    <certificateReference findValue="String"
                          isChainIncluded="Boolean"
                          storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                          storeLocation="LocalMachine/CurrentUser"
                          x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
    <dns value="String" />
    <rsa value="String" />
    <servicePrincipalName value="String" />
    <usePrincipalName value="String" />
  </identity>
</issuerMetadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eee7e-103">属性および要素</span><span class="sxs-lookup"><span data-stu-id="eee7e-103">Attributes and Elements</span></span>  

 <span data-ttu-id="eee7e-104">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="eee7e-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eee7e-105">属性</span><span class="sxs-lookup"><span data-stu-id="eee7e-105">Attributes</span></span>  
  
|<span data-ttu-id="eee7e-106">属性</span><span class="sxs-lookup"><span data-stu-id="eee7e-106">Attribute</span></span>|<span data-ttu-id="eee7e-107">説明</span><span class="sxs-lookup"><span data-stu-id="eee7e-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eee7e-108">address</span><span class="sxs-lookup"><span data-stu-id="eee7e-108">address</span></span>|<span data-ttu-id="eee7e-109">必須の `string` 属性です。</span><span class="sxs-lookup"><span data-stu-id="eee7e-109">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="eee7e-110">エンドポイントのアドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="eee7e-110">Specifies the address of the endpoint.</span></span> <span data-ttu-id="eee7e-111">アドレスは、絶対 URI にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="eee7e-111">The address must be an absolute URI.</span></span> <span data-ttu-id="eee7e-112">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="eee7e-112">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eee7e-113">子要素</span><span class="sxs-lookup"><span data-stu-id="eee7e-113">Child Elements</span></span>  
  
|<span data-ttu-id="eee7e-114">要素</span><span class="sxs-lookup"><span data-stu-id="eee7e-114">Element</span></span>|<span data-ttu-id="eee7e-115">説明</span><span class="sxs-lookup"><span data-stu-id="eee7e-115">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="eee7e-116">アドレス ヘッダーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="eee7e-116">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="eee7e-117">メッセージを交換する他のエンドポイントによるエンドポイントの認証を可能にする ID です。</span><span class="sxs-lookup"><span data-stu-id="eee7e-117">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eee7e-118">親要素</span><span class="sxs-lookup"><span data-stu-id="eee7e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="eee7e-119">要素</span><span class="sxs-lookup"><span data-stu-id="eee7e-119">Element</span></span>|<span data-ttu-id="eee7e-120">説明</span><span class="sxs-lookup"><span data-stu-id="eee7e-120">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="eee7e-121">要素のメッセージレベルセキュリティの設定を定義し [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="eee7e-121">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eee7e-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="eee7e-122">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="eee7e-123">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="eee7e-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="eee7e-124">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="eee7e-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="eee7e-125">カスタム バインディングを使用したセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="eee7e-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="eee7e-126">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="eee7e-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
