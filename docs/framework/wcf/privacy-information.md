---
description: '詳細情報: Windows Communication Foundation のプライバシー情報'
title: Windows Communication Foundation のプライバシー情報
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: 4f942e84a072d15a12b6db7cc2c310d629a59f6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726690"
---
# <a name="windows-communication-foundation-privacy-information"></a><span data-ttu-id="e261c-103">Windows Communication Foundation のプライバシー情報</span><span class="sxs-lookup"><span data-stu-id="e261c-103">Windows Communication Foundation Privacy Information</span></span>

<span data-ttu-id="e261c-104">Microsoft は、エンドユーザーのプライバシーの保護に努めています。</span><span class="sxs-lookup"><span data-stu-id="e261c-104">Microsoft is committed to protecting end user privacy.</span></span> <span data-ttu-id="e261c-105">Windows Communication Foundation (WCF) バージョン3.0 を使用してアプリケーションをビルドすると、アプリケーションがエンドユーザーのプライバシーに影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e261c-105">When you build an application using Windows Communication Foundation (WCF), version 3.0, your application may impact your end users' privacy.</span></span> <span data-ttu-id="e261c-106">たとえば、アプリケーションが明示的にユーザーの連絡先情報を収集することがあります。つまり、アプリケーションがインターネットを経由して Web サイトに情報を要求したり、情報を送信したりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="e261c-106">For example, your application may explicitly collect user contact information, or it may request or send information over the Internet to your Web site.</span></span> <span data-ttu-id="e261c-107">マイクロソフトの技術をアプリケーションに組み込んでいる場合、その技術にプライバシーに影響を与える可能性がある独自の動作が存在することがあります。</span><span class="sxs-lookup"><span data-stu-id="e261c-107">If you embed Microsoft technology in your application, that technology may have its own behavior that might affect privacy.</span></span> <span data-ttu-id="e261c-108">WCF は、お客様またはエンドユーザーが Microsoft に送信することを選択しない限り、アプリケーションからマイクロソフトに情報を送信しません。</span><span class="sxs-lookup"><span data-stu-id="e261c-108">WCF does not send any information to Microsoft from your application unless you or the end user choose to send it to us.</span></span>  
  
## <a name="wcf-in-brief"></a><span data-ttu-id="e261c-109">WCF の概要</span><span class="sxs-lookup"><span data-stu-id="e261c-109">WCF in Brief</span></span>  

 <span data-ttu-id="e261c-110">WCF は、開発者が分散アプリケーションを構築できるようにする Microsoft .NET Framework を使用する分散メッセージングフレームワークです。</span><span class="sxs-lookup"><span data-stu-id="e261c-110">WCF is a distributed messaging framework using the Microsoft .NET Framework that allows developers to build distributed applications.</span></span> <span data-ttu-id="e261c-111">2 つのアプリケーション間で交換されるメッセージには、ヘッダーと本文情報が入ります。</span><span class="sxs-lookup"><span data-stu-id="e261c-111">Messages communicated between two applications contain header and body information.</span></span>  
  
 <span data-ttu-id="e261c-112">ヘッダーには、アプリケーションが使用するサービスに応じて、メッセージ ルーティング、セキュリティ情報、トランザクションなどの情報が追加されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-112">Headers may contain message routing, security information, transactions, and more depending on the services used by the application.</span></span> <span data-ttu-id="e261c-113">メッセージは、通常、既定で暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-113">Messages are typically encrypted by default.</span></span> <span data-ttu-id="e261c-114">ただし、`BasicHttpBinding` を使用する場合は例外です。このバインディングは、セキュリティで保護されていない従来の Web サービスで使用するために設計されています。</span><span class="sxs-lookup"><span data-stu-id="e261c-114">The one exception is when using the `BasicHttpBinding`, which was designed for use with non-secured, legacy Web services.</span></span> <span data-ttu-id="e261c-115">アプリケーションの設計者であるユーザーには最終設計に対する責任があります。</span><span class="sxs-lookup"><span data-stu-id="e261c-115">As the application designer, you are responsible for the final design.</span></span> <span data-ttu-id="e261c-116">SOAP 本文内のメッセージには、アプリケーション固有のデータが含まれます。ただし、アプリケーションによって定義された個人情報など、このデータは、WCF 暗号化機能または機密性機能を使用してセキュリティで保護することができます。</span><span class="sxs-lookup"><span data-stu-id="e261c-116">Messages in the SOAP body contain application-specific data; however, this data, such as application-defined personal information, can be secured by using WCF encryption or confidentiality features.</span></span> <span data-ttu-id="e261c-117">次のセクションでは、プライバシーに影響を与える可能性がある機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="e261c-117">The following sections describe the features that potentially impact privacy.</span></span>  
  
## <a name="messaging"></a><span data-ttu-id="e261c-118">メッセージング</span><span class="sxs-lookup"><span data-stu-id="e261c-118">Messaging</span></span>  

 <span data-ttu-id="e261c-119">各 WCF メッセージには、メッセージの送信先と応答の送信先を指定するアドレスヘッダーがあります。</span><span class="sxs-lookup"><span data-stu-id="e261c-119">Each WCF message has an address header that specifies the message destination and where the reply should go.</span></span>  
  
 <span data-ttu-id="e261c-120">エンドポイント アドレスのアドレス構成要素は、エンドポイントを識別する URI (Uniform Resource Identifier) です。</span><span class="sxs-lookup"><span data-stu-id="e261c-120">The address component of an endpoint address is a Uniform Resource Identifier (URI) that identifies the endpoint.</span></span> <span data-ttu-id="e261c-121">このアドレスは、ネットワーク アドレスまたは論理アドレスのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="e261c-121">The address can be a network address or a logical address.</span></span> <span data-ttu-id="e261c-122">アドレスには、コンピューター名 (ホスト名、完全修飾ドメイン名) と IP アドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-122">The address may include machine name (hostname, fully qualified domain name) and an IP address.</span></span> <span data-ttu-id="e261c-123">また、エンドポイント アドレスには、グローバル一意識別子 (GUID)、または各アドレスを識別するために使用される一時アドレス指定用に GUID のコレクションを入れることもできます。</span><span class="sxs-lookup"><span data-stu-id="e261c-123">The endpoint address may also contain a globally unique identifier (GUID), or a collection of GUIDs for temporary addressing used to discern each address.</span></span> <span data-ttu-id="e261c-124">各メッセージには、GUID 形式のメッセージ ID があります。</span><span class="sxs-lookup"><span data-stu-id="e261c-124">Each message contains a message ID that is a GUID.</span></span> <span data-ttu-id="e261c-125">この機能は、WS-Addressing 参照仕様に準拠します。</span><span class="sxs-lookup"><span data-stu-id="e261c-125">This feature follows the WS-Addressing reference standard.</span></span>  
  
 <span data-ttu-id="e261c-126">WCF メッセージングレイヤーは、個人情報をローカルコンピューターに書き込みません。</span><span class="sxs-lookup"><span data-stu-id="e261c-126">The WCF messaging layer does not write any personal information to the local machine.</span></span> <span data-ttu-id="e261c-127">ただし、サービスの開発者が個人情報を公開するサービスを作成した場合は、ネットワーク レベルで個人情報を公開することがあります。このような例として、エンドポイント名に個人名を使用している場合や、エンドポイントの Web サービス記述言語に個人情報を追加しても、https を使用して WSDL にアクセスすることをクライアントに要求しない場合などがあります。</span><span class="sxs-lookup"><span data-stu-id="e261c-127">However, it might propagate personal information at the network level if a service developer has created a service that exposes such information (for example, by using a person's name in an endpoint name, or including personal information in the endpoint's Web Services Description Language but not requiring clients to use https to access the WSDL).</span></span> <span data-ttu-id="e261c-128">また、開発者が個人情報を公開するエンドポイントに対して [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) ツールを実行した場合、ツールの出力にその情報が含まれている可能性があり、出力ファイルはローカルハードディスクに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="e261c-128">Also, if a developer runs the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) tool against an endpoint that exposes personal information, the tool's output could contain that information, and the output file is written to the local hard disk.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="e261c-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="e261c-129">Hosting</span></span>  

 <span data-ttu-id="e261c-130">WCF のホスティング機能を使用すると、アプリケーションをオンデマンドで開始したり、複数のアプリケーション間でポートの共有を有効にしたりできます。</span><span class="sxs-lookup"><span data-stu-id="e261c-130">The hosting feature in WCF allows applications to start on demand or to enable port sharing between multiple applications.</span></span> <span data-ttu-id="e261c-131">WCF アプリケーションは、ASP.NET と同様にインターネットインフォメーションサービス (IIS) でホストできます。</span><span class="sxs-lookup"><span data-stu-id="e261c-131">A WCF application can be hosted in Internet Information Services (IIS), similar to ASP.NET.</span></span>  
  
 <span data-ttu-id="e261c-132">ホストでは、特定の情報をネットワークに公開せず、コンピューター上にデータを格納しません。</span><span class="sxs-lookup"><span data-stu-id="e261c-132">Hosting does not expose any specific information on the network and it does not keep data on the machine.</span></span>  
  
