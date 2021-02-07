---
description: '詳細については、「方法: セキュリティで保護されたセッションを作成する」をご覧ください。'
title: '方法: セキュリティで保護されたセッションを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: 7d1c76ed2925c3c4cca4242f3f02b8850fb64f19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734712"
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="ec2da-103">方法: セキュリティで保護されたセッションを作成する</span><span class="sxs-lookup"><span data-stu-id="ec2da-103">How to: Create a Secure Session</span></span>

<span data-ttu-id="ec2da-104">バインディングを除き、 [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) Windows Communication Foundation (WCF) のシステム指定のバインディングでは、メッセージセキュリティが有効になっている場合、セキュリティで保護されたセッションが自動的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="ec2da-104">With the exception of the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in Windows Communication Foundation (WCF) automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="ec2da-105">既定では、セキュリティで保護されたセッションは、再利用される Web サーバーで存続します。</span><span class="sxs-lookup"><span data-stu-id="ec2da-105">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="ec2da-106">セキュリティで保護されたセッションが確立されると、クライアントとサービスが、セキュリティで保護されたセッションに関連付けられているキーをキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="ec2da-106">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="ec2da-107">メッセージを交換するときは、キャッシュされたキーの識別子のみが交換されます。</span><span class="sxs-lookup"><span data-stu-id="ec2da-107">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="ec2da-108">Web サーバーが再利用される場合は、Web サーバーが識別子のキャッシュされたキーを取得できないようにキャッシュも再利用されます。</span><span class="sxs-lookup"><span data-stu-id="ec2da-108">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="ec2da-109">これが発生した場合、例外がクライアントにスローされます。</span><span class="sxs-lookup"><span data-stu-id="ec2da-109">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="ec2da-110">ステートフルなセキュリティ コンテキスト トークン (SCT: Security Context Token) を使用するセキュリティで保護されたセッションは、再利用される Web サーバーで存続することができます。</span><span class="sxs-lookup"><span data-stu-id="ec2da-110">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> <span data-ttu-id="ec2da-111">セキュリティで保護されたセッションでのステートフルな SCT の使用の詳細については、「 [方法: セキュリティで保護されたセッションのセキュリティコンテキストトークンを作成](how-to-create-a-security-context-token-for-a-secure-session.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec2da-111">For more information about using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="ec2da-112">サービスが、システム提供のバインディングの 1 つを使用して、セキュリティで保護されたセッションを使用するように指定するには</span><span class="sxs-lookup"><span data-stu-id="ec2da-112">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
- <span data-ttu-id="ec2da-113">メッセージ セキュリティをサポートするシステム提供のバインディングを使用するようにサービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="ec2da-113">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="ec2da-114">バインディングを除き、 [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) システム指定のバインディングがメッセージセキュリティを使用するように構成されている場合、WCF は自動的にセキュリティで保護されたセッションを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec2da-114">With the exception of the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, WCF automatically uses secure sessions.</span></span> <span data-ttu-id="ec2da-115">次の表は、メッセージ セキュリティをサポートするシステム提供のバインディングを示し、そのバインディングでメッセージ セキュリティが既定のセキュリティ機構であるかどうかを示しています。</span><span class="sxs-lookup"><span data-stu-id="ec2da-115">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="ec2da-116">システム提供のバインディング</span><span class="sxs-lookup"><span data-stu-id="ec2da-116">System-provided binding</span></span>|<span data-ttu-id="ec2da-117">構成要素</span><span class="sxs-lookup"><span data-stu-id="ec2da-117">Configuration element</span></span>|<span data-ttu-id="ec2da-118">既定でメッセージ セキュリティが有効</span><span class="sxs-lookup"><span data-stu-id="ec2da-118">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="ec2da-119">いいえ</span><span class="sxs-lookup"><span data-stu-id="ec2da-119">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="ec2da-120">はい</span><span class="sxs-lookup"><span data-stu-id="ec2da-120">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="ec2da-121">はい</span><span class="sxs-lookup"><span data-stu-id="ec2da-121">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="ec2da-122">はい</span><span class="sxs-lookup"><span data-stu-id="ec2da-122">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="ec2da-123">いいえ</span><span class="sxs-lookup"><span data-stu-id="ec2da-123">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="ec2da-124">いいえ</span><span class="sxs-lookup"><span data-stu-id="ec2da-124">No</span></span>|  
  
     <span data-ttu-id="ec2da-125">次のコード例では、構成を使用して、 `wsHttpBinding_Calculator` [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 、メッセージセキュリティ、およびセキュリティで保護されたセッションを使用するという名前のバインディングを指定します。</span><span class="sxs-lookup"><span data-stu-id="ec2da-125">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
    ```xml  
    <bindings>  
      <WSHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </WSHttpBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="ec2da-126">次のコード例では、、メッセージセキュリティ、およびセキュリティで保護されたセッションを使用してサービスをセキュリティで保護するように指定してい [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) `secureCalculator` ます。</span><span class="sxs-lookup"><span data-stu-id="ec2da-126">The following code example specifies that the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    > <span data-ttu-id="ec2da-127">では、 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 属性をに設定することによって、セキュリティで保護されたセッションを無効にすることができます `establishSecurityContext` `false` 。</span><span class="sxs-lookup"><span data-stu-id="ec2da-127">Secure sessions can be turned off for the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="ec2da-128">他のシステム提供のバインディングについては、カスタム バインドを作成することでのみ、セキュリティで保護されたセッションを無効にできます。</span><span class="sxs-lookup"><span data-stu-id="ec2da-128">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="ec2da-129">カスタム バインドを使用して、サービスでセキュリティで保護されたセッションが使用されるように指定するには</span><span class="sxs-lookup"><span data-stu-id="ec2da-129">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
- <span data-ttu-id="ec2da-130">セキュリティで保護されたセッションで SOAP メッセージが保護されるように指定したカスタム バインドを作成します。</span><span class="sxs-lookup"><span data-stu-id="ec2da-130">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     <span data-ttu-id="ec2da-131">カスタムバインディングの作成の詳細については、「 [方法: System-Provided バインディングをカスタマイズ](../extending/how-to-customize-a-system-provided-binding.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec2da-131">For more information about creating a custom binding, see [How to: Customize a System-Provided Binding](../extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="ec2da-132">次のコード例で使用されている構成では、セキュリティで保護されたセッションを使用して SOAP メッセージを保護するカスタム バインドを指定しています。</span><span class="sxs-lookup"><span data-stu-id="ec2da-132">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
    ```xml  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="customBinding_Calculator">  
          <security authenticationMode="SecureConversation" />  
          <secureConversationBootstrap authenticationMode="SspiNegotiated" />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="ec2da-133">セキュリティで保護されたセッションをブートストラップするための <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> 認証モードを使用する、カスタム バインドを作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ec2da-133">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ec2da-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec2da-134">See also</span></span>

- [<span data-ttu-id="ec2da-135">WCF のバインディングの概要</span><span class="sxs-lookup"><span data-stu-id="ec2da-135">WCF Bindings Overview</span></span>](../bindings-overview.md)
