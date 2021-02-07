---
description: 詳細については、「Windows 認証エラーのデバッグ」を参照してください。
title: Windows 認証エラーのデバッグ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
- WCF, Windows authentication
ms.assetid: 181be4bd-79b1-4a66-aee2-931887a6d7cc
ms.openlocfilehash: cfc8bf8ce9b9c5da3d9b25949321ed1ac2b62d98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756488"
---
# <a name="debug-windows-authentication-errors"></a><span data-ttu-id="b8a9a-103">Windows 認証エラーのデバッグ</span><span class="sxs-lookup"><span data-stu-id="b8a9a-103">Debug Windows authentication errors</span></span>

<span data-ttu-id="b8a9a-104">セキュリティ機構として Windows 認証を使用する場合、セキュリティ サポート プロバイダー インターフェイス (SSPI: Security Support Provider Interface) がセキュリティ プロセスを処理します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-104">When using Windows authentication as a security mechanism, the Security Support Provider Interface (SSPI) handles security processes.</span></span> <span data-ttu-id="b8a9a-105">SSPI 層でセキュリティエラーが発生すると、Windows Communication Foundation (WCF) によって表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-105">When security errors occur at the SSPI layer, they are surfaced by Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="b8a9a-106">このトピックでは、エラーの診断に役立つフレームワークと一連の質問を示します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-106">This topic provides a framework and set of questions to help diagnose the errors.</span></span>  
  
 <span data-ttu-id="b8a9a-107">Kerberos プロトコルの概要については、 [kerberos の説明](/previous-versions/windows/it-pro/windows-2000-server/bb742516(v=technet.10))を参照してください。SSPI の概要については、「 [sspi](/windows/win32/secauthn/sspi)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-107">For an overview of the Kerberos protocol, see [Kerberos Explained](/previous-versions/windows/it-pro/windows-2000-server/bb742516(v=technet.10)); for an overview of SSPI, see [SSPI](/windows/win32/secauthn/sspi).</span></span>  
  
 <span data-ttu-id="b8a9a-108">Windows 認証の場合、WCF は通常、クライアントとサービスの間で Kerberos 相互認証を実行する *ネゴシエート* セキュリティサポートプロバイダー (SSP) を使用します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-108">For Windows authentication, WCF typically uses the *Negotiate* Security Support Provider (SSP), which performs Kerberos mutual authentication between the client and service.</span></span> <span data-ttu-id="b8a9a-109">Kerberos プロトコルが使用できない場合、既定では、WCF は NT LAN Manager (NTLM) にフォールバックします。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-109">If the Kerberos protocol is not available, by default WCF falls back to NT LAN Manager (NTLM).</span></span> <span data-ttu-id="b8a9a-110">ただし、Kerberos プロトコルのみを使用するように WCF を構成することができます (および Kerberos が使用できない場合は例外をスローします)。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-110">However, you can configure WCF to use only the Kerberos protocol (and to throw an exception if Kerberos is not available).</span></span> <span data-ttu-id="b8a9a-111">Kerberos プロトコルの制限付き形式を使用するように WCF を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-111">You can also configure WCF to use restricted forms of the Kerberos protocol.</span></span>  
  
## <a name="debugging-methodology"></a><span data-ttu-id="b8a9a-112">デバッグ方法</span><span class="sxs-lookup"><span data-stu-id="b8a9a-112">Debugging Methodology</span></span>  

 <span data-ttu-id="b8a9a-113">基本的な方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-113">The basic method is as follows:</span></span>  
  
1. <span data-ttu-id="b8a9a-114">Windows 認証を使用しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-114">Determine whether you are using Windows authentication.</span></span> <span data-ttu-id="b8a9a-115">他の方式を使用している場合には、このトピックは該当しません。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-115">If you are using any other scheme, this topic does not apply.</span></span>  
  
2. <span data-ttu-id="b8a9a-116">Windows 認証を使用していることがわかっている場合は、WCF 構成で Kerberos 直接またはネゴシエートのどちらを使用するかを決定します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-116">If you are sure you are using Windows authentication, determine whether your WCF configuration uses Kerberos direct or Negotiate.</span></span>  
  
