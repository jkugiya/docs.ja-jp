---
description: 詳細については、「セキュリティプロトコルバージョン1.0」を参照してください。
title: セキュリティ プロトコル バージョン 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
ms.openlocfilehash: c807f0b844fb9cb861148afa63d83826a9740c98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752731"
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="c4e4f-103">セキュリティ プロトコル バージョン 1.0</span><span class="sxs-lookup"><span data-stu-id="c4e4f-103">Security Protocols version 1.0</span></span>

<span data-ttu-id="c4e4f-104">Web サービス セキュリティ プロトコルには、既存のエンタープライズ メッセージング セキュリティのあらゆる要件に対応する Web サービス セキュリティ機構が用意されています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-104">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="c4e4f-105">このセクションでは、 <xref:System.ServiceModel.Channels.SecurityBindingElement> 次の Web サービスのセキュリティプロトコルについて、Windows Communication Foundation (WCF) バージョン1.0 の詳細 (で実装) について説明します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-105">This section describes the Windows Communication Foundation (WCF) version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="c4e4f-106">仕様/ドキュメント</span><span class="sxs-lookup"><span data-stu-id="c4e4f-106">Specification/Document</span></span>|<span data-ttu-id="c4e4f-107">リンク</span><span class="sxs-lookup"><span data-stu-id="c4e4f-107">Link</span></span>|  
|-|-|  
|<span data-ttu-id="c4e4f-108">WSS SOAP Message Security 1.0</span><span class="sxs-lookup"><span data-stu-id="c4e4f-108">WSS: SOAP Message Security 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|
|<span data-ttu-id="c4e4f-109">WSS: Username Token Profile 1.0</span><span class="sxs-lookup"><span data-stu-id="c4e4f-109">WSS: Username Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="c4e4f-110">WSS: X509 Token Profile 1.0</span><span class="sxs-lookup"><span data-stu-id="c4e4f-110">WSS: X509 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|
|<span data-ttu-id="c4e4f-111">WSS: SAML 1.1 Token Profile 1.0</span><span class="sxs-lookup"><span data-stu-id="c4e4f-111">WSS: SAML 1.1 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|
|<span data-ttu-id="c4e4f-112">WSS SOAP Message Security 1.1</span><span class="sxs-lookup"><span data-stu-id="c4e4f-112">WSS: SOAP Message Security 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|
|<span data-ttu-id="c4e4f-113">WSS Username Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="c4e4f-113">WSS Username Token Profile 1.1</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="c4e4f-114">WSS: X.509 Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="c4e4f-114">WSS: X.509 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|
|<span data-ttu-id="c4e4f-115">WSS: Kerberos Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="c4e4f-115">WSS: Kerberos Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|
|<span data-ttu-id="c4e4f-116">WSS: SAML 1.1 Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="c4e4f-116">WSS: SAML 1.1 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|
|<span data-ttu-id="c4e4f-117">WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="c4e4f-117">WS-Secure Conversation</span></span>|<http://specs.xmlsoap.org/ws/2005/02/sc/WS-SecureConversation.pdf>|
|<span data-ttu-id="c4e4f-118">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="c4e4f-118">WS-Trust</span></span>|<http://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf>|
|<span data-ttu-id="c4e4f-119">Application Note:</span><span class="sxs-lookup"><span data-stu-id="c4e4f-119">Application Note:</span></span><br /><br /> <span data-ttu-id="c4e4f-120">Using WS-Trust for TLS Handshake</span><span class="sxs-lookup"><span data-stu-id="c4e4f-120">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="c4e4f-121">公開予定</span><span class="sxs-lookup"><span data-stu-id="c4e4f-121">To be published</span></span>|  
|<span data-ttu-id="c4e4f-122">Application Note:</span><span class="sxs-lookup"><span data-stu-id="c4e4f-122">Application Note:</span></span><br /><br /> <span data-ttu-id="c4e4f-123">Using WS-Trust for SPNEGO</span><span class="sxs-lookup"><span data-stu-id="c4e4f-123">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="c4e4f-124">公開予定</span><span class="sxs-lookup"><span data-stu-id="c4e4f-124">To be published</span></span>|  
|<span data-ttu-id="c4e4f-125">Application Note:</span><span class="sxs-lookup"><span data-stu-id="c4e4f-125">Application Note:</span></span><br /><br /> <span data-ttu-id="c4e4f-126">Web Services Addressing Endpoint References And Identity</span><span class="sxs-lookup"><span data-stu-id="c4e4f-126">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="c4e4f-127">公開予定</span><span class="sxs-lookup"><span data-stu-id="c4e4f-127">To be published</span></span>|  
|<span data-ttu-id="c4e4f-128">WS-SecurityPolicy 1.1</span><span class="sxs-lookup"><span data-stu-id="c4e4f-128">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="c4e4f-129">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="c4e4f-129">(2005/07)</span></span>|<http://specs.xmlsoap.org/ws/2005/07/securitypolicy/ws-securitypolicy.pdf><br /><br /> <span data-ttu-id="c4e4f-130">OASIS WS SX テクニカル委員会に提出された [エラッタ](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) によって修正されました</span><span class="sxs-lookup"><span data-stu-id="c4e4f-130">as amended by [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) submitted to OASIS WS-SX Technical Committee</span></span> |  
  
 <span data-ttu-id="c4e4f-131">WCF version 1 には、Web サービスのセキュリティ構成の基礎として使用できる17の認証モードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-131">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="c4e4f-132">各モードは、次のような一般的な展開要件について最適化されています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-132">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
- <span data-ttu-id="c4e4f-133">クライアントとサービスの認証に使用する資格情報</span><span class="sxs-lookup"><span data-stu-id="c4e4f-133">Credentials used to authenticate client and service.</span></span>  
  
- <span data-ttu-id="c4e4f-134">メッセージまたはトランスポートのセキュリティ保護機構</span><span class="sxs-lookup"><span data-stu-id="c4e4f-134">Message or transport security protection mechanisms.</span></span>  
  
