---
description: '詳細については、「方法: 双方向フェデレーションバインディングを作成する」を参照してください。'
title: '方法: 双方向フェデレーション バインディングを作成する'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 92d5eeeffab88d88aa245b51738048dced2d5d2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779908"
---
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="9b867-103">方法: 双方向フェデレーション バインディングを作成する</span><span class="sxs-lookup"><span data-stu-id="9b867-103">How to: Create a Duplex Federated Binding</span></span>

<span data-ttu-id="9b867-104"><xref:System.ServiceModel.WSFederationHttpBinding> はデータグラムと要求/応答メッセージの交換コントラクトのみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="9b867-104"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="9b867-105">双方向メッセージ交換コントラクトを使用するには、カスタム バインディングを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b867-105">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="9b867-106">次の手順は、構成の中でそれを行う方法を説明します。HTTP と TCP トランスポートにはメッセージ モード セキュリティを、TCP トランスポートには混合モード セキュリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="9b867-106">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="9b867-107">このトピックの最後に 3 つのバインディングすべてのサンプル コードがあります。</span><span class="sxs-lookup"><span data-stu-id="9b867-107">Sample code showing all 3 bindings is at the end of this topic.</span></span>

<span data-ttu-id="9b867-108">バインディングはコード内でも作成できます。</span><span class="sxs-lookup"><span data-stu-id="9b867-108">You can also create the binding in code.</span></span> <span data-ttu-id="9b867-109">作成するバインド要素スタックの説明については、「 [方法: カスタムバインディングを使用してカスタムバインディングを作成](how-to-create-a-custom-binding-using-the-securitybindingelement.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b867-109">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="9b867-110">HTTP で双方向カスタム フェデレーション バインディングを作成するには</span><span class="sxs-lookup"><span data-stu-id="9b867-110">To create a duplex federated custom binding with HTTP</span></span>

1. <span data-ttu-id="9b867-111">[\<bindings>](../../configure-apps/file-schema/wcf/bindings.md)構成ファイルのノードで、要素を作成 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) します。</span><span class="sxs-lookup"><span data-stu-id="9b867-111">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="9b867-112">要素内に、 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 属性をに設定して要素を作成 `name` `FederationDuplexHttpMessageSecurityBinding` します。</span><span class="sxs-lookup"><span data-stu-id="9b867-112">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="9b867-113">要素内に、 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 属性をに設定して要素を作成 `authenticationMode` `SecureConversation` します。</span><span class="sxs-lookup"><span data-stu-id="9b867-113">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="9b867-114">要素内に、 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 属性を [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` またはに設定して要素を作成し `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` ます。</span><span class="sxs-lookup"><span data-stu-id="9b867-114">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="9b867-115">要素の後 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) に、空の [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) 要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="9b867-115">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>

6. <span data-ttu-id="9b867-116">要素の後 [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) に、空の [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) 要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="9b867-116">Following the [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element.</span></span>

7. <span data-ttu-id="9b867-117">要素の後 [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) に、空の [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) 要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="9b867-117">Following the [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="9b867-118">TCP メッセージ セキュリティ モードで双方向カスタム フェデレーション バインディングを作成するには</span><span class="sxs-lookup"><span data-stu-id="9b867-118">To create a duplex federated custom binding with TCP message security mode</span></span>

1. <span data-ttu-id="9b867-119">[\<bindings>](../../configure-apps/file-schema/wcf/bindings.md)構成ファイルのノードで、要素を作成 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) します。</span><span class="sxs-lookup"><span data-stu-id="9b867-119">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="9b867-120">要素内に、 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 属性をに設定して要素を作成 `name` `FederationDuplexTcpMessageSecurityBinding` します。</span><span class="sxs-lookup"><span data-stu-id="9b867-120">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="9b867-121">要素内に、 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 属性をに設定して要素を作成 `authenticationMode` `SecureConversation` します。</span><span class="sxs-lookup"><span data-stu-id="9b867-121">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="9b867-122">要素内に、 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 属性を [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` またはに設定して要素を作成し `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` ます。</span><span class="sxs-lookup"><span data-stu-id="9b867-122">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="9b867-123">要素の後 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) に、空の [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) 要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="9b867-123">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="9b867-124">TCP 混合セキュリティ モードで双方向カスタム フェデレーション バインディングを作成するには</span><span class="sxs-lookup"><span data-stu-id="9b867-124">To create a duplex federated custom binding with TCP mixed security mode</span></span>

1. <span data-ttu-id="9b867-125">[\<bindings>](../../configure-apps/file-schema/wcf/bindings.md)構成ファイルのノードで、要素を作成 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) します。</span><span class="sxs-lookup"><span data-stu-id="9b867-125">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="9b867-126">要素内に、 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 属性をに設定して要素を作成 `name` `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` します。</span><span class="sxs-lookup"><span data-stu-id="9b867-126">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>

3. <span data-ttu-id="9b867-127">要素内に、 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 属性をに設定して要素を作成 `authenticationMode` `SecureConversation` します。</span><span class="sxs-lookup"><span data-stu-id="9b867-127">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="9b867-128">要素内に、 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 属性を [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) `authenticationMode` またはに設定して要素を作成し `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` ます。</span><span class="sxs-lookup"><span data-stu-id="9b867-128">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="9b867-129">要素の後 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) に、空の [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) 要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="9b867-129">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>

6. <span data-ttu-id="9b867-130">要素の後 [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) に、空の [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) 要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="9b867-130">Following the [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="code-sample"></a><span data-ttu-id="9b867-131">コード サンプル</span><span class="sxs-lookup"><span data-stu-id="9b867-131">Code Sample</span></span>

### <a name="sample-with-3-bindings"></a><span data-ttu-id="9b867-132">3 つのバインディングの例</span><span class="sxs-lookup"><span data-stu-id="9b867-132">Sample with 3 Bindings</span></span>

1. <span data-ttu-id="9b867-133">次のコードを構成ファイルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="9b867-133">Insert the following code into your configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="9b867-134">例</span><span class="sxs-lookup"><span data-stu-id="9b867-134">Example</span></span>

```xml
<bindings>
   <customBinding>
      <binding name="FederationDuplexHttpMessageSecurityBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />
          </security>
          <compositeDuplex />
          <oneWay />
          <httpTransport />
       </binding>
<!-- duplex over https is not supported -->
       <binding name="FederationDuplexTcpMessageSecurityBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />
          </security>
          <tcpTransport />
       </binding>
       <binding name="FederationDuplexTcpTransportSecurityWithMessageCredentialsBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenOverTransport" />
          </security>
<!-- requireClientCertificate = true or <windowsStreamSecurity /> can be used, but does not make sense for most scenarios -->
          <sslStreamSecurity />
          <tcpTransport />
       </binding>
    </customBinding>
</bindings>
```
