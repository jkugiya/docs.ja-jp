---
description: '詳細情報: クライアントのセキュリティ保護'
title: クライアントのセキュリティ保護
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
ms.openlocfilehash: d78ad2fba00a0707dcf1c63681d9d76e68a31c00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99676444"
---
# <a name="securing-clients"></a><span data-ttu-id="f6058-103">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="f6058-103">Securing Clients</span></span>

<span data-ttu-id="f6058-104">Windows Communication Foundation (WCF) では、サービスはクライアントのセキュリティ要件を決定します。</span><span class="sxs-lookup"><span data-stu-id="f6058-104">In Windows Communication Foundation (WCF), the service dictates the security requirements for clients.</span></span> <span data-ttu-id="f6058-105">つまり、使用するセキュリティ モード、およびクライアントが資格情報を提供するかどうかは、サービスによって指定されます。</span><span class="sxs-lookup"><span data-stu-id="f6058-105">That is, the service specifies what security mode to use, and whether or not the client must provide a credential.</span></span> <span data-ttu-id="f6058-106">そのため、クライアントをセキュリティで保護するプロセスは、サービスから取得したメタデータ (公開されている場合) を使用してクライアントを構築するという簡単なものになります。</span><span class="sxs-lookup"><span data-stu-id="f6058-106">The process of securing a client, therefore, is simple: use the metadata obtained from the service (if it is published) and build a client.</span></span> <span data-ttu-id="f6058-107">クライアントを構成する方法は、メタデータによって指定されます。</span><span class="sxs-lookup"><span data-stu-id="f6058-107">The metadata specifies how to configure the client.</span></span> <span data-ttu-id="f6058-108">クライアントが資格情報を提供することをサービスが要求する場合、要件に適した資格情報を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6058-108">If the service requires that the client supply a credential, then you must obtain a credential that fits the requirement.</span></span> <span data-ttu-id="f6058-109">ここでは、このプロセスについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="f6058-109">This topic discusses the process in further detail.</span></span> <span data-ttu-id="f6058-110">セキュリティで保護されたサービスの作成の詳細については、「 [サービスのセキュリティ保護](securing-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6058-110">For more information about creating a secure service, see [Securing Services](securing-services.md).</span></span>  
  
## <a name="the-service-specifies-security"></a><span data-ttu-id="f6058-111">サービスによるセキュリティの指定</span><span class="sxs-lookup"><span data-stu-id="f6058-111">The Service Specifies Security</span></span>  

 <span data-ttu-id="f6058-112">既定では、WCF バインドではセキュリティ機能が有効になっています。</span><span class="sxs-lookup"><span data-stu-id="f6058-112">By default, WCF bindings have security features enabled.</span></span> <span data-ttu-id="f6058-113">(例外は <xref:System.ServiceModel.BasicHttpBinding> です)。このため、WCF を使用してサービスを作成した場合、認証、機密性、および整合性を確保するためにセキュリティを実装する可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="f6058-113">(The exception is the <xref:System.ServiceModel.BasicHttpBinding>.) Therefore, if the service was created using WCF, there is a greater chance that it will implement security to ensure authentication, confidentiality, and integrity.</span></span> <span data-ttu-id="f6058-114">この場合、サービスが提供するメタデータによって、セキュリティで保護された通信チャネルの確立に必要なものが示されます。</span><span class="sxs-lookup"><span data-stu-id="f6058-114">In that case, the metadata the service provides will indicate what it requires to establish a secure communication channel.</span></span> <span data-ttu-id="f6058-115">サービス メタデータにセキュリティ要件がまったく含まれていない場合には、サービスでセキュリティ スキーム (SSL (Secure Sockets Layer) over HTTP など) を強制する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="f6058-115">If the service metadata does not include any security requirements, there is no way to impose a security scheme, such as Secure Sockets Layer (SSL) over HTTP, on a service.</span></span> <span data-ttu-id="f6058-116">ただし、サービスがクライアントに資格情報の提供を求める場合は、クライアントの開発者、展開担当者、または管理者は、クライアントがサービスに対して認証を受けるときに実際に使用する資格情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6058-116">If, however, the service requires the client to supply a credential, then the client developer, deployer, or administrator must supply the actual credential that the client will use to authenticate itself to the service.</span></span>  
  
