---
description: '詳細情報: <certificate> 要素'
title: <certificate> 要素
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: 3f67435d86f19f81c1f6fe1fe2a9a8afbef69e53
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639134"
---
# <a name="certificate-element"></a><span data-ttu-id="e9509-103">\<certificate> 要素</span><span class="sxs-lookup"><span data-stu-id="e9509-103">\<certificate> Element</span></span>

<span data-ttu-id="e9509-104">ピアツーピア クライアントのメッセージの署名と暗号化に使用する X.509 証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9509-104">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="e9509-105">構文</span><span class="sxs-lookup"><span data-stu-id="e9509-105">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9509-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e9509-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e9509-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9509-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9509-108">属性</span><span class="sxs-lookup"><span data-stu-id="e9509-108">Attributes</span></span>  
  
|<span data-ttu-id="e9509-109">属性</span><span class="sxs-lookup"><span data-stu-id="e9509-109">Attribute</span></span>|<span data-ttu-id="e9509-110">説明</span><span class="sxs-lookup"><span data-stu-id="e9509-110">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="e9509-111">X.509 証明書ストアで検索する値を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="e9509-111">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="e9509-112">属性に格納されている型は、指定された `x509FindType` の要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9509-112">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="e9509-113">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="e9509-113">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="e9509-114">クライアントがピアの証明書の検証に使用する X.509 証明書ストアの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9509-114">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="e9509-115">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e9509-115">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e9509-116">-   LocalMachine: ローカル マシンに割り当てられた証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="e9509-116">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="e9509-117">-   CurrentUser: 現在のユーザーに割り当てられた証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="e9509-117">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="e9509-118">既定値は LocalMachine です。</span><span class="sxs-lookup"><span data-stu-id="e9509-118">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="e9509-119">開く X.509 証明書ストアの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9509-119">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="e9509-120">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e9509-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e9509-121">-   AddressBook: 他のユーザー用の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="e9509-121">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="e9509-122">-   AuthRoot: サードパーティ証明機関 (CA) の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="e9509-122">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="e9509-123">-   CertificateAuthority: 中間証明機関 (CA) の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="e9509-123">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="e9509-124">-   Disallowed: 失効した証明書の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="e9509-124">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="e9509-125">-   My: 個人用証明書の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="e9509-125">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="e9509-126">-   Root: 信頼されたルート証明機関 (CA) の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="e9509-126">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="e9509-127">-   TrustedPeople: 直接信頼されたユーザーやリソースの証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="e9509-127">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="e9509-128">-   TrustedPublisher: 直接信頼された発行者の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="e9509-128">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="e9509-129">既定値は My です。</span><span class="sxs-lookup"><span data-stu-id="e9509-129">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="e9509-130">実行する X.509 検索の種類を定義します。</span><span class="sxs-lookup"><span data-stu-id="e9509-130">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="e9509-131">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e9509-131">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e9509-132">-   FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="e9509-132">-   FindByThumbPrint</span></span><br /><span data-ttu-id="e9509-133">-   FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="e9509-133">-   FindBySubjectName</span></span><br /><span data-ttu-id="e9509-134">-   FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="e9509-134">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="e9509-135">-   FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="e9509-135">-   FindByIssuerName</span></span><br /><span data-ttu-id="e9509-136">-   FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="e9509-136">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="e9509-137">-   FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="e9509-137">-   FindBySerialNumber</span></span><br /><span data-ttu-id="e9509-138">-   FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="e9509-138">-   FindByTimeValid</span></span><br /><span data-ttu-id="e9509-139">-   FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="e9509-139">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="e9509-140">-   FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="e9509-140">-   FindByTemplateName</span></span><br /><span data-ttu-id="e9509-141">-   FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="e9509-141">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="e9509-142">-   FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="e9509-142">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="e9509-143">-   FindByExtension</span><span class="sxs-lookup"><span data-stu-id="e9509-143">-   FindByExtension</span></span><br /><span data-ttu-id="e9509-144">-   FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="e9509-144">-   FindByKeyUsage</span></span><br /><span data-ttu-id="e9509-145">-   FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="e9509-145">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="e9509-146">`findValue` 属性に格納されている型は、指定された `X509FindType` の要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9509-146">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="e9509-147">既定値は FindBySubjectDistinguishedName です。</span><span class="sxs-lookup"><span data-stu-id="e9509-147">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9509-148">子要素</span><span class="sxs-lookup"><span data-stu-id="e9509-148">Child Elements</span></span>  

 <span data-ttu-id="e9509-149">なし。</span><span class="sxs-lookup"><span data-stu-id="e9509-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9509-150">親要素</span><span class="sxs-lookup"><span data-stu-id="e9509-150">Parent Elements</span></span>  
  
|<span data-ttu-id="e9509-151">要素</span><span class="sxs-lookup"><span data-stu-id="e9509-151">Element</span></span>|<span data-ttu-id="e9509-152">説明</span><span class="sxs-lookup"><span data-stu-id="e9509-152">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="e9509-153">ピアツーピア クライアントの認証時に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9509-153">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9509-154">解説</span><span class="sxs-lookup"><span data-stu-id="e9509-154">Remarks</span></span>  

 <span data-ttu-id="e9509-155">この構成要素には、ピア メッシュ内の近隣ノードを認証するときに使用される X509Certificate2 インスタンスが格納されます。</span><span class="sxs-lookup"><span data-stu-id="e9509-155">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="e9509-156">ピアツーピア プログラミングの詳細については、「[ピアツーピア ネットワーク](../../../wcf/feature-details/peer-to-peer-networking.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9509-156">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9509-157">例</span><span class="sxs-lookup"><span data-stu-id="e9509-157">Example</span></span>  

 <span data-ttu-id="e9509-158">次のコードは、ピアツーピア シナリオで使用される証明書の検索方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9509-158">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="e9509-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9509-159">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="e9509-160">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="e9509-160">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="e9509-161">ピアツーピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="e9509-161">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="e9509-162">[ピア チャネル メッセージの認証](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e9509-162">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="e9509-163">[ピア チャネル カスタム認証](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e9509-163">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="e9509-164">セキュリティによるピア チャネル アプリケーションの保護</span><span class="sxs-lookup"><span data-stu-id="e9509-164">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