- <span data-ttu-id="c4e4f-135">メッセージ交換パターン</span><span class="sxs-lookup"><span data-stu-id="c4e4f-135">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="c4e4f-136">認証モード</span><span class="sxs-lookup"><span data-stu-id="c4e4f-136">Authentication Mode</span></span>|<span data-ttu-id="c4e4f-137">クライアント認証</span><span class="sxs-lookup"><span data-stu-id="c4e4f-137">Client Authentication</span></span>|<span data-ttu-id="c4e4f-138">[サーバー認証]</span><span class="sxs-lookup"><span data-stu-id="c4e4f-138">Server Authentication</span></span>|<span data-ttu-id="c4e4f-139">モード</span><span class="sxs-lookup"><span data-stu-id="c4e4f-139">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="c4e4f-140">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="c4e4f-140">UserNameOverTransport</span></span>|<span data-ttu-id="c4e4f-141">ユーザー名/パスワード</span><span class="sxs-lookup"><span data-stu-id="c4e4f-141">User name/password</span></span>|<span data-ttu-id="c4e4f-142">X509</span><span class="sxs-lookup"><span data-stu-id="c4e4f-142">X509</span></span>|<span data-ttu-id="c4e4f-143">トランスポート</span><span class="sxs-lookup"><span data-stu-id="c4e4f-143">Transport</span></span>|  
|<span data-ttu-id="c4e4f-144">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="c4e4f-144">CertificateOverTransport</span></span>|<span data-ttu-id="c4e4f-145">X509</span><span class="sxs-lookup"><span data-stu-id="c4e4f-145">X509</span></span>|<span data-ttu-id="c4e4f-146">X509</span><span class="sxs-lookup"><span data-stu-id="c4e4f-146">X509</span></span>|<span data-ttu-id="c4e4f-147">トランスポート</span><span class="sxs-lookup"><span data-stu-id="c4e4f-147">Transport</span></span>|  
|<span data-ttu-id="c4e4f-148">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="c4e4f-148">KerberosOverTransport</span></span>|<span data-ttu-id="c4e4f-149">Windows</span><span class="sxs-lookup"><span data-stu-id="c4e4f-149">Windows</span></span>|<span data-ttu-id="c4e4f-150">X509</span><span class="sxs-lookup"><span data-stu-id="c4e4f-150">X509</span></span>|<span data-ttu-id="c4e4f-151">トランスポート</span><span class="sxs-lookup"><span data-stu-id="c4e4f-151">Transport</span></span>|  
|<span data-ttu-id="c4e4f-152">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="c4e4f-152">IssuedTokenOverTransport</span></span>|<span data-ttu-id="c4e4f-153">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="c4e4f-153">Federated</span></span>|<span data-ttu-id="c4e4f-154">X509</span><span class="sxs-lookup"><span data-stu-id="c4e4f-154">X509</span></span>|<span data-ttu-id="c4e4f-155">トランスポート</span><span class="sxs-lookup"><span data-stu-id="c4e4f-155">Transport</span></span>|  
|<span data-ttu-id="c4e4f-156">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="c4e4f-156">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="c4e4f-157">Windows SSPI ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="c4e4f-157">Windows Sspi Negotiated</span></span>|<span data-ttu-id="c4e4f-158">Windows SSPI ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="c4e4f-158">Windows Sspi Negotiated</span></span>|<span data-ttu-id="c4e4f-159">トランスポート</span><span class="sxs-lookup"><span data-stu-id="c4e4f-159">Transport</span></span>|  
|<span data-ttu-id="c4e4f-160">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="c4e4f-160">AnonymousForCertificate</span></span>|<span data-ttu-id="c4e4f-161">なし</span><span class="sxs-lookup"><span data-stu-id="c4e4f-161">None</span></span>|<span data-ttu-id="c4e4f-162">X509</span><span class="sxs-lookup"><span data-stu-id="c4e4f-162">X509</span></span>|<span data-ttu-id="c4e4f-163">Message</span><span class="sxs-lookup"><span data-stu-id="c4e4f-163">Message</span></span>|  
|<span data-ttu-id="c4e4f-164">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="c4e4f-164">UserNameForCertificate</span></span>|<span data-ttu-id="c4e4f-165">ユーザー名/パスワード</span><span class="sxs-lookup"><span data-stu-id="c4e4f-165">User name/password</span></span>|<span data-ttu-id="c4e4f-166">X509</span><span class="sxs-lookup"><span data-stu-id="c4e4f-166">X509</span></span>|<span data-ttu-id="c4e4f-167">Message</span><span class="sxs-lookup"><span data-stu-id="c4e4f-167">Message</span></span>|  
|<span data-ttu-id="c4e4f-168">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="c4e4f-168">MutualCertificate</span></span>|<span data-ttu-id="c4e4f-169">X509</span><span class="sxs-lookup"><span data-stu-id="c4e4f-169">X509</span></span>|<span data-ttu-id="c4e4f-170">X509</span><span class="sxs-lookup"><span data-stu-id="c4e4f-170">X509</span></span>|<span data-ttu-id="c4e4f-171">Message</span><span class="sxs-lookup"><span data-stu-id="c4e4f-171">Message</span></span>|  
|<span data-ttu-id="c4e4f-172">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="c4e4f-172">MutualCertificateDuplex</span></span>|<span data-ttu-id="c4e4f-173">X509</span><span class="sxs-lookup"><span data-stu-id="c4e4f-173">X509</span></span>|<span data-ttu-id="c4e4f-174">X509</span><span class="sxs-lookup"><span data-stu-id="c4e4f-174">X509</span></span>|<span data-ttu-id="c4e4f-175">Message</span><span class="sxs-lookup"><span data-stu-id="c4e4f-175">Message</span></span>|  
|<span data-ttu-id="c4e4f-176">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="c4e4f-176">IssuedTokenForCertificate</span></span>|<span data-ttu-id="c4e4f-177">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="c4e4f-177">Federated</span></span>|<span data-ttu-id="c4e4f-178">X509</span><span class="sxs-lookup"><span data-stu-id="c4e4f-178">X509</span></span>|<span data-ttu-id="c4e4f-179">Message</span><span class="sxs-lookup"><span data-stu-id="c4e4f-179">Message</span></span>|  
|<span data-ttu-id="c4e4f-180">Kerberos</span><span class="sxs-lookup"><span data-stu-id="c4e4f-180">Kerberos</span></span>|<span data-ttu-id="c4e4f-181">Windows</span><span class="sxs-lookup"><span data-stu-id="c4e4f-181">Windows</span></span>|<span data-ttu-id="c4e4f-182">Windows</span><span class="sxs-lookup"><span data-stu-id="c4e4f-182">Windows</span></span>|<span data-ttu-id="c4e4f-183">Message</span><span class="sxs-lookup"><span data-stu-id="c4e4f-183">Message</span></span>|  
|<span data-ttu-id="c4e4f-184">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="c4e4f-184">IssuedToken</span></span>|<span data-ttu-id="c4e4f-185">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="c4e4f-185">Federated</span></span>|<span data-ttu-id="c4e4f-186">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="c4e4f-186">Federated</span></span>|<span data-ttu-id="c4e4f-187">Message</span><span class="sxs-lookup"><span data-stu-id="c4e4f-187">Message</span></span>|  
|<span data-ttu-id="c4e4f-188">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="c4e4f-188">SspiNegotiated</span></span>|<span data-ttu-id="c4e4f-189">Windows SSPI ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="c4e4f-189">Windows Sspi Negotiated</span></span>|<span data-ttu-id="c4e4f-190">Windows SSPI ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="c4e4f-190">Windows Sspi Negotiated</span></span>|<span data-ttu-id="c4e4f-191">Message</span><span class="sxs-lookup"><span data-stu-id="c4e4f-191">Message</span></span>|  
|<span data-ttu-id="c4e4f-192">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="c4e4f-192">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="c4e4f-193">なし</span><span class="sxs-lookup"><span data-stu-id="c4e4f-193">None</span></span>|<span data-ttu-id="c4e4f-194">X509、TLS ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="c4e4f-194">X509, TLS-Nego</span></span>|<span data-ttu-id="c4e4f-195">Message</span><span class="sxs-lookup"><span data-stu-id="c4e4f-195">Message</span></span>|  
|<span data-ttu-id="c4e4f-196">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="c4e4f-196">UserNameForSslNegotiated</span></span>|<span data-ttu-id="c4e4f-197">ユーザー名/パスワード</span><span class="sxs-lookup"><span data-stu-id="c4e4f-197">User name/password</span></span>|<span data-ttu-id="c4e4f-198">X509、TLS ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="c4e4f-198">X509, TLS-Nego</span></span>|<span data-ttu-id="c4e4f-199">Message</span><span class="sxs-lookup"><span data-stu-id="c4e4f-199">Message</span></span>|  
|<span data-ttu-id="c4e4f-200">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="c4e4f-200">MutualSslNegotiated</span></span>|<span data-ttu-id="c4e4f-201">X509</span><span class="sxs-lookup"><span data-stu-id="c4e4f-201">X509</span></span>|<span data-ttu-id="c4e4f-202">X509、TLS ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="c4e4f-202">X509, TLS-Nego</span></span>|<span data-ttu-id="c4e4f-203">Message</span><span class="sxs-lookup"><span data-stu-id="c4e4f-203">Message</span></span>|  
|<span data-ttu-id="c4e4f-204">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="c4e4f-204">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="c4e4f-205">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="c4e4f-205">Federated</span></span>|<span data-ttu-id="c4e4f-206">X509、TLS ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="c4e4f-206">X509, TLS-Nego</span></span>|<span data-ttu-id="c4e4f-207">Message</span><span class="sxs-lookup"><span data-stu-id="c4e4f-207">Message</span></span>|  
  
 <span data-ttu-id="c4e4f-208">このような認証モードを使用するエンドポイントは、WS-SecurityPolicy (WS-SP) を使用してセキュリティ要件を表現できます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-208">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="c4e4f-209">ここでは、各認証モードのセキュリティ ヘッダーとインフラストラクチャ メッセージの構造について説明します。また、ポリシーとメッセージの例も示します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-209">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="c4e4f-210">WCF では、WS-SecureConversation を利用して、アプリケーション間での複数メッセージの交換を保護するためのセキュリティで保護されたセッションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-210">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="c4e4f-211">実装の詳細については、後述の「セキュリティで保護されたセッション」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-211">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="c4e4f-212">WCF には、認証モードに加えて、ほとんどのメッセージセキュリティベースの認証モード (署名と暗号化操作の順序、アルゴリズムスイート、キーの派生、署名の確認など) に適用される一般的な保護メカニズムを制御するための設定があります。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-212">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="c4e4f-213">このドキュメントでは、以下のプレフィックスと名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-213">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="c4e4f-214">Prefix</span><span class="sxs-lookup"><span data-stu-id="c4e4f-214">Prefix</span></span>|<span data-ttu-id="c4e4f-215">名前空間</span><span class="sxs-lookup"><span data-stu-id="c4e4f-215">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="c4e4f-216">s</span><span class="sxs-lookup"><span data-stu-id="c4e4f-216">s</span></span>|<http://www.w3.org/2003/05/soap-envelope/>|