## <a name="obtaining-metadata"></a><span data-ttu-id="f6058-117">メタデータの取得</span><span class="sxs-lookup"><span data-stu-id="f6058-117">Obtaining Metadata</span></span>  

 <span data-ttu-id="f6058-118">クライアントを作成する場合、最初の手順はクライアントが通信を行うサービスからメタデータを取得することです。</span><span class="sxs-lookup"><span data-stu-id="f6058-118">When creating a client, the first step is to obtain the metadata for the service that the client will communicate with.</span></span> <span data-ttu-id="f6058-119">これは、次の 2 つの方法で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f6058-119">This can be done in two ways.</span></span> <span data-ttu-id="f6058-120">最初に、サービスが metadata exchange (MEX) エンドポイントを公開するか、または HTTP または HTTPS 経由でメタデータを使用できるようにする場合、 [ServiceModel メタデータユーティリティツール (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)を使用してメタデータをダウンロードできます。これにより、クライアントのコードファイルと構成ファイルの両方が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f6058-120">First, if the service publishes a metadata exchange (MEX) endpoint or makes its metadata available over HTTP or HTTPS, you can download the metadata using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), which generates both code files for a client as well as a configuration file.</span></span> <span data-ttu-id="f6058-121">(このツールの使用方法の詳細については、「 [WCF クライアントを使用したサービスへのアクセス](accessing-services-using-a-wcf-client.md)」を参照してください)。サービスが MEX エンドポイントを公開しておらず、そのメタデータを HTTP または HTTPS で使用できない場合は、サービスの作成者に、セキュリティ要件とメタデータについてのドキュメントを問い合わせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6058-121">(For more information about using the tool, see [Accessing Services Using a WCF Client](accessing-services-using-a-wcf-client.md).) If the service does not publish a MEX endpoint and also does not make its metadata available over HTTP or HTTPS, you must contact the service creator for documentation that describes the security requirements and the metadata.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f6058-122">メタデータが信頼されたソースのものであり、改ざんされていないことを確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f6058-122">It is recommended that the metadata come from a trusted source and that it not be tampered with.</span></span> <span data-ttu-id="f6058-123">HTTP プロトコルを使用して取得したメタデータはクリア テキストで送信されるため、改ざんされるおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="f6058-123">Metadata retrieved using the HTTP protocol is sent in clear text and can be tampered with.</span></span> <span data-ttu-id="f6058-124">サービスで <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> プロパティおよび <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> プロパティを使用している場合は、サービス作成者から提供された URL で、HTTPS プロトコルを使用してデータをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="f6058-124">If the service uses the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> and <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> properties, use the URL the service creator supplied to download the data using the HTTPS protocol.</span></span>  
  
