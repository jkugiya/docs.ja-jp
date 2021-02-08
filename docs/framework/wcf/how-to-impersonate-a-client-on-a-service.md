---
description: '詳細については、「方法: サービスでクライアントを偽装する」を参照してください。'
title: '方法: サービスでクライアントに偽装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, impersonation
- impersonation
- WCF, security
ms.assetid: 431db851-a75b-4009-9fe2-247243d810d3
ms.openlocfilehash: 84d50b0c22161a829da66e42b4b3bbf004b68487
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779375"
---
# <a name="how-to-impersonate-a-client-on-a-service"></a><span data-ttu-id="7001c-103">方法: サービスでクライアントに偽装する</span><span class="sxs-lookup"><span data-stu-id="7001c-103">How to: Impersonate a Client on a Service</span></span>

<span data-ttu-id="7001c-104">Windows Communication Foundation (WCF) サービスでクライアントを偽装すると、サービスはクライアントに代わってアクションを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7001c-104">Impersonating a client on a Windows Communication Foundation (WCF) service enables the service to perform actions on behalf of the client.</span></span> <span data-ttu-id="7001c-105">コンピューター上のディレクトリやファイルへのアクセス、または SQL Server データベースへのアクセスなど、アクセス制御リスト (ACL) のチェックを受けるアクションでは、ACL のチェックがクライアントのユーザー アカウントに対して行われます。</span><span class="sxs-lookup"><span data-stu-id="7001c-105">For actions subject to access control list (ACL) checks, such as access to directories and files on a machine or access to a SQL Server database, the ACL check is against the client user account.</span></span> <span data-ttu-id="7001c-106">ここでは、Windows ドメインのクライアントで、クライアント偽装レベルを設定できるようにするために必要な基本的な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="7001c-106">This topic shows the basic steps required to enable a client in a Windows domain to set a client impersonation level.</span></span> <span data-ttu-id="7001c-107">このパターンの実施例については、「 [Impersonating the Client](./samples/impersonating-the-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7001c-107">For a working example of this, see [Impersonating the Client](./samples/impersonating-the-client.md).</span></span> <span data-ttu-id="7001c-108">クライアントの偽装の詳細については、「 [委任と偽装](./feature-details/delegation-and-impersonation-with-wcf.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7001c-108">For more information about client impersonation, see [Delegation and Impersonation](./feature-details/delegation-and-impersonation-with-wcf.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7001c-109">クライアントとサービスが同じコンピューター上で実行されており、クライアントがシステム アカウント ( `Local System` や `Network Service`など) で実行されているときに、ステートレスなセキュリティ コンテキスト トークンを使用してセキュリティで保護されたセッションを確立した場合、クライアントを偽装することはできません。</span><span class="sxs-lookup"><span data-stu-id="7001c-109">When the client and service are running on the same computer and the client is running under a system account (that is, `Local System` or `Network Service`), the client cannot be impersonated when a secure session is established with stateful Security Context tokens.</span></span> <span data-ttu-id="7001c-110">通常、WinForms アプリケーションやコンソール アプリケーションは、現在ログインしているアカウントで実行されるため、既定でそのアカウントを偽装できます。</span><span class="sxs-lookup"><span data-stu-id="7001c-110">A WinForms or console application typically is run under the currently logged in account, so that account can be impersonated by default.</span></span> <span data-ttu-id="7001c-111">ただし、クライアントが ASP.NET ページで、そのページが IIS 6.0 または IIS 7.0 でホストされている場合、既定では、クライアントはアカウントで実行され `Network Service` ます。</span><span class="sxs-lookup"><span data-stu-id="7001c-111">However, when the client is an ASP.NET page and that page is hosted in IIS 6.0 or IIS 7.0, then the client does run under the `Network Service` account by default.</span></span> <span data-ttu-id="7001c-112">セキュリティで保護されたセッションをサポートするシステム提供のすべてのバインディングは、ステートフルなセキュリティ コンテキスト トークンを既定で使用します。</span><span class="sxs-lookup"><span data-stu-id="7001c-112">All of the system-provided bindings that support secure sessions use a stateless Security Context token by default.</span></span> <span data-ttu-id="7001c-113">ただし、クライアントが ASP.NET ページであり、ステートフルなセキュリティコンテキストトークンを使用してセキュリティで保護されたセッションを使用している場合、クライアントを偽装することはできません。</span><span class="sxs-lookup"><span data-stu-id="7001c-113">However, if the client is an ASP.NET page and secure sessions with stateful Security Context tokens are used, the client cannot be impersonated.</span></span> <span data-ttu-id="7001c-114">セキュリティで保護されたセッションでのステートフルなセキュリティコンテキストトークンの使用の詳細については、「 [方法: セキュリティで保護されたセッションのセキュリティコンテキストトークンを作成](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7001c-114">For more information about using stateful Security Context tokens in a secure session, see [How to: Create a Security Context Token for a Secure Session](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a><span data-ttu-id="7001c-115">サービスにキャッシュされた Windows トークンでクライアントの偽装を有効にするには</span><span class="sxs-lookup"><span data-stu-id="7001c-115">To enable impersonation of a client from a cached Windows token on a service</span></span>  
  
1. <span data-ttu-id="7001c-116">サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="7001c-116">Create the service.</span></span> <span data-ttu-id="7001c-117">この基本的な手順のチュートリアルについては、「 [Getting Started Tutorial](getting-started-tutorial.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7001c-117">For a tutorial of this basic procedure, see [Getting Started Tutorial](getting-started-tutorial.md).</span></span>  
  
2. <span data-ttu-id="7001c-118">Windows 認証を使用してセッションを作成するバインディング ( <xref:System.ServiceModel.NetTcpBinding> や <xref:System.ServiceModel.WSHttpBinding>など) を使用します。</span><span class="sxs-lookup"><span data-stu-id="7001c-118">Use a binding that uses Windows authentication and creates a session, such as <xref:System.ServiceModel.NetTcpBinding> or <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
3. <span data-ttu-id="7001c-119">サービスのインターフェイスの実装を作成するときには、クライアントの偽装を必要とするメソッドに <xref:System.ServiceModel.OperationBehaviorAttribute> クラスを適用します。</span><span class="sxs-lookup"><span data-stu-id="7001c-119">When creating the implementation of the service's interface, apply the <xref:System.ServiceModel.OperationBehaviorAttribute> class to the method that requires client impersonation.</span></span> <span data-ttu-id="7001c-120"><xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> プロパティを <xref:System.ServiceModel.ImpersonationOption.Required>に設定します。</span><span class="sxs-lookup"><span data-stu-id="7001c-120">Set the <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> property to <xref:System.ServiceModel.ImpersonationOption.Required>.</span></span>  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a><span data-ttu-id="7001c-121">クライアントに許可される偽装レベルを設定するには</span><span class="sxs-lookup"><span data-stu-id="7001c-121">To set the allowed impersonation level on the client</span></span>  
  
1. <span data-ttu-id="7001c-122">[ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)を使用して、サービス クライアント コードを作成します。</span><span class="sxs-lookup"><span data-stu-id="7001c-122">Create service client code by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="7001c-123">詳細については、「 [WCF クライアントを使用したサービスへのアクセス](accessing-services-using-a-wcf-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7001c-123">For more information, see [Accessing Services Using a WCF Client](accessing-services-using-a-wcf-client.md).</span></span>  
  
2. <span data-ttu-id="7001c-124">WCF クライアントを作成した後、 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> クラスのプロパティを <xref:System.ServiceModel.Security.WindowsClientCredential> 列挙値のいずれかに設定し <xref:System.Security.Principal.TokenImpersonationLevel> ます。</span><span class="sxs-lookup"><span data-stu-id="7001c-124">After creating the WCF client, set the <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property of the <xref:System.ServiceModel.Security.WindowsClientCredential> class to one of the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration values.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7001c-125"><xref:System.Security.Principal.TokenImpersonationLevel.Delegation>を使用するには、ネゴシエート Kerberos 認証 ( *"マルチレッグ"* Kerberos または *"マルチステップ"* Kerberos と呼ぶこともあります) を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7001c-125">To use <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, negotiated Kerberos authentication (sometimes called *multi-leg* or *multi-step* Kerberos) must be used.</span></span> <span data-ttu-id="7001c-126">これを実装する方法の詳細については、「 [セキュリティのベストプラクティス](./feature-details/best-practices-for-security-in-wcf.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7001c-126">For a description of how to implement this, see [Best Practices for Security](./feature-details/best-practices-for-security-in-wcf.md).</span></span>  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7001c-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="7001c-127">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
- <xref:System.Security.Principal.TokenImpersonationLevel>
- [<span data-ttu-id="7001c-128">クライアントの偽装</span><span class="sxs-lookup"><span data-stu-id="7001c-128">Impersonating the Client</span></span>](./samples/impersonating-the-client.md)
- [<span data-ttu-id="7001c-129">委任と偽装</span><span class="sxs-lookup"><span data-stu-id="7001c-129">Delegation and Impersonation</span></span>](./feature-details/delegation-and-impersonation-with-wcf.md)
