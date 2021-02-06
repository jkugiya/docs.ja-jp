---
description: '詳細については、「方法: メタデータエンドポイントをセキュリティで保護する」をご覧ください。'
title: '方法: セキュリティで保護されたメタデータ エンドポイント'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: bcce3fd0708049435c791cae5064f84133dfd612
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643307"
---
# <a name="how-to-secure-metadata-endpoints"></a><span data-ttu-id="b6452-103">方法: セキュリティで保護されたメタデータ エンドポイント</span><span class="sxs-lookup"><span data-stu-id="b6452-103">How to: Secure Metadata Endpoints</span></span>

<span data-ttu-id="b6452-104">サービスのメタデータには、悪意のあるユーザーに利用される可能性がある、アプリケーションに関する機密情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b6452-104">Metadata for a service can contain sensitive information about your application that a malicious user can leverage.</span></span> <span data-ttu-id="b6452-105">また、サービスのコンシューマーにも、サービスのメタデータを取得するためのセキュリティで保護された機構が必要です。</span><span class="sxs-lookup"><span data-stu-id="b6452-105">Consumers of your service may also require a secure mechanism for obtaining metadata about your service.</span></span> <span data-ttu-id="b6452-106">したがって、状況に応じて、セキュリティで保護されたエンドポイントを使用してメタデータを公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6452-106">Therefore, it is sometimes necessary to publish your metadata using a secure endpoint.</span></span>