## <a name="message-security"></a><span data-ttu-id="e261c-133">メッセージのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="e261c-133">Message Security</span></span>  

 <span data-ttu-id="e261c-134">WCF セキュリティは、メッセージングアプリケーションのセキュリティ機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="e261c-134">WCF security provides the security capabilities for messaging applications.</span></span> <span data-ttu-id="e261c-135">提供するセキュリティ機能には、認証と承認があります。</span><span class="sxs-lookup"><span data-stu-id="e261c-135">The security functions provided include authentication and authorization.</span></span>  
  
 <span data-ttu-id="e261c-136">認証は、クライアントとサービスとの間で資格情報を交換することによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-136">Authentication is performed by passing credentials between the clients and services.</span></span> <span data-ttu-id="e261c-137">認証は、次のように、トランスポート レベルのセキュリティまたは SOAP メッセージ レベルのセキュリティで実行できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-137">Authentication can be either through transport-level security or through SOAP message-level security, as follows:</span></span>  
  
- <span data-ttu-id="e261c-138">SOAP メッセージ セキュリティでは、発行者に応じて、ユーザー名とパスワード、X.509 証明書、Kerberos チケット、SAML トークンのような資格情報を使用して認証が実行されます。このすべての資格情報は、個人情報を含んでいる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e261c-138">In SOAP message security, authentication is performed through credentials like username/passwords, X.509 certificates, Kerberos tickets, and SAML tokens, all of which might contain personal information, depending on the issuer.</span></span>  
  
- <span data-ttu-id="e261c-139">トランスポート セキュリティでは、HTTP 認証方式 (Basic、Digest、Negotiate、Integrated Windows Authorization、NTLM、None、および Anonymous) のような従来のトランスポート認証機構によって認証が実行されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-139">Using transport security, authentication is done through traditional transport authentication mechanisms like HTTP authentication schemes (Basic, Digest, Negotiate, Integrated Windows Authorization, NTLM, None, and Anonymous), and form authentication.</span></span>  
  
 <span data-ttu-id="e261c-140">認証によって、通信するエンドポイント間にセキュリティで保護されたセッションを確立できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-140">Authentication can result in a secure session established between the communicating endpoints.</span></span> <span data-ttu-id="e261c-141">このセッションは、セキュリティ セッションの有効期間が切れるまで有効な GUID によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-141">The session is identified by a GUID that lasts the lifetime of the security session.</span></span> <span data-ttu-id="e261c-142">格納されるデータと格納場所を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="e261c-142">The following table shows what is kept and where.</span></span>  
  
|<span data-ttu-id="e261c-143">データ</span><span class="sxs-lookup"><span data-stu-id="e261c-143">Data</span></span>|<span data-ttu-id="e261c-144">ストレージ</span><span class="sxs-lookup"><span data-stu-id="e261c-144">Storage</span></span>|  
|----------|-------------|  
|<span data-ttu-id="e261c-145">ユーザー名、X.509 証明書、Kerberos トークンなどのプレゼンテーション資格情報、および資格情報への参照</span><span class="sxs-lookup"><span data-stu-id="e261c-145">Presentation credentials, such as username, X.509 certificates, Kerberos tokens, and references to credentials.</span></span>|<span data-ttu-id="e261c-146">Windows 証明書ストアなど、標準の Windows 資格情報管理機構</span><span class="sxs-lookup"><span data-stu-id="e261c-146">Standard Windows credential management mechanisms such as the Windows certificate store.</span></span>|  
|<span data-ttu-id="e261c-147">ユーザー名とパスワードなど、ユーザーのメンバーシップ情報</span><span class="sxs-lookup"><span data-stu-id="e261c-147">User membership information, such as usernames and passwords.</span></span>|<span data-ttu-id="e261c-148">ASP.NET メンバーシッププロバイダー。</span><span class="sxs-lookup"><span data-stu-id="e261c-148">ASP.NET membership providers.</span></span>|  
|<span data-ttu-id="e261c-149">クライアントに対するサービスの認証に使用されるサービスの ID 情報</span><span class="sxs-lookup"><span data-stu-id="e261c-149">Identity information about the service used to authenticate the service to clients.</span></span>|<span data-ttu-id="e261c-150">サービスのエンドポイント アドレス</span><span class="sxs-lookup"><span data-stu-id="e261c-150">Endpoint address of the service.</span></span>|  
|<span data-ttu-id="e261c-151">呼び出し元情報</span><span class="sxs-lookup"><span data-stu-id="e261c-151">Caller information.</span></span>|<span data-ttu-id="e261c-152">監査ログ</span><span class="sxs-lookup"><span data-stu-id="e261c-152">Auditing logs.</span></span>|  
  
## <a name="auditing"></a><span data-ttu-id="e261c-153">監査</span><span class="sxs-lookup"><span data-stu-id="e261c-153">Auditing</span></span>  

 <span data-ttu-id="e261c-154">監査では、認証イベントと承認イベントの成功と失敗を記録します。</span><span class="sxs-lookup"><span data-stu-id="e261c-154">Auditing records the success and failure of authentication and authorization events.</span></span> <span data-ttu-id="e261c-155">監査レコードには、サービス URI、アクション URI、および呼び出し元の ID が入ります。</span><span class="sxs-lookup"><span data-stu-id="e261c-155">Auditing records contain the following data: service URI, action URI, and the caller's identification.</span></span>  
  
 <span data-ttu-id="e261c-156">また、監査では、管理者がメッセージ ログの設定 (オンまたはオフ) を変更した時刻を記録します。その理由は、メッセージ ログが、ヘッダーと本文のアプリケーション固有のデータをログに記録する可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="e261c-156">Auditing also records when the administrator modifies the configuration of message logging (turning it on or off), because message logging may log application-specific data in headers and bodies.</span></span> <span data-ttu-id="e261c-157">Windows XP では、レコードはアプリケーションイベントログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-157">For Windows XP, a record is logged in the application event log.</span></span> <span data-ttu-id="e261c-158">Windows Vista および Windows Server 2003 では、レコードがセキュリティイベントログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-158">For Windows Vista and Windows Server 2003, a record is logged in the security event log.</span></span>  
  
