---
title: '方法: トランスポート セキュリティとメッセージ資格情報を使用する'
description: メッセージ資格情報を使用してトランスポート セキュリティを実装する方法について説明します。これにより、WCF でのトランスポートとメッセージのセキュリティ モードが最適になります。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
ms.openlocfilehash: dbf04572e19d0dfc2508b3f8c3295ffae78ca0f4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268314"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a><span data-ttu-id="565aa-103">方法: トランスポート セキュリティとメッセージ資格情報を使用する</span><span class="sxs-lookup"><span data-stu-id="565aa-103">How to: Use Transport Security and Message Credentials</span></span>

<span data-ttu-id="565aa-104">トランスポートとメッセージの両方の資格情報を使用してサービスをセキュリティで保護する場合、Windows Communication Foundation (WCF) では、トランスポートとメッセージの両方のセキュリティ モードが最適に使用されます。</span><span class="sxs-lookup"><span data-stu-id="565aa-104">Securing a service with both transport and message credentials uses the best of both Transport and Message security modes in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="565aa-105">つまり、トランスポート層セキュリティでは整合性と機密性が提供され、メッセージ層セキュリティでは、厳密なトランスポート セキュリティ機構では実現できないさまざまな資格情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="565aa-105">In sum, transport-layer security provides integrity and confidentiality, while message-layer security provides a variety of credentials that are not possible with strict transport security mechanisms.</span></span> <span data-ttu-id="565aa-106">ここでは、<xref:System.ServiceModel.WSHttpBinding> バインディングと <xref:System.ServiceModel.NetTcpBinding> バインディングを使用して、メッセージ資格情報付きトランスポートを実装するための基本手順を示します。</span><span class="sxs-lookup"><span data-stu-id="565aa-106">This topic shows the basic steps for implementing transport with message credentials using the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> bindings.</span></span> <span data-ttu-id="565aa-107">セキュリティ モードの設定の詳細については、「[方法: セキュリティ モードを設定する](../how-to-set-the-security-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="565aa-107">For more information about setting the security mode, see [How to: Set the Security Mode](../how-to-set-the-security-mode.md).</span></span>  
  
 <span data-ttu-id="565aa-108">セキュリティ モードを `TransportWithMessageCredential` に設定した場合、トランスポート レベルのセキュリティを提供する実際の機構はトランスポートによって決まります。</span><span class="sxs-lookup"><span data-stu-id="565aa-108">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="565aa-109">この機構は、HTTP の場合は SSL (Secure Sockets Layer) over HTTP (HTTPS)、TCP の場合は SSL over TCP または Windows です。</span><span class="sxs-lookup"><span data-stu-id="565aa-109">For HTTP, the mechanism is Secure Sockets Layer (SSL) over HTTP (HTTPS); for TCP, it is SSL over TCP or Windows.</span></span>  
  
 <span data-ttu-id="565aa-110">トランスポートが HTTP (<xref:System.ServiceModel.WSHttpBinding> を使用) の場合は、トランスポート レベルのセキュリティが SSL over HTTP によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="565aa-110">If the transport is HTTP (using the <xref:System.ServiceModel.WSHttpBinding>), SSL over HTTP provides the transport-level security.</span></span> <span data-ttu-id="565aa-111">この場合、このトピックで後述するように、ポートにバインドされた SSL 証明書を使用してサービスをホストするコンピューターを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="565aa-111">In that case, you must configure the computer hosting the service with an SSL certificate bound to a port, as shown later in this topic.</span></span>  
  
 <span data-ttu-id="565aa-112">トランスポートが TCP (<xref:System.ServiceModel.NetTcpBinding> を使用) の場合、既定では、Windows セキュリティ または SSL over TCP によってトランスポート レベルのセキュリティが提供されます。</span><span class="sxs-lookup"><span data-stu-id="565aa-112">If the transport is TCP (using the <xref:System.ServiceModel.NetTcpBinding>), by default the transport-level security provided is Windows security, or SSL over TCP.</span></span> <span data-ttu-id="565aa-113">SSL over TCP を使用する場合は、このトピックで後述するように、<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> メソッドを使用して証明書を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="565aa-113">When using SSL over TCP, you must specify the certificate using the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method, as shown later in this topic.</span></span>  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="565aa-114">WSHttpBinding と証明書を使用してトランスポート セキュリティを提供するには (コードを使用する場合)</span><span class="sxs-lookup"><span data-stu-id="565aa-114">To use the WSHttpBinding with a certificate for transport security (in code)</span></span>  
  
1. <span data-ttu-id="565aa-115">HttpCfg.exe ツールを使用して、コンピューターの任意のポートに SSL 証明書をバインドします。</span><span class="sxs-lookup"><span data-stu-id="565aa-115">Use the HttpCfg.exe tool to bind an SSL certificate to a port on the machine.</span></span> <span data-ttu-id="565aa-116">詳細については、「[方法: SSL 証明書を使用してポートを構成する](how-to-configure-a-port-with-an-ssl-certificate.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="565aa-116">For more information, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
2. <span data-ttu-id="565aa-117"><xref:System.ServiceModel.WSHttpBinding> クラスのインスタンスを作成し、<xref:System.ServiceModel.WSHttpSecurity.Mode%2A> プロパティを <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> に設定します。</span><span class="sxs-lookup"><span data-stu-id="565aa-117">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
3. <span data-ttu-id="565aa-118"><xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> プロパティに適切な値を設定します。</span><span class="sxs-lookup"><span data-stu-id="565aa-118">Set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="565aa-119">(詳細については、「[資格情報の種類の選択](selecting-a-credential-type.md)」を参照してください。)次のコードでは、<xref:System.ServiceModel.MessageCredentialType.Certificate> 値を使用しています。</span><span class="sxs-lookup"><span data-stu-id="565aa-119">(For more information, see [Selecting a Credential Type](selecting-a-credential-type.md).) The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4. <span data-ttu-id="565aa-120">適切なベース アドレスを持つ <xref:System.Uri> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="565aa-120">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="565aa-121">このアドレスでは、"HTTPS" スキームを使用し、コンピューターの実際の名前と SSL 証明書のバインド先のポート番号を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="565aa-121">Note that the address must use the "HTTPS" scheme and must contain the actual name of the machine and the port number that the SSL certificate is bound to.</span></span> <span data-ttu-id="565aa-122">(または、構成で基本アドレスを設定できます。)</span><span class="sxs-lookup"><span data-stu-id="565aa-122">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5. <span data-ttu-id="565aa-123"><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> メソッドを使用してサービス エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="565aa-123">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
6. <span data-ttu-id="565aa-124"><xref:System.ServiceModel.ServiceHost> のインスタンスを作成し、<xref:System.ServiceModel.ICommunicationObject.Open%2A> メソッドを呼び出します。コードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="565aa-124">Create the instance of the <xref:System.ServiceModel.ServiceHost> and call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="565aa-125">NetTcpBinding と証明書を使用してトランスポート セキュリティを提供するには (コードを使用する場合)</span><span class="sxs-lookup"><span data-stu-id="565aa-125">To use the NetTcpBinding with a certificate for transport security (in code)</span></span>  
  
1. <span data-ttu-id="565aa-126"><xref:System.ServiceModel.NetTcpBinding> クラスのインスタンスを作成し、<xref:System.ServiceModel.NetTcpSecurity.Mode%2A> プロパティを <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> に設定します。</span><span class="sxs-lookup"><span data-stu-id="565aa-126">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2. <span data-ttu-id="565aa-127"><xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> を適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="565aa-127">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="565aa-128">次のコードでは、<xref:System.ServiceModel.MessageCredentialType.Certificate> 値を使用しています。</span><span class="sxs-lookup"><span data-stu-id="565aa-128">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
3. <span data-ttu-id="565aa-129">適切なベース アドレスを持つ <xref:System.Uri> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="565aa-129">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="565aa-130">アドレスには "net.tcp" スキーマを使用する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="565aa-130">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="565aa-131">(または、構成で基本アドレスを設定できます。)</span><span class="sxs-lookup"><span data-stu-id="565aa-131">(Alternatively, you can set the base address in configuration.)</span></span>  
  
4. <span data-ttu-id="565aa-132"><xref:System.ServiceModel.ServiceHost> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="565aa-132">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
5. <span data-ttu-id="565aa-133"><xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> クラスの <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> メソッドを使用して、サービスに X.509 資格情報を明示的に設定します。</span><span class="sxs-lookup"><span data-stu-id="565aa-133">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
6. <span data-ttu-id="565aa-134"><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> メソッドを使用してサービス エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="565aa-134">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
7. <span data-ttu-id="565aa-135">次のコードに示すように、<xref:System.ServiceModel.ICommunicationObject.Open%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="565aa-135">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a><span data-ttu-id="565aa-136">NetTcpBinding と Windows を使用してトランスポート セキュリティを提供するには (コードを使用する場合)</span><span class="sxs-lookup"><span data-stu-id="565aa-136">To use the NetTcpBinding with Windows for transport security (in code)</span></span>  
  
1. <span data-ttu-id="565aa-137"><xref:System.ServiceModel.NetTcpBinding> クラスのインスタンスを作成し、<xref:System.ServiceModel.NetTcpSecurity.Mode%2A> プロパティを <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> に設定します。</span><span class="sxs-lookup"><span data-stu-id="565aa-137">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2. <span data-ttu-id="565aa-138">トランスポート セキュリティが Windows を使用するように、<xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> を <xref:System.ServiceModel.TcpClientCredentialType.Windows> に設定します </span><span class="sxs-lookup"><span data-stu-id="565aa-138">Set the transport security to use Windows by setting the <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> to <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span></span> <span data-ttu-id="565aa-139">(これは、既定の設定です)。</span><span class="sxs-lookup"><span data-stu-id="565aa-139">(Note that this is the default.)</span></span>  
  
3. <span data-ttu-id="565aa-140"><xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> を適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="565aa-140">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="565aa-141">次のコードでは、<xref:System.ServiceModel.MessageCredentialType.Certificate> 値を使用しています。</span><span class="sxs-lookup"><span data-stu-id="565aa-141">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4. <span data-ttu-id="565aa-142">適切なベース アドレスを持つ <xref:System.Uri> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="565aa-142">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="565aa-143">アドレスには "net.tcp" スキーマを使用する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="565aa-143">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="565aa-144">(または、構成で基本アドレスを設定できます。)</span><span class="sxs-lookup"><span data-stu-id="565aa-144">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5. <span data-ttu-id="565aa-145"><xref:System.ServiceModel.ServiceHost> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="565aa-145">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
6. <span data-ttu-id="565aa-146"><xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> クラスの <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> メソッドを使用して、サービスに X.509 資格情報を明示的に設定します。</span><span class="sxs-lookup"><span data-stu-id="565aa-146">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
7. <span data-ttu-id="565aa-147"><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> メソッドを使用してサービス エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="565aa-147">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
8. <span data-ttu-id="565aa-148">次のコードに示すように、<xref:System.ServiceModel.ICommunicationObject.Open%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="565aa-148">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a><span data-ttu-id="565aa-149">構成の使用</span><span class="sxs-lookup"><span data-stu-id="565aa-149">Using Configuration</span></span>  
  
#### <a name="to-use-the-wshttpbinding"></a><span data-ttu-id="565aa-150">WSHttpBinding を使用するには</span><span class="sxs-lookup"><span data-stu-id="565aa-150">To use the WSHttpBinding</span></span>  
  
1. <span data-ttu-id="565aa-151">ポートにバインドされた SSL 証明書を使用してコンピューターを構成します </span><span class="sxs-lookup"><span data-stu-id="565aa-151">Configure the computer with an SSL certificate bound to a port.</span></span> <span data-ttu-id="565aa-152">(詳細については、「[方法: SSL 証明書を使用してポートを構成する](how-to-configure-a-port-with-an-ssl-certificate.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="565aa-152">(For more information, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md)).</span></span> <span data-ttu-id="565aa-153">この構成では、<`transport`> 要素値を設定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="565aa-153">You do not need to set a <`transport`> element value with this configuration.</span></span>  
  
2. <span data-ttu-id="565aa-154">メッセージ レベルのセキュリティのクライアント資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="565aa-154">Specify the client credential type for the message-level security.</span></span> <span data-ttu-id="565aa-155">次の例では、<`message`> 要素の `clientCredentialType` 属性を `UserName` に設定しています。</span><span class="sxs-lookup"><span data-stu-id="565aa-155">The following example sets the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a><span data-ttu-id="565aa-156">NetTcpBinding と証明書を使用してトランスポート セキュリティを提供するには</span><span class="sxs-lookup"><span data-stu-id="565aa-156">To use the NetTcpBinding with a certificate for transport security</span></span>  
  
1. <span data-ttu-id="565aa-157">SSL over TCP の場合、`<behaviors>` 要素内で証明書を明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="565aa-157">For SSL over TCP, you must explicitly specify the certificate in the `<behaviors>` element.</span></span> <span data-ttu-id="565aa-158">既定のストアの場所 (ローカル コンピューターの個人ストア) にある証明書を、発行者で指定する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="565aa-158">The following example specifies a certificate by its issuer in the default store location (local machine and personal stores).</span></span>  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
       <behavior name="mySvcBehavior">  
           <serviceCredentials>  
             <serviceCertificate findValue="contoso.com"  
                                 x509FindType="FindByIssuerName" />  
           </serviceCredentials>  
       </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="565aa-159">[\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) をバインディング セクションに追加します</span><span class="sxs-lookup"><span data-stu-id="565aa-159">Add a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section</span></span>  
  
3. <span data-ttu-id="565aa-160">バインド要素を追加して、`name` 属性を適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="565aa-160">Add a binding element, and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="565aa-161"><`security`> 要素を追加し、`mode` 属性に `TransportWithMessageCredential` を設定します。</span><span class="sxs-lookup"><span data-stu-id="565aa-161">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
5. <span data-ttu-id="565aa-162"><`message>` 要素を追加し、`clientCredentialType` 属性に適切な値を設定します。</span><span class="sxs-lookup"><span data-stu-id="565aa-162">Add a <`message>` element, and set the `clientCredentialType` attribute to an appropriate value.</span></span>  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <message clientCredentialType="Windows" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a><span data-ttu-id="565aa-163">NetTcpBinding と Windows を使用してトランスポート セキュリティを提供するには</span><span class="sxs-lookup"><span data-stu-id="565aa-163">To use the NetTcpBinding with Windows for transport security</span></span>  
  
1. <span data-ttu-id="565aa-164">[\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) をバインディング セクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="565aa-164">Add a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section,</span></span>  
  
2. <span data-ttu-id="565aa-165"><`binding`> 要素を追加し、`name` 属性に適切な値を設定します。</span><span class="sxs-lookup"><span data-stu-id="565aa-165">Add a <`binding`> element and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="565aa-166"><`security`> 要素を追加し、`mode` 属性に `TransportWithMessageCredential` を設定します。</span><span class="sxs-lookup"><span data-stu-id="565aa-166">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
4. <span data-ttu-id="565aa-167"><`transport`> 要素を追加し、`clientCredentialType` 属性に `Windows` を設定します。</span><span class="sxs-lookup"><span data-stu-id="565aa-167">Add a <`transport`> element and set the `clientCredentialType` attribute to `Windows`.</span></span>  
  
5. <span data-ttu-id="565aa-168"><`message`> 要素を追加し、`clientCredentialType` 属性に適切な値を設定します。</span><span class="sxs-lookup"><span data-stu-id="565aa-168">Add a <`message`> element and set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="565aa-169">次のコードは、値を証明書に設定します。</span><span class="sxs-lookup"><span data-stu-id="565aa-169">The following code sets the value to a certificate.</span></span>  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <transport clientCredentialType="Windows" />  
           <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="565aa-170">関連項目</span><span class="sxs-lookup"><span data-stu-id="565aa-170">See also</span></span>

- [<span data-ttu-id="565aa-171">方法: セキュリティ モードを設定する</span><span class="sxs-lookup"><span data-stu-id="565aa-171">How to: Set the Security Mode</span></span>](../how-to-set-the-security-mode.md)
- [<span data-ttu-id="565aa-172">サービスのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="565aa-172">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="565aa-173">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="565aa-173">Securing Services and Clients</span></span>](securing-services-and-clients.md)
