---
description: '詳細については、「方法: ローカル発行者を構成する」を参照してください。'
title: '方法: ローカル発行者を設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
ms.openlocfilehash: 1c950c2bbbb55954fc65e35632523ea14ee3ac00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780168"
---
# <a name="how-to-configure-a-local-issuer"></a><span data-ttu-id="6f364-103">方法: ローカル発行者を設定する</span><span class="sxs-lookup"><span data-stu-id="6f364-103">How to: Configure a Local Issuer</span></span>

<span data-ttu-id="6f364-104">ここでは、発行済みトークンに対してローカル発行者を使用するようにクライアントを構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6f364-104">This topic describes how to configure a client to use a local issuer for issued tokens.</span></span>

<span data-ttu-id="6f364-105">クライアントがフェデレーション サービスと通信する場合、クライアントが自分をフェデレーション サービスに対して認証するときに使用するトークンの発行元となるセキュリティ トークン サービスのアドレスが、サービスによって指定されることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="6f364-105">Often, when a client communicates with a federated service, the service specifies the address of the security token service that is expected to issue the token the client will use to authenticate itself to the federated service.</span></span> <span data-ttu-id="6f364-106">特定の状況では、クライアントが *ローカル発行者* を使用するように構成されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="6f364-106">In certain situations, the client may be configured to use a *local issuer*.</span></span>