3. <span data-ttu-id="b8a9a-117">構成で Kerberos プロトコルと NTLM のどちらを使用しているかを確認した後は、現在のコンテキストでのエラー メッセージを理解できます。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-117">Once you have determined whether your configuration is using the Kerberos protocol or NTLM, you can understand error messages in the correct context.</span></span>  
  
### <a name="availability-of-the-kerberos-protocol-and-ntlm"></a><span data-ttu-id="b8a9a-118">Kerberos プロトコルと NTLM の可用性</span><span class="sxs-lookup"><span data-stu-id="b8a9a-118">Availability of the Kerberos Protocol and NTLM</span></span>  

 <span data-ttu-id="b8a9a-119">Kerberos SSP は、Kerberos キー配布センター (KDC: Key Distribution Center) として機能するドメイン コントローラーを必要とします。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-119">The Kerberos SSP requires a domain controller to act as the Kerberos Key Distribution Center (KDC).</span></span> <span data-ttu-id="b8a9a-120">Kerberos プロトコルを使用できるのは、クライアントとサービスの両方がドメイン ID を使用している場合だけです。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-120">The Kerberos protocol is available only when both the client and service are using domain identities.</span></span> <span data-ttu-id="b8a9a-121">次の表に示すように、アカウントの他の組み合わせでは NTLM が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-121">In other account combinations, NTLM is used, as summarized in the following table.</span></span>  
  
 <span data-ttu-id="b8a9a-122">この表の列見出しは、サーバーが使用すると考えられるアカウントの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-122">The table headers show possible account types used by the server.</span></span> <span data-ttu-id="b8a9a-123">左の列は、クライアントが使用すると考えられるアカウントの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-123">The left column shows possible account types used by the client.</span></span>  
  
||<span data-ttu-id="b8a9a-124">Local User</span><span class="sxs-lookup"><span data-stu-id="b8a9a-124">Local User</span></span>|<span data-ttu-id="b8a9a-125">[ローカル システム]</span><span class="sxs-lookup"><span data-stu-id="b8a9a-125">Local System</span></span>|<span data-ttu-id="b8a9a-126">Domain User</span><span class="sxs-lookup"><span data-stu-id="b8a9a-126">Domain User</span></span>|<span data-ttu-id="b8a9a-127">Domain Machine</span><span class="sxs-lookup"><span data-stu-id="b8a9a-127">Domain Machine</span></span>|  
|-|----------------|------------------|-----------------|--------------------|  
|<span data-ttu-id="b8a9a-128">Local User</span><span class="sxs-lookup"><span data-stu-id="b8a9a-128">Local User</span></span>|<span data-ttu-id="b8a9a-129">NTLM</span><span class="sxs-lookup"><span data-stu-id="b8a9a-129">NTLM</span></span>|<span data-ttu-id="b8a9a-130">NTLM</span><span class="sxs-lookup"><span data-stu-id="b8a9a-130">NTLM</span></span>|<span data-ttu-id="b8a9a-131">NTLM</span><span class="sxs-lookup"><span data-stu-id="b8a9a-131">NTLM</span></span>|<span data-ttu-id="b8a9a-132">NTLM</span><span class="sxs-lookup"><span data-stu-id="b8a9a-132">NTLM</span></span>|  
|<span data-ttu-id="b8a9a-133">[ローカル システム]</span><span class="sxs-lookup"><span data-stu-id="b8a9a-133">Local System</span></span>|<span data-ttu-id="b8a9a-134">匿名 NTLM</span><span class="sxs-lookup"><span data-stu-id="b8a9a-134">Anonymous NTLM</span></span>|<span data-ttu-id="b8a9a-135">匿名 NTLM</span><span class="sxs-lookup"><span data-stu-id="b8a9a-135">Anonymous NTLM</span></span>|<span data-ttu-id="b8a9a-136">匿名 NTLM</span><span class="sxs-lookup"><span data-stu-id="b8a9a-136">Anonymous NTLM</span></span>|<span data-ttu-id="b8a9a-137">匿名 NTLM</span><span class="sxs-lookup"><span data-stu-id="b8a9a-137">Anonymous NTLM</span></span>|  
|<span data-ttu-id="b8a9a-138">Domain User</span><span class="sxs-lookup"><span data-stu-id="b8a9a-138">Domain User</span></span>|<span data-ttu-id="b8a9a-139">NTLM</span><span class="sxs-lookup"><span data-stu-id="b8a9a-139">NTLM</span></span>|<span data-ttu-id="b8a9a-140">NTLM</span><span class="sxs-lookup"><span data-stu-id="b8a9a-140">NTLM</span></span>|<span data-ttu-id="b8a9a-141">Kerberos</span><span class="sxs-lookup"><span data-stu-id="b8a9a-141">Kerberos</span></span>|<span data-ttu-id="b8a9a-142">Kerberos</span><span class="sxs-lookup"><span data-stu-id="b8a9a-142">Kerberos</span></span>|  
|<span data-ttu-id="b8a9a-143">Domain Machine</span><span class="sxs-lookup"><span data-stu-id="b8a9a-143">Domain Machine</span></span>|<span data-ttu-id="b8a9a-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="b8a9a-144">NTLM</span></span>|<span data-ttu-id="b8a9a-145">NTLM</span><span class="sxs-lookup"><span data-stu-id="b8a9a-145">NTLM</span></span>|<span data-ttu-id="b8a9a-146">Kerberos</span><span class="sxs-lookup"><span data-stu-id="b8a9a-146">Kerberos</span></span>|<span data-ttu-id="b8a9a-147">Kerberos</span><span class="sxs-lookup"><span data-stu-id="b8a9a-147">Kerberos</span></span>|  
  
 <span data-ttu-id="b8a9a-148">具体的には、次の 4 種類のアカウントがあります。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-148">Specifically, the four account types include:</span></span>  
  
