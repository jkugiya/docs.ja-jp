---
description: '詳細については、次を参照してください: <certificate> of <clientCertificate> 要素'
title: <certificate><clientCertificate>要素の
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: a677c04055016c77794dd99a8c237b5eb6c13f5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639095"
---
# <a name="certificate-of-clientcertificate-element"></a><span data-ttu-id="beb8e-103">\<certificate>\<clientCertificate>要素の</span><span class="sxs-lookup"><span data-stu-id="beb8e-103">\<certificate> of \<clientCertificate> Element</span></span>

<span data-ttu-id="beb8e-104">メッセージの署名と暗号化に使用される X.509 証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="beb8e-104">Specifies an X.509 certificate used to sign and encrypt messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="beb8e-105">構文</span><span class="sxs-lookup"><span data-stu-id="beb8e-105">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="beb8e-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="beb8e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="beb8e-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="beb8e-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="beb8e-108">属性</span><span class="sxs-lookup"><span data-stu-id="beb8e-108">Attributes</span></span>  
  
|<span data-ttu-id="beb8e-109">属性</span><span class="sxs-lookup"><span data-stu-id="beb8e-109">Attribute</span></span>|<span data-ttu-id="beb8e-110">説明</span><span class="sxs-lookup"><span data-stu-id="beb8e-110">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="beb8e-111">X.509 証明書ストアで検索する値を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="beb8e-111">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="beb8e-112">属性に含まれている型は、指定された X509FindType の要件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="beb8e-112">The type contained in the attribute must satisfy the requirements of the specified X509FindType.</span></span> <span data-ttu-id="beb8e-113">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="beb8e-113">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="beb8e-114">クライアントがサーバーの証明書の検証に使用する X.509 証明書ストアの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="beb8e-114">Specifies the location of the X.509 certificate store that the client uses to validate the server’s certificate against.</span></span> <span data-ttu-id="beb8e-115">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="beb8e-115">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="beb8e-116">-LocalMachine: ローカルコンピューターに割り当てられた証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="beb8e-116">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="beb8e-117">-CurrentUser: 現在のユーザーに割り当てられている証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="beb8e-117">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="beb8e-118">既定値は LocalMachine です。</span><span class="sxs-lookup"><span data-stu-id="beb8e-118">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="beb8e-119">開く X.509 証明書ストアの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="beb8e-119">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="beb8e-120">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="beb8e-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="beb8e-121">-アドレス帳: 他のユーザーの証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="beb8e-121">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="beb8e-122">-AuthRoot: サードパーティ証明機関 (Ca) の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="beb8e-122">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="beb8e-123">-Microsoft-windows-certificationauthority: 中間証明機関 (Ca) の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="beb8e-123">-   CertificationAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="beb8e-124">-許可されていません: 失効した証明書の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="beb8e-124">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="beb8e-125">-My: 個人証明書の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="beb8e-125">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="beb8e-126">-Root: 信頼されたルート証明機関 (Ca) の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="beb8e-126">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="beb8e-127">-TrustedPeople: 直接信頼されている人間とリソースの証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="beb8e-127">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="beb8e-128">-TrustedPublisher: 直接信頼された発行元の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="beb8e-128">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="beb8e-129">既定値は My です。</span><span class="sxs-lookup"><span data-stu-id="beb8e-129">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="beb8e-130">実行する X.509 検索の種類を定義します。</span><span class="sxs-lookup"><span data-stu-id="beb8e-130">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="beb8e-131">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="beb8e-131">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="beb8e-132">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="beb8e-132">-   FindByThumbPrint</span></span><br /><span data-ttu-id="beb8e-133">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="beb8e-133">-   FindBySubjectName</span></span><br /><span data-ttu-id="beb8e-134">-Findbysubjectdistinguishedname です</span><span class="sxs-lookup"><span data-stu-id="beb8e-134">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="beb8e-135">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="beb8e-135">-   FindByIssuerName</span></span><br /><span data-ttu-id="beb8e-136">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="beb8e-136">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="beb8e-137">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="beb8e-137">-   FindBySerialNumber</span></span><br /><span data-ttu-id="beb8e-138">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="beb8e-138">-   FindByTimeValid</span></span><br /><span data-ttu-id="beb8e-139">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="beb8e-139">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="beb8e-140">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="beb8e-140">-   FindByTemplateName</span></span><br /><span data-ttu-id="beb8e-141">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="beb8e-141">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="beb8e-142">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="beb8e-142">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="beb8e-143">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="beb8e-143">-   FindByExtension</span></span><br /><span data-ttu-id="beb8e-144">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="beb8e-144">-   FindByKeyUsage</span></span><br /><span data-ttu-id="beb8e-145">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="beb8e-145">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="beb8e-146">`findValue` 属性に含まれている型は、指定された X509FindType の要件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="beb8e-146">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="beb8e-147">既定値は FindBySubjectDistinguishedName です。</span><span class="sxs-lookup"><span data-stu-id="beb8e-147">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="beb8e-148">子要素</span><span class="sxs-lookup"><span data-stu-id="beb8e-148">Child Elements</span></span>  

 <span data-ttu-id="beb8e-149">なし。</span><span class="sxs-lookup"><span data-stu-id="beb8e-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="beb8e-150">親要素</span><span class="sxs-lookup"><span data-stu-id="beb8e-150">Parent Elements</span></span>  
  