|<span data-ttu-id="c4e4f-217">sp</span><span class="sxs-lookup"><span data-stu-id="c4e4f-217">sp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/>|
|<span data-ttu-id="c4e4f-218">a</span><span class="sxs-lookup"><span data-stu-id="c4e4f-218">a</span></span>|<http://www.w3.org/2005/08/addressing>|  
|<span data-ttu-id="c4e4f-219">wsse</span><span class="sxs-lookup"><span data-stu-id="c4e4f-219">wsse</span></span>|<span data-ttu-id="c4e4f-220">未定 - OASIS WSS 1.0 の URI</span><span class="sxs-lookup"><span data-stu-id="c4e4f-220">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="c4e4f-221">wsse11</span><span class="sxs-lookup"><span data-stu-id="c4e4f-221">wsse11</span></span>|<span data-ttu-id="c4e4f-222">未定 - OASIS WSS 1.1 の URI</span><span class="sxs-lookup"><span data-stu-id="c4e4f-222">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="c4e4f-223">wsu</span><span class="sxs-lookup"><span data-stu-id="c4e4f-223">wsu</span></span>|<span data-ttu-id="c4e4f-224">未定 - OASIS WSS 1.0 Utility の URI</span><span class="sxs-lookup"><span data-stu-id="c4e4f-224">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="c4e4f-225">ds</span><span class="sxs-lookup"><span data-stu-id="c4e4f-225">ds</span></span>|<span data-ttu-id="c4e4f-226">未定 - W3C XMLDSig の URI</span><span class="sxs-lookup"><span data-stu-id="c4e4f-226">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="c4e4f-227">wst</span><span class="sxs-lookup"><span data-stu-id="c4e4f-227">wst</span></span>|<span data-ttu-id="c4e4f-228">未定 - WS-Trust 2005/02 の URI</span><span class="sxs-lookup"><span data-stu-id="c4e4f-228">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="c4e4f-229">wssc</span><span class="sxs-lookup"><span data-stu-id="c4e4f-229">wssc</span></span>|<span data-ttu-id="c4e4f-230">未定 - WS-SecureConversation 2005/02 の URI</span><span class="sxs-lookup"><span data-stu-id="c4e4f-230">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="c4e4f-231">wsaw</span><span class="sxs-lookup"><span data-stu-id="c4e4f-231">wsaw</span></span>|<span data-ttu-id="c4e4f-232">未定 - WS-Addressing ポリシーの名前空間</span><span class="sxs-lookup"><span data-stu-id="c4e4f-232">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="c4e4f-233">wsp</span><span class="sxs-lookup"><span data-stu-id="c4e4f-233">wsp</span></span>|<http://schemas.xmlsoap.org/ws/2004/09/policy>|  
|<span data-ttu-id="c4e4f-234">mssp</span><span class="sxs-lookup"><span data-stu-id="c4e4f-234">mssp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy>|
  