<span data-ttu-id="6f364-107">フェデレーションバインディングの発行者アドレスがまたはの場合、Windows Communication Foundation (WCF) はローカル発行者を使用し `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null` ます。</span><span class="sxs-lookup"><span data-stu-id="6f364-107">Windows Communication Foundation (WCF) uses a local issuer in cases where the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`.</span></span> <span data-ttu-id="6f364-108">そのような場合は、ローカルの発行者およびバインディングのアドレスと共に <xref:System.ServiceModel.Description.ClientCredentials> を構成し、その発行者との通信に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f364-108">In such cases, you must configure the <xref:System.ServiceModel.Description.ClientCredentials> with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>

> [!NOTE]
> <span data-ttu-id="6f364-109"><xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A>クラスのプロパティがに設定されている場合 `ClientCredentials` `true` 、ローカル発行者のアドレスが指定されておらず、または他のフェデレーションバインドによって指定された発行者のアドレスが、、またはである場合は、 [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null` Windows CardSpace 発行者が使用されます。</span><span class="sxs-lookup"><span data-stu-id="6f364-109">If the <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> property of the `ClientCredentials` class is set to `true`, a local issuer address is not specified, and the issuer address specified by the [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) or other federated binding is `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`, `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, or is `null`, then the Windows CardSpace issuer is used.</span></span>

## <a name="to-configure-the-local-issuer-in-code"></a><span data-ttu-id="6f364-110">コードでローカル発行者を構成するには</span><span class="sxs-lookup"><span data-stu-id="6f364-110">To configure the local issuer in code</span></span>

1. <span data-ttu-id="6f364-111"><xref:System.ServiceModel.Security.IssuedTokenClientCredential> 型の変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="6f364-111">Create a variable of type <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>

2. <span data-ttu-id="6f364-112"><xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> クラスの `ClientCredentials` プロパティから返されるインスタンスに変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="6f364-112">Set the variable to the instance returned from the <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> property of the `ClientCredentials` class.</span></span> <span data-ttu-id="6f364-113">このインスタンスは、(<xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> から継承された) クライアントの <xref:System.ServiceModel.ClientBase%601> プロパティ、または <xref:System.ServiceModel.ChannelFactory.Credentials%2A> の <xref:System.ServiceModel.ChannelFactory> プロパティから次のように返されます。</span><span class="sxs-lookup"><span data-stu-id="6f364-113">That instance is returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the client (inherited from <xref:System.ServiceModel.ClientBase%601>) or the <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property of the <xref:System.ServiceModel.ChannelFactory>:</span></span>

     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]

3. <span data-ttu-id="6f364-114"><xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> プロパティを <xref:System.ServiceModel.EndpointAddress> の新規インスタンスに設定します。このとき、次のようにコンストラクターに対する引数としてローカル発行者のアドレスを使用します。</span><span class="sxs-lookup"><span data-stu-id="6f364-114">Set the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> property to a new instance of the <xref:System.ServiceModel.EndpointAddress>, with the address of the local issuer as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]

     <span data-ttu-id="6f364-115">あるいは、次のように新規の <xref:System.Uri> インスタンスをコンストラクターへの引数として作成します。</span><span class="sxs-lookup"><span data-stu-id="6f364-115">Alternatively, create a new <xref:System.Uri> instance as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]

     <span data-ttu-id="6f364-116">パラメーターは、 `addressHeaders` のように、インスタンスの配列です <xref:System.ServiceModel.Channels.AddressHeader> 。</span><span class="sxs-lookup"><span data-stu-id="6f364-116">The `addressHeaders` parameter is an array of <xref:System.ServiceModel.Channels.AddressHeader> instances, as shown.</span></span>

     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]

4. <span data-ttu-id="6f364-117">プロパティを使用して、ローカル発行者のバインディングを設定し <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="6f364-117">Set the binding for the local issuer using the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]

5. <span data-ttu-id="6f364-118">任意。</span><span class="sxs-lookup"><span data-stu-id="6f364-118">Optional.</span></span> <span data-ttu-id="6f364-119">ローカル発行者に対して構成したエンドポイントの動作を <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> プロパティから返されるコレクションに追加することにより、この動作を次のように追加します。</span><span class="sxs-lookup"><span data-stu-id="6f364-119">Add configured endpoint behaviors for the local issuer by adding such behaviors to the collection returned by the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]

## <a name="to-configure-the-local-issuer-in-configuration"></a><span data-ttu-id="6f364-120">構成でローカル発行者を構成するには</span><span class="sxs-lookup"><span data-stu-id="6f364-120">To configure the local issuer in configuration</span></span>

1. <span data-ttu-id="6f364-121">要素の [\<localIssuer>](../../configure-apps/file-schema/wcf/localissuer.md) 子要素として、 [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) エンドポイント動作の要素の子である要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="6f364-121">Create a [\<localIssuer>](../../configure-apps/file-schema/wcf/localissuer.md) element as a child of the [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) element that is itself a child of the [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) element in an endpoint behavior.</span></span>

2. <span data-ttu-id="6f364-122">`address` 属性を、トークン要求を受け入れるローカル発行者のアドレスに設定します。</span><span class="sxs-lookup"><span data-stu-id="6f364-122">Set the `address` attribute to the address of the local issuer that will accept token requests.</span></span>

3. <span data-ttu-id="6f364-123">`binding` および `bindingConfiguration` 属性を、ローカル発行者のエンドポイントと通信するときに使用する適切なバインディングを参照する値に設定します。</span><span class="sxs-lookup"><span data-stu-id="6f364-123">Set the `binding` and `bindingConfiguration` attributes to values that reference the appropriate binding to use when communicating with the local issuer endpoint.</span></span>

4. <span data-ttu-id="6f364-124">任意。</span><span class="sxs-lookup"><span data-stu-id="6f364-124">Optional.</span></span> <span data-ttu-id="6f364-125">要素を [\<identity>](../../configure-apps/file-schema/wcf/identity.md) <> 要素の子として設定 `localIssuer` し、ローカル発行者の id 情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="6f364-125">Set the [\<identity>](../../configure-apps/file-schema/wcf/identity.md) element as a child of the <`localIssuer`> element and specify identity information for the local issuer.</span></span>

5. <span data-ttu-id="6f364-126">任意。</span><span class="sxs-lookup"><span data-stu-id="6f364-126">Optional.</span></span> <span data-ttu-id="6f364-127">要素を [\<headers>](../../configure-apps/file-schema/wcf/headers.md) <> 要素の子として設定 `localIssuer` し、ローカル発行者を正しくアドレス指定するために必要な追加のヘッダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="6f364-127">Set the [\<headers>](../../configure-apps/file-schema/wcf/headers.md) element as a child of the <`localIssuer`> element and specify additional headers that are required in order to correctly address the local issuer.</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="6f364-128">.NET Framework のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="6f364-128">.NET Framework Security</span></span>

<span data-ttu-id="6f364-129">特定のバインディングに対して発行者アドレスとバインディングが指定されている場合、ローカル発行者はこのバインディングを使用するエンドポイントには使用されません。</span><span class="sxs-lookup"><span data-stu-id="6f364-129">Note that if an issuer address and binding are specified for a given binding, the local issuer is not used for endpoints that use that binding.</span></span> <span data-ttu-id="6f364-130">ローカル発行者を常に使用する必要があるクライアントには、このようなバインディングが使用されることがないこと、または発行者アドレスが `null` となるようにクライアントによってバインディングが変更されることが保証されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f364-130">Clients who expect to always use the local issuer should ensure that they do not use such a binding or that they modify the binding so that the issuer address is `null`.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f364-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f364-131">See also</span></span>

- [<span data-ttu-id="6f364-132">方法: フェデレーション サービスで資格情報を設定する</span><span class="sxs-lookup"><span data-stu-id="6f364-132">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="6f364-133">方法: フェデレーション クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="6f364-133">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)
- [<span data-ttu-id="6f364-134">方法: WSFederationHttpBinding を作成する</span><span class="sxs-lookup"><span data-stu-id="6f364-134">How to: Create a WSFederationHttpBinding</span></span>](how-to-create-a-wsfederationhttpbinding.md)