## <a name="transactions"></a><span data-ttu-id="e261c-159">トランザクション</span><span class="sxs-lookup"><span data-stu-id="e261c-159">Transactions</span></span>  

 <span data-ttu-id="e261c-160">トランザクション機能は、WCF アプリケーションにトランザクションサービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="e261c-160">The transactions feature provides transactional services to a WCF application.</span></span>  
  
 <span data-ttu-id="e261c-161">トランザクションの伝達で使用されるトランザクション ヘッダーには、GUID 形式のトランザクション ID または登録リスト ID を追加できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-161">Transaction headers used in transaction propagation may contain Transaction IDs or Enlistment IDs, which are GUIDs.</span></span>  
  
 <span data-ttu-id="e261c-162">トランザクション機能では、Microsoft 分散トランザクション コーディネーター (MSDTC) トランザクション マネージャー (Windows コンポーネントの 1 つ) を使用して、トランザクション状態を管理します。</span><span class="sxs-lookup"><span data-stu-id="e261c-162">The Transactions feature uses the Microsoft Distributed Transaction Coordinator (MSDTC) Transaction Manager (a Windows component) to manage transaction state.</span></span> <span data-ttu-id="e261c-163">既定では、トランザクション マネージャー間の通信は暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-163">By default, communications between Transactions Managers are encrypted.</span></span> <span data-ttu-id="e261c-164">トランザクション マネージャーは、エンドポイント参照、トランザクション ID、および登録リスト ID を永続状態の一部としてログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-164">Transaction Managers may log endpoint references, Transaction IDs, and Enlistment IDs as part of their durable state.</span></span> <span data-ttu-id="e261c-165">この状態の有効期間は、トランザクション マネージャーのログ ファイルの有効期間によって決まります。</span><span class="sxs-lookup"><span data-stu-id="e261c-165">The lifetime of this state is determined by the lifetime of the Transaction Manager’s log file.</span></span> <span data-ttu-id="e261c-166">MSDTC サービスがこのログを所有し、管理します。</span><span class="sxs-lookup"><span data-stu-id="e261c-166">The MSDTC service owns and maintains this log.</span></span>  
  
 <span data-ttu-id="e261c-167">トランザクション機能は、WS-Coordination 仕様と WS-AtomicTransaction 仕様を実装します。</span><span class="sxs-lookup"><span data-stu-id="e261c-167">The Transactions feature implements the WS-Coordination and WS-Atomic Transaction standards.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="e261c-168">信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="e261c-168">Reliable Sessions</span></span>  

 <span data-ttu-id="e261c-169">WCF の信頼できるセッションでは、トランスポートまたは中継エラーが発生したときにメッセージが転送されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-169">Reliable sessions in WCF provide the transfer of messages when transport or intermediary failures occur.</span></span> <span data-ttu-id="e261c-170">信頼できるセッションは、基になるトランスポート (たとえば、ワイヤレス ネットワーク上の TCP 接続) が切断している場合やメッセージを紛失した場合 (HTTP プロキシでの送受信メッセージの破棄) でも、正確に 1 回のメッセージ転送を実行します。</span><span class="sxs-lookup"><span data-stu-id="e261c-170">They provide an exactly-once transfer of messages even when the underlying transport disconnects (for example, a TCP connection on a wireless network) or loses a message (an HTTP proxy dropping an outgoing or incoming message).</span></span> <span data-ttu-id="e261c-171">また、メッセージが送信された順序を維持するので、メッセージの並べ替え (マルチパス ルーティングの場合に発生する可能性がある) を回復できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-171">Reliable sessions also recover message reordering (as may happen in the case of multipath routing), preserving the order in which the messages were sent.</span></span>  
  
 <span data-ttu-id="e261c-172">信頼できるセッションは、WS-ReliableMessaging (WS-RM) プロトコルを使用して実装されています。</span><span class="sxs-lookup"><span data-stu-id="e261c-172">Reliable sessions are implemented using the WS-ReliableMessaging (WS-RM) protocol.</span></span> <span data-ttu-id="e261c-173">これによって追加される WS-RM ヘッダーには、特定の信頼できるセッションに関連付けられたすべてのメッセージの識別に使用されるセッション情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e261c-173">They add WS-RM headers that contain session information, which is used to identify all messages associated with a particular reliable session.</span></span> <span data-ttu-id="e261c-174">各 WS-RM セッションには、GUID 形式の識別子があります。</span><span class="sxs-lookup"><span data-stu-id="e261c-174">Each WS-RM session has an identifier, which is a GUID.</span></span>  
  
 <span data-ttu-id="e261c-175">エンドユーザーのコンピューターには、個人情報は保持されません。</span><span class="sxs-lookup"><span data-stu-id="e261c-175">No personal information is retained on the end user's machine.</span></span>  
  
## <a name="queued-channels"></a><span data-ttu-id="e261c-176">キューに置かれたチャネル</span><span class="sxs-lookup"><span data-stu-id="e261c-176">Queued Channels</span></span>  

 <span data-ttu-id="e261c-177">キューは、送信元アプリケーションが送ったメッセージを受信側アプリケーションに代わって保存しておき、後で受信側アプリケーションに転送します。</span><span class="sxs-lookup"><span data-stu-id="e261c-177">Queues store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span> <span data-ttu-id="e261c-178">受信側アプリケーションが一時的な場合なども、キューによって、送信元アプリケーションから受信側アプリケーションへのメッセージの転送を確実に実行できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-178">They help ensure the transfer of messages from sending applications to receiving applications when, for example, the receiving application is transient.</span></span> <span data-ttu-id="e261c-179">WCF では、トランスポートとして Microsoft Message Queuing (MSMQ) を使用したキューのサポートを提供しています。</span><span class="sxs-lookup"><span data-stu-id="e261c-179">WCF provides support for queuing by using Microsoft Message Queuing (MSMQ) as a transport.</span></span>  
  
 <span data-ttu-id="e261c-180">キューに置かれたチャネル機能では、ヘッダーをメッセージに追加しません。</span><span class="sxs-lookup"><span data-stu-id="e261c-180">The queued channels feature does not add headers to a message.</span></span> <span data-ttu-id="e261c-181">代わりに、適切なメッセージ キューのメッセージ プロパティ セットを備えたメッセージ キューのメッセージを作成し、メッセージ キューのメソッドを呼び出して、メッセージ キューのキューにメッセージを追加します。</span><span class="sxs-lookup"><span data-stu-id="e261c-181">Instead it creates a Message Queuing message with appropriate Message Queuing message properties set, and invokes Message Queuing methods to put the message in the Message Queuing queue.</span></span> <span data-ttu-id="e261c-182">メッセージ キューは、Windows に付属しているオプション コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="e261c-182">Message Queuing is an optional component that ships with Windows.</span></span>  
  
 <span data-ttu-id="e261c-183">キューに置かれたチャネル機能によってエンドユーザーのコンピューターに保持される情報はありません。これは、メッセージキューをキューインフラストラクチャとして使用するためです。</span><span class="sxs-lookup"><span data-stu-id="e261c-183">No information is retained on the end user's machine by the queued channels feature, because it uses Message Queuing as the queuing infrastructure.</span></span>  
  
## <a name="com-integration"></a><span data-ttu-id="e261c-184">COM+ 統合</span><span class="sxs-lookup"><span data-stu-id="e261c-184">COM+ Integration</span></span>  

 <span data-ttu-id="e261c-185">この機能は、既存の COM および COM + 機能をラップして、WCF サービスと互換性のあるサービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e261c-185">This feature wraps existing COM and COM+ functionality to create services that are compatible with WCF services.</span></span> <span data-ttu-id="e261c-186">この機能は、特定のヘッダーを使用せず、エンドユーザーのコンピューター上のデータを保持しません。</span><span class="sxs-lookup"><span data-stu-id="e261c-186">This feature does not use specific headers and it does not retain data on the end user's machine.</span></span>  
  
## <a name="com-service-moniker"></a><span data-ttu-id="e261c-187">COM サービス モニカー</span><span class="sxs-lookup"><span data-stu-id="e261c-187">COM Service Moniker</span></span>  

 <span data-ttu-id="e261c-188">これにより、標準の WCF クライアントにアンマネージラッパーが提供されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-188">This provides an unmanaged wrapper to a standard WCF client.</span></span> <span data-ttu-id="e261c-189">この機能は、ネットワーク上で特定のヘッダーを使用せず、コンピューターにデータを保持しません。</span><span class="sxs-lookup"><span data-stu-id="e261c-189">This feature does not have specific headers on the wire nor does it persist data on the machine.</span></span>  
  
