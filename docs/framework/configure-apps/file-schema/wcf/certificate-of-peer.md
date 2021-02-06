---
description: 詳細については <certificate> 、 <peer>
title: <certificate> の <peer>
ms.date: 03/30/2017
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
ms.openlocfilehash: e48a96a3f1fa486b19289584ae0c059eb5b7048d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639056"
---
# <a name="certificate-of-peer"></a><span data-ttu-id="9b4d2-103">\<certificate> の \<peer></span><span class="sxs-lookup"><span data-stu-id="9b4d2-103">\<certificate> of \<peer></span></span>

<span data-ttu-id="9b4d2-104">ピアで使用される証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-104">Specifies a certificate used by a peer.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="9b4d2-105">構文</span><span class="sxs-lookup"><span data-stu-id="9b4d2-105">Syntax</span></span>  
  
```xml  
<certificate findValue = "String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b4d2-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9b4d2-106">Attributes and Elements</span></span>  

 <span data-ttu-id="9b4d2-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b4d2-108">属性</span><span class="sxs-lookup"><span data-stu-id="9b4d2-108">Attributes</span></span>  
  
|<span data-ttu-id="9b4d2-109">属性</span><span class="sxs-lookup"><span data-stu-id="9b4d2-109">Attribute</span></span>|<span data-ttu-id="9b4d2-110">説明</span><span class="sxs-lookup"><span data-stu-id="9b4d2-110">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="9b4d2-111">X.509 証明書ストアで検索する値を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-111">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="9b4d2-112">属性に格納されている型は、指定された `x509FindType` の要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-112">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="9b4d2-113">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-113">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="9b4d2-114">クライアントがピアの証明書の検証に使用する X.509 証明書ストアの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-114">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="9b4d2-115">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-115">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9b4d2-116">-LocalMachine: ローカルコンピューターに割り当てられた証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-116">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="9b4d2-117">-CurrentUser: 現在のユーザーに割り当てられている証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-117">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="9b4d2-118">既定値は LocalMachine です。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-118">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="9b4d2-119">開く X.509 証明書ストアの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-119">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="9b4d2-120">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9b4d2-121">-アドレス帳: 他のユーザーの証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-121">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="9b4d2-122">-AuthRoot: サードパーティの証明機関 (Ca) の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-122">-   AuthRoot: Certificate store for third-party certificate authorities (CAs).</span></span><br /><span data-ttu-id="9b4d2-123">-CertificateAuthority: 中間証明機関 (Ca) の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-123">-   CertificateAuthority: Certificate store for intermediate certificate authorities (CAs).</span></span><br /><span data-ttu-id="9b4d2-124">-許可されていません: 失効した証明書の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-124">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="9b4d2-125">-My: 個人証明書の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-125">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="9b4d2-126">-Root: 信頼されたルート証明機関 (Ca) の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-126">-   Root: Certificate store for trusted root certificate authorities (CAs).</span></span><br /><span data-ttu-id="9b4d2-127">-TrustedPeople: 直接信頼されている人間とリソースの証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-127">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="9b4d2-128">-TrustedPublisher: 直接信頼された発行元の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-128">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="9b4d2-129">既定値は My です。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-129">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="9b4d2-130">実行する X.509 検索の種類を定義します。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-130">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="9b4d2-131">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-131">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9b4d2-132">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="9b4d2-132">-   FindByThumbPrint</span></span><br /><span data-ttu-id="9b4d2-133">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="9b4d2-133">-   FindBySubjectName</span></span><br /><span data-ttu-id="9b4d2-134">-Findbysubjectdistinguishedname です</span><span class="sxs-lookup"><span data-stu-id="9b4d2-134">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="9b4d2-135">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="9b4d2-135">-   FindByIssuerName</span></span><br /><span data-ttu-id="9b4d2-136">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="9b4d2-136">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="9b4d2-137">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="9b4d2-137">-   FindBySerialNumber</span></span><br /><span data-ttu-id="9b4d2-138">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="9b4d2-138">-   FindByTimeValid</span></span><br /><span data-ttu-id="9b4d2-139">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="9b4d2-139">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="9b4d2-140">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="9b4d2-140">-   FindByTemplateName</span></span><br /><span data-ttu-id="9b4d2-141">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="9b4d2-141">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="9b4d2-142">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="9b4d2-142">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="9b4d2-143">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="9b4d2-143">-   FindByExtension</span></span><br /><span data-ttu-id="9b4d2-144">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="9b4d2-144">-   FindByKeyUsage</span></span><br /><span data-ttu-id="9b4d2-145">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="9b4d2-145">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="9b4d2-146">`findValue` 属性に格納されている型は、指定された `X509FindType` の要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-146">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="9b4d2-147">既定値は FindBySubjectDistinguishedName です。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-147">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9b4d2-148">子要素</span><span class="sxs-lookup"><span data-stu-id="9b4d2-148">Child Elements</span></span>  

 <span data-ttu-id="9b4d2-149">なし。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9b4d2-150">親要素</span><span class="sxs-lookup"><span data-stu-id="9b4d2-150">Parent Elements</span></span>  
  
|<span data-ttu-id="9b4d2-151">要素</span><span class="sxs-lookup"><span data-stu-id="9b4d2-151">Element</span></span>|<span data-ttu-id="9b4d2-152">説明</span><span class="sxs-lookup"><span data-stu-id="9b4d2-152">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="9b4d2-153">ピア ノードの現在の資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-153">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b4d2-154">解説</span><span class="sxs-lookup"><span data-stu-id="9b4d2-154">Remarks</span></span>  

 <span data-ttu-id="9b4d2-155">この構成要素には、ピア メッシュ内の近隣ノードを認証するときに使用される `X509Certificate2` インスタンスが格納されます。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-155">This configuration element contains an `X509Certificate2` instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="9b4d2-156">ピアツーピアプログラミングの詳細については、「 [ピアツーピアネットワーク](../../../wcf/feature-details/peer-to-peer-networking.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b4d2-156">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b4d2-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b4d2-157">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="9b4d2-158">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="9b4d2-158">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="9b4d2-159">ピアツーピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="9b4d2-159">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="9b4d2-160">[ピア チャネル メッセージの認証](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9b4d2-160">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="9b4d2-161">[ピア チャネル カスタム認証](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9b4d2-161">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="9b4d2-162">セキュリティによるピア チャネル アプリケーションの保護</span><span class="sxs-lookup"><span data-stu-id="9b4d2-162">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="9b4d2-163">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="9b4d2-163">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
