---
description: '詳細情報: <issuedTokenParameters>'
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 92c8f5aa25ddb71561eb702ba3eb0396456008a6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725663"
---
# \<issuedTokenParameters>

<span data-ttu-id="52acc-102">フェデレーション セキュリティのシナリオで発行されるセキュリティ トークンのパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="52acc-102">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenParameters>**  
  
## <a name="syntax"></a><span data-ttu-id="52acc-103">構文</span><span class="sxs-lookup"><span data-stu-id="52acc-103">Syntax</span></span>  
  
```xml  
<issuedTokenParameters defaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"
                       inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"
                       keySize="Integer"
                       keyType="AsymmetricKey/BearerKey/SymmetricKey"
                       tokenType="String">
  <additionalRequestParameters />
  <claimTypeRequirements>
    <add claimType="URI"
         isOptional="Boolean" />
  </claimTypeRequirements>
  <issuer address="String"
          binding="" />
  <issuerMetadata address="String" />
</issuedTokenParameters>
```  
  
## <a name="type"></a><span data-ttu-id="52acc-104">種類</span><span class="sxs-lookup"><span data-stu-id="52acc-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52acc-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="52acc-105">Attributes and Elements</span></span>  

 <span data-ttu-id="52acc-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="52acc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52acc-107">属性</span><span class="sxs-lookup"><span data-stu-id="52acc-107">Attributes</span></span>  
  
|<span data-ttu-id="52acc-108">属性</span><span class="sxs-lookup"><span data-stu-id="52acc-108">Attribute</span></span>|<span data-ttu-id="52acc-109">説明</span><span class="sxs-lookup"><span data-stu-id="52acc-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52acc-110">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="52acc-110">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="52acc-111">バインドでサポートする必要があるセキュリティ仕様 (WS-Security、WS-Trust、WS-Secure Conversation、および WS-Security Policy) のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="52acc-111">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="52acc-112">この値は、<xref:System.ServiceModel.MessageSecurityVersion> 型です。</span><span class="sxs-lookup"><span data-stu-id="52acc-112">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="52acc-113">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="52acc-113">inclusionMode</span></span>|<span data-ttu-id="52acc-114">トークン包含要件を指定します。</span><span class="sxs-lookup"><span data-stu-id="52acc-114">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="52acc-115">この属性は <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="52acc-115">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="52acc-116">keySize</span><span class="sxs-lookup"><span data-stu-id="52acc-116">keySize</span></span>|<span data-ttu-id="52acc-117">トークン キー サイズを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="52acc-117">An integer that specifies the token key size.</span></span> <span data-ttu-id="52acc-118">既定値は 256 です。</span><span class="sxs-lookup"><span data-stu-id="52acc-118">The default value is 256.</span></span>|  
|<span data-ttu-id="52acc-119">keyType</span><span class="sxs-lookup"><span data-stu-id="52acc-119">keyType</span></span>|<span data-ttu-id="52acc-120">キーの型を指定する <xref:System.IdentityModel.Tokens.SecurityKeyType> の有効な値。</span><span class="sxs-lookup"><span data-stu-id="52acc-120">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="52acc-121">既定では、 `SymmetricKey`です。</span><span class="sxs-lookup"><span data-stu-id="52acc-121">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="52acc-122">tokenType</span><span class="sxs-lookup"><span data-stu-id="52acc-122">tokenType</span></span>|<span data-ttu-id="52acc-123">トークンの種類を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="52acc-123">A string that specifies the token type.</span></span> <span data-ttu-id="52acc-124">既定値は "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML" です。</span><span class="sxs-lookup"><span data-stu-id="52acc-124">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52acc-125">子要素</span><span class="sxs-lookup"><span data-stu-id="52acc-125">Child Elements</span></span>  
  
|<span data-ttu-id="52acc-126">要素</span><span class="sxs-lookup"><span data-stu-id="52acc-126">Element</span></span>|<span data-ttu-id="52acc-127">説明</span><span class="sxs-lookup"><span data-stu-id="52acc-127">Description</span></span>|  
|-------------|-----------------|  
|[\<additionalRequestParameters>](additionalrequestparameters-element.md)|<span data-ttu-id="52acc-128">追加の要求パラメーターを指定する構成要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="52acc-128">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="52acc-129">必須のクレームの種類のコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="52acc-129">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="52acc-130">フェデレーション シナリオでは、サービスが受信資格情報についての要件を記述します。</span><span class="sxs-lookup"><span data-stu-id="52acc-130">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="52acc-131">たとえば、受信資格情報は、特定のクレーム タイプのセットを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52acc-131">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="52acc-132">このコレクションの要素はそれぞれ、フェデレーション資格情報に表示されると予想される必須の要求および省略可能な要求の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="52acc-132">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[\<issuer>](issuer-of-issuedtokenparameters.md)|<span data-ttu-id="52acc-133">現在のトークンを発行するエンドポイントを指定する構成要素。</span><span class="sxs-lookup"><span data-stu-id="52acc-133">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[\<issuerMetadata>](issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="52acc-134">トークン発行者のメタデータのエンドポイント アドレスを指定する構成要素。</span><span class="sxs-lookup"><span data-stu-id="52acc-134">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="52acc-135">親要素</span><span class="sxs-lookup"><span data-stu-id="52acc-135">Parent Elements</span></span>  
  
|<span data-ttu-id="52acc-136">要素</span><span class="sxs-lookup"><span data-stu-id="52acc-136">Element</span></span>|<span data-ttu-id="52acc-137">説明</span><span class="sxs-lookup"><span data-stu-id="52acc-137">Description</span></span>|  
|-------------|-----------------|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="52acc-138">セキュリティで保護されたメッセージ交換サービスの開始に使用される既定値を指定します。</span><span class="sxs-lookup"><span data-stu-id="52acc-138">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="52acc-139">カスタム バインドのセキュリティ オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="52acc-139">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52acc-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="52acc-140">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="52acc-141">バインド</span><span class="sxs-lookup"><span data-stu-id="52acc-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="52acc-142">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="52acc-142">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="52acc-143">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="52acc-143">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="52acc-144">方法: SecurityBindingElement を使用してカスタム バインドを作成する</span><span class="sxs-lookup"><span data-stu-id="52acc-144">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="52acc-145">カスタム バインディング セキュリティ</span><span class="sxs-lookup"><span data-stu-id="52acc-145">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="52acc-146">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="52acc-146">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="52acc-147">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="52acc-147">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="52acc-148">カスタム バインディングを使用したセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="52acc-148">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="52acc-149">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="52acc-149">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