## <a name="validating-security"></a><span data-ttu-id="f6058-125">セキュリティの検証</span><span class="sxs-lookup"><span data-stu-id="f6058-125">Validating Security</span></span>  

 <span data-ttu-id="f6058-126">メタデータのソースは、信頼されたソースと信頼関係のないソースの 2 つに大きく分けられます。</span><span class="sxs-lookup"><span data-stu-id="f6058-126">Metadata sources can be divided into two broad categories: trust sources and untrusted sources.</span></span> <span data-ttu-id="f6058-127">ソースを信頼しており、そのソースのセキュリティで保護された MEX エンドポイントからクライアント コードとその他のメタデータをダウンロードしている場合、何の懸念もなく、クライアントをビルドし、適切な資格情報を提供して実行できます。</span><span class="sxs-lookup"><span data-stu-id="f6058-127">If you trust a source and have downloaded the client code and other metadata from that source's secure MEX endpoint, then you can build the client, supply it with the right credentials, and run it with no other concerns.</span></span>  
  
 <span data-ttu-id="f6058-128">ただし、ほとんど未知のソースからクライアントとメタデータをダウンロードする場合は、コードで使用しているセキュリティ対策を検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6058-128">However, if you elect to download a client and metadata from a source that you know little about, be sure to validate the security measures the code uses.</span></span> <span data-ttu-id="f6058-129">たとえば、サービスにより (最低でも) 機密性と整合性とが要求されていない場合は、個人情報や財務情報を送信するクライアントを作成するようなことは絶対に避けてください。</span><span class="sxs-lookup"><span data-stu-id="f6058-129">For example, you must not simply create a client that sends your personal or financial information to a service unless the service demands confidentiality and integrity (at the very least).</span></span> <span data-ttu-id="f6058-130">このような情報が表示されるため、サービスの所有者は、このような情報を開示する範囲に信頼する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6058-130">You should trust the owner of the service to the extent that you are willing to disclose such information, because such information will be visible to them.</span></span>  
  
 <span data-ttu-id="f6058-131">したがって、信頼できないソースから受け取ったコードとメタデータを使用する場合には、それがこちらの必要とするセキュリティ レベルを満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6058-131">As a rule, therefore, when using code and metadata from an untrusted source, check the code and metadata to ensure that it meets the security level that you require.</span></span>  
  
## <a name="setting-a-client-credential"></a><span data-ttu-id="f6058-132">クライアント資格情報の設定</span><span class="sxs-lookup"><span data-stu-id="f6058-132">Setting a Client Credential</span></span>  

 <span data-ttu-id="f6058-133">クライアントへの資格情報の設定には、次の 2 つの手順があります。</span><span class="sxs-lookup"><span data-stu-id="f6058-133">Setting a client credential on a client consists of two steps:</span></span>  
  
1. <span data-ttu-id="f6058-134">サービスが必要とする *クライアント資格情報の種類* を決定します。</span><span class="sxs-lookup"><span data-stu-id="f6058-134">Determine the *client credential type* the service requires.</span></span> <span data-ttu-id="f6058-135">これは、2 つある方法のどちらかによって行います。</span><span class="sxs-lookup"><span data-stu-id="f6058-135">This is accomplished by one of two methods.</span></span> <span data-ttu-id="f6058-136">1 つ目の方法として、サービス作成者からドキュメントを入手している場合は、このドキュメントにサービスが要求するクライアント資格情報の種類が示されています (クライアント資格情報の種類が指定されている場合)。</span><span class="sxs-lookup"><span data-stu-id="f6058-136">First, if you have documentation from the service creator, it should specify the client credential type (if any) the service requires.</span></span> <span data-ttu-id="f6058-137">2 番目の方法は Svcutil.exe ツールによって作成された構成ファイルしかない場合で、個々のバインディングを調べることで必要な資格情報の種類を特定できます。</span><span class="sxs-lookup"><span data-stu-id="f6058-137">Second, if you have only a configuration file generated by the Svcutil.exe tool, you can examine the individual bindings to determine what credential type is required.</span></span>  
  
2. <span data-ttu-id="f6058-138">実際のクライアント資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="f6058-138">Specify an actual client credential.</span></span> <span data-ttu-id="f6058-139">実際のクライアント資格情報は、型と区別するために *クライアント資格* 情報の値と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="f6058-139">The actual client credential is called a *client credential value* to distinguish it from the type.</span></span> <span data-ttu-id="f6058-140">たとえば、クライアント資格情報の種類として証明書が指定されている場合、サービスが信頼する証明機関によって発行された X.509 証明書を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6058-140">For example, if the client credential type specifies a certificate, you must supply an X.509 certificate that is issued by a certification authority the service trusts.</span></span>  
  