|<span data-ttu-id="beb8e-151">要素</span><span class="sxs-lookup"><span data-stu-id="beb8e-151">Element</span></span>|<span data-ttu-id="beb8e-152">説明</span><span class="sxs-lookup"><span data-stu-id="beb8e-152">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a><span data-ttu-id="beb8e-153">解説</span><span class="sxs-lookup"><span data-stu-id="beb8e-153">Remarks</span></span>  

 <span data-ttu-id="beb8e-154">`<certificate>` 要素は、サービスがクライアントと安全に通信するために、サービスが前もってクライアントの証明書を持っている必要がある場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="beb8e-154">The `<certificate>` element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="beb8e-155">このような状況は、双方向通信パターンを使用する場合に生じます。</span><span class="sxs-lookup"><span data-stu-id="beb8e-155">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="beb8e-156">より一般的な要求/応答パターンでは、クライアントは自身の証明書を要求に含め、サービスはそれを使用してクライアントへの応答を暗号化し、署名します。</span><span class="sxs-lookup"><span data-stu-id="beb8e-156">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="beb8e-157">一方、双方向通信パターンでは、サービスにはクライアントからの要求が来ないので、クライアントの証明書をあらかじめ取得することで、クライアント宛のメッセージのセキュリティを保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="beb8e-157">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="beb8e-158">このため、クライアントの証明書を帯域外のネゴシエーションで取得し、この要素を使用して証明書を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="beb8e-158">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="beb8e-159">双方向サービスの詳細については、「 [方法: 双方向コントラクトを作成](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="beb8e-159">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="beb8e-160">例</span><span class="sxs-lookup"><span data-stu-id="beb8e-160">Example</span></span>  

 <span data-ttu-id="beb8e-161">次のコードは、`<authentication>` 要素の適切な X.509 証明書とカスタム検証タイプの検索方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="beb8e-161">The following code specifies how to find an appropriate X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
                   storeLocation="CurrentUser"
                   storeName="TrustedPeople"
                   x509FindType="FindByIssuerName" />
      <authentication customCertificateValidatorType="MyTypes.Coho"
                      certificateValidationMode="Custom"
                      revocationMode="Offline"
                      includeWindowsGroups="false"
                      mapClientCertificateToWindowsAccount="true" />
    </clientCertificate>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="beb8e-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="beb8e-162">See also</span></span>

- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>
- [<span data-ttu-id="beb8e-163">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="beb8e-163">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="beb8e-164">方法: カスタム証明書検証を使用するサービスを作成する</span><span class="sxs-lookup"><span data-stu-id="beb8e-164">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="beb8e-165">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="beb8e-165">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