<span data-ttu-id="b6452-107">一般に、メタデータエンドポイントは、アプリケーションエンドポイントを保護するために Windows Communication Foundation (WCF) に定義されている標準のセキュリティ機構を使用して保護されます。</span><span class="sxs-lookup"><span data-stu-id="b6452-107">Metadata endpoints are generally secured using the standard security mechanisms defined in Windows Communication Foundation (WCF) for securing application endpoints.</span></span> <span data-ttu-id="b6452-108">詳細については、[セキュリティの概要](security-overview.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6452-108">For more information, see [Security Overview](security-overview.md).</span></span>

<span data-ttu-id="b6452-109">ここでは、SSL (Secure Sockets Layer) 証明書によって保護されたエンドポイント (つまり、HTTPS エンドポイント) を作成する手順を示します。</span><span class="sxs-lookup"><span data-stu-id="b6452-109">This topic walks through the steps to create an endpoint secured by a Secure Sockets Layer (SSL) certificate or, in other words, an HTTPS endpoint.</span></span>

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a><span data-ttu-id="b6452-110">セキュリティで保護された HTTPS GET メタデータ エンドポイントをコードで作成するには</span><span class="sxs-lookup"><span data-stu-id="b6452-110">To create a secure HTTPS GET metadata endpoint in code</span></span>

1. <span data-ttu-id="b6452-111">適切な X.509 証明書を使用してポートを構成します。</span><span class="sxs-lookup"><span data-stu-id="b6452-111">Configure a port with an appropriate X.509 certificate.</span></span> <span data-ttu-id="b6452-112">この証明書は信頼された証明機関から発行され、かつ "サービス承認" の用途に使用される必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6452-112">The certificate must come from a trusted authority, and it must have an intended use of "Service Authorization."</span></span> <span data-ttu-id="b6452-113">証明書をポートに関連付けるには、HttpCfg.exe ツールを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6452-113">You must use the HttpCfg.exe tool to attach the certificate to the port.</span></span> <span data-ttu-id="b6452-114">「 [方法: SSL 証明書を使用してポートを構成する](how-to-configure-a-port-with-an-ssl-certificate.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6452-114">See [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="b6452-115">証明書またはそのドメイン ネーム システム (DNS: Domain Name System) のサブジェクトが、コンピューターの名前と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6452-115">The subject of the certificate or its Domain Name System (DNS) must match the name of the computer.</span></span> <span data-ttu-id="b6452-116">これは、HTTPS 機構が最初に実行する手順に、呼び出されたアドレスと同じ URI (Uniform Resource Identifier) に対して証明書が発行されているかどうかのチェックが含まれるために必要です。</span><span class="sxs-lookup"><span data-stu-id="b6452-116">This is essential because one of the first steps the HTTPS mechanism performs is to check that the certificate is issued to the same Uniform Resource Identifier (URI) as the address upon which it is invoked.</span></span>

2. <span data-ttu-id="b6452-117"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> クラスの新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b6452-117">Create a new instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class.</span></span>

3. <span data-ttu-id="b6452-118"><xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> クラスの <xref:System.ServiceModel.Description.ServiceMetadataBehavior> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="b6452-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> property of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class to `true`.</span></span>

4. <span data-ttu-id="b6452-119"><xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> プロパティを適切な URL に設定します。</span><span class="sxs-lookup"><span data-stu-id="b6452-119">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> property to an appropriate URL.</span></span> <span data-ttu-id="b6452-120">絶対アドレスを指定する場合、URL はスキームで始まる必要があることに注意してください `https://` 。</span><span class="sxs-lookup"><span data-stu-id="b6452-120">Note that if you specify an absolute address, the URL must begin with the scheme `https://`.</span></span> <span data-ttu-id="b6452-121">相対アドレスを指定する場合は、サービス ホストに HTTPS ベースのアドレスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6452-121">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="b6452-122">このプロパティが設定されていない場合、既定のアドレスは ""、またはサービスに HTTPS ベースのアドレスを直接指定したものになります。</span><span class="sxs-lookup"><span data-stu-id="b6452-122">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>

5. <span data-ttu-id="b6452-123">作成したインスタンスを、<xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> クラスの <xref:System.ServiceModel.Description.ServiceDescription> プロパティから返される動作コレクションに追加します。コードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b6452-123">Add the instance to the behaviors collection that the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property of the <xref:System.ServiceModel.Description.ServiceDescription> class returns, as shown in the following code.</span></span>

    [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
    [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a><span data-ttu-id="b6452-124">セキュリティで保護された HTTPS GET メタデータ エンドポイントを構成で作成するには</span><span class="sxs-lookup"><span data-stu-id="b6452-124">To create a secure HTTPS GET metadata endpoint in configuration</span></span>

1. <span data-ttu-id="b6452-125">[\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) サービスの構成ファイルの要素に要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="b6452-125">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element of the configuration file for your service.</span></span>

2. <span data-ttu-id="b6452-126">要素 [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) に要素を追加 [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) します。</span><span class="sxs-lookup"><span data-stu-id="b6452-126">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) element to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

3. <span data-ttu-id="b6452-127">要素 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) に要素を追加 `<serviceBehaviors>` します。</span><span class="sxs-lookup"><span data-stu-id="b6452-127">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element to the `<serviceBehaviors>` element.</span></span>

4. <span data-ttu-id="b6452-128">`name` 要素の `<behavior>` 属性を適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="b6452-128">Set the `name` attribute of the `<behavior>` element to an appropriate value.</span></span> <span data-ttu-id="b6452-129">`name` 属性は必須です。</span><span class="sxs-lookup"><span data-stu-id="b6452-129">The `name` attribute is required.</span></span> <span data-ttu-id="b6452-130">下の例では、`mySvcBehavior` を値として使用しています。</span><span class="sxs-lookup"><span data-stu-id="b6452-130">The example below uses the value `mySvcBehavior`.</span></span>

5. <span data-ttu-id="b6452-131">を [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) 要素に追加し `<behavior>` ます。</span><span class="sxs-lookup"><span data-stu-id="b6452-131">Add a [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) to the `<behavior>` element.</span></span>

6. <span data-ttu-id="b6452-132">`httpsGetEnabled` 要素の `<serviceMetadata>` 属性を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="b6452-132">Set the `httpsGetEnabled` attribute of the `<serviceMetadata>` element to `true`.</span></span>

7. <span data-ttu-id="b6452-133">`httpsGetUrl` 要素の `<serviceMetadata>` 属性を適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="b6452-133">Set the `httpsGetUrl` attribute of the `<serviceMetadata>` element to an appropriate value.</span></span> <span data-ttu-id="b6452-134">絶対アドレスを指定する場合、URL はスキームで始まる必要があることに注意してください `https://` 。</span><span class="sxs-lookup"><span data-stu-id="b6452-134">Note that if you specify an absolute address, the URL must begin with the scheme `https://`.</span></span> <span data-ttu-id="b6452-135">相対アドレスを指定する場合は、サービス ホストに HTTPS ベースのアドレスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6452-135">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="b6452-136">このプロパティが設定されていない場合、既定のアドレスは ""、またはサービスに HTTPS ベースのアドレスを直接指定したものになります。</span><span class="sxs-lookup"><span data-stu-id="b6452-136">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>

8. <span data-ttu-id="b6452-137">サービスで動作を使用するには、 `behaviorConfiguration` 要素の属性を [\<service>](../../configure-apps/file-schema/wcf/service.md) behavior 要素の name 属性の値に設定します。</span><span class="sxs-lookup"><span data-stu-id="b6452-137">To use the behavior with a service, set the `behaviorConfiguration` attribute of the [\<service>](../../configure-apps/file-schema/wcf/service.md) element to the value of the name attribute of the behavior element.</span></span> <span data-ttu-id="b6452-138">完全な構成コードを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="b6452-138">The following configuration code shows a complete example.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
     <system.serviceModel>
      <behaviors>
       <serviceBehaviors>
        <behavior name="mySvcBehavior">
         <serviceMetadata httpsGetEnabled="true"
              httpsGetUrl="https://localhost:8036/calcMetadata" />
        </behavior>
       </serviceBehaviors>
      </behaviors>
     <services>
      <service behaviorConfiguration="mySvcBehavior"
            name="Microsoft.Security.Samples.Calculator">
       <endpoint address="http://localhost:8037/ServiceModelSamples/calculator"
       binding="wsHttpBinding" bindingConfiguration=""
       contract="Microsoft.Security.Samples.ICalculator" />
      </service>
     </services>
    </system.serviceModel>
    </configuration>
    ```

## <a name="example"></a><span data-ttu-id="b6452-139">例</span><span class="sxs-lookup"><span data-stu-id="b6452-139">Example</span></span>

<span data-ttu-id="b6452-140">次の例では、<xref:System.ServiceModel.ServiceHost> クラスのインスタンスを作成して、エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="b6452-140">The following example creates an instance of a <xref:System.ServiceModel.ServiceHost> class and adds an endpoint.</span></span> <span data-ttu-id="b6452-141">次に、<xref:System.ServiceModel.Description.ServiceMetadataBehavior> クラスのインスタンスを作成し、プロパティを設定してセキュリティで保護された Metadata Exchange ポイントを作成しています。</span><span class="sxs-lookup"><span data-stu-id="b6452-141">The code then creates an instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class and sets the properties to create a secure metadata exchange point.</span></span>

[!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
[!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="b6452-142">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b6452-142">Compiling the Code</span></span>

<span data-ttu-id="b6452-143">このコード例では、次の名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="b6452-143">The code example uses the following namespaces:</span></span>

- <xref:System.ServiceModel?displayProperty=nameWithType>

- <xref:System.ServiceModel.Description?displayProperty=nameWithType>

## <a name="see-also"></a><span data-ttu-id="b6452-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6452-144">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [<span data-ttu-id="b6452-145">方法: SSL 証明書を使用してポートを構成する</span><span class="sxs-lookup"><span data-stu-id="b6452-145">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="b6452-146">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="b6452-146">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="b6452-147">メタデータを使用する場合のセキュリティ上の考慮事項</span><span class="sxs-lookup"><span data-stu-id="b6452-147">Security Considerations with Metadata</span></span>](security-considerations-with-metadata.md)
- [<span data-ttu-id="b6452-148">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="b6452-148">Securing Services and Clients</span></span>](securing-services-and-clients.md)