### <a name="determining-the-client-credential-type"></a><span data-ttu-id="f6058-141">クライアント資格情報の種類の特定</span><span class="sxs-lookup"><span data-stu-id="f6058-141">Determining the Client Credential Type</span></span>  

 <span data-ttu-id="f6058-142">Svcutil.exe ツールによって生成された構成ファイルがある場合は、セクションを調べて、 [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) 必要なクライアント資格情報の種類を確認します。</span><span class="sxs-lookup"><span data-stu-id="f6058-142">If you have the configuration file the Svcutil.exe tool generated, examine the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) section to determine what client credential type is required.</span></span> <span data-ttu-id="f6058-143">このセクション内には、セキュリティ要件を指定するバインド要素があります。</span><span class="sxs-lookup"><span data-stu-id="f6058-143">Within the section are binding elements that specify the security requirements.</span></span> <span data-ttu-id="f6058-144">具体的には、 \<security> 各バインドの要素を調べます。</span><span class="sxs-lookup"><span data-stu-id="f6058-144">Specifically, examine the \<security> Element of each binding.</span></span> <span data-ttu-id="f6058-145">この要素には `mode` 属性が含まれており、3 つの値のいずれか (`Message`、`Transport`、または `TransportWithMessageCredential`) に設定できます。</span><span class="sxs-lookup"><span data-stu-id="f6058-145">That element includes the `mode` attribute, which you can set to one of three possible values (`Message`, `Transport`, or `TransportWithMessageCredential`).</span></span> <span data-ttu-id="f6058-146">この属性の値によってモードが決定され、このモードによってどの子要素が有効なのかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="f6058-146">The value of the attribute determines the mode, and the mode determines which of the child elements is significant.</span></span>  
  
 <span data-ttu-id="f6058-147">`<security>`要素には、要素または要素のいずれか `<transport>` `<message>` 、またはその両方を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f6058-147">The `<security>` element can contain either a `<transport>` or `<message>` element, or both.</span></span> <span data-ttu-id="f6058-148">セキュリティ モードと一致する要素が有効な要素です。</span><span class="sxs-lookup"><span data-stu-id="f6058-148">The significant element is the one that matches the security mode.</span></span> <span data-ttu-id="f6058-149">たとえば、次のコードでは、セキュリティ モードを `"Message"`、`<message>` 要素のクライアント資格情報の種類を `"Certificate"` に指定しています。</span><span class="sxs-lookup"><span data-stu-id="f6058-149">For example, the following code specifies that the security mode is `"Message"`, and the client credential type for the `<message>` element is `"Certificate"`.</span></span> <span data-ttu-id="f6058-150">この場合、`<transport>` 要素は無視できます。</span><span class="sxs-lookup"><span data-stu-id="f6058-150">In this case, the `<transport>` element can be ignored.</span></span> <span data-ttu-id="f6058-151">ただし、`<message>` 要素で X.509 証明書を提示する必要があることが指定されています。</span><span class="sxs-lookup"><span data-stu-id="f6058-151">However, the `<message>` element specifies that an X.509 certificate must be supplied.</span></span>  

```xml  
<wsHttpBinding>  
    <binding name="WSHttpBinding_ICalculator">  
       <security mode="Message">  
           <transport clientCredentialType="Windows"
                      realm="" />  
           <message clientCredentialType="Certificate"
                    negotiateServiceCredential="true"  
                    algorithmSuite="Default"
                    establishSecurityContext="true" />  
       </security>  
    </binding>  
</wsHttpBinding>  
```  

 <span data-ttu-id="f6058-152">次の例に示すように、`clientCredentialType` 属性が `"Windows"` に設定されている場合は、実際の資格情報の値を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f6058-152">Note that if the `clientCredentialType` attribute is set to `"Windows"`, as shown in the following example, you do not need to supply an actual credential value.</span></span> <span data-ttu-id="f6058-153">これは、Windows 統合セキュリティでは、クライアントを実行しているユーザーの実際の資格情報 (Kerberos トークン) が提供されるためです。</span><span class="sxs-lookup"><span data-stu-id="f6058-153">This is because the Windows integrated security provides the actual credential (a Kerberos token) of the person who is running the client.</span></span>  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a><span data-ttu-id="f6058-154">クライアント資格情報の値の設定</span><span class="sxs-lookup"><span data-stu-id="f6058-154">Setting the Client Credential Value</span></span>  

 <span data-ttu-id="f6058-155">クライアントが資格情報を提供する必要があると特定された場合は、クライアントを構成する適切なメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f6058-155">If it is determined that the client must supply a credential, use the appropriate method to configure the client.</span></span> <span data-ttu-id="f6058-156">たとえば、クライアント証明書を設定するには、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f6058-156">For example, to set a client certificate, use the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span>  
  
 <span data-ttu-id="f6058-157">X.509 証明書は広く使用されている資格情報の形式です。</span><span class="sxs-lookup"><span data-stu-id="f6058-157">A common form of credential is the X.509 certificate.</span></span> <span data-ttu-id="f6058-158">資格情報は次の 2 つの方法で提供できます。</span><span class="sxs-lookup"><span data-stu-id="f6058-158">You can supply the credential in two ways:</span></span>  
  