## <a name="1-token-profiles"></a><span data-ttu-id="c4e4f-235">1. トークンプロファイル</span><span class="sxs-lookup"><span data-stu-id="c4e4f-235">1. Token Profiles</span></span>  

 <span data-ttu-id="c4e4f-236">Web サービス セキュリティ仕様では、資格情報をセキュリティ トークンとして表します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-236">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="c4e4f-237">WCF では、次のトークンの種類がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-237">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="c4e4f-238">1.1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="c4e4f-238">1.1 UsernameToken</span></span>  

 <span data-ttu-id="c4e4f-239">WCF は、次の制約がある UsernameToken10 および UsernameToken11 プロファイルに従います。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-239">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="c4e4f-240">R1101 : UsernameToken\Password 要素の PasswordType 属性では、#PasswordText (既定値) を省略するか、指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-240">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="c4e4f-241">機能拡張を使用すると、#PasswordDigest を実装できます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-241">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="c4e4f-242">#PasswordDigest は、十分に安全性の高いパスワード保護機構であると誤解されがちであることが報告されています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-242">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="c4e4f-243">しかし、#PasswordDigest は、UsernameToken の暗号化の代替として使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-243">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="c4e4f-244">#PasswordDigest の第一の目的は、リプレイ攻撃から保護することです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-244">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="c4e4f-245">WCF 認証モードでは、メッセージ署名を使用することによって、リプレイ攻撃の脅威が軽減されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-245">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="c4e4f-246">B1102 WCF は、UsernameToken の Nonce および作成されたサブ要素を出力しません。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-246">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="c4e4f-247">これらのサブ要素は、リプレイ検出を支援するためのものです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-247">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="c4e4f-248">WCF では、代わりにメッセージ署名を使用します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-248">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="c4e4f-249">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) では、パスワードからのキー派生機能が導入されています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-249">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="c4e4f-250">B1103 : UsernameToken のパスワードをキー派生に使用することはできません。したがって、暗号化操作では使用できません。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-250">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="c4e4f-251">理由 : パスワードは、一般に暗号化操作に使用するには脆弱すぎると見なされています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-251">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="c4e4f-252">1.2 X509 トークン</span><span class="sxs-lookup"><span data-stu-id="c4e4f-252">1.2 X509 Token</span></span>  

 <span data-ttu-id="c4e4f-253">WCF では、資格情報の種類として X509v3 証明書をサポートしており、次の制約がある X509TokenProfile 1.0 と X509TokenProfile 1.1 に従います。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-253">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="c4e4f-254">R1201 : BinarySecurityToken 要素に X509v3 証明書が含まれている場合、この要素の ValueType 属性の値は #X509v3 であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-254">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="c4e4f-255">WSS X509 Token Profile 1.0 および 1.1 では、値の種類として #X509PKIPathv1 と #PKCS7 も定義されています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-255">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="c4e4f-256">WCF では、これらの型はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-256">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="c4e4f-257">R1202 : X509 証明書に SubjectKeyIdentifier (SKI) 拡張が含まれている場合、トークンへの外部参照に wsse:KeyIdentifier を使用する必要があります。この場合、ValueType 属性に #X509SubjectKeyIdentifier を指定し、証明書の SKI 拡張の Base64 でエンコードされた値を含めます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-257">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="c4e4f-258">SKI 参照は幅広く実装されており、相互運用性の高い外部参照型であることが証明されています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-258">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="c4e4f-259">R1203 : X509 セキュリティ トークンへの外部参照では、ds:X509IssuerSerial を使用できません。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-259">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="c4e4f-260">R1204 : X509TokenProfile1.1 を使用している場合、X509 セキュリティ トークンへの外部参照では、WS-Security 1.1 で導入された拇印を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-260">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="c4e4f-261">WCF は、X509issuerserial をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-261">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="c4e4f-262">ただし、、X509issuerserial には相互運用性の問題があります。 WCF では、文字列を使用して、X509issuerserial の2つの値を比較します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-262">However There are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="c4e4f-263">したがって、サブジェクト名のコンポーネントの並べ替えと、WCF サービスへの送信に証明書への参照が含まれている場合、証明書が見つからない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-263">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="c4e4f-264">1.3 Kerberos トークン</span><span class="sxs-lookup"><span data-stu-id="c4e4f-264">1.3 Kerberos Token</span></span>  

 <span data-ttu-id="c4e4f-265">WCF では、次の制約により、Windows 認証の目的で KerberosTokenProfile 1.1 がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-265">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="c4e4f-266">R1301 : GSS_API と Kerberos 仕様で定義されているように、Kerberos トークンは GSS によってラップされた Kerberos v4 AP_REQ の値を伝達する必要があります。また、値 #GSS_Kerberosv5_AP_REQ が指定された ValueType 属性を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-266">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="c4e4f-267">WCF では、ベア AP-要求ではなく、GSS によってラップされた Kerberos AP を使用します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-267">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="c4e4f-268">これは、セキュリティのベスト プラクティスです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-268">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="c4e4f-269">1.4 SAML v1.1 トークン</span><span class="sxs-lookup"><span data-stu-id="c4e4f-269">1.4 SAML v1.1 Token</span></span>  

 <span data-ttu-id="c4e4f-270">WCF は、SAML v1.1 トークンの WSS SAML トークンプロファイル1.0 および1.1 をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-270">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="c4e4f-271">SAML トークンの形式のその他のバージョンも実装できます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-271">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="c4e4f-272">1.5 セキュリティ コンテキスト トークン</span><span class="sxs-lookup"><span data-stu-id="c4e4f-272">1.5 Security Context Token</span></span>  

 <span data-ttu-id="c4e4f-273">WCF では、Ws-secureconversation で導入されたセキュリティコンテキストトークン (SCT) がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-273">WCF supports the Security Context Token (SCT) introduced in WS-SecureConversation.</span></span> <span data-ttu-id="c4e4f-274">SCT は、SecureConversation と、後述する TLS および SSPI の各バイナリ ネゴシエーション プロトコルで確立されたセキュリティ コンテキストを表すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-274">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="c4e4f-275">2. 一般的なメッセージセキュリティパラメーター</span><span class="sxs-lookup"><span data-stu-id="c4e4f-275">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="c4e4f-276">2.1 タイムスタンプ</span><span class="sxs-lookup"><span data-stu-id="c4e4f-276">2.1 TimeStamp</span></span>  

 <span data-ttu-id="c4e4f-277">タイムスタンプの有無は、<xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> クラスの <xref:System.ServiceModel.Channels.SecurityBindingElement> プロパティを使用して制御します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-277">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="c4e4f-278">WCF は、常に wsse: Created および wsse: Expires フィールドを使用して wsse: TimeStamp をシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-278">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="c4e4f-279">署名を使用する場合、wsse:TimeStamp は必ず署名されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-279">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="c4e4f-280">2.2 保護の順序</span><span class="sxs-lookup"><span data-stu-id="c4e4f-280">2.2 Protection Order</span></span>  

 <span data-ttu-id="c4e4f-281">WCF は、"暗号化前に署名する" と "署名前に暗号化する" (セキュリティポリシー 1.1) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-281">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="c4e4f-282">WS-Security 1.1 の SignatureConfirmation 機構を使用していない場合、"署名前に暗号化" を使用して保護されたメッセージを開くと、置き換え攻撃への署名が行われます。また、暗号化された内容に署名すると監査が困難になります。これらの理由から、"暗号化前に署名" を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-282">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="c4e4f-283">2.3 署名の保護</span><span class="sxs-lookup"><span data-stu-id="c4e4f-283">2.3 Signature Protection</span></span>  

 <span data-ttu-id="c4e4f-284">"署名前に暗号化" を使用する場合、暗号化された内容や署名キー (特に、脆弱なキー マテリアルでカスタム トークンを使用する場合) を推測するブルート フォース攻撃を防ぐために、署名を保護することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-284">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="c4e4f-285">2.4 アルゴリズム スイート</span><span class="sxs-lookup"><span data-stu-id="c4e4f-285">2.4 Algorithm Suite</span></span>  

 <span data-ttu-id="c4e4f-286">WCF では、セキュリティポリシー1.1 に示されているすべてのアルゴリズムスイートがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-286">WCF supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="c4e4f-287">2.5 キー派生</span><span class="sxs-lookup"><span data-stu-id="c4e4f-287">2.5 Key Derivation</span></span>  

 <span data-ttu-id="c4e4f-288">WCF では、「Ws-secureconversation」で説明されているように、"対称キーのキー派生" を使用します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-288">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="c4e4f-289">2.6 署名確認</span><span class="sxs-lookup"><span data-stu-id="c4e4f-289">2.6 Signature Confirmation</span></span>  

 <span data-ttu-id="c4e4f-290">署名確認によって "man-in-the-middle" 攻撃から保護することで、署名セットを保護できます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-290">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="c4e4f-291">2.7 セキュリティ ヘッダーのレイアウト</span><span class="sxs-lookup"><span data-stu-id="c4e4f-291">2.7 Security Header Layout</span></span>  

 <span data-ttu-id="c4e4f-292">各認証モードでは、セキュリティ ヘッダーの特定のレイアウトが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-292">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="c4e4f-293">セキュリティ ヘッダー内の要素は、部分的に順序付けられています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-293">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="c4e4f-294">セキュリティ ヘッダーの子要素の順序を定義するために、WS-Security Policy では、以下のセキュリティ ヘッダー レイアウト モードが定義されています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-294">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c4e4f-295">高</span><span class="sxs-lookup"><span data-stu-id="c4e4f-295">Strict</span></span>|<span data-ttu-id="c4e4f-296">"使用前に宣言する" という一般的原則に基づき、Security Policy のセクション 7.7.1 に記載された番号付きレイアウト ルールに従って、項目がセキュリティ ヘッダーに追加されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-296">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="c4e4f-297">Lax</span><span class="sxs-lookup"><span data-stu-id="c4e4f-297">Lax</span></span>|<span data-ttu-id="c4e4f-298">WSS: SOAP Message Security に準拠した任意の順序で、項目がセキュリティ ヘッダーに追加されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-298">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="c4e4f-299">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="c4e4f-299">LaxTimestampFirst</span></span>|<span data-ttu-id="c4e4f-300">セキュリティ ヘッダー内の最初の項目が wsse:Timestamp でなければならないという点を除き、Lax と同じです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-300">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="c4e4f-301">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="c4e4f-301">LaxTimestampLast</span></span>|<span data-ttu-id="c4e4f-302">セキュリティ ヘッダー内の最後の項目が wsse:Timestamp でなければならないという点を除き、Lax と同じです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-302">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="c4e4f-303">WCF では、セキュリティヘッダーレイアウトの4つのモードすべてがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-303">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="c4e4f-304">後ほど示す各認証モードのセキュリティ ヘッダーの構造とメッセージの例では、"Strict" モードに従っています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-304">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="c4e4f-305">2. 一般的なメッセージセキュリティパラメーター</span><span class="sxs-lookup"><span data-stu-id="c4e4f-305">2. Common Message Security Parameters</span></span>  

 <span data-ttu-id="c4e4f-306">このセクションでは、各認証モードのポリシーの例、およびクライアントとサービスによって交換されるメッセージのセキュリティ ヘッダーの構造を示す例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-306">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="c4e4f-307">6.1 トランスポートの保護</span><span class="sxs-lookup"><span data-stu-id="c4e4f-307">6.1 Transport Protection</span></span>  

 <span data-ttu-id="c4e4f-308">WCF は、セキュリティで保護されたトランスポートを使用してメッセージを保護する5つの認証モードを提供します。UserNameOverTransport、CertificateOverTransport、KerberosOverTransport、IssuedTokenOverTransport、および SspiNegotiatedOverTransport。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-308">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="c4e4f-309">これらの認証モードは、SecurityPolicy に記載されたトランスポート バインディングを使用して構築されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-309">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="c4e4f-310">UserNameOverTransport 認証モードの場合、UsernameToken は署名付きサポート トークンです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-310">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="c4e4f-311">その他の認証モードでは、トークンは署名付き保証トークンとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-311">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="c4e4f-312">SecurityPolicy の Appendix C.1.2 および C.1.3 には、セキュリティ ヘッダーのレイアウトの詳細が記載されています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-312">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="c4e4f-313">以降のセキュリティ ヘッダーの例は、指定の認証モードの Strict レイアウトを示しています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-313">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="c4e4f-314">すべてのケースで、トークンの "派生キー" プロパティの値は "false" です。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-314">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="c4e4f-315">トランスポート バインディングの各プロパティの値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-315">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="c4e4f-316">タイムスタンプ : true</span><span class="sxs-lookup"><span data-stu-id="c4e4f-316">Timestamp: true</span></span>  
  
 <span data-ttu-id="c4e4f-317">セキュリティ ヘッダーのレイアウト : Strict</span><span class="sxs-lookup"><span data-stu-id="c4e4f-317">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="c4e4f-318">アルゴリズム スイート : Basic256</span><span class="sxs-lookup"><span data-stu-id="c4e4f-318">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="c4e4f-319">6.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="c4e4f-319">6.1.1 UsernameOverTransport</span></span>  

 <span data-ttu-id="c4e4f-320">この認証モードでは、クライアントはユーザー名トークンを使用して認証を行います。ユーザー名トークンは、イニシエーターから受信者に必ず送信される署名付きサポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-320">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="c4e4f-321">サービスはトランスポート層で X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-321">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="c4e4f-322">使用するバインディングは、トランスポート バインディングです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-322">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="c4e4f-323">のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-323">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='UsernameOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:SignedSupportingTokens >  
        <wsp:Policy>  
          <sp:UsernameToken
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:WssUsernameToken10 />
            </wsp:Policy>  
          </sp:UsernameToken>  
        </wsp:Policy>  
      </sp:SignedSupportingTokens>  
      <sp:Wss11 >  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10 >  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="c4e4f-324">セキュリティ ヘッダーのレイアウト</span><span class="sxs-lookup"><span data-stu-id="c4e4f-324">Security Header Layout</span></span>  
  
 <span data-ttu-id="c4e4f-325">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-325">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:UsernameToken>  
  ...  
  </wsse:UsernameToken>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-326">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-326">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="c4e4f-327">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="c4e4f-327">6.1.2 CertificateOverTransport</span></span>  

 <span data-ttu-id="c4e4f-328">この認証モードでは、クライアントは X.509 証明書を使用して認証を行います。X.509 証明書は、イニシエーターから受信者に必ず送信される保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-328">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="c4e4f-329">サービスはトランスポート層で X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-329">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="c4e4f-330">使用するバインディングは、トランスポート バインディングです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-330">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="c4e4f-331">のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-331">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CertificateOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding xmlns:sp='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy' >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
             <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:RequireThumbprintReference />
              <sp:WssX509V3Token10 />
            </wsp:Policy>  
          </sp:X509Token>  
          <sp:SignedParts>  
            <sp:Header Name='To'
