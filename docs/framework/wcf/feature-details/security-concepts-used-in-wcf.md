---
description: 詳細については、「WCF で使用されるセキュリティの概念」を参照してください。
title: WCF で使用されるセキュリティの概要
ms.date: 03/30/2017
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
ms.openlocfilehash: 5ad5b80c69e5dec5675879984fbcd2585b295dd4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779765"
---
# <a name="security-concepts-used-in-wcf"></a><span data-ttu-id="9bed4-103">WCF で使用されるセキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="9bed4-103">Security Concepts Used in WCF</span></span>

<span data-ttu-id="9bed4-104">Windows Communication Foundation (WCF) セキュリティは、さまざまなセキュリティインフラストラクチャで既に使用および展開されている概念に基づいて構築されています。</span><span class="sxs-lookup"><span data-stu-id="9bed4-104">Windows Communication Foundation (WCF) security is built upon concepts already in use and deployed in various security infrastructures.</span></span>  
  
 <span data-ttu-id="9bed4-105">WCF は、Secure Sockets Layer (SSL) over HTTP (HTTPS) などの一部のインフラストラクチャをサポートします。</span><span class="sxs-lookup"><span data-stu-id="9bed4-105">WCF supports some of those infrastructures, such as Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="9bed4-106">ただし、WCF は、SOAP でエンコードされたメッセージに対して、より新しい相互運用可能なセキュリティ標準 (WS-SECURITY など) を実装することで、既存のセキュリティインフラストラクチャをサポートすることを超えています。</span><span class="sxs-lookup"><span data-stu-id="9bed4-106">However, WCF goes beyond supporting existing security infrastructures by implementing newer interoperable security standards (such as WS-Security) over SOAP-encoded messages.</span></span> <span data-ttu-id="9bed4-107">既存の機構と新規の相互運用可能な標準のどちらを使用する場合でも、背後にあるセキュリティ概念に変わりはありません。</span><span class="sxs-lookup"><span data-stu-id="9bed4-107">Whether you are using existing mechanisms or new interoperable standards, the security concepts behind both are the same.</span></span> <span data-ttu-id="9bed4-108">既存のインフラストラクチャおよび新しい標準を支える概念を理解することが、アプリケーションにとって最善のセキュリティ モデルを実装するための要になります。</span><span class="sxs-lookup"><span data-stu-id="9bed4-108">Understanding the concepts behind existing infrastructures and the newer standards is central to implementing the best security model for an application.</span></span>  
  
## <a name="introduction-to-security-for-wcf-web-services"></a><span data-ttu-id="9bed4-109">WCF Web サービスのセキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="9bed4-109">Introduction to Security for WCF Web Services</span></span>  