- <span data-ttu-id="f6058-159">クライアント コードで (`SetCertificate` メソッドを使用して) プログラミングする方法。</span><span class="sxs-lookup"><span data-stu-id="f6058-159">By programming it in your client code (using the `SetCertificate` method).</span></span>  
  
 <span data-ttu-id="f6058-160">[\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)次に示すように、クライアントの構成ファイルのセクションを追加し、要素を使用し `clientCredentials` ます。</span><span class="sxs-lookup"><span data-stu-id="f6058-160">By adding a [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) section of the configuration file for the client and using the `clientCredentials` element (shown below).</span></span>  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a><span data-ttu-id="f6058-161">\<clientCredentials>コード内での値の設定</span><span class="sxs-lookup"><span data-stu-id="f6058-161">Setting a \<clientCredentials> Value in Code</span></span>  

 <span data-ttu-id="f6058-162">コードに値を設定するには、 [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) クラスのプロパティにアクセスする必要があり <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> <xref:System.ServiceModel.ClientBase%601> ます。</span><span class="sxs-lookup"><span data-stu-id="f6058-162">To set a [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) value in code, you must access the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class.</span></span> <span data-ttu-id="f6058-163">このプロパティは、次の表に示すように、各種の資格情報の種類にアクセスできる <xref:System.ServiceModel.Description.ClientCredentials> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="f6058-163">The property returns a <xref:System.ServiceModel.Description.ClientCredentials> object that allows access to various credential types, as shown in the following table.</span></span>  
  
