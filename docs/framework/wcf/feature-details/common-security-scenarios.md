---
description: '詳細情報: 一般的なセキュリティシナリオ'
title: 一般的なセキュリティ シナリオ
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
ms.openlocfilehash: ad4e3964a4a018793653b5eb48b91ca566840abb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743513"
---
# <a name="common-security-scenarios"></a><span data-ttu-id="2f6c0-103">一般的なセキュリティ シナリオ</span><span class="sxs-lookup"><span data-stu-id="2f6c0-103">Common Security Scenarios</span></span>

<span data-ttu-id="2f6c0-104">ここでは、考えられるさまざまなクライアントおよびサービスのセキュリティ構成の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-104">The topics in this section catalog a number of possible client and service security configurations.</span></span> <span data-ttu-id="2f6c0-105">構成はさまざまな要因により異なります。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-105">Configurations vary according to a number of factors.</span></span> <span data-ttu-id="2f6c0-106">たとえば、サービスやクライアントがイントラネット上にあるかどうか、また、セキュリティが Windows とトランスポート (HTTPS など) のどちらで提供されるかなどが考えられます。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-106">For example, whether a service or client is on an intranet, or whether the security is provided by Windows or transport (such as HTTPS).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2f6c0-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2f6c0-107">In This Section</span></span>  

 [<span data-ttu-id="2f6c0-108">セキュリティで保護されていないインターネット環境のクライアントとサービス</span><span class="sxs-lookup"><span data-stu-id="2f6c0-108">Internet Unsecured Client and Service</span></span>](internet-unsecured-client-and-service.md)  
 <span data-ttu-id="2f6c0-109">セキュリティで保護されていないパブリックなクライアントとサービスの例です。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-109">An example of a public, unsecured client and service.</span></span>  
  
 [<span data-ttu-id="2f6c0-110">セキュリティで保護されていないイントラネットのクライアントとサービス</span><span class="sxs-lookup"><span data-stu-id="2f6c0-110">Intranet Unsecured Client and Service</span></span>](intranet-unsecured-client-and-service.md)  
 <span data-ttu-id="2f6c0-111">セキュリティで保護されたプライベートネットワークに関する情報を WCF アプリケーションに提供するために開発された基本的な Windows Communication Foundation (WCF) サービス。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-111">A basic Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span>  
  
 [<span data-ttu-id="2f6c0-112">基本認証でのトランスポート セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2f6c0-112">Transport Security with Basic Authentication</span></span>](transport-security-with-basic-authentication.md)  
 <span data-ttu-id="2f6c0-113">アプリケーションは、カスタム認証を使用して、クライアントにログオンを許可します。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-113">The application allows clients to log on using custom authentication.</span></span>  
  
 [<span data-ttu-id="2f6c0-114">トランスポート セキュリティと Windows 認証</span><span class="sxs-lookup"><span data-stu-id="2f6c0-114">Transport Security with Windows Authentication</span></span>](transport-security-with-windows-authentication.md)  
 <span data-ttu-id="2f6c0-115">Windows セキュリティによってセキュリティ保護されたクライアントとサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-115">Shows a client and service secured by Windows security.</span></span>  
  
 [<span data-ttu-id="2f6c0-116">トランスポート セキュリティと匿名クライアント</span><span class="sxs-lookup"><span data-stu-id="2f6c0-116">Transport Security with an Anonymous Client</span></span>](transport-security-with-an-anonymous-client.md)  
 <span data-ttu-id="2f6c0-117">このシナリオでは HTTPS などのようなトランスポート セキュリティを使用して、機密性と整合性を強化します。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-117">This scenario uses transport security (such as HTTPS) to ensure confidentiality and integrity.</span></span>  
  
 [<span data-ttu-id="2f6c0-118">トランスポート セキュリティと証明書認証</span><span class="sxs-lookup"><span data-stu-id="2f6c0-118">Transport Security with Certificate Authentication</span></span>](transport-security-with-certificate-authentication.md)  
 <span data-ttu-id="2f6c0-119">証明書によってセキュリティ保護されたクライアントとサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-119">Shows a client and service secured by a certificate.</span></span>  
  
 [<span data-ttu-id="2f6c0-120">メッセージ セキュリティと匿名クライアント</span><span class="sxs-lookup"><span data-stu-id="2f6c0-120">Message Security with an Anonymous Client</span></span>](message-security-with-an-anonymous-client.md)  
 <span data-ttu-id="2f6c0-121">WCF メッセージセキュリティによってセキュリティ保護されたクライアントとサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-121">Shows a client and service secured by WCF message security.</span></span>  
  
 [<span data-ttu-id="2f6c0-122">ユーザー名クライアントを使用したメッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2f6c0-122">Message Security with a User Name Client</span></span>](message-security-with-a-user-name-client.md)  
 <span data-ttu-id="2f6c0-123">クライアントは、ドメイン ユーザー名とパスワードを使用してクライアントのログオンを許可する Windows フォーム アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-123">The client is a Windows Forms application that allows clients to log on using a domain user name and password.</span></span>  
  
 [<span data-ttu-id="2f6c0-124">メッセージ セキュリティと証明書クライアント</span><span class="sxs-lookup"><span data-stu-id="2f6c0-124">Message Security with a Certificate Client</span></span>](message-security-with-a-certificate-client.md)  
 <span data-ttu-id="2f6c0-125">サーバー側の証明書は複数あり、クライアント側の証明書はそれぞれ 1 つです。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-125">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="2f6c0-126">セキュリティのコンテキストは、トランスポート層セキュリティ (TLS: Transport Layer Security) ネゴシエーションを介して確立されます。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-126">A security context is established through Transport Layer Security (TLS) negotiation.</span></span>  
  
 [<span data-ttu-id="2f6c0-127">Windows クライアントとのメッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2f6c0-127">Message Security with a Windows Client</span></span>](message-security-with-a-windows-client.md)  
 <span data-ttu-id="2f6c0-128">証明書クライアントのバリエーションの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-128">A variation of the certificate client.</span></span> <span data-ttu-id="2f6c0-129">サーバー側の証明書は複数あり、クライアント側の証明書はそれぞれ 1 つです。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-129">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="2f6c0-130">セキュリティのコンテキストは TLS ネゴシエーションを介して確立されます。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-130">A security context is established through TLS negotiation.</span></span>  
  
 [<span data-ttu-id="2f6c0-131">資格情報ネゴシエーションを使用しない Windows クライアントを使用するメッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2f6c0-131">Message Security with a Windows Client without Credential Negotiation</span></span>](message-security-with-a-windows-client-without-credential-negotiation.md)  
 <span data-ttu-id="2f6c0-132">Kerberos ドメインによってセキュリティ保護されたクライアントとサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-132">Shows a client and service secured by a Kerberos domain.</span></span>  
  
 [<span data-ttu-id="2f6c0-133">メッセージ セキュリティと相互の証明書</span><span class="sxs-lookup"><span data-stu-id="2f6c0-133">Message Security with Mutual Certificates</span></span>](message-security-with-mutual-certificates.md)  
 <span data-ttu-id="2f6c0-134">サーバー側の証明書は複数あり、クライアント側の証明書はそれぞれ 1 つです。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-134">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="2f6c0-135">サーバーの証明書はアプリケーションと共に配布され、帯域外でも使用可能です。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-135">The server certificate is distributed with the application and is available out of band.</span></span>  
  
 [<span data-ttu-id="2f6c0-136">発行済みトークンを使用したメッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2f6c0-136">Message Security with Issued Tokens</span></span>](message-security-with-issued-tokens.md)  
 <span data-ttu-id="2f6c0-137">フェデレーション セキュリティにより独立したドメイン間で信頼を確立できます。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-137">Federated security that enables the establishment of trust between independent domains.</span></span>  
  
 [<span data-ttu-id="2f6c0-138">信頼できるサブシステム</span><span class="sxs-lookup"><span data-stu-id="2f6c0-138">Trusted Subsystem</span></span>](trusted-subsystem.md)  
 <span data-ttu-id="2f6c0-139">クライアントは、ネットワーク全体に分散している 1 つ以上の Web サービスにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-139">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="2f6c0-140">Web サービスは、セキュリティで保護する必要がある追加のリソース (データベースや他の Web サービスなど) にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2f6c0-140">The Web services access additional resources (such as databases or other Web services) that must be secured.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2f6c0-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f6c0-141">Reference</span></span>  

 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="2f6c0-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f6c0-142">Related Sections</span></span>  

 [<span data-ttu-id="2f6c0-143">承認</span><span class="sxs-lookup"><span data-stu-id="2f6c0-143">Authorization</span></span>](authorization-in-wcf.md)  
  
 [<span data-ttu-id="2f6c0-144">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="2f6c0-144">Security Overview</span></span>](security-overview.md)  
  
 [<span data-ttu-id="2f6c0-145">Security</span><span class="sxs-lookup"><span data-stu-id="2f6c0-145">Security</span></span>](security.md)  
  
 [<span data-ttu-id="2f6c0-146">バインディングとセキュリティ</span><span class="sxs-lookup"><span data-stu-id="2f6c0-146">Bindings and Security</span></span>](bindings-and-security.md)  
  
 [<span data-ttu-id="2f6c0-147">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="2f6c0-147">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
  
 [<span data-ttu-id="2f6c0-148">認証</span><span class="sxs-lookup"><span data-stu-id="2f6c0-148">Authentication</span></span>](authentication-in-wcf.md)  
  
 [<span data-ttu-id="2f6c0-149">承認</span><span class="sxs-lookup"><span data-stu-id="2f6c0-149">Authorization</span></span>](authorization-in-wcf.md)  
  
 [<span data-ttu-id="2f6c0-150">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="2f6c0-150">Federation and Issued Tokens</span></span>](federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="2f6c0-151">監査</span><span class="sxs-lookup"><span data-stu-id="2f6c0-151">Auditing</span></span>](auditing-security-events.md)  
  
## <a name="see-also"></a><span data-ttu-id="2f6c0-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f6c0-152">See also</span></span>

- [<span data-ttu-id="2f6c0-153">セキュリティ ガイドラインとベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="2f6c0-153">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)
- <span data-ttu-id="2f6c0-154">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="2f6c0-154">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