Namespace='http://www.w3.org/2005/08/addressing' />
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="c4e4f-332">セキュリティ ヘッダーのレイアウト</span><span class="sxs-lookup"><span data-stu-id="c4e4f-332">Security Header Layout</span></span>  
  
 <span data-ttu-id="c4e4f-333">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-333">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wse:Timestamp u:Id="_0">  
  ...  
  </wse:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-334">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-334">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="c4e4f-335">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="c4e4f-335">6.1.3 IssuedTokenOverTransport</span></span>  

 <span data-ttu-id="c4e4f-336">この認証モードでは、クライアントはサービスに対する認証を行わず、セキュリティ トークン サービス (STS) により発行されたトークンを示すことで、共有キーの有無を示します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-336">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="c4e4f-337">発行されたトークンは、イニシエーターから受信者に必ず送信される保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-337">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="c4e4f-338">サービスはトランスポート層で X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-338">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="c4e4f-339">バインディングはトランスポート バインディングです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-339">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="c4e4f-340">のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-340">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='IssuedTokenOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:IssuedToken
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <sp:RequestSecurityTokenTemplate>  
              <wst:KeyType>  
              http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
              </wst:KeyType>
            </sp:RequestSecurityTokenTemplate>  
            <wsp:Policy>  
              <sp:RequireInternalReference />
            </wsp:Policy>  
          </sp:IssuedToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'
Namespace='http://www.w3.org/2005/08/addressing' />
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="c4e4f-341">セキュリティ ヘッダーのレイアウト</span><span class="sxs-lookup"><span data-stu-id="c4e4f-341">Security Header Layout</span></span>  
  
 <span data-ttu-id="c4e4f-342">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-342">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-343">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-343">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="c4e4f-344">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="c4e4f-344">6.1.4 KerberosOverTransport</span></span>  

 <span data-ttu-id="c4e4f-345">この認証モードを使用すると、クライアントは Kerberos チケットを使用してサービスに対する認証を行います。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-345">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="c4e4f-346">Kerberos トークンは、保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-346">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="c4e4f-347">サービスはトランスポート層で X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-347">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="c4e4f-348">バインディングはトランスポート バインディングです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-348">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="c4e4f-349">のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-349">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='KerberosOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:KerberosToken  
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
            <wsp:Policy>  
              <sp:WssGssKerberosV5ApReqToken11 />
            </wsp:Policy>  
          </sp:KerberosToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'
Namespace='http://www.w3.org/2005/08/addressing' />
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="c4e4f-350">セキュリティ ヘッダーのレイアウト</span><span class="sxs-lookup"><span data-stu-id="c4e4f-350">Security Header Layout</span></span>  
  
 <span data-ttu-id="c4e4f-351">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-351">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken ValueType="...#GSS_Kerberosv5_AP_REQ">  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-352">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-352">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="c4e4f-353">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="c4e4f-353">6.1.5 SspiNegotiatedOverTransport</span></span>  

 <span data-ttu-id="c4e4f-354">このモードでは、ネゴシエーション プロトコルを使用して、クライアントとサーバーの認証を行います。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-354">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="c4e4f-355">Kerberos を使用できる場合は Kerberos が使用され、それ以外の場合は NTLM が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-355">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="c4e4f-356">発行された SCT は、イニシエーターから受信者に必ず送信される保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-356">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="c4e4f-357">サービスは、トランスポート層で X.509 証明書により追加的に認証されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-357">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="c4e4f-358">使用するバインディングは、トランスポート バインディングです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-358">The binding used is a transport binding.</span></span> <span data-ttu-id="c4e4f-359">"SPNEGO" (ネゴシエーション) では、WCF が WS-TRUST で SSPI バイナリネゴシエーションプロトコルを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-359">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="c4e4f-360">このセクションで示すセキュリティ ヘッダーの例は、SPNEGO ハンドシェイクによって SCT が確立された後の状態を示しています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-360">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="c4e4f-361">のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-361">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SspiNegotiatedOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:SpnegoContextToken
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy />
          </sp:SpnegoContextToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'