- <span data-ttu-id="b8a9a-149">Local User : コンピューター専用のユーザー プロファイル。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-149">Local User: Machine-only user profile.</span></span> <span data-ttu-id="b8a9a-150">たとえば、`MachineName\Administrator` や `MachineName\ProfileName` などです。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-150">For example: `MachineName\Administrator` or `MachineName\ProfileName`.</span></span>  
  
- <span data-ttu-id="b8a9a-151">Local System : ドメインに参加していないコンピューターの SYSTEM ビルトイン アカウント。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-151">Local System: The built-in account SYSTEM on a machine that is not joined to a domain.</span></span>  
  
- <span data-ttu-id="b8a9a-152">Domain User : Windows ドメインのユーザー アカウント。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-152">Domain User: A user account on a Windows domain.</span></span> <span data-ttu-id="b8a9a-153">たとえば、`DomainName\ProfileName` のように指定します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-153">For example: `DomainName\ProfileName`.</span></span>  
  
- <span data-ttu-id="b8a9a-154">Domain Machine : Windows ドメインに参加しているコンピューターで実行されている、コンピューター ID を使用するプロセス。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-154">Domain Machine: A process with machine identity running on a machine joined to a Windows domain.</span></span> <span data-ttu-id="b8a9a-155">たとえば、`MachineName\Network Service` のように指定します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-155">For example: `MachineName\Network Service`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8a9a-156">サービス資格情報は、<xref:System.ServiceModel.ICommunicationObject.Open%2A> クラスの <xref:System.ServiceModel.ServiceHost> メソッドが呼び出されたときにキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-156">The service credential is captured when the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method of the <xref:System.ServiceModel.ServiceHost> class is called.</span></span> <span data-ttu-id="b8a9a-157">クライアント資格情報は、クライアントがメッセージを送信するたびに読み取られます。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-157">The client credential is read whenever the client sends a message.</span></span>  
  
## <a name="common-windows-authentication-problems"></a><span data-ttu-id="b8a9a-158">Windows 認証の一般的な問題</span><span class="sxs-lookup"><span data-stu-id="b8a9a-158">Common Windows Authentication Problems</span></span>  

 <span data-ttu-id="b8a9a-159">ここでは、Windows 認証に関するいくつかの一般的な問題と、考えられる解決策について説明します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-159">This section discusses some common Windows authentication problems and possible remedies.</span></span>  
  