## <a name="peer-channel"></a><span data-ttu-id="e261c-190">ピア チャネル</span><span class="sxs-lookup"><span data-stu-id="e261c-190">Peer Channel</span></span>  

 <span data-ttu-id="e261c-191">ピアチャネルを使用すると、WCF を使用してマルチパーティアプリケーションを開発できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-191">A peer channel enables development of multiparty applications using WCF.</span></span> <span data-ttu-id="e261c-192">マルチパーティ メッセージングはメッシュのコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-192">Multiparty messaging occurs in the context of a mesh.</span></span> <span data-ttu-id="e261c-193">メッシュは、ノードが参加できる名前によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-193">Meshes are identified by a name that nodes can join.</span></span> <span data-ttu-id="e261c-194">ピア チャネル内の各ノードは、ユーザー指定のポートで TCP リスナーを作成し、メッシュ内の他のノードとの接続を確立することによって、回復力を確保します。</span><span class="sxs-lookup"><span data-stu-id="e261c-194">Each node in the peer channel creates a TCP listener at a user-specified port and establishes connections with other nodes in the mesh to ensure resiliency.</span></span> <span data-ttu-id="e261c-195">メッシュ内の他のノードに接続するため、ノードは、リスナー アドレスやコンピューターの IP アドレスなど一部のデータをメッシュ内の他のノードと交換します。</span><span class="sxs-lookup"><span data-stu-id="e261c-195">To connect to other nodes in the mesh, nodes also exchange some data, including the listener address and the machine's IP addresses, with other nodes in the mesh.</span></span> <span data-ttu-id="e261c-196">メッシュ内で送信されるメッセージに送信者に関するセキュリティ情報を入れ、メッセージのなりすましと改ざんを防止することができます。</span><span class="sxs-lookup"><span data-stu-id="e261c-196">Messages sent around in the mesh can contain security information that pertains to the sender to prevent message spoofing and tampering.</span></span>  
  
 <span data-ttu-id="e261c-197">エンドユーザーのコンピューターには、個人情報は保存されません。</span><span class="sxs-lookup"><span data-stu-id="e261c-197">No personal information is stored on the end user's machine.</span></span>  
  
## <a name="it-professional-experience"></a><span data-ttu-id="e261c-198">IT 専門家向けの機能</span><span class="sxs-lookup"><span data-stu-id="e261c-198">IT Professional Experience</span></span>  
  
### <a name="tracing"></a><span data-ttu-id="e261c-199">トレース</span><span class="sxs-lookup"><span data-stu-id="e261c-199">Tracing</span></span>  

 <span data-ttu-id="e261c-200">WCF インフラストラクチャの診断機能では、トランスポート層とサービスモデルレイヤーを通過するメッセージと、これらのメッセージに関連付けられているアクティビティとイベントがログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-200">The diagnostics feature of the WCF infrastructure logs messages that pass through the transport and service model layers, and the activities and events associated with these messages.</span></span> <span data-ttu-id="e261c-201">この機能は既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="e261c-201">This feature is turned off by default.</span></span> <span data-ttu-id="e261c-202">アプリケーションの構成ファイルを使用して有効にし、実行時に WCF WMI プロバイダーを使用してトレース動作を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="e261c-202">It is enabled using the application’s configuration file and the tracing behavior may be modified using the WCF WMI provider at run time.</span></span> <span data-ttu-id="e261c-203">有効にすると、トレース インフラストラクチャは、メッセージ、アクティビティ、および処理イベントを含んだ診断トレースを構成済みリスナーに出力します。</span><span class="sxs-lookup"><span data-stu-id="e261c-203">When enabled, the tracing infrastructure emits a diagnostic trace that contains messages, activities, and processing events to configured listeners.</span></span> <span data-ttu-id="e261c-204">出力の形式と場所は、管理者が選択するリスナー構成によって決まりますが、通常は XML 形式のファイルです。</span><span class="sxs-lookup"><span data-stu-id="e261c-204">The format and location of the output are determined by the administrator’s listener configuration choices, but is typically an XML formatted file.</span></span> <span data-ttu-id="e261c-205">管理者は、トレース ファイルでアクセス制御リスト (ACL) を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e261c-205">The administrator is responsible for setting the access control list (ACL) on the trace files.</span></span> <span data-ttu-id="e261c-206">特に、Windows アクティベーション システム (WAS) でホストするとき、管理者は、ファイルがパブリック仮想ルート ディレクトリから提供されていないことを確認する必要があります (提供されることを望まない場合)。</span><span class="sxs-lookup"><span data-stu-id="e261c-206">In particular, when hosted by Windows Activation System (WAS), the administrator should make sure the files are not served from the public virtual root directory if that is not desired.</span></span>  
  
 <span data-ttu-id="e261c-207">トレースには、メッセージ ログとサービス モデル診断トレースの 2 種類があります。この 2 種類のトレースについて次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="e261c-207">There are two types of tracing: Message logging and Service Model diagnostic tracing, described in the following section.</span></span> <span data-ttu-id="e261c-208">この 2 つのトレースは、それぞれ <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> と <xref:System.ServiceModel> というトレース ソースから構成されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-208">Each type is configured through its own trace source: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> and <xref:System.ServiceModel>.</span></span> <span data-ttu-id="e261c-209">このログ トレース ソースは両方とも、アプリケーションにローカルなデータを取り込みます。</span><span class="sxs-lookup"><span data-stu-id="e261c-209">Both of these logging trace sources capture data that is local to the application.</span></span>  
  
### <a name="message-logging"></a><span data-ttu-id="e261c-210">メッセージ ログ</span><span class="sxs-lookup"><span data-stu-id="e261c-210">Message Logging</span></span>  

 <span data-ttu-id="e261c-211">メッセージ ログのトレース ソース (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) によって管理者は、システムを通過するメッセージをログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-211">The message logging trace source (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) allows an administrator to log the messages that flow through the system.</span></span> <span data-ttu-id="e261c-212">ユーザーは構成によって、メッセージ全体またはメッセージ ヘッダーだけをログに記録するかどうか、トランスポート レイヤーまたはサービス モデル レイヤーでログに記録するかどうか、および形式が正しくないメッセージをログに記録するかどうかを設定できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-212">Through configuration, the user may decide to log entire messages or message headers only, whether to log at the transport and/or service model layers, and whether to include malformed messages.</span></span> <span data-ttu-id="e261c-213">また、ユーザーは、フィルター処理を設定して、ログに記録するメッセージを制限できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-213">Also, the user may configure filtering to restrict which messages are logged.</span></span>  
  
 <span data-ttu-id="e261c-214">既定では、メッセージ ログは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="e261c-214">By default, message logging is disabled.</span></span> <span data-ttu-id="e261c-215">ローカル コンピューターの管理者は、アプリケーション レベルの管理者がメッセージ ログを有効にするのを防止できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-215">The local machine administrator can prevent the application-level administrator from turning message logging on.</span></span>  
  