Namespace='http://www.w3.org/2005/08/addressing' />
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples"></a><span data-ttu-id="c4e4f-362">セキュリティ ヘッダーの例</span><span class="sxs-lookup"><span data-stu-id="c4e4f-362">Security Header Examples</span></span>  

 <span data-ttu-id="c4e4f-363">WS-Trust バイナリ ネゴシエーションを使用して、SPNEGO ハンドシェイクによってセキュリティ コンテキスト トークンが確立されると、アプリケーション メッセージのセキュリティ ヘッダーは、次のような構造になります。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-363">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="c4e4f-364">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-364">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:SecurityContextToken u:Id="uuid-2202746a-7725-453d-8747-809cb718dab0-29" >  
  ...  
  </wssc:SecurityContextToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-365">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-365">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="c4e4f-366">6.2 X.509 証明書を使用したサービス認証</span><span class="sxs-lookup"><span data-stu-id="c4e4f-366">6.2 Using X.509 Certificates for Service Authentication</span></span>  

 <span data-ttu-id="c4e4f-367">このセクションでは、MutualCertificate WSS1.0、Mutual CertificateDuplex、MutualCertificate WSS1.1、AnonymousForCertificate、UserNameForCertificate、および IssuedTokenForCertificate の各認証モードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-367">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="c4e4f-368">6.2.1 MutualCertificate WSS1.0</span><span class="sxs-lookup"><span data-stu-id="c4e4f-368">6.2.1 MutualCertificate WSS1.0</span></span>  

 <span data-ttu-id="c4e4f-369">この認証モードでは、クライアントは X.509 証明書を使用して認証を行います。X.509 証明書は、イニシエーター トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-369">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="c4e4f-370">また、サービスは X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-370">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="c4e4f-371">使用するバインディングは、次のプロパティ値が設定された非対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-371">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="c4e4f-372">イニシエーター トークン : インクルード モードが .../IncludeToken/AlwaysToRecipient に設定されたクライアントの X.509 証明書</span><span class="sxs-lookup"><span data-stu-id="c4e4f-372">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="c4e4f-373">受信者トークン : インクルード モードが …/IncludeToken/Never に設定されたサーバーの X.509 証明書</span><span class="sxs-lookup"><span data-stu-id="c4e4f-373">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="c4e4f-374">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="c4e4f-374">Token Protection: False</span></span>  
  
 <span data-ttu-id="c4e4f-375">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="c4e4f-375">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="c4e4f-376">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="c4e4f-376">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="c4e4f-377">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="c4e4f-377">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="c4e4f-378">のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-378">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificate_WSS10_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="c4e4f-379">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="c4e4f-379">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="c4e4f-380">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-380">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-381">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-381">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-382">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="c4e4f-382">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="c4e4f-383">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-383">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-384">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-384">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="c4e4f-385">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="c4e4f-385">6.2.2 MutualCertificateDuplex</span></span>  

 <span data-ttu-id="c4e4f-386">この認証モードでは、クライアントは X.509 証明書を使用して認証を行います。X.509 証明書は、イニシエーター トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-386">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="c4e4f-387">また、サービスは X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-387">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="c4e4f-388">使用するバインディングは、次のプロパティ値が設定された非対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-388">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="c4e4f-389">イニシエーター トークン : インクルード モードが .../IncludeToken/AlwaysToRecipient に設定されたクライアントの X.509 証明書</span><span class="sxs-lookup"><span data-stu-id="c4e4f-389">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="c4e4f-390">受信者トークン : インクルード モードが .../IncludeToken/AlwaysToInitiator に設定されたサーバーの X509 証明書</span><span class="sxs-lookup"><span data-stu-id="c4e4f-390">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="c4e4f-391">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="c4e4f-391">Token Protection: False</span></span>  
  
 <span data-ttu-id="c4e4f-392">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="c4e4f-392">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="c4e4f-393">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="c4e4f-393">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="c4e4f-394">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="c4e4f-394">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="c4e4f-395">のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-395">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificateDuplex_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToInitiator' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="c4e4f-396">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="c4e4f-396">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="c4e4f-397">要求と応答</span><span class="sxs-lookup"><span data-stu-id="c4e4f-397">Request and Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="c4e4f-398">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="c4e4f-398">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="c4e4f-399">要求と応答</span><span class="sxs-lookup"><span data-stu-id="c4e4f-399">Request and Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="c4e4f-400">6.2.3 X.509 サービス認証での SymmetricBinding の使用</span><span class="sxs-lookup"><span data-stu-id="c4e4f-400">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  

 <span data-ttu-id="c4e4f-401">"WSS10" では、X509 トークンを使用するシナリオのサポートが制限されていました。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-401">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="c4e4f-402">たとえば、サービスの X509 トークンだけを使用して、メッセージの署名と暗号化を保護することはできませんでした。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-402">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="c4e4f-403">"WSS11" では、EncryptedKey を共通鍵トークンとして使用する方法が導入されています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-403">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="c4e4f-404">これにより、サービスの X.509 証明書の暗号化された一時キーを使用して、要求メッセージと応答メッセージの両方を保護できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-404">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="c4e4f-405">セクション 6.4 で説明する認証モードでは、このパターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-405">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="c4e4f-406">WS-SecurityPolicy には、サービスの X509 トークンを保護トークンとして使用して SymmetricBinding を使用するこのパターンが記載されています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-406">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="c4e4f-407">AnonymousForCertificate、UsernameForCertificate、MutualCertificate WSS11、および IssuedTokenForCertificate の各認証モードはすべて、以下のプロパティ値が設定された sp:SymmetricBinding の同様のインスタンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-407">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="c4e4f-408">保護トークン: インクルード モードが .../IncludeToken/Never に設定されたサーバーの X509 証明書</span><span class="sxs-lookup"><span data-stu-id="c4e4f-408">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="c4e4f-409">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="c4e4f-409">Token Protection: False</span></span>  
  
 <span data-ttu-id="c4e4f-410">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="c4e4f-410">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="c4e4f-411">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="c4e4f-411">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="c4e4f-412">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="c4e4f-412">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="c4e4f-413">前述の各認証モードは、使用するサポート トークンだけが異なります。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-413">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="c4e4f-414">AnonymousForCertificate はサポート トークンをまったく使用せず、MutualCertificate WSS 1.1 は保証サポート トークンとしてクライアントの X509 証明書を使用します。また、UserNameForCertificate は署名付きサポート トークンとしてユーザー名トークンを使用し、IssuedTokenForCertificate は保証サポート トークンとして発行済みトークンを使用します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-414">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="c4e4f-415">のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-415">Policy</span></span>  
  
 <span data-ttu-id="c4e4f-416">対称バインディング</span><span class="sxs-lookup"><span data-stu-id="c4e4f-416">Symmetric Binding</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SymmetricCert_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                  <sp:RequireThumbprintReference />
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />  
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting Token Assertions appear here -->  
      ...  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
          <sp:RequireSignatureConfirmation />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="c4e4f-417">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="c4e4f-417">6.2.4 AnonymousForCertificate</span></span>  

 <span data-ttu-id="c4e4f-418">この認証モードでは、クライアントは匿名になり、X.509 証明書を使用してサービスが認証されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-418">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="c4e4f-419">使用するバインディングは、6.4.2 で説明する対称バインディングのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-419">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="c4e4f-420">のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-420">Policy</span></span>  
  
 <span data-ttu-id="c4e4f-421">バインディングの詳細については、前述の 6.2.3 の「ポリシー」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-421">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="c4e4f-422">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="c4e4f-422">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="c4e4f-423">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-423">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-424">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-424">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="c4e4f-425">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="c4e4f-425">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="c4e4f-426">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-426">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-427">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-427">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="c4e4f-428">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="c4e4f-428">6.2.5 UserNameForCertificate</span></span>  

 <span data-ttu-id="c4e4f-429">この認証モードでは、クライアントはユーザー名トークンを使用してサーバーに対する認証を行います。ユーザー名トークンは、署名付きサポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-429">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="c4e4f-430">X.509 証明書を使用したクライアントに対するサービス認証。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-430">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="c4e4f-431">使用するバインディングは、クライアントによって生成され、サービスの公開キーで暗号化されたキーを保護トークンとして使用する対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-431">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="c4e4f-432">のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-432">Policy</span></span>  
  
 <span data-ttu-id="c4e4f-433">バインディングの詳細については、前述の 6.2.3 の「ポリシー」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-433">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="c4e4f-434">署名付きサポート トークン</span><span class="sxs-lookup"><span data-stu-id="c4e4f-434">Signed Supporting Token</span></span>  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="c4e4f-435">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="c4e4f-435">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="c4e4f-436">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-436">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-437">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-437">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="c4e4f-438">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="c4e4f-438">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="c4e4f-439">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-439">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-440">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-440">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="c4e4f-441">6.2.6 MutualCertificate (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="c4e4f-441">6.2.6 MutualCertificate (WSS 1.1)</span></span>  

 <span data-ttu-id="c4e4f-442">この認証モードでは、クライアントは X.509 証明書を使用して認証を行います。X.509 証明書は、保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-442">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="c4e4f-443">また、サービスは X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-443">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="c4e4f-444">使用するバインディングは、クライアントによって生成され、サービスの公開キーで暗号化されたキーを保護トークンとして使用する対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-444">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="c4e4f-445">のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-445">Policy</span></span>  
  
 <span data-ttu-id="c4e4f-446">バインディングの詳細については、前述の 6.2.3 の「ポリシー」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-446">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="c4e4f-447">保証サポート トークン</span><span class="sxs-lookup"><span data-stu-id="c4e4f-447">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />
        <sp:WssX509V3Token10 />
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="c4e4f-448">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="c4e4f-448">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="c4e4f-449">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-449">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-450">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-450">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="c4e4f-451">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="c4e4f-451">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="c4e4f-452">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-452">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-453">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-453">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="c4e4f-454">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="c4e4f-454">6.2.7 IssuedTokenForCertificate</span></span>  

 <span data-ttu-id="c4e4f-455">この認証モードでは、クライアントはサービスに対する認証を行わず、STS により発行されたトークンを示すことで、共有キーの有無を示します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-455">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="c4e4f-456">発行済みトークンは、保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-456">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="c4e4f-457">X.509 証明書を使用したクライアントに対するサービス認証。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-457">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="c4e4f-458">使用するバインディングは、クライアントによって生成され、サービスの公開キーで暗号化されたキーを保護トークンとして使用する対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-458">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="c4e4f-459">のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-459">Policy</span></span>  
  
 <span data-ttu-id="c4e4f-460">バインディングの詳細については、前述の 6.2.3 の「ポリシー」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-460">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="c4e4f-461">保証サポート トークン</span><span class="sxs-lookup"><span data-stu-id="c4e4f-461">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
       </wst:KeyType>  
     </sp:RequestSecurityTokenTemplate>  
     <wsp:Policy>  
       <sp:RequireDerivedKeys />
       <sp:RequireInternalReference />
     </wsp:Policy>  
   </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="c4e4f-462">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="c4e4f-462">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="c4e4f-463">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-463">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-464">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-464">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="c4e4f-465">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="c4e4f-465">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="c4e4f-466">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-466">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-467">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-467">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
