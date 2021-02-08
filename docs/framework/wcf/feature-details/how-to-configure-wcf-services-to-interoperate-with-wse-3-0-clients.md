---
description: '詳細については、「方法: WCF サービスを構成して WSE 3.0 クライアントと相互運用する」を参照してください。'
title: '方法: WCF サービスと WSE 3.0 クライアントを相互運用するために構成する'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: d48b24ac7787a9863744ee9b6a4a984cb6b371e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779934"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="56b3e-103">方法: WCF サービスと WSE 3.0 クライアントを相互運用するために構成する</span><span class="sxs-lookup"><span data-stu-id="56b3e-103">How to: Configure WCF Services to Interoperate with WSE 3.0 Clients</span></span>

<span data-ttu-id="56b3e-104">Windows Communication Foundation (WCF) サービスは、3.0 年8月2004バージョンの WS-Addressing 仕様を使用するように WCF サービスが構成されている場合に、Microsoft .NET (WSE) クライアントの Web サービス拡張とのワイヤレベルの互換性があります。</span><span class="sxs-lookup"><span data-stu-id="56b3e-104">Windows Communication Foundation (WCF) services are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) clients when WCF services are configured to use the August 2004 version of the WS-Addressing specification.</span></span>

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="56b3e-105">WCF サービスを WSE 3.0 クライアントと相互運用できるようにするには</span><span class="sxs-lookup"><span data-stu-id="56b3e-105">To enable a WCF service to interoperate with WSE 3.0 clients</span></span>