#### <a name="encrypted-and-decrypted-message-logging"></a><span data-ttu-id="e261c-216">暗号化および復号化されるメッセージ ログ</span><span class="sxs-lookup"><span data-stu-id="e261c-216">Encrypted and Decrypted Message Logging</span></span>  

 <span data-ttu-id="e261c-217">メッセージは、以下に説明するようにログに記録され、暗号化および復号化されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-217">Messages are logged, encrypted, or decrypted, as described in the following terms.</span></span>  
  
 <span data-ttu-id="e261c-218">トランスポート ログ</span><span class="sxs-lookup"><span data-stu-id="e261c-218">Transport Logging</span></span>  
 <span data-ttu-id="e261c-219">トランスポート レベルで送受信されるメッセージをログに記録します。</span><span class="sxs-lookup"><span data-stu-id="e261c-219">Logs messages received and sent at the transport level.</span></span> <span data-ttu-id="e261c-220">このメッセージは、すべてのヘッダーを含んでいて、ネットワーク上に送信される前と受信されるときに暗号化できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-220">These messages contain all headers, and may be encrypted before being sent on the wire and when being received.</span></span>  
  
 <span data-ttu-id="e261c-221">メッセージがネットワーク上に送信される前と受信されるときに暗号化される場合、そのメッセージは暗号化されたままログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-221">If messages are encrypted before being sent on the wire and when they are received, they are logged encrypted as well.</span></span> <span data-ttu-id="e261c-222">例外は、セキュリティ プロトコル (https) を使用する場合です。メッセージは、ネットワーク上で暗号化されている場合でも、送信前と受信後は復号化された状態でログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-222">An exception is when a security protocol is used (https): they are then logged decrypted before being sent and after being received even if they are encrypted on the wire.</span></span>  
  
 <span data-ttu-id="e261c-223">サービス ログ</span><span class="sxs-lookup"><span data-stu-id="e261c-223">Service Logging</span></span>  
 <span data-ttu-id="e261c-224">チャネル ヘッダー処理が実行された後、ユーザー コードを入力する直前と直後に、サービス モデル レベルで送受信されるメッセージをログに記録します。</span><span class="sxs-lookup"><span data-stu-id="e261c-224">Logs messages received or sent at the service model level, after channel header processing has occurred, just before and after entering user code.</span></span>  
  
 <span data-ttu-id="e261c-225">このレベルでログに記録されるメッセージは、ネットワーク上でセキュリティ保護され、暗号化されている場合でも復号化されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-225">Messages logged at this level are decrypted even if they were secured and encrypted on the wire.</span></span>  
  
 <span data-ttu-id="e261c-226">形式が正しくないメッセージのログ</span><span class="sxs-lookup"><span data-stu-id="e261c-226">Malformed Message Logging</span></span>  
 <span data-ttu-id="e261c-227">WCF インフラストラクチャが理解または処理できないメッセージをログに記録します。</span><span class="sxs-lookup"><span data-stu-id="e261c-227">Logs messages that the WCF infrastructure cannot understand or process.</span></span>  
  
 <span data-ttu-id="e261c-228">メッセージは、暗号化の有無を問わず、そのままの状態でログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-228">Messages are logged as-is, that is, encrypted or not</span></span>  
  
 <span data-ttu-id="e261c-229">暗号化されていない形式または暗号化されていない形式でメッセージをログに記録する場合、既定では、WCF は、メッセージをログに記録する前に、セキュリティキーや個人情報を削除します</span><span class="sxs-lookup"><span data-stu-id="e261c-229">When messages are logged in decrypted or unencrypted form, by default WCF removes security keys and potentially personal information from the messages before logging them.</span></span> <span data-ttu-id="e261c-230">次のセクションでは、削除される情報と削除が実行される状況について説明します。</span><span class="sxs-lookup"><span data-stu-id="e261c-230">The next sections describe what information is removed, and when.</span></span> <span data-ttu-id="e261c-231">キーと個人情報の可能性がある情報をログに記録するには、コンピューターの管理者とアプリケーションを配置するユーザーの両方が、所定の構成操作を実行して既定の動作を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e261c-231">The machine administrator and application deployer must both take certain configuration actions to change the default behavior to log keys and potentially personal information.</span></span>  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="e261c-232">復号化されたまたは暗号化されていないメッセージをログに記録するときにメッセージ ヘッダーから削除される情報</span><span class="sxs-lookup"><span data-stu-id="e261c-232">Information Removed from Message Headers When Logging Decrypted/Unencrypted Messages</span></span>  

 <span data-ttu-id="e261c-233">メッセージが復号化された状態または暗号化されていない状態でログに記録される場合、既定ではメッセージがログに記録される前に、セキュリティ キーと個人情報の可能性がある情報がメッセージ ヘッダーとメッセージ本文から削除されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-233">When messages are logged in decrypted/unencrypted form, security keys and potentially personal information are removed by default from message headers and message bodies before they are logged.</span></span> <span data-ttu-id="e261c-234">次の一覧は、WCF がキーおよび可能性のある個人情報を考慮することを示しています。</span><span class="sxs-lookup"><span data-stu-id="e261c-234">The following list shows what WCF considers keys and potentially personal information.</span></span>  
  
 <span data-ttu-id="e261c-235">削除されるキー :</span><span class="sxs-lookup"><span data-stu-id="e261c-235">Keys that are removed:</span></span>  
  
 <span data-ttu-id="e261c-236">\- Xmlns: wst = " http://schemas.xmlsoap.org/ws/2004/04/trust " および xmlns: wst = " http://schemas.xmlsoap.org/ws/2005/02/trust " の場合</span><span class="sxs-lookup"><span data-stu-id="e261c-236">\- For xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"</span></span>  
  
 <span data-ttu-id="e261c-237">wst:BinarySecret</span><span class="sxs-lookup"><span data-stu-id="e261c-237">wst:BinarySecret</span></span>  
  
 <span data-ttu-id="e261c-238">wst:Entropy</span><span class="sxs-lookup"><span data-stu-id="e261c-238">wst:Entropy</span></span>  
  
 <span data-ttu-id="e261c-239">\- Xmlns: wsse = " http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd " と xmlns: wsse = " http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd " の場合</span><span class="sxs-lookup"><span data-stu-id="e261c-239">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="e261c-240">wsse:Password</span><span class="sxs-lookup"><span data-stu-id="e261c-240">wsse:Password</span></span>  
  
 <span data-ttu-id="e261c-241">wsse:Nonce</span><span class="sxs-lookup"><span data-stu-id="e261c-241">wsse:Nonce</span></span>  
  
 <span data-ttu-id="e261c-242">削除される個人情報の可能性がある情報 :</span><span class="sxs-lookup"><span data-stu-id="e261c-242">Potentially personal information that is removed:</span></span>  
  
 <span data-ttu-id="e261c-243">\- Xmlns: wsse = " http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd " と xmlns: wsse = " http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd " の場合</span><span class="sxs-lookup"><span data-stu-id="e261c-243">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="e261c-244">wsse:Username</span><span class="sxs-lookup"><span data-stu-id="e261c-244">wsse:Username</span></span>  
  
 <span data-ttu-id="e261c-245">wsse:BinarySecurityToken</span><span class="sxs-lookup"><span data-stu-id="e261c-245">wsse:BinarySecurityToken</span></span>  
  
 <span data-ttu-id="e261c-246">\- Xmlns の場合: saml = "urn: oasis: names: tc: SAML: 1.0: assertion": 太字 (下) の項目が削除されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-246">\- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:</span></span>  
  
 <span data-ttu-id="e261c-247">\<主張</span><span class="sxs-lookup"><span data-stu-id="e261c-247">\<Assertion</span></span>  
  
 <span data-ttu-id="e261c-248">MajorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="e261c-248">MajorVersion="1"</span></span>  
  
 <span data-ttu-id="e261c-249">MinorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="e261c-249">MinorVersion="1"</span></span>  
  
 <span data-ttu-id="e261c-250">AssertionId="[ID]"</span><span class="sxs-lookup"><span data-stu-id="e261c-250">AssertionId="[ID]"</span></span>  
  
 <span data-ttu-id="e261c-251">Issuer="[string]"</span><span class="sxs-lookup"><span data-stu-id="e261c-251">Issuer="[string]"</span></span>  
  
 <span data-ttu-id="e261c-252">IssueInstant="[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="e261c-252">IssueInstant="[dateTime]"</span></span>  
  
 >  
  
 \<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]">  
  
 \<AudienceRestrictionCondition>  
  
 <span data-ttu-id="e261c-253">\<Audience>uri\</Audience>+</span><span class="sxs-lookup"><span data-stu-id="e261c-253">\<Audience>[uri]\</Audience>+</span></span>  
  
 \</AudienceRestrictionCondition>*  
  
 \<DoNotCacheCondition />*  
  
 <span data-ttu-id="e261c-254"><\!--抽象基本型</span><span class="sxs-lookup"><span data-stu-id="e261c-254"><\!-- abstract base type</span></span>  
  
 \<Condition />*  
  
 -->  
  
 <span data-ttu-id="e261c-255">\</Conditions>?</span><span class="sxs-lookup"><span data-stu-id="e261c-255">\</Conditions>?</span></span>  
  
 \<Advice>  
  
 <span data-ttu-id="e261c-256">\<AssertionIDReference>番号\</AssertionIDReference>\*</span><span class="sxs-lookup"><span data-stu-id="e261c-256">\<AssertionIDReference>[ID]\</AssertionIDReference>\*</span></span>  
  
 <span data-ttu-id="e261c-257">\<Assertion>主張\</Assertion>\*</span><span class="sxs-lookup"><span data-stu-id="e261c-257">\<Assertion>[assertion]\</Assertion>\*</span></span>  
  
 <span data-ttu-id="e261c-258">[any]\*</span><span class="sxs-lookup"><span data-stu-id="e261c-258">[any]\*</span></span>  
  
 <span data-ttu-id="e261c-259">\</Advice>?</span><span class="sxs-lookup"><span data-stu-id="e261c-259">\</Advice>?</span></span>  
  
 <span data-ttu-id="e261c-260"><\!--抽象基本型</span><span class="sxs-lookup"><span data-stu-id="e261c-260"><\!-- Abstract base types</span></span>  
  
 \<Statement />*  
  
 \<SubjectStatement>  
  
 \<Subject>  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 \<SubjectConfirmation>  
  
 <span data-ttu-id="e261c-261">\<ConfirmationMethod>AnyUri\</ConfirmationMethod>+</span><span class="sxs-lookup"><span data-stu-id="e261c-261">\<ConfirmationMethod>[anyUri]\</ConfirmationMethod>+</span></span>  
  
 <span data-ttu-id="e261c-262">\<SubjectConfirmationData>[任意] \</SubjectConfirmationData> ?</span><span class="sxs-lookup"><span data-stu-id="e261c-262">\<SubjectConfirmationData>[any]\</SubjectConfirmationData>?</span></span>  
  
 <span data-ttu-id="e261c-263">\<ds:KeyInfo>...\</ds:KeyInfo>?</span><span class="sxs-lookup"><span data-stu-id="e261c-263">\<ds:KeyInfo>...\</ds:KeyInfo>?</span></span>  
  
 <span data-ttu-id="e261c-264">\</SubjectConfirmation>?</span><span class="sxs-lookup"><span data-stu-id="e261c-264">\</SubjectConfirmation>?</span></span>  
  
 \</Subject>  
  
 \</SubjectStatement>*  
  
 -->  
  
 <span data-ttu-id="e261c-265">\<AuthenticationStatement</span><span class="sxs-lookup"><span data-stu-id="e261c-265">\<AuthenticationStatement</span></span>  
  
 <span data-ttu-id="e261c-266">AuthenticationMethod="[uri]"</span><span class="sxs-lookup"><span data-stu-id="e261c-266">AuthenticationMethod="[uri]"</span></span>  
  
 <span data-ttu-id="e261c-267">AuthenticationInstant="[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="e261c-267">AuthenticationInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="e261c-268">[Subject]</span><span class="sxs-lookup"><span data-stu-id="e261c-268">[Subject]</span></span>  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 <span data-ttu-id="e261c-269"><AuthorityBinding</span><span class="sxs-lookup"><span data-stu-id="e261c-269"><AuthorityBinding</span></span>  
  
 <span data-ttu-id="e261c-270">AuthorityKind="[QName]"</span><span class="sxs-lookup"><span data-stu-id="e261c-270">AuthorityKind="[QName]"</span></span>  
  
 <span data-ttu-id="e261c-271">Location="[uri]"</span><span class="sxs-lookup"><span data-stu-id="e261c-271">Location="[uri]"</span></span>  
  
 <span data-ttu-id="e261c-272">Binding="[uri]"</span><span class="sxs-lookup"><span data-stu-id="e261c-272">Binding="[uri]"</span></span>  
  
 />*  
  
 \</AuthenticationStatement>*  
  
 \<AttributeStatement>  
  
 <span data-ttu-id="e261c-273">[Subject]</span><span class="sxs-lookup"><span data-stu-id="e261c-273">[Subject]</span></span>  
  
 <span data-ttu-id="e261c-274">\<属性</span><span class="sxs-lookup"><span data-stu-id="e261c-274">\<Attribute</span></span>  
  
 <span data-ttu-id="e261c-275">AttributeName="[string]"</span><span class="sxs-lookup"><span data-stu-id="e261c-275">AttributeName="[string]"</span></span>  
  
 <span data-ttu-id="e261c-276">AttributeNamespace="[uri]"</span><span class="sxs-lookup"><span data-stu-id="e261c-276">AttributeNamespace="[uri]"</span></span>  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 \</Attribute>+  
  
 \</AttributeStatement>*  
  
 <span data-ttu-id="e261c-277">\<Authorizationdecisionstatement に</span><span class="sxs-lookup"><span data-stu-id="e261c-277">\<AuthorizationDecisionStatement</span></span>  
  
 <span data-ttu-id="e261c-278">Resource="[uri]"</span><span class="sxs-lookup"><span data-stu-id="e261c-278">Resource="[uri]"</span></span>  
  
 <span data-ttu-id="e261c-279">Decision = "[許可&#124;拒否&#124;不定]"</span><span class="sxs-lookup"><span data-stu-id="e261c-279">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span></span>  
  
 >  
  
 <span data-ttu-id="e261c-280">[Subject]</span><span class="sxs-lookup"><span data-stu-id="e261c-280">[Subject]</span></span>  
  
 <span data-ttu-id="e261c-281">\<Action Namespace="[uri]">文字列\</Action>+</span><span class="sxs-lookup"><span data-stu-id="e261c-281">\<Action Namespace="[uri]">[string]\</Action>+</span></span>  
  
 \<Evidence>  
  
 <span data-ttu-id="e261c-282">\<AssertionIDReference>番号\</AssertionIDReference>+</span><span class="sxs-lookup"><span data-stu-id="e261c-282">\<AssertionIDReference>[ID]\</AssertionIDReference>+</span></span>  
  
 <span data-ttu-id="e261c-283">\<Assertion>主張\</Assertion>+</span><span class="sxs-lookup"><span data-stu-id="e261c-283">\<Assertion>[assertion]\</Assertion>+</span></span>  
  
 <span data-ttu-id="e261c-284">\</Evidence>?</span><span class="sxs-lookup"><span data-stu-id="e261c-284">\</Evidence>?</span></span>  
  
 \</AuthorizationDecisionStatement>*  
  
 \</Assertion>  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="e261c-285">復号化されたまたは暗号化されていないメッセージをログに記録するときにメッセージ本文から削除される情報</span><span class="sxs-lookup"><span data-stu-id="e261c-285">Information Removed from Message Bodies When Logging Decrypted/Unencrypted Messages</span></span>  

 <span data-ttu-id="e261c-286">前に説明したように、WCF では、暗号化された暗号化されていないメッセージや暗号化されていないメッセージのメッセージヘッダーから、キーと既知の可能性がある</span><span class="sxs-lookup"><span data-stu-id="e261c-286">As previously described, WCF removes keys and known potentially personal information from message headers for logged decrypted/unencrypted messages.</span></span> <span data-ttu-id="e261c-287">さらに、WCF は、キー交換に関連するセキュリティメッセージについて説明する次の一覧の本文要素とアクションの本文から、キーと既知の可能性がある個人情報を削除します。</span><span class="sxs-lookup"><span data-stu-id="e261c-287">In addition, WCF removes keys and known potentially personal information from message bodies for the body elements and actions in the following list, which describe security messages involved in key exchange.</span></span>  
  
 <span data-ttu-id="e261c-288">次の名前空間の場合 :</span><span class="sxs-lookup"><span data-stu-id="e261c-288">For the following namespaces:</span></span>  
  
 <span data-ttu-id="e261c-289">xmlns: wst = " http://schemas.xmlsoap.org/ws/2004/04/trust " および xmlns: wst = " http://schemas.xmlsoap.org/ws/2005/02/trust " (たとえば、使用可能なアクションがない場合)</span><span class="sxs-lookup"><span data-stu-id="e261c-289">xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust" (for example, if no action available)</span></span>  
  
 <span data-ttu-id="e261c-290">キー交換を伴うこの本文要素について情報が削除されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-290">Information is removed for these body elements, which involve key exchange:</span></span>  
  
 <span data-ttu-id="e261c-291">wst:RequestSecurityToken</span><span class="sxs-lookup"><span data-stu-id="e261c-291">wst:RequestSecurityToken</span></span>  
  
 <span data-ttu-id="e261c-292">wst:RequestSecurityTokenResponse</span><span class="sxs-lookup"><span data-stu-id="e261c-292">wst:RequestSecurityTokenResponse</span></span>  
  
 <span data-ttu-id="e261c-293">wst:RequestSecurityTokenResponseCollection</span><span class="sxs-lookup"><span data-stu-id="e261c-293">wst:RequestSecurityTokenResponseCollection</span></span>  
  
 <span data-ttu-id="e261c-294">次の各アクションについても情報が削除されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-294">Information is also removed for each of the following Actions:</span></span>  
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend`
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a><span data-ttu-id="e261c-295">情報が削除されないアプリケーション固有のヘッダーと本文データ</span><span class="sxs-lookup"><span data-stu-id="e261c-295">No Information Is Removed from Application-specific Headers and Body Data</span></span>  

 <span data-ttu-id="e261c-296">WCF では、アプリケーション固有のヘッダー (クエリ文字列など) や本文データ (クレジットカード番号など) の個人情報は追跡されません。</span><span class="sxs-lookup"><span data-stu-id="e261c-296">WCF does not track personal information in application-specific headers (for example, query strings) or body data (for example, credit card number).</span></span>  
  
 <span data-ttu-id="e261c-297">メッセージ ログが有効な場合、アプリケーション固有のヘッダーと本文情報にある個人情報はログに表示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e261c-297">When message logging is on, personal information in application-specific headers and body information may be visible in the logs.</span></span> <span data-ttu-id="e261c-298">そのため、この場合もアプリケーションを配置するユーザーが、構成ファイルとログ ファイルに対する ACL を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e261c-298">Again, the application deployer is responsible for setting the ACLs on the configuration and log files.</span></span> <span data-ttu-id="e261c-299">また、この情報を表示したくない場合はログ記録を無効にしたり、ログ記録後にログファイルからこの情報を除外したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="e261c-299">They also can turn off logging if they don't want this information to be visible, or filter out this information from the log files after it is logged.</span></span>  
  
### <a name="service-model-tracing"></a><span data-ttu-id="e261c-300">サービス モデル トレース</span><span class="sxs-lookup"><span data-stu-id="e261c-300">Service Model Tracing</span></span>  

 <span data-ttu-id="e261c-301">サービス モデルのトレース ソース (<xref:System.ServiceModel>) によって、メッセージ処理に関するアクティビティとイベントのトレースを実行できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-301">The Service Model trace source (<xref:System.ServiceModel>) enables tracing of activities and events related to message processing.</span></span> <span data-ttu-id="e261c-302">この機能では、<xref:System.Diagnostics> から .NET Framework 診断機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="e261c-302">This feature uses the .NET Framework diagnostic functionality from <xref:System.Diagnostics>.</span></span> <span data-ttu-id="e261c-303"><xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> プロパティと同様、場所とその ACL は、.NET Framework アプリケーションの構成ファイルを使用してユーザーが設定できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-303">As with the <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> property, the location and its ACL are user-configurable using .NET Framework application configuration files.</span></span> <span data-ttu-id="e261c-304">メッセージ ログと同様、管理者がトレースを有効にするときに必ずファイルの場所が設定されるので、管理者は ACL を制御できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-304">As with message logging, the file location is always configured when the administrator enables tracing; thus, the administrator controls the ACL.</span></span>  
  
 <span data-ttu-id="e261c-305">スコープ内のメッセージに含まれるメッセージ ヘッダーをトレースします。</span><span class="sxs-lookup"><span data-stu-id="e261c-305">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="e261c-306">前のセクションで説明した、メッセージ ヘッダーに含まれる個人情報の可能性がある情報を非表示にする場合と同じ規則が適用されます。既定では、先に示した個人情報はトレース時にヘッダーから削除されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-306">The same rules for hiding potentially personal information in message headers in the previous section apply: the personal information previously identified is removed by default from the headers in traces.</span></span> <span data-ttu-id="e261c-307">個人情報の可能性がある情報をログに記録するには、コンピューターの管理者とアプリケーションを配置するユーザーの両方が構成を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e261c-307">Both the machine administrator and the application deployer must modify the configuration in order to log potentially personal information.</span></span> <span data-ttu-id="e261c-308">ただし、アプリケーション固有のヘッダーにある個人情報はトレース時にログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-308">However, personal information contained in application-specific headers is logged in traces.</span></span> <span data-ttu-id="e261c-309">アプリケーションを配置するユーザーは、構成ファイルとトレース ファイルに対する ACL を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e261c-309">The application deployer is responsible for setting the ACLs on the configuration and trace files.</span></span> <span data-ttu-id="e261c-310">また、トレースを無効にしてこの情報を非表示にしたり、ログ記録後にトレースファイルからこの情報を除外したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="e261c-310">They can also turn off tracing to hide this information or filter out this information from the trace files after it's logged.</span></span>  
  
 <span data-ttu-id="e261c-311">ServiceModel トレースの一部として、一意な ID (呼び出されたアクティビティ ID、通常は GUID) は、インフラストラクチャのさまざまな部分を通過するメッセージとして、異なる複数のアクティビティを結合します。</span><span class="sxs-lookup"><span data-stu-id="e261c-311">As part of ServiceModel Tracing, Unique IDs (called Activity IDs, and typically a GUID) link different activities together as a message flows through different parts of the infrastructure.</span></span>  
  
#### <a name="custom-trace-listeners"></a><span data-ttu-id="e261c-312">カスタム トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="e261c-312">Custom Trace Listeners</span></span>  

 <span data-ttu-id="e261c-313">メッセージ ログとトレースの両方で、カスタム トレース リスナーを構成できます。このリスナーは、ネットワーク上で、リモート データベースなどにトレースとメッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-313">For both message logging and tracing, a custom trace listener can be configured, which can send traces and messages on the wire (for example, to a remote database).</span></span> <span data-ttu-id="e261c-314">アプリケーションを配置するユーザーは、カスタム リスナーを構成するか、ユーザーがリスナーを構成できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e261c-314">The application deployer is responsible for configuring custom listeners or enabling users to do so.</span></span> <span data-ttu-id="e261c-315">また、リモートの場所で公開されている個人情報や、この場所に Acl を適切に適用するためにも責任を持ちます。</span><span class="sxs-lookup"><span data-stu-id="e261c-315">They are also responsible for any personal information exposed at the remote location and for properly applying ACLs to this location.</span></span>  
  
### <a name="other-features-for-it-professionals"></a><span data-ttu-id="e261c-316">IT 専門家向けのその他の機能</span><span class="sxs-lookup"><span data-stu-id="e261c-316">Other features for IT Professionals</span></span>  

 <span data-ttu-id="e261c-317">WCF には、WMI (Windows に付属) を介して WCF インフラストラクチャの構成情報を公開する WMI プロバイダーがあります。</span><span class="sxs-lookup"><span data-stu-id="e261c-317">WCF has a WMI provider that exposes the WCF infrastructure configuration information through WMI (shipped with Windows).</span></span> <span data-ttu-id="e261c-318">既定では、WMI インターフェイスは管理者が利用できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-318">By default, the WMI interface is available to administrators.</span></span>  
  
 <span data-ttu-id="e261c-319">WCF 構成では、.NET Framework 構成メカニズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="e261c-319">WCF configuration uses the .NET Framework configuration mechanism.</span></span> <span data-ttu-id="e261c-320">構成ファイルはコンピューターに保存されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-320">The configuration files are stored on the machine.</span></span> <span data-ttu-id="e261c-321">アプリケーション開発者と管理者が、アプリケーションの要件に応じて構成ファイルと ACL を作成します。</span><span class="sxs-lookup"><span data-stu-id="e261c-321">The application developer and the administrator create the configuration files and ACL for each of the application's requirements.</span></span> <span data-ttu-id="e261c-322">構成ファイルには、エンドポイント アドレスと証明書ストア内の証明書へのリンクを入れることができます。</span><span class="sxs-lookup"><span data-stu-id="e261c-322">A configuration file can contain endpoint addresses and links to certificates in the certificate store.</span></span> <span data-ttu-id="e261c-323">証明書を使用してアプリケーション データを提供し、アプリケーションによって使用される機能の各プロパティを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="e261c-323">The certificates can be used to provide application data to configure various properties of the features used by the application.</span></span>  
  
 <span data-ttu-id="e261c-324">また、WCF では、メソッドを呼び出すことによって .NET Framework プロセスダンプ機能も使用し <xref:System.Environment.FailFast%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="e261c-324">WCF also uses the .NET Framework process dump functionality by calling the <xref:System.Environment.FailFast%2A> method.</span></span>  
  
### <a name="it-pro-tools"></a><span data-ttu-id="e261c-325">IT 専門家のツール</span><span class="sxs-lookup"><span data-stu-id="e261c-325">IT Pro Tools</span></span>  

 <span data-ttu-id="e261c-326">また、WCF には、Windows SDK に付属する次の IT プロフェッショナル向けツールも用意されています。</span><span class="sxs-lookup"><span data-stu-id="e261c-326">WCF also provides the following IT professional tools, which ship in the Windows SDK.</span></span>  
  
#### <a name="svctraceviewerexe"></a><span data-ttu-id="e261c-327">SvcTraceViewer.exe</span><span class="sxs-lookup"><span data-stu-id="e261c-327">SvcTraceViewer.exe</span></span>  

 <span data-ttu-id="e261c-328">ビューアーには、WCF トレースファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e261c-328">The viewer displays WCF trace files.</span></span> <span data-ttu-id="e261c-329">このビューアーは、トレースに含まれているすべての情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="e261c-329">The viewer shows whatever information is contained in the traces.</span></span>  
  
#### <a name="svcconfigeditorexe"></a><span data-ttu-id="e261c-330">SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="e261c-330">SvcConfigEditor.exe</span></span>  

 <span data-ttu-id="e261c-331">ユーザーは、エディターを使用して、WCF 構成ファイルを作成および編集できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-331">The editor allows the user to create and edit WCF configuration files.</span></span> <span data-ttu-id="e261c-332">このエディターは、構成ファイルに含まれているすべての情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="e261c-332">The editor shows whatever information is contained in the configuration files.</span></span> <span data-ttu-id="e261c-333">テキスト エディターでも同じタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-333">The same task can be accomplished with a text editor.</span></span>  
  
#### <a name="servicemodel_reg"></a><span data-ttu-id="e261c-334">ServiceModel_Reg</span><span class="sxs-lookup"><span data-stu-id="e261c-334">ServiceModel_Reg</span></span>  

 <span data-ttu-id="e261c-335">このツールでは、コンピューター上の ServiceModel のインストールを管理できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-335">This tool allows the user to manage ServiceModel installs on a machine.</span></span> <span data-ttu-id="e261c-336">このツールでは、実行時にステータスメッセージがコンソールウィンドウに表示され、プロセス内で WCF インストールの構成に関する情報が表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="e261c-336">The tool displays status messages in a console window when it runs and, in the process, may display information about the configuration of the WCF installation.</span></span>  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a><span data-ttu-id="e261c-337">WSATConfig.exe と WSATUI.dll</span><span class="sxs-lookup"><span data-stu-id="e261c-337">WSATConfig.exe and WSATUI.dll</span></span>  

 <span data-ttu-id="e261c-338">これらのツールを使用すると、IT 担当者は WCF で相互運用可能な WS-AtomicTransaction ネットワークサポートを構成できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-338">These tools allow IT Professionals to configure interoperable WS-AtomicTransaction network support in WCF.</span></span> <span data-ttu-id="e261c-339">このツールは、レジストリに格納された最も一般的に使用される WS-AtomicTransaction 設定の値を表示し、ユーザーはこのツールを使用してその値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-339">The tools display and allow the user to change the values of the most commonly used WS-AtomicTransaction settings stored in the registry.</span></span>  
  
## <a name="cross-cutting-features"></a><span data-ttu-id="e261c-340">広範囲に使用できる機能</span><span class="sxs-lookup"><span data-stu-id="e261c-340">Cross-cutting Features</span></span>  

 <span data-ttu-id="e261c-341">次の機能は広範囲に使用できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-341">The following features are cross-cutting.</span></span> <span data-ttu-id="e261c-342">つまり、前述の任意の機能と共に構成できます。</span><span class="sxs-lookup"><span data-stu-id="e261c-342">That is, they can be composed with any of the preceding features.</span></span>  
  
### <a name="service-framework"></a><span data-ttu-id="e261c-343">サービス フレームワーク</span><span class="sxs-lookup"><span data-stu-id="e261c-343">Service Framework</span></span>  

 <span data-ttu-id="e261c-344">ヘッダーには、インスタンス ID を入れることができます。このインスタンス ID は、メッセージを CLR クラスのインスタンスに関連付ける GUID です。</span><span class="sxs-lookup"><span data-stu-id="e261c-344">Headers can contain an instance ID, which is a GUID that associates a message with an instance of a CLR class.</span></span>  
  
 <span data-ttu-id="e261c-345">Web サービス記述言語 (WSDL) には、ポートの定義が入ります。</span><span class="sxs-lookup"><span data-stu-id="e261c-345">The Web Services Description Language (WSDL) contains a definition of the port.</span></span> <span data-ttu-id="e261c-346">各ポートには、エンドポイント アドレス、およびアプリケーションが使用するサービスを表すバインディングがあります。</span><span class="sxs-lookup"><span data-stu-id="e261c-346">Each port has an endpoint address and a binding that represents the services used by the application.</span></span> <span data-ttu-id="e261c-347">WSDL の公開は、構成を使用して無効にできます。</span><span class="sxs-lookup"><span data-stu-id="e261c-347">Exposing WSDL can be turned off using configuration.</span></span> <span data-ttu-id="e261c-348">コンピューターに保持される情報はありません。</span><span class="sxs-lookup"><span data-stu-id="e261c-348">No information is retained on the machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e261c-349">関連項目</span><span class="sxs-lookup"><span data-stu-id="e261c-349">See also</span></span>

- [<span data-ttu-id="e261c-350">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="e261c-350">Windows Communication Foundation</span></span>](index.md)
- [<span data-ttu-id="e261c-351">Security</span><span class="sxs-lookup"><span data-stu-id="e261c-351">Security</span></span>](./feature-details/security.md)