## <a name="63-kerberos"></a><span data-ttu-id="c4e4f-468">6.3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="c4e4f-468">6.3 Kerberos</span></span>  

 <span data-ttu-id="c4e4f-469">この認証モードを使用すると、クライアントは Kerberos チケットを使用してサービスに対する認証を行います。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-469">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="c4e4f-470">また、その同じチケットによってサーバーが認証されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-470">That same ticket also provides server authentication.</span></span> <span data-ttu-id="c4e4f-471">使用するバインディングは、以下のプロパティが設定された対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-471">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="c4e4f-472">保護トークン: インクルード モードが .../IncludeToken/Once に設定された Kerberos チケット</span><span class="sxs-lookup"><span data-stu-id="c4e4f-472">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="c4e4f-473">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="c4e4f-473">Token Protection: False</span></span>  
  
 <span data-ttu-id="c4e4f-474">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="c4e4f-474">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="c4e4f-475">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="c4e4f-475">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="c4e4f-476">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="c4e4f-476">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="c4e4f-477">のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-477">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='Kerberos_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:KerberosToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                  <sp:WssGssKerberosV5ApReqToken11 />
                </wsp:Policy>  
              </sp:KerberosToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="c4e4f-478">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="c4e4f-478">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="c4e4f-479">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-479">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-480">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-480">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="c4e4f-481">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="c4e4f-481">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="c4e4f-482">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-482">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-483">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-483">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="c4e4f-484">6.4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="c4e4f-484">6.4 IssuedToken</span></span>  

 <span data-ttu-id="c4e4f-485">この認証モードでは、クライアントはサービスに対する認証を行わず、STS により発行されたトークンを示すことで、共有キーの有無を示します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-485">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="c4e4f-486">サービスはクライアントに対する認証を行いませんが、そのサービスだけがキーを復号化できるように、STS は発行されたトークンの一部として共有キーを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-486">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="c4e4f-487">使用するバインディングは、以下のプロパティが設定された対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-487">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="c4e4f-488">保護トークン: インクルード モードが .../IncludeToken/AlwaysToRecipient に設定された発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="c4e4f-488">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="c4e4f-489">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="c4e4f-489">Token Protection: False</span></span>  
  
 <span data-ttu-id="c4e4f-490">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="c4e4f-490">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="c4e4f-491">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="c4e4f-491">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="c4e4f-492">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="c4e4f-492">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="c4e4f-493">のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-493">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple3_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <sp:RequestSecurityTokenTemplate>  
                  <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
                  </wst:KeyType>
                </sp:RequestSecurityTokenTemplate>  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                  <sp:RequireInternalReference />
                </wsp:Policy>  
              </sp:IssuedToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="c4e4f-494">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="c4e4f-494">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="c4e4f-495">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-495">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-496">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-496">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="c4e4f-497">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="c4e4f-497">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="c4e4f-498">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-498">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-499">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-499">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="c4e4f-500">6.5 SslNegotiated を使用したサービス認証</span><span class="sxs-lookup"><span data-stu-id="c4e4f-500">6.5 Using SslNegotiated for Service Authentication</span></span>  

 <span data-ttu-id="c4e4f-501">このセクションでは、WS-SecureConversation (WS-SC) ごとのセキュリティ コンテキスト トークンである保護トークンと共に、対称バインディングを使用する認証モードのグループについて説明します。WS-SecureConversation (WS-SC) のキー値は、WS-Trust (WS-T) RST/RSTR メッセージで TLS プロトコルを実行することによりネゴシエートされます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-501">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="c4e4f-502">WS-Trust を使用した TLS ハンドシェイク実装の詳細は、TLSNEGO に記述されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-502">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="c4e4f-503">ここで示すメッセージの例は、セキュリティ コンテキストに関連付けられた SCT が、ハンドシェイクによって既に確立されていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-503">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="c4e4f-504">使用するバインディングは、以下のプロパティが設定された対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-504">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="c4e4f-505">保護トークン: インクルード モードが .../IncludeToken/Never に設定された SslContextToken</span><span class="sxs-lookup"><span data-stu-id="c4e4f-505">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="c4e4f-506">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="c4e4f-506">Token Protection: False</span></span>  
  
 <span data-ttu-id="c4e4f-507">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="c4e4f-507">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="c4e4f-508">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="c4e4f-508">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="c4e4f-509">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="c4e4f-509">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="c4e4f-510">6.5.1 SslNegotiated サービス認証のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-510">6.5.1 Policy for SslNegotiated service authentication</span></span>  

 <span data-ttu-id="c4e4f-511">このセクションで説明するすべての認証モードのポリシーは、使用する署名付きサポート トークンまたは保証トークンだけが異なります。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-511">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SslNegotiated_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <mssp:SslContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient'>  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                </wsp:Policy>  
              </mssp:SslContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting token assertions go here -->  
      ..  
      <sp:Wss11>
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="c4e4f-512">6.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="c4e4f-512">6.5.2 AnonymousForSslNegotiated</span></span>  

 <span data-ttu-id="c4e4f-513">この認証モードでは、クライアントは匿名になり、X.509 証明書を使用してサービスが認証されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-513">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="c4e4f-514">使用するバインディングは、前述の 6.5.1 に示した対称バインディングのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-514">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="c4e4f-515">のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-515">Policy</span></span>  
  
 <span data-ttu-id="c4e4f-516">バインディングの詳細については、前述の 6.5.1 の「ポリシー」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-516">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="c4e4f-517">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="c4e4f-517">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="c4e4f-518">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-518">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-519">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-519">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="c4e4f-520">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="c4e4f-520">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="c4e4f-521">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-521">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-522">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-522">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="c4e4f-523">6.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="c4e4f-523">6.5.3 UserNameForSslNegotiated</span></span>  

 <span data-ttu-id="c4e4f-524">この認証モードでは、クライアントはユーザー名トークンを使用して認証を行います。ユーザー名トークンは、署名付きサポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-524">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="c4e4f-525">サービスは X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-525">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="c4e4f-526">使用するバインディングは、6.5.1 で説明した対称バインディングのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-526">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="c4e4f-527">のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-527">Policy</span></span>  
  
 <span data-ttu-id="c4e4f-528">バインディングの詳細については、前述の 6.5.1 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-528">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="c4e4f-529">署名付きサポート トークン</span><span class="sxs-lookup"><span data-stu-id="c4e4f-529">Signed Supporting Token</span></span>  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="c4e4f-530">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="c4e4f-530">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="c4e4f-531">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-531">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-532">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-532">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="c4e4f-533">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="c4e4f-533">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="c4e4f-534">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-534">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-535">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-535">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="c4e4f-536">6.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="c4e4f-536">6.5.4 IssuedTokenForSslNegotiated</span></span>  

 <span data-ttu-id="c4e4f-537">この認証モードでは、クライアントはサービスに対する認証を行わず、STS により発行されたトークンを示すことで、共有キーの有無を示します。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-537">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="c4e4f-538">発行済みトークンは、保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-538">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="c4e4f-539">サービスは X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-539">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="c4e4f-540">使用するバインディングは、前述の 6.5.1 に示した対称バインディングのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-540">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="c4e4f-541">のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-541">Policy</span></span>  
  
 <span data-ttu-id="c4e4f-542">バインディングの詳細については、前述の 6.5.1 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-542">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="c4e4f-543">保証サポート トークン</span><span class="sxs-lookup"><span data-stu-id="c4e4f-543">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
        </wst:KeyType>
      </sp:RequestSecurityTokenTemplate>  
      <wsp:Policy>  
        <sp:RequireDerivedKeys />
        <sp:RequireInternalReference />
      </wsp:Policy>  
    </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="c4e4f-544">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="c4e4f-544">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="c4e4f-545">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-545">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-546">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-546">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="c4e4f-547">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="c4e4f-547">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="c4e4f-548">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-548">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-549">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-549">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="c4e4f-550">6.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="c4e4f-550">6.5.5 MutualSslNegotiated</span></span>  

 <span data-ttu-id="c4e4f-551">この認証モードでは、クライアントとサービスは X.509 証明書を使用して認証を行います。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-551">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="c4e4f-552">使用するバインディングは、前述の 6.5.1 に示した対称バインディングのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-552">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="c4e4f-553">のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-553">Policy</span></span>  
  
 <span data-ttu-id="c4e4f-554">バインディングの詳細については、前述の 6.5.1 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-554">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="c4e4f-555">保証サポート トークン</span><span class="sxs-lookup"><span data-stu-id="c4e4f-555">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />
        <sp:WssX509V3Token10 />
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="c4e4f-556">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="c4e4f-556">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="c4e4f-557">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-557">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-558">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-558">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="c4e4f-559">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="c4e4f-559">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="c4e4f-560">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-560">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-561">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-561">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="c4e4f-562">6.6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="c4e4f-562">6.6 SspiNegotiated</span></span>  

 <span data-ttu-id="c4e4f-563">この認証モードを使用すると、クライアントとサーバーの認証を実行するために、ネゴシエーション プロトコルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-563">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="c4e4f-564">Kerberos を使用できる場合は Kerberos が使用され、それ以外の場合は NTLM が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-564">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="c4e4f-565">使用するバインディングは、以下のプロパティが設定された対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-565">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="c4e4f-566">保護トークン: インクルード モードが .../IncludeToken/AlwaysToRecipient に設定された SpnegoContextToken</span><span class="sxs-lookup"><span data-stu-id="c4e4f-566">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="c4e4f-567">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="c4e4f-567">Token Protection: False</span></span>  
  
 <span data-ttu-id="c4e4f-568">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="c4e4f-568">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="c4e4f-569">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="c4e4f-569">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="c4e4f-570">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="c4e4f-570">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="c4e4f-571">のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-571">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple13_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                </wsp:Policy>  
              </sp:SpnegoContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="c4e4f-572">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="c4e4f-572">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="c4e4f-573">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-573">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-574">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-574">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="c4e4f-575">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="c4e4f-575">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="c4e4f-576">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-576">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-577">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-577">Response</span></span>  
  
