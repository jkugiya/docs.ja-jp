---
description: '詳細については、「方法: サポート資格情報を作成する」を参照してください。'
title: '方法: サポート資格情報を作成する'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 2f84e58eb0b8df5e1297fcbc50ddcac96db4fe5c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793819"
---
# <a name="how-to-create-a-supporting-credential"></a><span data-ttu-id="905ec-103">方法: サポート資格情報を作成する</span><span class="sxs-lookup"><span data-stu-id="905ec-103">How to: Create a Supporting Credential</span></span>

<span data-ttu-id="905ec-104">カスタムのセキュリティ スキームでは、複数の資格情報が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="905ec-104">It is possible to have a custom security scheme that requires more than one credential.</span></span> <span data-ttu-id="905ec-105">たとえば、サービスが、ユーザー名とパスワードだけでなく、クライアントが 18 歳以上であることを証明する資格情報もクライアントに要求することがあります。</span><span class="sxs-lookup"><span data-stu-id="905ec-105">For example, a service may demand from the client not just a user name and password, but also a credential that proves the client is over the age of 18.</span></span> <span data-ttu-id="905ec-106">2番目の資格情報は、 *サポート資格情報* です。</span><span class="sxs-lookup"><span data-stu-id="905ec-106">The second credential is a *supporting credential*.</span></span> <span data-ttu-id="905ec-107">このトピックでは、Windows Communication Foundation (WCF) クライアントでこのような資格情報を実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="905ec-107">This topic explains how to implement such credentials in an Windows Communication Foundation (WCF) client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="905ec-108">サポート資格情報の仕様は、WS-SecurityPolicy 仕様の一部です。</span><span class="sxs-lookup"><span data-stu-id="905ec-108">The specification for supporting credentials is part of the WS-SecurityPolicy specification.</span></span> <span data-ttu-id="905ec-109">詳細については、「 [Web Services Security の仕様](/previous-versions/dotnet/articles/ms951273(v=msdn.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="905ec-109">For more information, see [Web Services Security Specifications](/previous-versions/dotnet/articles/ms951273(v=msdn.10)).</span></span>  
  
## <a name="supporting-tokens"></a><span data-ttu-id="905ec-110">トークンのサポート</span><span class="sxs-lookup"><span data-stu-id="905ec-110">Supporting Tokens</span></span>  

 <span data-ttu-id="905ec-111">簡単に言えば、メッセージセキュリティを使用する場合は、メッセージをセキュリティで保護するために、 *プライマリ資格情報* (たとえば、x.509 証明書または Kerberos チケット) が常に使用されます。</span><span class="sxs-lookup"><span data-stu-id="905ec-111">In brief, when you use message security, a *primary credential* is always used to secure the message (for example, an X.509 certificate or a Kerberos ticket).</span></span>  
  
 <span data-ttu-id="905ec-112">仕様で定義されているように、セキュリティバインディングでは、 *トークン* を使用してメッセージ交換をセキュリティで保護します。</span><span class="sxs-lookup"><span data-stu-id="905ec-112">As defined by the specification, a security binding uses *tokens* to secure the message exchange.</span></span> <span data-ttu-id="905ec-113">*トークン* は、セキュリティ資格情報の表現です。</span><span class="sxs-lookup"><span data-stu-id="905ec-113">A *token* is a representation of a security credential.</span></span>  
  
 <span data-ttu-id="905ec-114">セキュリティ バインディングは、セキュリティ バインディング ポリシーで特定されたプライマリ トークンを使用して、署名を作成します。</span><span class="sxs-lookup"><span data-stu-id="905ec-114">The security binding uses a primary token identified in the security binding policy to create a signature.</span></span> <span data-ttu-id="905ec-115">この署名は、 *メッセージ署名* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="905ec-115">This signature is referred to as the *message signature*.</span></span>  
  
 <span data-ttu-id="905ec-116">メッセージ署名に関連付けられたトークンによって提供されるクレームを増やすために、追加のトークンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="905ec-116">Additional tokens can be specified to augment the claims provided by the token associated with the message signature.</span></span>  
  
## <a name="endorsing-signing-and-encrypting"></a><span data-ttu-id="905ec-117">保証、署名、および暗号化</span><span class="sxs-lookup"><span data-stu-id="905ec-117">Endorsing, Signing, and Encrypting</span></span>  

 <span data-ttu-id="905ec-118">サポート資格情報は、メッセージ内で送信される *サポートトークン* になります。</span><span class="sxs-lookup"><span data-stu-id="905ec-118">A supporting credential results in a *supporting token* transmitted inside the message.</span></span> <span data-ttu-id="905ec-119">WS-SecurityPolicy 仕様では、次の表に示すように、サポート トークンをメッセージに追加する方法が 4 つ定義されています。</span><span class="sxs-lookup"><span data-stu-id="905ec-119">The WS-SecurityPolicy specification defines four ways to attach a supporting token to the message, as described in the following table.</span></span>  
  
|<span data-ttu-id="905ec-120">目的</span><span class="sxs-lookup"><span data-stu-id="905ec-120">Purpose</span></span>|<span data-ttu-id="905ec-121">説明</span><span class="sxs-lookup"><span data-stu-id="905ec-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="905ec-122">符号付き</span><span class="sxs-lookup"><span data-stu-id="905ec-122">Signed</span></span>|<span data-ttu-id="905ec-123">サポート トークンはセキュリティ ヘッダーに追加され、メッセージ署名によって署名されます。</span><span class="sxs-lookup"><span data-stu-id="905ec-123">The supporting token is included in the security header and is signed by the message signature.</span></span>|  
|<span data-ttu-id="905ec-124">保証</span><span class="sxs-lookup"><span data-stu-id="905ec-124">Endorsing</span></span>|<span data-ttu-id="905ec-125">保証 *トークン* は、メッセージ署名に署名します。</span><span class="sxs-lookup"><span data-stu-id="905ec-125">An *endorsing token* signs the message signature.</span></span>|  
|<span data-ttu-id="905ec-126">署名および保証</span><span class="sxs-lookup"><span data-stu-id="905ec-126">Signed and Endorsing</span></span>|<span data-ttu-id="905ec-127">署名付き保証トークンは、メッセージ署名から生成された `ds:Signature` 要素全体を署名し、それ自体がこのメッセージ署名によって署名されます。つまり、両方のトークン (メッセージ署名に使用されるトークンと署名付き保証トークン) がお互いに署名します。</span><span class="sxs-lookup"><span data-stu-id="905ec-127">Signed, endorsing tokens sign the entire `ds:Signature` element produced from the message signature and are themselves signed by that message signature; that is, both tokens (the token used for the message signature and the signed endorsing token) sign each other.</span></span>|  
|<span data-ttu-id="905ec-128">署名および暗号化</span><span class="sxs-lookup"><span data-stu-id="905ec-128">Signed and Encrypting</span></span>|<span data-ttu-id="905ec-129">暗号化された署名付きサポート トークンは、`wsse:SecurityHeader` に表示されたときに暗号化されている署名付きサポート トークンです。</span><span class="sxs-lookup"><span data-stu-id="905ec-129">Signed, encrypted supporting tokens are signed supporting tokens that are also encrypted when they appear in the `wsse:SecurityHeader`.</span></span>|  
  
## <a name="programming-supporting-credentials"></a><span data-ttu-id="905ec-130">サポート資格情報のプログラミング</span><span class="sxs-lookup"><span data-stu-id="905ec-130">Programming Supporting Credentials</span></span>  

 <span data-ttu-id="905ec-131">サポートトークンを使用するサービスを作成するには、を作成する必要があり [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="905ec-131">To create a service that uses supporting tokens you must create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span> <span data-ttu-id="905ec-132">(詳細については、「 [方法: カスタムバインディングを使用してカスタムバインディングを作成](how-to-create-a-custom-binding-using-the-securitybindingelement.md)する」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="905ec-132">(For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span></span>  
  
 <span data-ttu-id="905ec-133">カスタム バインドを作成する最初の手順は、次の 3 種類のいずれかのセキュリティ バインド要素を作成することです。</span><span class="sxs-lookup"><span data-stu-id="905ec-133">The first step when creating a custom binding is to create a security binding element, which can be one of three types:</span></span>  
  
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="905ec-134">すべてのクラスは、次の 4 つの関連プロパティを備えた <xref:System.ServiceModel.Channels.SecurityBindingElement> から継承します。</span><span class="sxs-lookup"><span data-stu-id="905ec-134">All classes inherit from the <xref:System.ServiceModel.Channels.SecurityBindingElement>, which includes four relevant properties:</span></span>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a><span data-ttu-id="905ec-135">スコープ</span><span class="sxs-lookup"><span data-stu-id="905ec-135">Scopes</span></span>  

 <span data-ttu-id="905ec-136">サポート資格情報には、次の 2 つのスコープがあります。</span><span class="sxs-lookup"><span data-stu-id="905ec-136">Two scopes exist for supporting credentials:</span></span>  
  
- <span data-ttu-id="905ec-137">エンド *ポイントサポートトークン* は、エンドポイントのすべての操作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="905ec-137">*Endpoint supporting tokens* support all operations of an endpoint.</span></span> <span data-ttu-id="905ec-138">つまり、サポート トークンによって表される資格情報は、エンドポイントの任意の操作が呼び出されたときにいつでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="905ec-138">That is, the credential that the supporting token represents can be used whenever any endpoint operations are invoked.</span></span>  
  
- <span data-ttu-id="905ec-139">*操作* をサポートするトークンは、特定のエンドポイント操作だけをサポートします。</span><span class="sxs-lookup"><span data-stu-id="905ec-139">*Operation supporting tokens* support only a specific endpoint operation.</span></span>  
  
 <span data-ttu-id="905ec-140">プロパティ名に示されているように、サポート資格情報は必須またはオプションのどちらかになることができます。</span><span class="sxs-lookup"><span data-stu-id="905ec-140">As indicated by the property names, supporting credentials can be either required or optional.</span></span> <span data-ttu-id="905ec-141">つまり、サポート資格情報は必須ではありませんが、存在する場合は使用され、存在しない場合も認証は失敗しません。</span><span class="sxs-lookup"><span data-stu-id="905ec-141">That is, if the supporting credential is used if it is present, although it is not necessary, but the authentication will not fail if it is not present.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="905ec-142">手順</span><span class="sxs-lookup"><span data-stu-id="905ec-142">Procedures</span></span>  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a><span data-ttu-id="905ec-143">サポート資格情報を備えたカスタム バインドを作成するには</span><span class="sxs-lookup"><span data-stu-id="905ec-143">To create a custom binding that includes supporting credentials</span></span>  
  
1. <span data-ttu-id="905ec-144">セキュリティ バインド要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="905ec-144">Create a security binding element.</span></span> <span data-ttu-id="905ec-145">次の例では、<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 認証モードで `UserNameForCertificate` を作成します。</span><span class="sxs-lookup"><span data-stu-id="905ec-145">The example below creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> with the `UserNameForCertificate` authentication mode.</span></span> <span data-ttu-id="905ec-146"><xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="905ec-146">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> method.</span></span>  
  
2. <span data-ttu-id="905ec-147">サポート パラメーターを対応するプロパティ (`Endorsing`、`Signed`、`SignedEncrypted`、または `SignedEndorsed`) によって返される型のコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="905ec-147">Add the supporting parameter to the collection of types returned by the appropriate property (`Endorsing`, `Signed`, `SignedEncrypted`, or `SignedEndorsed`).</span></span> <span data-ttu-id="905ec-148"><xref:System.ServiceModel.Security.Tokens> 名前空間に存在する型には、<xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters> など、一般的に使用される型があります。</span><span class="sxs-lookup"><span data-stu-id="905ec-148">The types in the <xref:System.ServiceModel.Security.Tokens> namespace include commonly used types, such as the <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="905ec-149">例</span><span class="sxs-lookup"><span data-stu-id="905ec-149">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="905ec-150">説明</span><span class="sxs-lookup"><span data-stu-id="905ec-150">Description</span></span>  

 <span data-ttu-id="905ec-151"><xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> のインスタンスを作成し、<xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> クラスのインスタンスを、Endorsing プロパティによって返されるコレクションに追加する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="905ec-151">The following example creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and adds an instance of the <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> class to the collection the Endorsing property returned.</span></span>  
  
### <a name="code"></a><span data-ttu-id="905ec-152">コード</span><span class="sxs-lookup"><span data-stu-id="905ec-152">Code</span></span>  

 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="905ec-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="905ec-153">See also</span></span>

- [<span data-ttu-id="905ec-154">方法: SecurityBindingElement を使用してカスタム バインドを作成する</span><span class="sxs-lookup"><span data-stu-id="905ec-154">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