<span data-ttu-id="9bed4-110">Microsoft のパターンとプラクティスグループでは、 [WCF セキュリティガイド](https://archive.codeplex.com/?p=wcfsecurityguide)と呼ばれる詳細なホワイトペーパーを作成しました。</span><span class="sxs-lookup"><span data-stu-id="9bed4-110">The Microsoft Patterns and Practices group wrote an in-depth white paper called [WCF Security Guide](https://archive.codeplex.com/?p=wcfsecurityguide).</span></span> <span data-ttu-id="9bed4-111">このホワイトペーパーでは、web サービス、主要な WCF セキュリティの概念、イントラネットアプリケーションのシナリオ、およびインターネットアプリケーションのシナリオに関連する基本的なセキュリティの概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="9bed4-111">This white paper describes the fundamental security concepts as they relate to web services, key WCF security concepts, intranet application scenarios, and internet application scenarios.</span></span>  
  
## <a name="industry-wide-security-specifications"></a><span data-ttu-id="9bed4-112">業界標準のセキュリティ仕様</span><span class="sxs-lookup"><span data-stu-id="9bed4-112">Industry-Wide Security Specifications</span></span>  
  
### <a name="public-key-infrastructure"></a><span data-ttu-id="9bed4-113">公開キー基盤</span><span class="sxs-lookup"><span data-stu-id="9bed4-113">Public Key Infrastructure</span></span>  

<span data-ttu-id="9bed4-114">公開キー基盤 (PKI) は、デジタル証明書、証明機関、およびその他の登録機関のシステムであり、公開キー暗号化を使用して、電子取引に関連する各パーティを検証および認証します。</span><span class="sxs-lookup"><span data-stu-id="9bed4-114">Public Key Infrastructure (PKI) is a system of digital certificates, certification authorities, and other registration authorities that verify and authenticate each party involved in an electronic transaction through the use of public-key cryptography.</span></span>
  
### <a name="kerberos-protocol"></a><span data-ttu-id="9bed4-115">Kerberos プロトコル</span><span class="sxs-lookup"><span data-stu-id="9bed4-115">Kerberos Protocol</span></span>  

 <span data-ttu-id="9bed4-116">*Kerberos プロトコル* は、Windows ドメインでユーザーを認証するセキュリティメカニズムを作成するための仕様です。</span><span class="sxs-lookup"><span data-stu-id="9bed4-116">The *Kerberos protocol* is a specification for creating a security mechanism that authenticates users on a Windows domain.</span></span> <span data-ttu-id="9bed4-117">ユーザーはドメイン内の他のエンティティと、セキュリティで保護されたコンテキストを確立できます。</span><span class="sxs-lookup"><span data-stu-id="9bed4-117">It allows a user to establish a secure context with other entities within a domain.</span></span> <span data-ttu-id="9bed4-118">Windows 2000 以降のプラットフォームでは、Kerberos プロトコルが既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="9bed4-118">Windows 2000 and later platforms use the Kerberos protocol by default.</span></span> <span data-ttu-id="9bed4-119">システムの機構を理解することは、イントラネット クライアントと対話するサービスを作成する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9bed4-119">Understanding the mechanisms of the system is useful when creating a service that will interact with intranet clients.</span></span> <span data-ttu-id="9bed4-120">さらに、 *Web Services Security Kerberos バインド* が広く公開されているため、kerberos プロトコルを使用してインターネットクライアントと通信できます (つまり、kerberos プロトコルは相互運用可能です)。</span><span class="sxs-lookup"><span data-stu-id="9bed4-120">In addition, since the *Web Services Security Kerberos Binding* is widely published, you can use the Kerberos protocol to communicate with Internet clients (that is, the Kerberos protocol is interoperable).</span></span> <span data-ttu-id="9bed4-121">Windows で Kerberos プロトコルを実装する方法の詳細については、「  [Microsoft kerberos](/windows/win32/secauthn/microsoft-kerberos)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9bed4-121">For more information about how the Kerberos protocol is implemented in Windows, see  [Microsoft Kerberos](/windows/win32/secauthn/microsoft-kerberos).</span></span>  
  
### <a name="x509-certificates"></a><span data-ttu-id="9bed4-122">X.509 証明書</span><span class="sxs-lookup"><span data-stu-id="9bed4-122">X.509 Certificates</span></span>  

 <span data-ttu-id="9bed4-123">X.509 証明書は、セキュリティ アプリケーションで使用される主要な資格情報の形式です。</span><span class="sxs-lookup"><span data-stu-id="9bed4-123">X.509 certificates are a primary credential form used in security applications.</span></span> <span data-ttu-id="9bed4-124">X.509 証明書の詳細については、「 [X.509 公開キー証明書](/windows/win32/seccertenroll/about-x-509-public-key-certificates)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9bed4-124">For more information on X.509 certificates see [X.509 Public Key Certificates](/windows/win32/seccertenroll/about-x-509-public-key-certificates).</span></span> <span data-ttu-id="9bed4-125">X.509 証明書は証明書ストア内に格納されます。</span><span class="sxs-lookup"><span data-stu-id="9bed4-125">X.509 certificates are stored within a certificate store.</span></span> <span data-ttu-id="9bed4-126">Windows を実行しているコンピューターには、それぞれ目的が異なる数種類の証明書ストアがあります。</span><span class="sxs-lookup"><span data-stu-id="9bed4-126">A computer running Windows has several kinds of certificate stores, each with a different purpose.</span></span> <span data-ttu-id="9bed4-127">さまざまなストアの詳細については、「 [証明書ストア](/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9bed4-127">For more information about the different stores, see [Certificate Stores](/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10)).</span></span>  
  
## <a name="web-services-security-specifications"></a><span data-ttu-id="9bed4-128">Web サービスのセキュリティ仕様</span><span class="sxs-lookup"><span data-stu-id="9bed4-128">Web Services Security Specifications</span></span>  

 <span data-ttu-id="9bed4-129">システム定義のバインディングでは、一般に使用されるさまざまな Web サービスのセキュリティ仕様をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="9bed4-129">The system-defined bindings support many commonly used web services security specifications.</span></span> <span data-ttu-id="9bed4-130">システム指定のバインディングとそれらがサポートする web サービスの仕様の完全な一覧については、「 [System-Provided 相互運用性バインドでサポートされる Web サービスプロトコル](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9bed4-130">For a complete list of system-provided bindings and the web services specifications they support see: [Web Services Protocols Supported by System-Provided Interoperability Bindings](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)</span></span>  
  
## <a name="access-control-mechanisms"></a><span data-ttu-id="9bed4-131">アクセス制御機構</span><span class="sxs-lookup"><span data-stu-id="9bed4-131">Access Control Mechanisms</span></span>  

 <span data-ttu-id="9bed4-132">WCF には、サービスや操作へのアクセスを制御するさまざまな方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="9bed4-132">WCF provides a number of ways to control access to a service or operation.</span></span> <span data-ttu-id="9bed4-133">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="9bed4-133">Among them are</span></span>  
  
1. <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2. <span data-ttu-id="9bed4-134">ASP.NET メンバーシップ プロバイダー</span><span class="sxs-lookup"><span data-stu-id="9bed4-134">ASP.NET Membership Provider</span></span>  
  
3. <span data-ttu-id="9bed4-135">ASP.NET ロール プロバイダー</span><span class="sxs-lookup"><span data-stu-id="9bed4-135">ASP.NET Role Provider</span></span>  
  
4. <span data-ttu-id="9bed4-136">承認マネージャー</span><span class="sxs-lookup"><span data-stu-id="9bed4-136">Authorization Manager</span></span>  
  
5. <span data-ttu-id="9bed4-137">ID モデル</span><span class="sxs-lookup"><span data-stu-id="9bed4-137">Identity Model</span></span>  
  
 <span data-ttu-id="9bed4-138">これらのトピックの詳細については、「」、「 [Access Control メカニズム](access-control-mechanisms.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9bed4-138">For more information on these topics see, [Access Control Mechanisms](access-control-mechanisms.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bed4-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="9bed4-139">See also</span></span>

- [<span data-ttu-id="9bed4-140">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="9bed4-140">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="9bed4-141">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9bed4-141">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