1. <span data-ttu-id="56b3e-106">WCF サービスのカスタムバインドを定義します。</span><span class="sxs-lookup"><span data-stu-id="56b3e-106">Define a custom binding for the WCF service.</span></span>

    <span data-ttu-id="56b3e-107">メッセージ エンコーディングに 2004 年 8 月版の WS-Addressing 仕様が使用されるように指定するには、カスタム バインディングを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56b3e-107">To specify that the August 2004 version of the WS-Addressing specification is used for message encoding, a custom binding must be created.</span></span>

    1. <span data-ttu-id="56b3e-108">[\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) サービスの構成ファイルのに子を追加します。</span><span class="sxs-lookup"><span data-stu-id="56b3e-108">Add a child [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) to the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) of the service's configuration file.</span></span>

    2. <span data-ttu-id="56b3e-109">にを追加し、属性を設定することにより、バインディングの名前を指定し [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) `name` ます。</span><span class="sxs-lookup"><span data-stu-id="56b3e-109">Specify a name for the binding, by adding a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) to the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) and setting the `name` attribute.</span></span>

    3. <span data-ttu-id="56b3e-110">に子を追加することによって、認証モードと、WSE 3.0 と互換性のあるメッセージをセキュリティで保護するために使用される WS-Security 仕様のバージョンを指定し [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) ます。</span><span class="sxs-lookup"><span data-stu-id="56b3e-110">Specify an authentication mode and the version of the WS-Security specifications that are used to secure messages that are compatible with WSE 3.0, by adding a child [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) to the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md).</span></span>

        <span data-ttu-id="56b3e-111">認証モードを設定するには、 `authenticationMode` の属性を設定し [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="56b3e-111">To set the authentication mode, set the `authenticationMode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="56b3e-112">認証モードは、WSE 3.0 の設定不要のセキュリティ アサーションとほぼ同等です。</span><span class="sxs-lookup"><span data-stu-id="56b3e-112">An authentication mode is roughly equivalent to a turnkey security assertion in WSE 3.0.</span></span> <span data-ttu-id="56b3e-113">次の表では、WCF の認証モードを WSE 3.0 のターンキーセキュリティアサーションにマップします。</span><span class="sxs-lookup"><span data-stu-id="56b3e-113">The following table maps authentication modes in WCF to turnkey security assertions in WSE 3.0.</span></span>

        |<span data-ttu-id="56b3e-114">WCF 認証モード</span><span class="sxs-lookup"><span data-stu-id="56b3e-114">WCF Authentication Mode</span></span>|<span data-ttu-id="56b3e-115">WSE 3.0 の設定不要のセキュリティ アサーション</span><span class="sxs-lookup"><span data-stu-id="56b3e-115">WSE 3.0 turnkey security assertion</span></span>|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        <span data-ttu-id="56b3e-116">\* とターンキーのセキュリティアサーションの主な違いの1つ `mutualCertificate10Security` `mutualCertificate11Security` は、WSE が SOAP メッセージをセキュリティで保護するために使用する WS-Security 仕様のバージョンです。</span><span class="sxs-lookup"><span data-stu-id="56b3e-116">\* One of the primary differences between the `mutualCertificate10Security` and `mutualCertificate11Security` turnkey security assertions is the version of the WS-Security specification that WSE uses to secure the SOAP messages.</span></span> <span data-ttu-id="56b3e-117">`mutualCertificate10Security` では WS-Security 1.0 が使用され、`mutualCertificate11Security` では WS-Security 1.1 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="56b3e-117">For `mutualCertificate10Security`, WS-Security 1.0 is used, whereas WS-Security 1.1 is used for `mutualCertificate11Security`.</span></span> <span data-ttu-id="56b3e-118">WCF の場合、WS-Security 指定のバージョンはの属性で指定され `messageSecurityVersion` [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="56b3e-118">For WCF, the version of the WS-Security specification is specified in the `messageSecurityVersion` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>

        <span data-ttu-id="56b3e-119">SOAP メッセージをセキュリティで保護するために使用される WS-Security 仕様のバージョンを設定するには、の属性を設定し `messageSecurityVersion` [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="56b3e-119">To set the version of the WS-Security specification that is used to secure SOAP messages, set the `messageSecurityVersion` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="56b3e-120">WSE 3.0 と相互運用するには、`messageSecurityVersion` 属性の値を <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A> に設定します。</span><span class="sxs-lookup"><span data-stu-id="56b3e-120">To interoperate with WSE 3.0, set the value of the `messageSecurityVersion` attribute to <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span></span>

    4. <span data-ttu-id="56b3e-121">を追加し、を値に設定することによって、WS-Addressing 仕様の8月2004バージョンが WCF によって使用されることを指定し [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) `messageVersion` <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="56b3e-121">Specify that the August 2004 version of the WS-Addressing specification is used by WCF by adding a [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) and set the `messageVersion` to its value to <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span></span>

        > [!NOTE]
        > <span data-ttu-id="56b3e-122">SOAP 1.2 の使用時には、`messageVersion` 属性を <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A> に設定します。</span><span class="sxs-lookup"><span data-stu-id="56b3e-122">When you are using SOAP 1.2, set the `messageVersion` attribute to <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span></span>

2. <span data-ttu-id="56b3e-123">サービスがカスタム バインドを使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="56b3e-123">Specify that the service uses the custom binding.</span></span>

    1. <span data-ttu-id="56b3e-124">`binding`要素の属性 [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) をに設定 `customBinding` します。</span><span class="sxs-lookup"><span data-stu-id="56b3e-124">Set the `binding` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element to `customBinding`.</span></span>

    2. <span data-ttu-id="56b3e-125">`bindingConfiguration`要素の属性 [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) を `name` 、カスタムバインドのの属性で指定された値に設定し [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) ます。</span><span class="sxs-lookup"><span data-stu-id="56b3e-125">Set the `bindingConfiguration` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element to the value specified in the `name` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) for the custom binding.</span></span>

## <a name="example"></a><span data-ttu-id="56b3e-126">例</span><span class="sxs-lookup"><span data-stu-id="56b3e-126">Example</span></span>

<span data-ttu-id="56b3e-127">次のコード例では、`Service.HelloWorldService` が WSE 3.0 クライアントと相互運用するためにカスタム バインドを使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="56b3e-127">The following code example specifies that the `Service.HelloWorldService` uses a custom binding to interoperate with WSE 3.0 clients.</span></span> <span data-ttu-id="56b3e-128">カスタム バインドには 2004 年 8 月版の WS-Addressing が指定され、WS-Security 1.1 の一連の仕様が、交換されるメッセージのエンコードに使用されます。</span><span class="sxs-lookup"><span data-stu-id="56b3e-128">The custom binding specifies that the August 2004 version of the WS-Addressing and the WS-Security 1.1 set of specifications are used to encode the exchanged messages.</span></span> <span data-ttu-id="56b3e-129">メッセージは、<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> 認証モードを使用してセキュリティ保護されます。</span><span class="sxs-lookup"><span data-stu-id="56b3e-129">The messages are secured using the <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> authentication mode.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <services>
      <service
        behaviorConfiguration="ServiceBehavior"
        name="Service.HelloWorldService">
        <endpoint binding="customBinding" address=""
          bindingConfiguration="ServiceBinding"
          contract="Service.IHelloWorld"></endpoint>
      </service>
    </services>

    <bindings>
      <customBinding>
        <binding name="ServiceBinding">
          <security authenticationMode="AnonymousForCertificate"
                  messageProtectionOrder="SignBeforeEncrypt"
                  messageSecurityVersion="WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10"
                  requireDerivedKeys="false">
          </security>
          <textMessageEncoding messageVersion ="Soap11WSAddressingAugust2004"></textMessageEncoding>
          <httpTransport/>
        </binding>
      </customBinding>
    </bindings>
    <behaviors>
      <behavior name="ServiceBehavior" returnUnknownExceptionsAsFaults="true">
        <serviceCredentials>
          <serviceCertificate findValue="CN=WCFQuickstartServer" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName"/>
        </serviceCredentials>
      </behavior>
    </behaviors>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="56b3e-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="56b3e-130">See also</span></span>

- [<span data-ttu-id="56b3e-131">方法: システム指定のバインディングをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="56b3e-131">How to: Customize a System-Provided Binding</span></span>](../extending/how-to-customize-a-system-provided-binding.md)
