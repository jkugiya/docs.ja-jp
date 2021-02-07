---
description: 詳細については <message> 、 <netMsmqBinding>
title: <message> の <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 0e8cf641ef8ba5361318f7b658d5d60beef6ce56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749585"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="2f943-103">\<message> の \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="2f943-103">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="2f943-104">この `netMsmqBinding` バインディングでの SOAP メッセージ セキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="2f943-104">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  

## <a name="syntax"></a><span data-ttu-id="2f943-105">構文</span><span class="sxs-lookup"><span data-stu-id="2f943-105">Syntax</span></span>

```xml
<netMsmqBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
    </security>
  </binding>
</netMsmqBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2f943-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2f943-106">Attributes and Elements</span></span>

<span data-ttu-id="2f943-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2f943-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2f943-108">属性</span><span class="sxs-lookup"><span data-stu-id="2f943-108">Attributes</span></span>

|<span data-ttu-id="2f943-109">属性</span><span class="sxs-lookup"><span data-stu-id="2f943-109">Attribute</span></span>|<span data-ttu-id="2f943-110">説明</span><span class="sxs-lookup"><span data-stu-id="2f943-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="2f943-111">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="2f943-111">algorithmSuite</span></span>|<span data-ttu-id="2f943-112">MSMQ トランスポートを介して送信されるメッセージにメッセージ ベースのセキュリティを実現するために使用されるメッセージの暗号化およびキー ラップ アルゴリズムを設定します。</span><span class="sxs-lookup"><span data-stu-id="2f943-112">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="2f943-113">既定値は `Aes256` です。</span><span class="sxs-lookup"><span data-stu-id="2f943-113">The default value is `Aes256`.</span></span> <span data-ttu-id="2f943-114">この属性は <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 型です。</span><span class="sxs-lookup"><span data-stu-id="2f943-114">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="2f943-115">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="2f943-115">clientCredentialType</span></span>|<span data-ttu-id="2f943-116">MSMQ トランスポートで送信されるメッセージに対してクライアント認証を実行するときに使用される資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="2f943-116">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="2f943-117">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2f943-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2f943-118">-None: サービスが匿名クライアントと対話できるようにします。</span><span class="sxs-lookup"><span data-stu-id="2f943-118">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="2f943-119">サービスとクライアントはいずれも資格情報を要求しません。</span><span class="sxs-lookup"><span data-stu-id="2f943-119">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="2f943-120">-Windows: これにより、Windows 資格情報の認証済みコンテキストで SOAP 交換を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2f943-120">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="2f943-121">これは、常に Kerberos ベースの認証を実行します。</span><span class="sxs-lookup"><span data-stu-id="2f943-121">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="2f943-122">-UserName: これにより、サービスは、ユーザー名資格情報を使用してクライアントの認証を要求できます。</span><span class="sxs-lookup"><span data-stu-id="2f943-122">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="2f943-123">この場合の資格情報は、動作に注意して指定する必要があり `clientCredentials` **ます。**  Windows Communication Foundation (WCF) では、パスワードダイジェストの送信、パスワードを使用したキーの派生、およびメッセージセキュリティのためのキーの使用はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2f943-123">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="2f943-124">したがって、[ユーザー名] 資格情報を使用する場合、WCF ではセキュリティ保護された交換が強制されます。</span><span class="sxs-lookup"><span data-stu-id="2f943-124">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="2f943-125">このモードは、サービス証明書が、`clientCredential` 動作および `serviceCertificate` を使用してクライアント側で指定されることを要求します。</span><span class="sxs-lookup"><span data-stu-id="2f943-125">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="2f943-126">-Certificate: これにより、サービスは、証明書を使用してクライアントを認証するよう要求できます。</span><span class="sxs-lookup"><span data-stu-id="2f943-126">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="2f943-127">この場合のクライアント資格情報は、`clientCredentials` 動作を使用して指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f943-127">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="2f943-128">この場合のサービス資格情報は、`clientCredentials` を指定して `serviceCertificate` 動作を使用することで、指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f943-128">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="2f943-129">-CardSpace: サービスでは、クライアントが CardSpace を使用して認証されるように要求できます。</span><span class="sxs-lookup"><span data-stu-id="2f943-129">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="2f943-130">`serviceCertificate` は、`clientCredential` 動作で提供される必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f943-130">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="2f943-131">既定値は `Windows` です。</span><span class="sxs-lookup"><span data-stu-id="2f943-131">The default value is `Windows`.</span></span> <span data-ttu-id="2f943-132">この属性は <xref:System.ServiceModel.MessageCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="2f943-132">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="2f943-133">子要素</span><span class="sxs-lookup"><span data-stu-id="2f943-133">Child Elements</span></span>

<span data-ttu-id="2f943-134">なし</span><span class="sxs-lookup"><span data-stu-id="2f943-134">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2f943-135">親要素</span><span class="sxs-lookup"><span data-stu-id="2f943-135">Parent Elements</span></span>

|<span data-ttu-id="2f943-136">要素</span><span class="sxs-lookup"><span data-stu-id="2f943-136">Element</span></span>|<span data-ttu-id="2f943-137">説明</span><span class="sxs-lookup"><span data-stu-id="2f943-137">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-netmsmqbinding.md)|<span data-ttu-id="2f943-138">バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="2f943-138">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="2f943-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f943-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="2f943-140">WCF のキュー</span><span class="sxs-lookup"><span data-stu-id="2f943-140">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="2f943-141">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="2f943-141">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2f943-142">バインド</span><span class="sxs-lookup"><span data-stu-id="2f943-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2f943-143">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="2f943-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2f943-144">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="2f943-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
