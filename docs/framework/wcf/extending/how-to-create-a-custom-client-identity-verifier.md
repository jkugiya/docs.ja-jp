---
description: '詳細については、「方法: カスタムクライアント Id 検証機能を作成する」を参照してください。'
title: '方法: カスタム クライアント ID 検証機能を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
ms.openlocfilehash: ee0cff59d877fbb6cd636f831cfccf4f51a3ab40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743695"
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a><span data-ttu-id="07bc2-103">方法: カスタム クライアント ID 検証機能を作成する</span><span class="sxs-lookup"><span data-stu-id="07bc2-103">How to: Create a Custom Client Identity Verifier</span></span>

<span data-ttu-id="07bc2-104">Windows Communication Foundation (WCF) の *id* 機能を使用すると、クライアントはサービスの予期される id を事前に指定できます。</span><span class="sxs-lookup"><span data-stu-id="07bc2-104">The *identity* feature of Windows Communication Foundation (WCF) enables a client to specify in advance the expected identity of the service.</span></span> <span data-ttu-id="07bc2-105">サーバーがクライアントに対して自身を認証するたびに、ID がこの予想 ID と照合されます</span><span class="sxs-lookup"><span data-stu-id="07bc2-105">Whenever a server authenticates itself to the client, the identity is checked against the expected identity.</span></span> <span data-ttu-id="07bc2-106">(Id とそのしくみの詳細については、「 [サービス id と認証](../feature-details/service-identity-and-authentication.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="07bc2-106">(For an explanation of identity and how it works, see [Service Identity and Authentication](../feature-details/service-identity-and-authentication.md).)</span></span>  
  
 <span data-ttu-id="07bc2-107">必要に応じて、カスタム ID 検証機能を使用して検証をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="07bc2-107">If needed, the verification can be customized using a custom identity verifier.</span></span> <span data-ttu-id="07bc2-108">たとえば、追加のサービス ID 検証チェックを実行できます。</span><span class="sxs-lookup"><span data-stu-id="07bc2-108">For example, you can perform additional service identity verification checks.</span></span> <span data-ttu-id="07bc2-109">この例では、カスタム ID 検証機能で、サーバーから戻された X.509 証明書の追加のクレームをチェックします。</span><span class="sxs-lookup"><span data-stu-id="07bc2-109">In this example, the custom identity verifier checks additional claims in the X.509 certificate returned from the server.</span></span> <span data-ttu-id="07bc2-110">サンプルアプリケーションについては、「 [サービス id のサンプル](../samples/service-identity-sample.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07bc2-110">For a sample application, see [Service Identity Sample](../samples/service-identity-sample.md).</span></span>  
  
### <a name="to-extend-the-endpointidentity-class"></a><span data-ttu-id="07bc2-111">EndpointIdentity クラスを拡張するには</span><span class="sxs-lookup"><span data-stu-id="07bc2-111">To extend the EndpointIdentity class</span></span>  
  
1. <span data-ttu-id="07bc2-112"><xref:System.ServiceModel.EndpointIdentity> クラスから派生する新しいクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="07bc2-112">Define a new class that derives from the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="07bc2-113">拡張子 `OrgEndpointIdentity` に名前を付ける例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="07bc2-113">This example names the extension `OrgEndpointIdentity`.</span></span>  
  
2. <span data-ttu-id="07bc2-114">拡張 <xref:System.ServiceModel.Security.IdentityVerifier> クラスで使用するプライベート メンバーとプロパティを追加し、サービスによって返されたセキュリティ トークンのクレームに対して ID チェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="07bc2-114">Add private members along with properties that will be used by the extended <xref:System.ServiceModel.Security.IdentityVerifier> class to perform the identity check against claims in the security token returned from the service.</span></span> <span data-ttu-id="07bc2-115">この例では、`OrganizationClaim` プロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="07bc2-115">This example defines one property: the `OrganizationClaim` property.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a><span data-ttu-id="07bc2-116">IdentityVerifier クラスを拡張するには</span><span class="sxs-lookup"><span data-stu-id="07bc2-116">To extend the IdentityVerifier class</span></span>  
  
1. <span data-ttu-id="07bc2-117"><xref:System.ServiceModel.Security.IdentityVerifier> から派生する新しいクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="07bc2-117">Define a new class that derives from <xref:System.ServiceModel.Security.IdentityVerifier>.</span></span> <span data-ttu-id="07bc2-118">拡張子 `CustomIdentityVerifier` に名前を付ける例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="07bc2-118">This example names the extension `CustomIdentityVerifier`.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2. <span data-ttu-id="07bc2-119"><xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="07bc2-119">Override the <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> method.</span></span> <span data-ttu-id="07bc2-120">このメソッドは、ID チェックが成功したか失敗したかを判定します。</span><span class="sxs-lookup"><span data-stu-id="07bc2-120">The method determines whether the identity check succeeded or failed.</span></span>  
  
3. <span data-ttu-id="07bc2-121">`CheckAccess` メソッドには 2 つのパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="07bc2-121">The `CheckAccess` method has two parameters.</span></span> <span data-ttu-id="07bc2-122">1 つ目は <xref:System.ServiceModel.EndpointIdentity> クラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="07bc2-122">The first is an instance of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="07bc2-123">2 つ目は <xref:System.IdentityModel.Policy.AuthorizationContext> クラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="07bc2-123">The second is an instance of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
     <span data-ttu-id="07bc2-124">メソッド実装では、<xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> クラスの <xref:System.IdentityModel.Policy.AuthorizationContext> プロパティから返されたクレームのコレクションを検査し、必要に応じて認証チェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="07bc2-124">In the method implementation, examine the collection of claims returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class, and perform authentication checks as required.</span></span> <span data-ttu-id="07bc2-125">この例では、まず種類が "識別名" のクレームをすべて検索し、次にその名前と <xref:System.ServiceModel.EndpointIdentity> の拡張 (`OrgEndpointIdentity`) とを比較します。</span><span class="sxs-lookup"><span data-stu-id="07bc2-125">This example begins by finding any claim that is of type "Distinguished Name" and then compares the name to the extension of the <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a><span data-ttu-id="07bc2-126">TryGetIdentity メソッドを実装するには</span><span class="sxs-lookup"><span data-stu-id="07bc2-126">To implement the TryGetIdentity method</span></span>  
  
1. <span data-ttu-id="07bc2-127"><xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> メソッドを実装します。このメソッドは、クライアントが <xref:System.ServiceModel.EndpointIdentity> クラスのインスタンスを返すことができるかどうかを判定します。</span><span class="sxs-lookup"><span data-stu-id="07bc2-127">Implement the <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> method, which determines whether an instance of the <xref:System.ServiceModel.EndpointIdentity> class can be returned by the client.</span></span> <span data-ttu-id="07bc2-128">WCF インフラストラクチャでは、最初にメソッドの実装を呼び出して、 `TryGetIdentity` メッセージからサービスの id を取得します。</span><span class="sxs-lookup"><span data-stu-id="07bc2-128">The WCF infrastructure calls the implementation of the `TryGetIdentity` method first to retrieve the service's identity from the message.</span></span> <span data-ttu-id="07bc2-129">次に、インフラストラクチャは、返された `CheckAccess` と `EndpointIdentity` を使用して <xref:System.IdentityModel.Policy.AuthorizationContext> 実装を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="07bc2-129">Next, the infrastructure calls the `CheckAccess` implementation with the returned `EndpointIdentity` and <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span>  
  
2. <span data-ttu-id="07bc2-130">`TryGetIdentity` メソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="07bc2-130">In the `TryGetIdentity` method, put the following code:</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a><span data-ttu-id="07bc2-131">カスタム バインディングを実装してカスタム ID 検証機能を設定するには</span><span class="sxs-lookup"><span data-stu-id="07bc2-131">To implement a custom binding and set the custom IdentityVerifier</span></span>  
  
1. <span data-ttu-id="07bc2-132"><xref:System.ServiceModel.Channels.Binding> オブジェクトを返すメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="07bc2-132">Create a method that returns a <xref:System.ServiceModel.Channels.Binding> object.</span></span> <span data-ttu-id="07bc2-133">この例は、まず <xref:System.ServiceModel.WSHttpBinding> クラスのインスタンスを作成し、そのセキュリティ モードを <xref:System.ServiceModel.SecurityMode.Message>、<xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> を <xref:System.ServiceModel.MessageCredentialType.None> に設定します。</span><span class="sxs-lookup"><span data-stu-id="07bc2-133">This example begins creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class and sets its security mode to <xref:System.ServiceModel.SecurityMode.Message>, and its <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> to <xref:System.ServiceModel.MessageCredentialType.None>.</span></span>  
  
2. <span data-ttu-id="07bc2-134"><xref:System.ServiceModel.Channels.BindingElementCollection> メソッドを使用して <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> を作成します。</span><span class="sxs-lookup"><span data-stu-id="07bc2-134">Create a <xref:System.ServiceModel.Channels.BindingElementCollection> using the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="07bc2-135">コレクションから <xref:System.ServiceModel.Channels.SecurityBindingElement> を返し、それを <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 変数にキャストします。</span><span class="sxs-lookup"><span data-stu-id="07bc2-135">Return the <xref:System.ServiceModel.Channels.SecurityBindingElement> from the collection and cast it to a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> variable.</span></span>  
  
4. <span data-ttu-id="07bc2-136"><xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> クラスの <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> プロパティを、以前作成した `CustomIdentityVerifier` クラスの新しいインスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="07bc2-136">Set the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> property of the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class to a new instance of the `CustomIdentityVerifier` class created previously.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5. <span data-ttu-id="07bc2-137">返されたカスタム バインドを使用してクライアントのインスタンスとクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="07bc2-137">The custom binding that is returned is used to create an instance of the client and class.</span></span> <span data-ttu-id="07bc2-138">これにより、クライアントは、次のコードに示すようにサービスのカスタム ID 検証チェックを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="07bc2-138">The client can then perform a custom identity verification check of the service as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="07bc2-139">例</span><span class="sxs-lookup"><span data-stu-id="07bc2-139">Example</span></span>  

 <span data-ttu-id="07bc2-140"><xref:System.ServiceModel.Security.IdentityVerifier> クラスの完全な実装方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="07bc2-140">The following example shows a complete implementation of the <xref:System.ServiceModel.Security.IdentityVerifier> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="07bc2-141">例</span><span class="sxs-lookup"><span data-stu-id="07bc2-141">Example</span></span>  

 <span data-ttu-id="07bc2-142"><xref:System.ServiceModel.EndpointIdentity> クラスの完全な実装方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="07bc2-142">The following example shows a complete implementation of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="07bc2-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="07bc2-143">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- <xref:System.ServiceModel.EndpointIdentity>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [<span data-ttu-id="07bc2-144">サービス ID サンプル</span><span class="sxs-lookup"><span data-stu-id="07bc2-144">Service Identity Sample</span></span>](../samples/service-identity-sample.md)
- [<span data-ttu-id="07bc2-145">承認ポリシー</span><span class="sxs-lookup"><span data-stu-id="07bc2-145">Authorization Policy</span></span>](../samples/authorization-policy.md)
