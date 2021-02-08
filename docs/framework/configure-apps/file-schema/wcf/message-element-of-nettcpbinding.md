---
description: '詳細情報: <message> の要素 <netTcpBinding>'
title: <message> の要素 <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 1d71edd9-c085-4c2e-b6d3-980c313366f9
ms.openlocfilehash: 10c1f2897bc880ca1f328b546357d3cf7cdb26a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802178"
---
# <a name="message-element-of-nettcpbinding"></a><span data-ttu-id="f7eb3-103">\<message> の要素 \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="f7eb3-103">\<message> element of \<netTcpBinding></span></span>

<span data-ttu-id="f7eb3-104">で構成されるエンドポイントのメッセージレベルのセキュリティ要件の種類を定義し [\<netTcpBinding>](nettcpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-104">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="f7eb3-105">構文</span><span class="sxs-lookup"><span data-stu-id="f7eb3-105">Syntax</span></span>  
  
```xml  
<message algorithmSuite="System.Servicemodel.Security.SecurityAlgorithmsuite"
         clientCredentialType="None/Windows/UserName/Certificate/IssuedToken" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7eb3-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f7eb3-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f7eb3-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7eb3-108">属性</span><span class="sxs-lookup"><span data-stu-id="f7eb3-108">Attributes</span></span>  
  
|<span data-ttu-id="f7eb3-109">属性</span><span class="sxs-lookup"><span data-stu-id="f7eb3-109">Attribute</span></span>|<span data-ttu-id="f7eb3-110">説明</span><span class="sxs-lookup"><span data-stu-id="f7eb3-110">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="f7eb3-111">メッセージの暗号化とキー ラップ アルゴリズムを設定します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-111">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="f7eb3-112">アルゴリズムとキー サイズは、<xref:System.ServiceModel.Security.SecurityAlgorithmSuite> クラスにより決まります。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-112">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="f7eb3-113">これらのアルゴリズムは、セキュリティ ポリシー言語 (WS-SecurityPolicy) 仕様で指定されたアルゴリズムにマップされます。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-113">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="f7eb3-114">次の表に、使用可能な値を示します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-114">Possible values are shown in the following table.</span></span> <span data-ttu-id="f7eb3-115">既定値は `Basic256` です。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-115">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="f7eb3-116">サービス バインディングで指定されている `algorithmSuite` 値が既定値と異なると、Svcutil.exe を使用して構成ファイルを生成したときにファイルが正しく生成されません。この場合は、構成ファイルを手動で編集して、この属性を適切な値に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-116">If the service binding specifies an `algorithmSuite` value that is not equal to the default, and you generate the configuration file using Svcutil.exe, then it is not generated correctly, and you must manually edit the configuration file to set this attribute to the desired value.</span></span>|  
|`clientCredentialType`|<span data-ttu-id="f7eb3-117">メッセージ ベースのセキュリティを使用してクライアント認証を実行するときに使用される資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-117">Specifies the type of credential to be used when performing client authentication using Message-based security.</span></span> <span data-ttu-id="f7eb3-118">次の表に、使用可能な値を示します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-118">Possible values are shown in the following table.</span></span> <span data-ttu-id="f7eb3-119">既定値は `UserName` です。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-119">The default value is `UserName`.</span></span> <span data-ttu-id="f7eb3-120">この属性は <xref:System.ServiceModel.MessageCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-120">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="f7eb3-121">algorithmSuite 属性</span><span class="sxs-lookup"><span data-stu-id="f7eb3-121">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="f7eb3-122">値</span><span class="sxs-lookup"><span data-stu-id="f7eb3-122">Value</span></span>|<span data-ttu-id="f7eb3-123">説明</span><span class="sxs-lookup"><span data-stu-id="f7eb3-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f7eb3-124">Basic128</span><span class="sxs-lookup"><span data-stu-id="f7eb3-124">Basic128</span></span>|<span data-ttu-id="f7eb3-125">Aes128 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-125">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="f7eb3-126">Basic192</span><span class="sxs-lookup"><span data-stu-id="f7eb3-126">Basic192</span></span>|<span data-ttu-id="f7eb3-127">Aes192 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-127">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="f7eb3-128">Basic256</span><span class="sxs-lookup"><span data-stu-id="f7eb3-128">Basic256</span></span>|<span data-ttu-id="f7eb3-129">Aes256 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-129">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="f7eb3-130">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="f7eb3-130">Basic256Rsa15</span></span>|<span data-ttu-id="f7eb3-131">メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-131">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="f7eb3-132">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="f7eb3-132">Basic192Rsa15</span></span>|<span data-ttu-id="f7eb3-133">メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-133">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="f7eb3-134">TripleDes</span><span class="sxs-lookup"><span data-stu-id="f7eb3-134">TripleDes</span></span>|<span data-ttu-id="f7eb3-135">TripleDes 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-135">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="f7eb3-136">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="f7eb3-136">Basic128Rsa15</span></span>|<span data-ttu-id="f7eb3-137">メッセージの暗号化には Aes128 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-137">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="f7eb3-138">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="f7eb3-138">TripleDesRsa15</span></span>|<span data-ttu-id="f7eb3-139">TripleDes 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-139">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="f7eb3-140">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="f7eb3-140">Basic128Sha256</span></span>|<span data-ttu-id="f7eb3-141">メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-141">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="f7eb3-142">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="f7eb3-142">Basic192Sha256</span></span>|<span data-ttu-id="f7eb3-143">メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-143">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="f7eb3-144">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="f7eb3-144">Basic256Sha256</span></span>|<span data-ttu-id="f7eb3-145">メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-145">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="f7eb3-146">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="f7eb3-146">TripleDesSha256</span></span>|<span data-ttu-id="f7eb3-147">メッセージの暗号化には TripleDes を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-147">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="f7eb3-148">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="f7eb3-148">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="f7eb3-149">メッセージの暗号化には Aes128 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-149">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="f7eb3-150">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="f7eb3-150">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="f7eb3-151">メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-151">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="f7eb3-152">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="f7eb3-152">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="f7eb3-153">メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-153">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="f7eb3-154">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="f7eb3-154">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="f7eb3-155">メッセージの暗号化には TripleDes を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-155">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="f7eb3-156">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="f7eb3-156">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="f7eb3-157">値</span><span class="sxs-lookup"><span data-stu-id="f7eb3-157">Value</span></span>|<span data-ttu-id="f7eb3-158">説明</span><span class="sxs-lookup"><span data-stu-id="f7eb3-158">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f7eb3-159">なし</span><span class="sxs-lookup"><span data-stu-id="f7eb3-159">None</span></span>|<span data-ttu-id="f7eb3-160">サービスが匿名クライアントと対話できるようになります。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-160">This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="f7eb3-161">サービス側では、サービスがクライアントの資格情報を必要としないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-161">On the service, this indicates that the service does not require any client credential.</span></span> <span data-ttu-id="f7eb3-162">クライアント側では、クライアントがクライアントの資格情報を提示しないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-162">On the client, this indicates that the client does not provide any client credential.</span></span>|  
|<span data-ttu-id="f7eb3-163">Windows</span><span class="sxs-lookup"><span data-stu-id="f7eb3-163">Windows</span></span>|<span data-ttu-id="f7eb3-164">SOAP 交換を、Windows 資格情報の認証されたコンテキストで行うことが可能になります。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-164">Allows the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span>|  
|<span data-ttu-id="f7eb3-165">UserName</span><span class="sxs-lookup"><span data-stu-id="f7eb3-165">UserName</span></span>|<span data-ttu-id="f7eb3-166">サービスが、UserName 資格情報を使用したクライアントの認証を要求できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-166">Allows the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="f7eb3-167">WCF では、パスワード ダイジェストの送信や、パスワードを使用したキーの派生およびこうしたキーの使用がサポートされません。これはメッセージのセキュリティを確保するためです。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-167">WCF does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="f7eb3-168">そのため、ユーザー名の資格情報を使用する場合、WCF はトランスポートがセキュリティで保護されることを強制します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-168">As such, WCF enforces that the transport is secured when using UserName credentials.</span></span> <span data-ttu-id="f7eb3-169">この資格情報モードは、`negotiateServiceCredential` 属性に基づいて、同時実行可能な交換か、同時実行できないネゴシエーションのいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-169">This credential mode results in either an interoperable exchange or a non-interoperable negotiation based on the `negotiateServiceCredential` attribute.</span></span>|  
|<span data-ttu-id="f7eb3-170">Certificate</span><span class="sxs-lookup"><span data-stu-id="f7eb3-170">Certificate</span></span>|<span data-ttu-id="f7eb3-171">証明書を使用したクライアントの認証を、サービスで要求することが可能になります。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-171">Allows the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="f7eb3-172">メッセージ セキュリティ モードが使用され、`negotiateServiceCredential` 属性が `false` に設定されている場合、クライアントにサービス証明書を準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-172">If message security mode is used and the `negotiateServiceCredential` attribute is set to `false`, the client must be provisioned with the service certificate.</span></span>|  
|<span data-ttu-id="f7eb3-173">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="f7eb3-173">IssuedToken</span></span>|<span data-ttu-id="f7eb3-174">通常はセキュリティ トークン サービス (STS) により発行されるカスタム トークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-174">Specifies a custom token, usually issued by a Security Token Service (STS).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f7eb3-175">子要素</span><span class="sxs-lookup"><span data-stu-id="f7eb3-175">Child Elements</span></span>  

 <span data-ttu-id="f7eb3-176">なし</span><span class="sxs-lookup"><span data-stu-id="f7eb3-176">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f7eb3-177">親要素</span><span class="sxs-lookup"><span data-stu-id="f7eb3-177">Parent Elements</span></span>  
  
|<span data-ttu-id="f7eb3-178">要素</span><span class="sxs-lookup"><span data-stu-id="f7eb3-178">Element</span></span>|<span data-ttu-id="f7eb3-179">説明</span><span class="sxs-lookup"><span data-stu-id="f7eb3-179">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="f7eb3-180"><xref:System.ServiceModel.Configuration.NetTcpBindingElement>のセキュリティ機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-180">Defines the security capabilities for the <xref:System.ServiceModel.Configuration.NetTcpBindingElement>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7eb3-181">解説</span><span class="sxs-lookup"><span data-stu-id="f7eb3-181">Remarks</span></span>  

 <span data-ttu-id="f7eb3-182">メッセージは、SOAP メッセージの整合性と機密性を確保し、通信ピアの相互認証を行うために、メッセージ レベルのセキュリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-182">Message uses message-level security for the integrity and confidentiality of the SOAP message, and for mutual authentication of the communication peers.</span></span> <span data-ttu-id="f7eb3-183">バインディング上でこのセキュリティ モードが選択された場合、チャネル スタックは、メッセージ セキュリティ バインド要素を使用して構成され、SOAP メッセージは WS-Security\* 標準に従って保護されます。</span><span class="sxs-lookup"><span data-stu-id="f7eb3-183">If this security mode is selected on a binding, the channel stack is configured with message security binding elements and the SOAP messages are secured in compliance with WS-Security\* standards.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7eb3-184">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7eb3-184">See also</span></span>

- <xref:System.ServiceModel.MessageSecurityOverTcp>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="f7eb3-185">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="f7eb3-185">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f7eb3-186">バインド</span><span class="sxs-lookup"><span data-stu-id="f7eb3-186">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f7eb3-187">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="f7eb3-187">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f7eb3-188">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="f7eb3-188">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