```xml  
<wsse:Security>  
<wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="67-secureconversation"></a><span data-ttu-id="c4e4f-578">6.7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="c4e4f-578">6.7 SecureConversation</span></span>  

 <span data-ttu-id="c4e4f-579">使用するバインディングは、WS-SecureConversation (WS-SC) ごとの SCT を保護トークンとして使用する対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-579">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="c4e4f-580">入れ子になったバインディング (このバインディング自体も、ネゴシエーション プロトコルを使用する対称バインディングです) に従い、SCT は WS-Trust (WS-Trust) または WS-SecureConversation (WS-SC) を使用してネゴシエートされます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-580">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="c4e4f-581">ネゴシエーション プロトコルは、可能であれば Kerberos を使用してクライアントとサーバーの認証を行います。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-581">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="c4e4f-582">Kerberos を使用できない場合は、NTLM が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4e4f-582">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="c4e4f-583">のポリシー</span><span class="sxs-lookup"><span data-stu-id="c4e4f-583">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SecureConversation_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SecureConversationToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                  <sp:BootstrapPolicy>  
                    <wsp:Policy>  
                      <sp:SignedParts>  
                        <sp:Body />
                        <sp:Header Name='To' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='From' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='FaultTo' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='ReplyTo' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='MessageID' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='RelatesTo' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='Action' Namespace='http://www.w3.org/2005/08/addressing' />
                      </sp:SignedParts>  
                      <sp:EncryptedParts>  
                        <sp:Body />
                      </sp:EncryptedParts>  
                      <sp:SymmetricBinding>  
                        <wsp:Policy>  
                          <sp:ProtectionToken>  
                            <wsp:Policy>  
                              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                                <wsp:Policy>  
                                  <sp:RequireDerivedKeys />
                                </wsp:Policy>  
                              </sp:SpnegoContextToken>  
                            </wsp:Policy>  
                          </sp:ProtectionToken>  
                          <sp:AlgorithmSuite>  
                            <wsp:Policy>  
                              <sp:Basic256 />
                            </wsp:Policy>  
                          </sp:AlgorithmSuite>  
                          <sp:Layout>  
                            <wsp:Policy>  
                              <sp:Strict />
                            </wsp:Policy>  
                          </sp:Layout>  
                          <sp:IncludeTimestamp />
                          <sp:EncryptSignature />
                          <sp:OnlySignEntireHeadersAndBody />
                        </wsp:Policy>  
                      </sp:SymmetricBinding>  
                      <sp:Wss11>  
                        <wsp:Policy>  
                          <sp:MustSupportRefKeyIdentifier />
                          <sp:MustSupportRefIssuerSerial />
                          <sp:MustSupportRefThumbprint />
                          <sp:MustSupportRefEncryptedKey />
                        </wsp:Policy>  
                      </sp:Wss11>  
                      <sp:Trust10>  
                        <wsp:Policy>  
                          <sp:MustSupportIssuedTokens />
                          <sp:RequireClientEntropy />
                          <sp:RequireServerEntropy />
                        </wsp:Policy>  
                      </sp:Trust10>  
                    </wsp:Policy>  
                  </sp:BootstrapPolicy>  
                </wsp:Policy>  
              </sp:SecureConversationToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="c4e4f-584">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="c4e4f-584">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="c4e4f-585">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-585">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-586">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-586">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="c4e4f-587">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="c4e4f-587">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="c4e4f-588">Request</span><span class="sxs-lookup"><span data-stu-id="c4e4f-588">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="c4e4f-589">Response</span><span class="sxs-lookup"><span data-stu-id="c4e4f-589">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```