### <a name="kerberos-protocol"></a><span data-ttu-id="b8a9a-160">Kerberos プロトコル</span><span class="sxs-lookup"><span data-stu-id="b8a9a-160">Kerberos Protocol</span></span>  
  
#### <a name="spnupn-problems-with-the-kerberos-protocol"></a><span data-ttu-id="b8a9a-161">Kerberos プロトコルでの SPN と UPN の問題</span><span class="sxs-lookup"><span data-stu-id="b8a9a-161">SPN/UPN Problems with the Kerberos Protocol</span></span>  

 <span data-ttu-id="b8a9a-162">Windows 認証を使用し、SSPI が Kerberos プロトコルを使用またはネゴシエートする場合、クライアント エンドポイントが使用する URL には、サービス URL 内のサービスのホストの完全修飾ドメイン名が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-162">When using Windows authentication, and the Kerberos protocol is used or negotiated by SSPI, the URL the client endpoint uses must include the fully qualified domain name of the service's host inside the service URL.</span></span> <span data-ttu-id="b8a9a-163">これは、サービスを実行しているアカウントがコンピューターの (既定の) サービス プリンシパル名 (SPN: Service Principal Name) キーにアクセスできることを前提としています。このキーは、コンピューターを Active Directory ドメインに追加したときに作成されます。コンピューターの SPN キーにアクセスできるようにするには、Network Service アカウントでサービスを実行するのが最も一般的な方法です。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-163">This assumes that the account under which the service is running has access to the machine (default) service principal name (SPN) key that is created when the computer is added to the Active Directory domain, which is most commonly done by running the service under the Network Service account.</span></span> <span data-ttu-id="b8a9a-164">サービスがコンピューターの SPN キーにアクセスできない場合は、クライアントのエンドポイント ID でサービスを実行しているアカウントの正しい SPN またはユーザー プリンシパル名 (UPN: User Principal Name) を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-164">If the service does not have access to the machine SPN key, you must supply the correct SPN or user principal name (UPN) of the account under which the service is running in the client's endpoint identity.</span></span> <span data-ttu-id="b8a9a-165">WCF での SPN と UPN の使用方法の詳細については、「 [サービス id と認証](service-identity-and-authentication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-165">For more information about how WCF works with SPN and UPN, see [Service Identity and Authentication](service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="b8a9a-166">Web ファームや Web ガーデンなどの負荷分散シナリオでは、各アプリケーションに一意のアカウントを定義し、そのアカウントに SPN を割り当て、アプリケーションのサービスすべてがそのアカウントで実行されるようにするのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-166">In load-balancing scenarios, such as Web farms or Web gardens, a common practice is to define a unique account for each application, assign an SPN to that account, and ensure that all of the application's services run in that account.</span></span>  
  
 <span data-ttu-id="b8a9a-167">サービスのアカウント用の SPN を取得するには、Active Directory ドメイン管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-167">To obtain an SPN for your service's account, you need to be an Active Directory domain administrator.</span></span> <span data-ttu-id="b8a9a-168">詳細については、「 [Windows 用の Kerberos テクニカル補完](/previous-versions/msp-n-p/ff649429(v=pandp.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-168">For more information, see [Kerberos Technical Supplement for Windows](/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span></span>  
  
#### <a name="kerberos-protocol-direct-requires-the-service-to-run-under-a-domain-machine-account"></a><span data-ttu-id="b8a9a-169">Kerberos プロトコル ダイレクトでは Domain Machine アカウントでサービスを実行する必要がある</span><span class="sxs-lookup"><span data-stu-id="b8a9a-169">Kerberos Protocol Direct Requires the Service to Run Under a Domain Machine Account</span></span>  

 <span data-ttu-id="b8a9a-170">この状況は、次のコードに示すように、`ClientCredentialType` プロパティが `Windows` に設定され、<xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> プロパティが `false` に設定されている場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-170">This occurs when the `ClientCredentialType` property is set to `Windows` and the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> property is set to `false`, as shown in the following code.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#1)]
 [!code-vb[C_DebuggingWindowsAuth#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#1)]  
  
 <span data-ttu-id="b8a9a-171">これを解決するには、ドメインに参加しているコンピューターで、Domain Machine アカウント (Network Service など) を使用してサービスを実行します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-171">To remedy, run the service using a Domain Machine account, such as Network Service, on a domain joined machine.</span></span>  
  
### <a name="delegation-requires-credential-negotiation"></a><span data-ttu-id="b8a9a-172">委任には資格情報ネゴシエーションが必要</span><span class="sxs-lookup"><span data-stu-id="b8a9a-172">Delegation Requires Credential Negotiation</span></span>  

 <span data-ttu-id="b8a9a-173">委任で Kerberos 認証プロトコルを使用するには、資格情報ネゴシエーションを使用する Kerberos プロトコル ("マルチレッグ" Kerberos または "マルチステップ" Kerberos とも呼ばれます) を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-173">To use the Kerberos authentication protocol with delegation, you must implement the Kerberos protocol with credential negotiation (sometimes called "multi-leg" or "multi-step" Kerberos).</span></span> <span data-ttu-id="b8a9a-174">資格情報ネゴシエーションを使用しない Kerberos 認証 ("ワンショット" Kerberos または "シングルレッグ" Kerberos とも呼ばれます) を実装した場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-174">If you implement Kerberos authentication without credential negotiation (sometimes called "one-shot" or "single-leg" Kerberos), an exception will be thrown.</span></span>  
  
 <span data-ttu-id="b8a9a-175">資格情報ネゴシエーションを使用する Kerberos を実装するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-175">To implement Kerberos with credential negotiation, do the following steps:</span></span>  
  
1. <span data-ttu-id="b8a9a-176"><xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> を <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> に設定して委任を実装します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-176">Implement delegation by setting <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> to <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span>  
  
2. <span data-ttu-id="b8a9a-177">次のような SSPI ネゴシエーションが必要です。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-177">Require SSPI negotiation:</span></span>  
  
    1. <span data-ttu-id="b8a9a-178">標準バインディングを使用する場合は、`NegotiateServiceCredential` プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-178">If you are using standard bindings, set the `NegotiateServiceCredential` property to `true`.</span></span>  
  
    2. <span data-ttu-id="b8a9a-179">カスタム バインドを使用する場合は、`AuthenticationMode` 要素の `Security` 属性を `SspiNegotiated` に設定します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-179">If you are using custom bindings, set the `AuthenticationMode` attribute of the `Security` element to `SspiNegotiated`.</span></span>  
  
3. <span data-ttu-id="b8a9a-180">次のように、NTLM を使用できないようにすることで、SSPI ネゴシエーションで Kerberos を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-180">Require the SSPI negotiation to use Kerberos by disallowing the use of NTLM:</span></span>  
  
    1. <span data-ttu-id="b8a9a-181">NTLM を使用できないようにするには、コードで `ChannelFactory.Credentials.Windows.AllowNtlm = false` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-181">Do this in code, with the following statement: `ChannelFactory.Credentials.Windows.AllowNtlm = false`</span></span>  
  
    2. <span data-ttu-id="b8a9a-182">構成ファイルで `allowNtlm` 属性を `false` に設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-182">Or you can do this in the configuration file by setting the `allowNtlm` attribute to `false`.</span></span> <span data-ttu-id="b8a9a-183">この属性は、に含まれてい [\<windows>](../../configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-183">This attribute is contained in the [\<windows>](../../configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md).</span></span>  
  
### <a name="ntlm-protocol"></a><span data-ttu-id="b8a9a-184">NTLM プロトコル</span><span class="sxs-lookup"><span data-stu-id="b8a9a-184">NTLM Protocol</span></span>  
  
#### <a name="negotiate-ssp-falls-back-to-ntlm-but-ntlm-is-disabled"></a><span data-ttu-id="b8a9a-185">ネゴシエート SSP は NTLM にフォールバックするが、NTLM が無効になっている</span><span class="sxs-lookup"><span data-stu-id="b8a9a-185">Negotiate SSP Falls Back to NTLM, but NTLM Is Disabled</span></span>  

 <span data-ttu-id="b8a9a-186"><xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A>プロパティがに設定されている `false` 場合、NTLM が使用されている場合、WINDOWS COMMUNICATION FOUNDATION (WCF) がベストエフォートで例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-186">The <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> property is set to `false`, which causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="b8a9a-187">このプロパティをに設定すると `false` 、NTLM 資格情報がネットワーク経由で送信されるのを防ぐことができません。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-187">Setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>  
  
 <span data-ttu-id="b8a9a-188">NTLM へのフォールバックを無効にする方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-188">The following shows how to disable fallback to NTLM.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#4)]
 [!code-vb[C_DebuggingWindowsAuth#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#4)]  
  
#### <a name="ntlm-logon-fails"></a><span data-ttu-id="b8a9a-189">NTLM ログオンが失敗する</span><span class="sxs-lookup"><span data-stu-id="b8a9a-189">NTLM Logon Fails</span></span>  

 <span data-ttu-id="b8a9a-190">サービスで、クライアント資格情報が無効です。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-190">The client credentials are not valid on the service.</span></span> <span data-ttu-id="b8a9a-191">ユーザー名とパスワードが正しく設定されており、サービスを実行しているコンピューターに認識されているアカウントに対応していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-191">Check that the user name and password are correctly set and correspond to an account that is known to the computer where the service is running.</span></span> <span data-ttu-id="b8a9a-192">NTLM では、指定された資格情報を使用してサービスのコンピューターにログオンします。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-192">NTLM uses the specified credentials to log on to the service's computer.</span></span> <span data-ttu-id="b8a9a-193">資格情報がクライアントを実行しているコンピューターで有効であっても、サービスのコンピューターでは無効な場合、このログオンは失敗します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-193">While the credentials may be valid on the computer where the client is running, this logon will fail if the credentials are not valid on the service's computer.</span></span>  
  
#### <a name="anonymous-ntlm-logon-occurs-but-anonymous-logons-are-disabled-by-default"></a><span data-ttu-id="b8a9a-194">匿名 NTLM ログオンが発生するが、既定では匿名ログオンが無効になっている</span><span class="sxs-lookup"><span data-stu-id="b8a9a-194">Anonymous NTLM Logon Occurs, but Anonymous Logons Are Disabled by Default</span></span>  

 <span data-ttu-id="b8a9a-195">次の例に示すように、クライアントの作成時に、<xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> プロパティを <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> に設定します。ただし、既定では、サーバーは匿名ログオンを許可しません。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-195">When creating a client, the <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property is set to <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, as shown in the following example, but by default the server disallows anonymous logons.</span></span> <span data-ttu-id="b8a9a-196">これは、<xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> クラスの <xref:System.ServiceModel.Security.WindowsServiceCredential> プロパティの既定値が `false` であるためです。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-196">This occurs because the default value of the <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> property of the <xref:System.ServiceModel.Security.WindowsServiceCredential> class is `false`.</span></span>  
  
 <span data-ttu-id="b8a9a-197">匿名ログオンを有効にすることを試みるクライアント コードを次に示します (既定のプロパティは `Identification` です)。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-197">The following client code attempts to enable anonymous logons (note that the default property is `Identification`).</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#5)]
 [!code-vb[C_DebuggingWindowsAuth#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#5)]  
  
 <span data-ttu-id="b8a9a-198">サーバーによって匿名ログオンを有効にするように既定値を変更するサービス コードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-198">The following service code changes the default to enable anonymous logons by the server.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#6)]
 [!code-vb[C_DebuggingWindowsAuth#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#6)]  
  
 <span data-ttu-id="b8a9a-199">権限借用の詳細については、「 [委任と偽装](delegation-and-impersonation-with-wcf.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-199">For more information about impersonation, see [Delegation and Impersonation](delegation-and-impersonation-with-wcf.md).</span></span>  
  
 <span data-ttu-id="b8a9a-200">もう 1 つの方法として、SYSTEM ビルトイン アカウントを使用する Windows サービスとしてクライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-200">Alternatively, the client is running as a Windows service, using the built-in account SYSTEM.</span></span>  
  
### <a name="other-problems"></a><span data-ttu-id="b8a9a-201">その他の問題</span><span class="sxs-lookup"><span data-stu-id="b8a9a-201">Other Problems</span></span>  
  
#### <a name="client-credentials-are-not-set-correctly"></a><span data-ttu-id="b8a9a-202">クライアント資格情報が正しく設定されていない</span><span class="sxs-lookup"><span data-stu-id="b8a9a-202">Client Credentials Are Not Set Correctly</span></span>  

 <span data-ttu-id="b8a9a-203">Windows 認証では、<xref:System.ServiceModel.Security.WindowsClientCredential> ではなく、<xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> クラスの <xref:System.ServiceModel.ClientBase%601> プロパティによって返された <xref:System.ServiceModel.Security.UserNamePasswordClientCredential> インスタンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-203">Windows authentication uses the <xref:System.ServiceModel.Security.WindowsClientCredential> instance returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class, not the <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>.</span></span> <span data-ttu-id="b8a9a-204">誤りのあるコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-204">The following shows an incorrect example.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#2)]
 [!code-vb[C_DebuggingWindowsAuth#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#2)]  
  
 <span data-ttu-id="b8a9a-205">正しいコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-205">The following shows the correct example.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#3)]
 [!code-vb[C_DebuggingWindowsAuth#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#3)]  
  
#### <a name="sspi-is-not-available"></a><span data-ttu-id="b8a9a-206">SSPI を使用できない</span><span class="sxs-lookup"><span data-stu-id="b8a9a-206">SSPI Is Not Available</span></span>  

 <span data-ttu-id="b8a9a-207">サーバーとして使用する場合、次のオペレーティングシステムは Windows 認証をサポートしていません: Windows XP Home Edition、Windows XP Media Center Edition、および Windows Vista Home エディション。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-207">The following operating systems do not support Windows authentication when used as a server: Windows XP Home Edition, Windows XP Media Center Edition, and Windows Vista Home editions.</span></span>  
  
#### <a name="developing-and-deploying-with-different-identities"></a><span data-ttu-id="b8a9a-208">異なる ID を使用した開発と展開</span><span class="sxs-lookup"><span data-stu-id="b8a9a-208">Developing and Deploying with Different Identities</span></span>  

 <span data-ttu-id="b8a9a-209">アプリケーションを 1 台のコンピューターで開発し、別のコンピューターに展開し、異なるアカウントの種類を使用して各コンピューターで認証を行う場合、動作の違いが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-209">If you develop your application on one machine, and deploy on another, and use different account types to authenticate on each machine, you may experience different behavior.</span></span> <span data-ttu-id="b8a9a-210">たとえば、`SSPI Negotiated` 認証モードを使用して Windows XP Professional コンピューターでアプリケーションを開発するとします。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-210">For example, suppose you develop your application on a Windows XP Pro machine using the `SSPI Negotiated` authentication mode.</span></span> <span data-ttu-id="b8a9a-211">ローカル ユーザー アカウントを使用して認証する場合は、NTLM プロトコルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-211">If you use a local user account to authenticate with, then NTLM protocol will be used.</span></span> <span data-ttu-id="b8a9a-212">アプリケーションを開発した後は、ドメイン アカウントで実行されるサービスを Windows Server 2003 コンピューターに展開します。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-212">Once the application is developed, you deploy the service to a Windows Server 2003 machine where it runs under a domain account.</span></span> <span data-ttu-id="b8a9a-213">この時点では、クライアントは Kerberos およびドメインコントローラーを使用するため、サービスを認証できません。</span><span class="sxs-lookup"><span data-stu-id="b8a9a-213">At this point, the client will not be able to authenticate the service because it will be using Kerberos and a domain controller.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8a9a-214">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8a9a-214">See also</span></span>

- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.ClientBase%601>
- [<span data-ttu-id="b8a9a-215">委任と偽装</span><span class="sxs-lookup"><span data-stu-id="b8a9a-215">Delegation and Impersonation</span></span>](delegation-and-impersonation-with-wcf.md)
- [<span data-ttu-id="b8a9a-216">サポートされていないシナリオ</span><span class="sxs-lookup"><span data-stu-id="b8a9a-216">Unsupported Scenarios</span></span>](unsupported-scenarios.md)