|<span data-ttu-id="f6058-164">ClientCredential プロパティ</span><span class="sxs-lookup"><span data-stu-id="f6058-164">ClientCredential Property</span></span>|<span data-ttu-id="f6058-165">説明</span><span class="sxs-lookup"><span data-stu-id="f6058-165">Description</span></span>|<span data-ttu-id="f6058-166">メモ</span><span class="sxs-lookup"><span data-stu-id="f6058-166">Notes</span></span>|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|<span data-ttu-id="f6058-167"><xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> を返します</span><span class="sxs-lookup"><span data-stu-id="f6058-167">Returns an <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential></span></span>|<span data-ttu-id="f6058-168">クライアントがサービスに対して自身を認証するために提供する X.509 証明書を表します。</span><span class="sxs-lookup"><span data-stu-id="f6058-168">Represents an X.509 certificate provided by the client to authenticate itself to the service.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|<span data-ttu-id="f6058-169"><xref:System.ServiceModel.Security.HttpDigestClientCredential> を返します</span><span class="sxs-lookup"><span data-stu-id="f6058-169">Returns an <xref:System.ServiceModel.Security.HttpDigestClientCredential></span></span>|<span data-ttu-id="f6058-170">HTTP ダイジェスト資格情報を表します。</span><span class="sxs-lookup"><span data-stu-id="f6058-170">Represents an HTTP digest credential.</span></span> <span data-ttu-id="f6058-171">この資格情報は、ユーザー名とパスワードのハッシュです。</span><span class="sxs-lookup"><span data-stu-id="f6058-171">The credential is a hash of the user name and password.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|<span data-ttu-id="f6058-172"><xref:System.ServiceModel.Security.IssuedTokenClientCredential> を返します</span><span class="sxs-lookup"><span data-stu-id="f6058-172">Returns an <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>|<span data-ttu-id="f6058-173">フェデレーション シナリオで通常使用される、セキュリティ トークン サービスによって発行されるカスタム セキュリティ トークンを表します。</span><span class="sxs-lookup"><span data-stu-id="f6058-173">Represents a custom security token issued by a Security Token Service, commonly used in federation scenarios.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|<span data-ttu-id="f6058-174"><xref:System.ServiceModel.Security.PeerCredential> を返します</span><span class="sxs-lookup"><span data-stu-id="f6058-174">Returns a <xref:System.ServiceModel.Security.PeerCredential></span></span>|<span data-ttu-id="f6058-175">Windows ドメインのピア メッシュに参加するためのピア資格情報を表します。</span><span class="sxs-lookup"><span data-stu-id="f6058-175">Represents a Peer credential for participation in a Peer mesh on a Windows domain.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|<span data-ttu-id="f6058-176"><xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> を返します</span><span class="sxs-lookup"><span data-stu-id="f6058-176">Returns an <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential></span></span>|<span data-ttu-id="f6058-177">帯域外ネゴシエーションでサービスによって提供される X.509 証明書を表します。</span><span class="sxs-lookup"><span data-stu-id="f6058-177">Represents an X.509 certificate provided by the service in an out-of-band negotiation.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|<span data-ttu-id="f6058-178"><xref:System.ServiceModel.Security.UserNamePasswordClientCredential> を返します</span><span class="sxs-lookup"><span data-stu-id="f6058-178">Returns a <xref:System.ServiceModel.Security.UserNamePasswordClientCredential></span></span>|<span data-ttu-id="f6058-179">ユーザー名とパスワードのペアを表します。</span><span class="sxs-lookup"><span data-stu-id="f6058-179">Represents a user name and password pair.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|<span data-ttu-id="f6058-180"><xref:System.ServiceModel.Security.WindowsClientCredential> を返します</span><span class="sxs-lookup"><span data-stu-id="f6058-180">Returns a <xref:System.ServiceModel.Security.WindowsClientCredential></span></span>|<span data-ttu-id="f6058-181">Windows クライアントの資格情報 (Kerberos 資格情報) を表します。</span><span class="sxs-lookup"><span data-stu-id="f6058-181">Represents a Windows client credential (a Kerberos credential).</span></span> <span data-ttu-id="f6058-182">このクラスのプロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="f6058-182">The properties of the class are read-only.</span></span>|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a><span data-ttu-id="f6058-183">\<clientCredentials>構成での値の設定</span><span class="sxs-lookup"><span data-stu-id="f6058-183">Setting a \<clientCredentials> Value in Configuration</span></span>  

 <span data-ttu-id="f6058-184">資格情報の値は、要素の子要素としてエンドポイントの動作を使用して指定し [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) ます。</span><span class="sxs-lookup"><span data-stu-id="f6058-184">Credential values are specified by using an endpoint behavior as child elements of the [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span> <span data-ttu-id="f6058-185">使用される要素は、クライアントの資格情報の種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="f6058-185">The element used depends on the client credential type.</span></span> <span data-ttu-id="f6058-186">たとえば、次の例では、<を使用して x.509 証明書を設定する構成を示して [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md) います。</span><span class="sxs-lookup"><span data-stu-id="f6058-186">For example, the following example shows the configuration to set an X.509 certificate using the <[\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>
        <behavior name="myEndpointBehavior">  
          <clientCredentials>  
            <clientCertificate findvalue="myMachineName"
            storeLocation="Current" X509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>
      </endpointBehaviors>
    </behaviors>
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="f6058-187">構成でクライアント資格情報を設定するには、 [\<endpointBehaviors>](../configure-apps/file-schema/wcf/endpointbehaviors.md) 構成ファイルに要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="f6058-187">To set the client credential in configuration, add an [\<endpointBehaviors>](../configure-apps/file-schema/wcf/endpointbehaviors.md) element to the configuration file.</span></span> <span data-ttu-id="f6058-188">さらに、 `behaviorConfiguration` 次の例に示すように、 [ \<endpoint> \<client> ](../configure-apps/file-schema/wcf/endpoint-of-client.md)追加された behavior 要素は、要素のの属性を使用してサービスのエンドポイントにリンクされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6058-188">Additionally, the added behavior element must be linked to the service's endpoint using the `behaviorConfiguration` attribute of the [\<endpoint> of \<client>](../configure-apps/file-schema/wcf/endpoint-of-client.md) element as shown in the following example.</span></span> <span data-ttu-id="f6058-189">`behaviorConfiguration` 属性の値は、動作の `name` 属性の値と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6058-189">The value of the `behaviorConfiguration` attribute must match the value of the behavior `name` attribute.</span></span>  

```xml
<configuration>
  <system.serviceModel>
    <client>
      <endpoint address="http://localhost/servicemodelsamples/service.svc"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                behaviorConfiguration="myEndpointBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>
  </system.serviceModel>
</configuration>
```
  
> [!NOTE]
> <span data-ttu-id="f6058-190">クライアント資格情報の値の中には、アプリケーション構成ファイルを使用して設定できないものがあります (ユーザー名とパスワードや、Windows ユーザーとパスワードの値など)。</span><span class="sxs-lookup"><span data-stu-id="f6058-190">Some of the client credential values cannot be set using application configuration files, for example, user name and password, or Windows user and password values.</span></span> <span data-ttu-id="f6058-191">このような資格情報の値は、コードでのみ指定できます。</span><span class="sxs-lookup"><span data-stu-id="f6058-191">Such credential values can be specified only in code.</span></span>  
  
 <span data-ttu-id="f6058-192">クライアント資格情報の設定の詳細については、「 [方法: クライアント資格情報の値を指定する](how-to-specify-client-credential-values.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6058-192">For more information about setting the client credential, see [How to: Specify Client Credential Values](how-to-specify-client-credential-values.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6058-193">次の構成例に示すように、`ClientCredentialType` が `SecurityMode` に設定されている場合、`"TransportWithMessageCredential",` は無視されます。</span><span class="sxs-lookup"><span data-stu-id="f6058-193">`ClientCredentialType` is ignored when `SecurityMode` is set to `"TransportWithMessageCredential",` as shown in the following sample configuration.</span></span>  
  
```xml  
<wsHttpBinding>  
    <binding name="PingBinding">  
        <security mode="TransportWithMessageCredential"  >  
           <message  clientCredentialType="UserName"
               establishSecurityContext="false"
               negotiateServiceCredential="false" />  
           <transport clientCredentialType="Certificate"  />  
         </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6058-194">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6058-194">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [\<bindings>](../configure-apps/file-schema/wcf/bindings.md)
- [<span data-ttu-id="f6058-195">構成エディター ツール (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="f6058-195">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](configuration-editor-tool-svcconfigeditor-exe.md)
- [<span data-ttu-id="f6058-196">サービスのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="f6058-196">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="f6058-197">WCF クライアントを使用したサービスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="f6058-197">Accessing Services Using a WCF Client</span></span>](accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="f6058-198">方法: クライアントの資格情報の値を指定する</span><span class="sxs-lookup"><span data-stu-id="f6058-198">How to: Specify Client Credential Values</span></span>](how-to-specify-client-credential-values.md)
- [<span data-ttu-id="f6058-199">ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="f6058-199">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="f6058-200">方法: クライアントの資格情報の種類を指定する</span><span class="sxs-lookup"><span data-stu-id="f6058-200">How to: Specify the Client Credential Type</span></span>](how-to-specify-the-client-credential-type.md)
