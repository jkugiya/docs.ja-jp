---
description: '詳細情報: <issuer>'
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 771fb8d0bee4e78b598bd20c4d99ec5180f9fb1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725637"
---
# \<issuer>

<span data-ttu-id="8f8a9-102">セキュリティ トークンを発行するセキュリティ トークン サービス (STS) を指定します。</span><span class="sxs-lookup"><span data-stu-id="8f8a9-102">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="8f8a9-103">構文</span><span class="sxs-lookup"><span data-stu-id="8f8a9-103">Syntax</span></span>  
  
```xml  
<issuer address="Uri">
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
</issuer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f8a9-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8f8a9-104">Attributes and Elements</span></span>  

 <span data-ttu-id="8f8a9-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8f8a9-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f8a9-106">属性</span><span class="sxs-lookup"><span data-stu-id="8f8a9-106">Attributes</span></span>  
  
|<span data-ttu-id="8f8a9-107">属性</span><span class="sxs-lookup"><span data-stu-id="8f8a9-107">Attribute</span></span>|<span data-ttu-id="8f8a9-108">説明</span><span class="sxs-lookup"><span data-stu-id="8f8a9-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8f8a9-109">address</span><span class="sxs-lookup"><span data-stu-id="8f8a9-109">address</span></span>|<span data-ttu-id="8f8a9-110">必須の文字列。</span><span class="sxs-lookup"><span data-stu-id="8f8a9-110">Required string.</span></span> <span data-ttu-id="8f8a9-111">STS の URL です。</span><span class="sxs-lookup"><span data-stu-id="8f8a9-111">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f8a9-112">子要素</span><span class="sxs-lookup"><span data-stu-id="8f8a9-112">Child Elements</span></span>  
  
|<span data-ttu-id="8f8a9-113">要素</span><span class="sxs-lookup"><span data-stu-id="8f8a9-113">Element</span></span>|<span data-ttu-id="8f8a9-114">説明</span><span class="sxs-lookup"><span data-stu-id="8f8a9-114">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="8f8a9-115">ビルダーが作成できるエンドポイントのアドレス ヘッダーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="8f8a9-115">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="8f8a9-116">発行されたトークンを使用する場合、クライアントでサーバーの認証を有効にする設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="8f8a9-116">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8f8a9-117">親要素</span><span class="sxs-lookup"><span data-stu-id="8f8a9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8f8a9-118">要素</span><span class="sxs-lookup"><span data-stu-id="8f8a9-118">Element</span></span>|<span data-ttu-id="8f8a9-119">説明</span><span class="sxs-lookup"><span data-stu-id="8f8a9-119">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="8f8a9-120">要素のメッセージレベルセキュリティの設定を定義し [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="8f8a9-120">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f8a9-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f8a9-121">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="8f8a9-122">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="8f8a9-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="8f8a9-123">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="8f8a9-123">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="8f8a9-124">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="8f8a9-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="8f8a9-125">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="8f8a9-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="8f8a9-126">カスタム バインディングを使用したセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="8f8a9-126">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="8f8a9-127">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="8f8a9-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
