---
description: 詳細については <transport> 、 <ws2007HttpBinding>
title: <transport> の <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 8c6890bc291458ba0849ab7a206487431b279576
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773434"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="ab04f-103">\<transport> の \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="ab04f-103">\<transport> of \<ws2007HttpBinding></span></span>

<span data-ttu-id="ab04f-104">HTTP トランスポートの認証設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="ab04f-104">Defines authentication settings for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="ab04f-105">構文</span><span class="sxs-lookup"><span data-stu-id="ab04f-105">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="ab04f-106">Type</span><span class="sxs-lookup"><span data-stu-id="ab04f-106">Type</span></span>  

 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab04f-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ab04f-107">Attributes and Elements</span></span>  

 <span data-ttu-id="ab04f-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab04f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab04f-109">属性</span><span class="sxs-lookup"><span data-stu-id="ab04f-109">Attributes</span></span>  
  
|<span data-ttu-id="ab04f-110">属性</span><span class="sxs-lookup"><span data-stu-id="ab04f-110">Attribute</span></span>|<span data-ttu-id="ab04f-111">説明</span><span class="sxs-lookup"><span data-stu-id="ab04f-111">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="ab04f-112">サービスに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="ab04f-112">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="ab04f-113">この属性は <xref:System.ServiceModel.HttpClientCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="ab04f-113">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="ab04f-114">ドメイン プロキシに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="ab04f-114">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="ab04f-115">この属性は <xref:System.ServiceModel.HttpProxyCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="ab04f-115">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="ab04f-116">ダイジェスト認証または基本認証の認証レルム。</span><span class="sxs-lookup"><span data-stu-id="ab04f-116">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="ab04f-117">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="ab04f-117">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="ab04f-118">認証レルムでは、少なくとも、認証を実行するホストの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="ab04f-118">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="ab04f-119">アクセス権のあるユーザーのコレクションも指定できます。</span><span class="sxs-lookup"><span data-stu-id="ab04f-119">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="ab04f-120">ユーザーは、認証レルムを照会して、複数のユーザー名とパスワードの候補のうち、どれを使用できるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="ab04f-120">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="ab04f-121">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="ab04f-121">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="ab04f-122">値</span><span class="sxs-lookup"><span data-stu-id="ab04f-122">Value</span></span>|<span data-ttu-id="ab04f-123">説明</span><span class="sxs-lookup"><span data-stu-id="ab04f-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ab04f-124">なし</span><span class="sxs-lookup"><span data-stu-id="ab04f-124">None</span></span>|<span data-ttu-id="ab04f-125">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="ab04f-125">Security is disabled.</span></span>|  
|<span data-ttu-id="ab04f-126">Basic</span><span class="sxs-lookup"><span data-stu-id="ab04f-126">Basic</span></span>|<span data-ttu-id="ab04f-127">基本認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="ab04f-127">Uses basic authentication.</span></span>|  
|<span data-ttu-id="ab04f-128">ダイジェスト</span><span class="sxs-lookup"><span data-stu-id="ab04f-128">Digest</span></span>|<span data-ttu-id="ab04f-129">ダイジェスト認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="ab04f-129">Uses digest authentication.</span></span>|  
|<span data-ttu-id="ab04f-130">Ntlm</span><span class="sxs-lookup"><span data-stu-id="ab04f-130">Ntlm</span></span>|<span data-ttu-id="ab04f-131">Windows ドメインのフォールバックとして NTLM 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="ab04f-131">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="ab04f-132">Windows</span><span class="sxs-lookup"><span data-stu-id="ab04f-132">Windows</span></span>|<span data-ttu-id="ab04f-133">統合 Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="ab04f-133">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="ab04f-134">Certificate</span><span class="sxs-lookup"><span data-stu-id="ab04f-134">Certificate</span></span>|<span data-ttu-id="ab04f-135">X.509 証明書を使用して、クライアントを認証します。</span><span class="sxs-lookup"><span data-stu-id="ab04f-135">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="ab04f-136">proxyCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="ab04f-136">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="ab04f-137">値</span><span class="sxs-lookup"><span data-stu-id="ab04f-137">Value</span></span>|<span data-ttu-id="ab04f-138">説明</span><span class="sxs-lookup"><span data-stu-id="ab04f-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ab04f-139">なし</span><span class="sxs-lookup"><span data-stu-id="ab04f-139">None</span></span>|<span data-ttu-id="ab04f-140">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="ab04f-140">Security is disabled.</span></span>|  
|<span data-ttu-id="ab04f-141">Basic</span><span class="sxs-lookup"><span data-stu-id="ab04f-141">Basic</span></span>|<span data-ttu-id="ab04f-142">基本認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="ab04f-142">Uses basic authentication.</span></span>|  
|<span data-ttu-id="ab04f-143">ダイジェスト</span><span class="sxs-lookup"><span data-stu-id="ab04f-143">Digest</span></span>|<span data-ttu-id="ab04f-144">ダイジェスト認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="ab04f-144">Uses digest authentication.</span></span>|  
|<span data-ttu-id="ab04f-145">Ntlm</span><span class="sxs-lookup"><span data-stu-id="ab04f-145">Ntlm</span></span>|<span data-ttu-id="ab04f-146">Windows ドメインのフォールバックとして NTLM を使用します。</span><span class="sxs-lookup"><span data-stu-id="ab04f-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="ab04f-147">Windows</span><span class="sxs-lookup"><span data-stu-id="ab04f-147">Windows</span></span>|<span data-ttu-id="ab04f-148">統合 Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="ab04f-148">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="ab04f-149">Certificate</span><span class="sxs-lookup"><span data-stu-id="ab04f-149">Certificate</span></span>|<span data-ttu-id="ab04f-150">X.509 証明書を使用して、クライアントを認証します。</span><span class="sxs-lookup"><span data-stu-id="ab04f-150">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab04f-151">子要素</span><span class="sxs-lookup"><span data-stu-id="ab04f-151">Child Elements</span></span>  

 <span data-ttu-id="ab04f-152">なし</span><span class="sxs-lookup"><span data-stu-id="ab04f-152">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ab04f-153">親要素</span><span class="sxs-lookup"><span data-stu-id="ab04f-153">Parent Elements</span></span>  
  
|<span data-ttu-id="ab04f-154">要素</span><span class="sxs-lookup"><span data-stu-id="ab04f-154">Element</span></span>|<span data-ttu-id="ab04f-155">説明</span><span class="sxs-lookup"><span data-stu-id="ab04f-155">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-ws2007httpbinding.md)|<span data-ttu-id="ab04f-156">要素のセキュリティ機能を表し [\<ws2007HttpBinding>](ws2007httpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="ab04f-156">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab04f-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab04f-157">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="ab04f-158">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="ab04f-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ab04f-159">バインド</span><span class="sxs-lookup"><span data-stu-id="ab04f-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ab04f-160">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="ab04f-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ab04f-161">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="ab04f-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
