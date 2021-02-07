---
description: '詳細情報: <localIssuer>'
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 38928f1bfd7740aa902de46958740a1e8fe63e5a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725481"
---
# \<localIssuer>

<span data-ttu-id="dba6b-102">セキュリティ トークンの取得に使用される、ローカル発行者のアドレスとバインディングを指定します。</span><span class="sxs-lookup"><span data-stu-id="dba6b-102">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localIssuer>**  
  
## <a name="syntax"></a><span data-ttu-id="dba6b-103">構文</span><span class="sxs-lookup"><span data-stu-id="dba6b-103">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dba6b-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="dba6b-104">Attributes and Elements</span></span>  

 <span data-ttu-id="dba6b-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="dba6b-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dba6b-106">属性</span><span class="sxs-lookup"><span data-stu-id="dba6b-106">Attributes</span></span>  
  
|<span data-ttu-id="dba6b-107">属性</span><span class="sxs-lookup"><span data-stu-id="dba6b-107">Attribute</span></span>|<span data-ttu-id="dba6b-108">説明</span><span class="sxs-lookup"><span data-stu-id="dba6b-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dba6b-109">address</span><span class="sxs-lookup"><span data-stu-id="dba6b-109">address</span></span>|<span data-ttu-id="dba6b-110">必須の文字列。</span><span class="sxs-lookup"><span data-stu-id="dba6b-110">Required string.</span></span> <span data-ttu-id="dba6b-111">ローカル発行者の URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="dba6b-111">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="dba6b-112">binding</span><span class="sxs-lookup"><span data-stu-id="dba6b-112">binding</span></span>|<span data-ttu-id="dba6b-113">省略可能な文字列。</span><span class="sxs-lookup"><span data-stu-id="dba6b-113">Optional string.</span></span> <span data-ttu-id="dba6b-114">システム指定のバインディングの 1 つ。</span><span class="sxs-lookup"><span data-stu-id="dba6b-114">One of the system-provided bindings.</span></span> <span data-ttu-id="dba6b-115">リストについては、「 [システム指定のバインディング](../../../wcf/system-provided-bindings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dba6b-115">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="dba6b-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="dba6b-116">bindingConfiguration</span></span>|<span data-ttu-id="dba6b-117">省略可能な文字列。</span><span class="sxs-lookup"><span data-stu-id="dba6b-117">Optional string.</span></span> <span data-ttu-id="dba6b-118">構成ファイル内に存在するバインディング構成を指定します。</span><span class="sxs-lookup"><span data-stu-id="dba6b-118">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dba6b-119">子要素</span><span class="sxs-lookup"><span data-stu-id="dba6b-119">Child Elements</span></span>  
  
|<span data-ttu-id="dba6b-120">要素</span><span class="sxs-lookup"><span data-stu-id="dba6b-120">Element</span></span>|<span data-ttu-id="dba6b-121">説明</span><span class="sxs-lookup"><span data-stu-id="dba6b-121">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="dba6b-122">ローカル発行者の ID 情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="dba6b-122">Specifies identity information for the local issuer.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="dba6b-123">ローカル発行者を正しくアドレス指定するために必要なアドレス ヘッダーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="dba6b-123">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="dba6b-124">`add` キーワードを使用して、このコレクションにヘッダーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="dba6b-124">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dba6b-125">親要素</span><span class="sxs-lookup"><span data-stu-id="dba6b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="dba6b-126">要素</span><span class="sxs-lookup"><span data-stu-id="dba6b-126">Element</span></span>|<span data-ttu-id="dba6b-127">説明</span><span class="sxs-lookup"><span data-stu-id="dba6b-127">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="dba6b-128">サービスに対するクライアントの認証に使用されるカスタム トークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="dba6b-128">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dba6b-129">解説</span><span class="sxs-lookup"><span data-stu-id="dba6b-129">Remarks</span></span>  

 <span data-ttu-id="dba6b-130">発行されたトークンをセキュリティ トークン サービス (STS) から取得する場合は、クライアント アプリケーションに、STS との通信に使用するアドレスとバインディングが構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="dba6b-130">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="dba6b-131">が <xref:System.ServiceModel.WSFederationHttpBinding> Security Token Service の URL を提供しない場合、またはフェデレーションバインディングの発行者アドレスが `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` またはの場合 `null` 、クライアントの Windows Communication Foundation (WCF) チャネルは、およびで指定された値を使用して `address` STS と通信し、発行され `binding` たトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="dba6b-131">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="dba6b-132">ローカル発行者の構成の詳細については、「 [方法: ローカル発行者を構成](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dba6b-132">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dba6b-133">例</span><span class="sxs-lookup"><span data-stu-id="dba6b-133">Example</span></span>  

 <span data-ttu-id="dba6b-134">次の例は、`address` 要素の `binding`、`bindingConfiguration`、および `localIssuer` 属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="dba6b-134">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
```xml  
<system.serviceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="MyEndpointBehavior">
        <clientCredentials>
          <issuedToken cacheIssuedTokens="false"
                       defaultKeyEntropyMode="ClientEntropy">
            <localIssuer address="net.tcp://cohowinery/tokens"
                         binding="netTcpBinding"
                         bindingConfiguration="myTcpBindingConfig" />
          </issuedToken>
        </clientCredentials>
      </behavior>
    </endpointBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="dba6b-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="dba6b-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="dba6b-136">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="dba6b-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="dba6b-137">方法: ローカル発行者を設定する</span><span class="sxs-lookup"><span data-stu-id="dba6b-137">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="dba6b-138">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="dba6b-138">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="dba6b-139">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="dba6b-139">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="dba6b-140">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="dba6b-140">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="dba6b-141">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="dba6b-141">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="dba6b-142">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="dba6b-142">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="dba6b-143">方法: フェデレーション クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="dba6b-143">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="dba6b-144">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="dba6b-144">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
