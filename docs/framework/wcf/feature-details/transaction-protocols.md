---
description: 詳細については、「トランザクションプロトコル」を参照してください。
title: トランザクション プロトコル
ms.date: 03/30/2017
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
ms.openlocfilehash: a790e5d79128fb606d89cb6a3b6a925b3084d481
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752692"
---
# <a name="transaction-protocols"></a><span data-ttu-id="b5b0d-103">トランザクション プロトコル</span><span class="sxs-lookup"><span data-stu-id="b5b0d-103">Transaction Protocols</span></span>

<span data-ttu-id="b5b0d-104">Windows Communication Foundation (WCF) は WS-Atomic トランザクションと WS-Coordination プロトコルを実装します。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-104">Windows Communication Foundation (WCF) implements WS-Atomic Transaction and WS-Coordination protocols.</span></span>  
  
|<span data-ttu-id="b5b0d-105">仕様/ドキュメント</span><span class="sxs-lookup"><span data-stu-id="b5b0d-105">Specification/Document</span></span>|<span data-ttu-id="b5b0d-106">Version</span><span class="sxs-lookup"><span data-stu-id="b5b0d-106">Version</span></span>|<span data-ttu-id="b5b0d-107">リンク</span><span class="sxs-lookup"><span data-stu-id="b5b0d-107">Link</span></span>|  
|-----------------------------|-------------|----------|  
|<span data-ttu-id="b5b0d-108">WS-Coordination</span><span class="sxs-lookup"><span data-stu-id="b5b0d-108">WS-Coordination</span></span>|<span data-ttu-id="b5b0d-109">1.0</span><span class="sxs-lookup"><span data-stu-id="b5b0d-109">1.0</span></span><br /><br /> <span data-ttu-id="b5b0d-110">1.1</span><span class="sxs-lookup"><span data-stu-id="b5b0d-110">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wscoor/><br /><br /> <https://docs.oasis-open.org/ws-tx/wscoor/2006/06>|  
|<span data-ttu-id="b5b0d-111">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="b5b0d-111">WS-AtomicTransaction</span></span>|<span data-ttu-id="b5b0d-112">1.0</span><span class="sxs-lookup"><span data-stu-id="b5b0d-112">1.0</span></span><br /><br /> <span data-ttu-id="b5b0d-113">1.1</span><span class="sxs-lookup"><span data-stu-id="b5b0d-113">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wsat/><br /><br /> <https://docs.oasis-open.org/ws-tx/wsat/2006/06>|  
  
 <span data-ttu-id="b5b0d-114">これらのプロトコル仕様の相互運用性は、アプリケーション間とトランザクション マネージャー間の 2 つのレベルで必要です (次の図を参照)。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-114">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="b5b0d-115">仕様では、相互運用性の両方のレベルについて、メッセージ形式とメッセージ交換が詳細に説明されます。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-115">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="b5b0d-116">アプリケーション間での交換に必要な一定のセキュリティ、信頼性、およびエンコーディングは、通常のアプリケーションによる交換にも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-116">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="b5b0d-117">ただし、トランザクション マネージャー間で適切な相互運用性を実現するには、特定のバインディングを使用するという合意が必要となります。通常、バインディングはユーザーによって構成されないためです。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-117">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="b5b0d-118">ここでは、WS-AtomicTransaction (WS-AT) 仕様のセキュリティに関する構成と、トランザクション マネージャー間の通信に使用されるセキュリティで保護されたバインディングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-118">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="b5b0d-119">このドキュメントで説明されているアプローチは、IBM、IONA、Sun Microsystems などを含む WS-AT および WS-Coordination の各種の実装でテスト済みのものです。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-119">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="b5b0d-120">次の図は、2つのトランザクションマネージャー (トランザクションマネージャー1とトランザクションマネージャー 2) と2つのアプリケーション (アプリケーション1とアプリケーション 2) 間の相互運用性を示しています。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-120">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2:</span></span>  
  
 ![トランザクションマネージャー間の対話を示すスクリーンショット。](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 <span data-ttu-id="b5b0d-122">1 つのイニシエーター (I) と 1 つの参加要素 (P) を持つ、一般的な WS-Coordination/WS-AtomicTransaction のシナリオを考えます。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-122">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="b5b0d-123">イニシエーターと参加要素の両方にトランザクション マネージャー (それぞれ ITM および PTM と呼びます) があります。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-123">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="b5b0d-124">2 フェーズ コミットは、このトピックでは 2PC と呼びます。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-124">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b5b0d-125">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="b5b0d-125">1. CreateCoordinationContext</span></span>|<span data-ttu-id="b5b0d-126">12. アプリケーションメッセージの応答</span><span class="sxs-lookup"><span data-stu-id="b5b0d-126">12. Application Message Response</span></span>|  
|<span data-ttu-id="b5b0d-127">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="b5b0d-127">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="b5b0d-128">13. コミット (完了)</span><span class="sxs-lookup"><span data-stu-id="b5b0d-128">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="b5b0d-129">3. 登録 (完了)</span><span class="sxs-lookup"><span data-stu-id="b5b0d-129">3. Register (Completion)</span></span>|<span data-ttu-id="b5b0d-130">14. 準備 (2PC)</span><span class="sxs-lookup"><span data-stu-id="b5b0d-130">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="b5b0d-131">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="b5b0d-131">4. RegisterResponse</span></span>|<span data-ttu-id="b5b0d-132">15. 準備 (2PC)</span><span class="sxs-lookup"><span data-stu-id="b5b0d-132">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="b5b0d-133">5. アプリケーションメッセージ</span><span class="sxs-lookup"><span data-stu-id="b5b0d-133">5. Application Message</span></span>|<span data-ttu-id="b5b0d-134">16. 準備済み (2PC)</span><span class="sxs-lookup"><span data-stu-id="b5b0d-134">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="b5b0d-135">6. CreateCoordinationContext とコンテキスト</span><span class="sxs-lookup"><span data-stu-id="b5b0d-135">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="b5b0d-136">17. 準備済み (2PC)</span><span class="sxs-lookup"><span data-stu-id="b5b0d-136">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="b5b0d-137">7. Register (持続性)</span><span class="sxs-lookup"><span data-stu-id="b5b0d-137">7. Register (Durable)</span></span>|<span data-ttu-id="b5b0d-138">18. コミット (完了)</span><span class="sxs-lookup"><span data-stu-id="b5b0d-138">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="b5b0d-139">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="b5b0d-139">8. RegisterResponse</span></span>|<span data-ttu-id="b5b0d-140">19. コミット (2PC)</span><span class="sxs-lookup"><span data-stu-id="b5b0d-140">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="b5b0d-141">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="b5b0d-141">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="b5b0d-142">20. コミット (2PC)</span><span class="sxs-lookup"><span data-stu-id="b5b0d-142">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="b5b0d-143">10. レジスタ (持続性)</span><span class="sxs-lookup"><span data-stu-id="b5b0d-143">10. Register (Durable)</span></span>|<span data-ttu-id="b5b0d-144">21. コミット済み (2PC)</span><span class="sxs-lookup"><span data-stu-id="b5b0d-144">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="b5b0d-145">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="b5b0d-145">11. RegisterResponse</span></span>|<span data-ttu-id="b5b0d-146">22. コミット済み (2PC)</span><span class="sxs-lookup"><span data-stu-id="b5b0d-146">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="b5b0d-147">このドキュメントでは、WS-AtomicTransaction 仕様のセキュリティに関する構成と、トランザクション マネージャー間の通信に使用されるセキュリティで保護されたバインディングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-147">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="b5b0d-148">このドキュメントで説明されているアプローチは、WS-AT および WS-Coordination の各種の実装でテスト済みのものです。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-148">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="b5b0d-149">この図および表では、セキュリティの観点から見た次の 4 つのクラスのメッセージを示しています。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-149">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
- <span data-ttu-id="b5b0d-150">アクティベーション メッセージ (CreateCoordinationContext と CreateCoordinationContextResponse)</span><span class="sxs-lookup"><span data-stu-id="b5b0d-150">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
- <span data-ttu-id="b5b0d-151">登録メッセージ (Register と RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="b5b0d-151">Registration messages (Register and RegisterResponse)</span></span>  
  
- <span data-ttu-id="b5b0d-152">プロトコル メッセージ (Prepare、Rollback、Commit、Aborted など)</span><span class="sxs-lookup"><span data-stu-id="b5b0d-152">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
- <span data-ttu-id="b5b0d-153">アプリケーション メッセージ</span><span class="sxs-lookup"><span data-stu-id="b5b0d-153">Application messages.</span></span>  
  
 <span data-ttu-id="b5b0d-154">最初の 3 つのメッセージ クラスはトランザクション マネージャーのメッセージと考えられます。これらのクラスのバインド構成については、後の「アプリケーション メッセージ交換」で説明します。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-154">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="b5b0d-155">4 番目のメッセージ クラスは、アプリケーション間のメッセージであり、後の「メッセージの例」で説明します。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-155">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="b5b0d-156">ここでは、これらの各クラスに対して WCF によって使用されるプロトコルバインドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-156">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="b5b0d-157">このドキュメントでは、次の XML 名前空間と関連付けられたプレフィックスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-157">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="b5b0d-158">Prefix</span><span class="sxs-lookup"><span data-stu-id="b5b0d-158">Prefix</span></span>|<span data-ttu-id="b5b0d-159">Version</span><span class="sxs-lookup"><span data-stu-id="b5b0d-159">Version</span></span>|<span data-ttu-id="b5b0d-160">名前空間 URI</span><span class="sxs-lookup"><span data-stu-id="b5b0d-160">Namespace URI</span></span>|  
|------------|-------------|-------------------|  
|<span data-ttu-id="b5b0d-161">s11</span><span class="sxs-lookup"><span data-stu-id="b5b0d-161">s11</span></span>||<https://schemas.xmlsoap.org/soap/envelope/>|  
|<span data-ttu-id="b5b0d-162">wsa</span><span class="sxs-lookup"><span data-stu-id="b5b0d-162">wsa</span></span>|<span data-ttu-id="b5b0d-163">1.0 より前</span><span class="sxs-lookup"><span data-stu-id="b5b0d-163">Pre-1.0</span></span><br /><br /> <span data-ttu-id="b5b0d-164">1.0</span><span class="sxs-lookup"><span data-stu-id="b5b0d-164">1.0</span></span>|`http://www.w3.org/2004/08/addressing`<br /><br /> <https://www.w3.org/2005/08/addressing/>|  
|<span data-ttu-id="b5b0d-165">wscoor</span><span class="sxs-lookup"><span data-stu-id="b5b0d-165">wscoor</span></span>|<span data-ttu-id="b5b0d-166">1.0</span><span class="sxs-lookup"><span data-stu-id="b5b0d-166">1.0</span></span><br /><br /> <span data-ttu-id="b5b0d-167">1.1</span><span class="sxs-lookup"><span data-stu-id="b5b0d-167">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wscoor/><br /><br /> <https://docs.oasis-open.org/ws-tx/wscoor/2006/06>|  
|<span data-ttu-id="b5b0d-168">wsat</span><span class="sxs-lookup"><span data-stu-id="b5b0d-168">wsat</span></span>|<span data-ttu-id="b5b0d-169">1.0</span><span class="sxs-lookup"><span data-stu-id="b5b0d-169">1.0</span></span><br /><br /> <span data-ttu-id="b5b0d-170">1.1</span><span class="sxs-lookup"><span data-stu-id="b5b0d-170">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wsat/><br /><br /> <https://docs.oasis-open.org/ws-tx/wsat/2006/06>|  
|<span data-ttu-id="b5b0d-171">t</span><span class="sxs-lookup"><span data-stu-id="b5b0d-171">t</span></span>|<span data-ttu-id="b5b0d-172">1.3 より前</span><span class="sxs-lookup"><span data-stu-id="b5b0d-172">Pre-1.3</span></span><br /><br /> <span data-ttu-id="b5b0d-173">1.3</span><span class="sxs-lookup"><span data-stu-id="b5b0d-173">1.3</span></span>|<http://schemas.xmlsoap.org/ws/2005/02/trust/><br /><br /> <https://docs.oasis-open.org/ws-sx/ws-trust/200512>|  
|<span data-ttu-id="b5b0d-174">o</span><span class="sxs-lookup"><span data-stu-id="b5b0d-174">o</span></span>||<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd>|  
|<span data-ttu-id="b5b0d-175">xsd</span><span class="sxs-lookup"><span data-stu-id="b5b0d-175">xsd</span></span>||<https://www.w3.org/2001/XMLSchema>|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="b5b0d-176">トランザクション マネージャー バインディング</span><span class="sxs-lookup"><span data-stu-id="b5b0d-176">Transaction Manager Bindings</span></span>  

 <span data-ttu-id="b5b0d-177">R1001: WS-AT 1.0 トランザクションに参加しているトランザクションマネージャーは、WS-Atomic トランザクションと WS-Coordination メッセージ交換に SOAP 1.1 と WS-Addressing 2004/08 を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-177">R1001: Transaction Managers participating in a WS-AT 1.0 transaction must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="b5b0d-178">R1002 : WS-AT 1.1 トランザクションに参加するトランザクション マネージャーは、SOAP 1.1、WS-Addressing 2005/08 for WS-Atomic Transaction、および WS-Coordination メッセージ交換を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-178">R1002: Transaction Managers participating in a WS-AT 1.1 transaction must use SOAP 1.1 and WS-Addressing 2005/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="b5b0d-179">アプリケーション メッセージは、後で説明するように、これらのバインディングに制限されません。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-179">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="b5b0d-180">トランザクション マネージャー HTTPS バインディング</span><span class="sxs-lookup"><span data-stu-id="b5b0d-180">Transaction Manager HTTPS Binding</span></span>  

 <span data-ttu-id="b5b0d-181">トランザクション マネージャー HTTPS バインディングは、セキュリティを実現してトランザクション ツリー内の送信者と受信者の各ペア間で信頼を確立するトランスポート セキュリティにのみ依存します。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-181">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="b5b0d-182">HTTPS トランスポート構成</span><span class="sxs-lookup"><span data-stu-id="b5b0d-182">HTTPS Transport Configuration</span></span>  

 <span data-ttu-id="b5b0d-183">トランザクション マネージャー ID を確立するために X.509 証明書が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-183">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="b5b0d-184">クライアントおよびサーバーの承認が必要です。クライアントおよびサーバーの承認は、以下のような実装詳細の状態にしておきます。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-184">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
- <span data-ttu-id="b5b0d-185">R1111 : ネットワーク経由で示された X.509 証明書は、発信元コンピューターの完全修飾ドメイン名 (FQDN) と一致するサブジェクト名を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-185">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
- <span data-ttu-id="b5b0d-186">B1112 : X.509 のサブジェクト名のチェックが成功するには、システム内の送信者と受信者の各ペア間で、DNS が機能している必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-186">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="b5b0d-187">アクティベーションと登録のバインド構成</span><span class="sxs-lookup"><span data-stu-id="b5b0d-187">Activation and Registration Binding Configuration</span></span>  

 <span data-ttu-id="b5b0d-188">WCF では、HTTPS 経由の相関関係を持つ要求/応答双方向バインドが必要です。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-188">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="b5b0d-189">(関連付けと要求/応答メッセージ交換パターンの詳細については、WS-AtomicTransaction 仕様のセクション 8 を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-189">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="b5b0d-190">2PC プロトコルのバインディング構成</span><span class="sxs-lookup"><span data-stu-id="b5b0d-190">2PC Protocol Binding Configuration</span></span>  

 <span data-ttu-id="b5b0d-191">WCF では、HTTPS 経由の一方向 (データグラム) メッセージがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-191">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="b5b0d-192">メッセージ間の関連付けは、実装詳細の状態にしておきます。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-192">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="b5b0d-193">B1131: 実装では `wsa:ReferenceParameters` 、WCF の2pc メッセージの相関関係を実現するために WS-Addressing に記載されているようにをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-193">B1131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="b5b0d-194">トランザクション マネージャーによる混合セキュリティ バインディング</span><span class="sxs-lookup"><span data-stu-id="b5b0d-194">Transaction Manager Mixed Security Binding</span></span>  

 <span data-ttu-id="b5b0d-195">これは、ID を確立するために、トランスポート セキュリティを WS-Coordination 発行済みトークン モデルと組み合わせて使用する代替の (混合モードの) バインディングです。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-195">This is an alternate (mixed mode) binding that uses transport security combined with the WS-Coordination Issued Token model for identity establishment purposes.</span></span> <span data-ttu-id="b5b0d-196">2 つのバインディングを区別する要素は、アクティベーションと登録のみです。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-196">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="b5b0d-197">HTTPS トランスポート構成</span><span class="sxs-lookup"><span data-stu-id="b5b0d-197">HTTPS Transport Configuration</span></span>  

 <span data-ttu-id="b5b0d-198">トランザクション マネージャー ID を確立するために X.509 証明書が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-198">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="b5b0d-199">クライアントおよびサーバーの承認が必要です。クライアントおよびサーバーの承認は、以下のような実装詳細の状態にしておきます。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-199">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="b5b0d-200">アクティベーション メッセージのバインド構成</span><span class="sxs-lookup"><span data-stu-id="b5b0d-200">Activation Message Binding Configuration</span></span>  

 <span data-ttu-id="b5b0d-201">アクティベーション メッセージは通常、アプリケーションとローカルのトランザクション マネージャー間で発生するため、相互運用には参加しません。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-201">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="b5b0d-202">B1221: WCF では、アクティベーションメッセージに双方向 HTTPS バインド (「 [メッセージングプロトコル](messaging-protocols.md)」で説明) を使用します。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-202">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="b5b0d-203">要求/応答メッセージは、WS-AT 1.0 の WS-Addressing 2004/08 と WS-AT 1.1 の WS-Addressing 2005/08 を使用して関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-203">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="b5b0d-204">WS-AtomicTransaction 仕様のセクション 8 では、関連付けとメッセージ交換のパターンについて詳細に説明されています。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-204">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
- <span data-ttu-id="b5b0d-205">R1222 : `CreateCoordinationContext` を受信すると、コーディネーターは、関連付けられている秘密の `SecurityContextToken` を使用して `STx` を発行します。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-205">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="b5b0d-206">このトークンは、WS-Trust の仕様に従って、`t:IssuedTokens` ヘッダー内に返されます。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-206">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
- <span data-ttu-id="b5b0d-207">R1223 : アクティベーションが既存のコーディネーション コンテキスト内で発生した場合、既存のコンテキストに関連付けられた `t:IssuedTokens` がある `SecurityContextToken` ヘッダーは、`CreateCoordinationContext` メッセージでフローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-207">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="b5b0d-208">`t:IssuedTokens`送信メッセージに添付するための新しいヘッダーを生成する必要があり `wscoor:CreateCoordinationContextResponse` ます。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-208">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="b5b0d-209">登録メッセージのバインディング構成</span><span class="sxs-lookup"><span data-stu-id="b5b0d-209">Registration Message Binding Configuration</span></span>  

 <span data-ttu-id="b5b0d-210">B1231: WCF では、双方向の HTTPS バインド (「 [メッセージングプロトコル](messaging-protocols.md)」で説明) を使用します。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-210">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](messaging-protocols.md)).</span></span> <span data-ttu-id="b5b0d-211">要求/応答メッセージは、WS-AT 1.0 の WS-Addressing 2004/08 と WS-AT 1.1 の WS-Addressing 2005/08 を使用して関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-211">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="b5b0d-212">WS-AtomicTransaction 仕様のセクション 8 では、関連付けとメッセージ交換のパターンについて詳細に説明されています。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-212">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="b5b0d-213">R1232: 送信 `wscoor:Register` メッセージには、 `IssuedTokenOverTransport` 「 [セキュリティプロトコル](security-protocols.md)」で説明されている認証モードを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-213">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](security-protocols.md).</span></span>  
  
 <span data-ttu-id="b5b0d-214">`wsse:Timestamp`要素は、発行されたを使用して署名する必要があり `SecurityContextToken STx` ます。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-214">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="b5b0d-215">この署名は特定のトランザクションに関連付けられたトークンを所有していることの証明であり、トランザクションに登録されている参加要素の認証で使用されます。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-215">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="b5b0d-216">RegistrationResponse メッセージは、HTTPS を使用して返信されます。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-216">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="b5b0d-217">2PC プロトコルのバインディング構成</span><span class="sxs-lookup"><span data-stu-id="b5b0d-217">2PC Protocol Binding Configuration</span></span>  

 <span data-ttu-id="b5b0d-218">WCF では、HTTPS 経由の一方向 (データグラム) メッセージがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-218">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="b5b0d-219">メッセージ間の関連付けは、実装詳細の状態にしておきます。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-219">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="b5b0d-220">B1241: 実装では `wsa:ReferenceParameters` 、WCF の2pc メッセージの相関関係を実現するために WS-Addressing に記載されているようにをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-220">B1241: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="b5b0d-221">アプリケーション メッセージ交換</span><span class="sxs-lookup"><span data-stu-id="b5b0d-221">Application Message Exchange</span></span>  

 <span data-ttu-id="b5b0d-222">アプリケーションでは、バインディングが次のセキュリティ要件を満たしている限り、アプリケーション間メッセージに任意のバインディングを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-222">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
- <span data-ttu-id="b5b0d-223">R2001 : アプリケーション間メッセージでは、メッセージのヘッダーの `t:IssuedTokens` に加えて `CoordinationContext` ヘッダーをフローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-223">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
- <span data-ttu-id="b5b0d-224">R2002 : `t:IssuedToken` の整合性と機密性が提供される必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-224">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="b5b0d-225">`CoordinationContext` ヘッダーには `wscoor:Identifier` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-225">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="b5b0d-226">の定義では `xsd:AnyURI` 絶対 uri と相対 uri の両方を使用できますが、WCF で `wscoor:Identifiers` は絶対 uri であるのみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-226">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="b5b0d-227">B2003: のが `wscoor:Identifier` `wscoor:CoordinationContext` 相対 URI の場合、トランザクション WCF サービスからエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-227">B2003: If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="b5b0d-228">メッセージの例</span><span class="sxs-lookup"><span data-stu-id="b5b0d-228">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="b5b0d-229">CreateCoordinationContext 要求/応答メッセージ</span><span class="sxs-lookup"><span data-stu-id="b5b0d-229">CreateCoordinationContext Request/Response Messages</span></span>  

 <span data-ttu-id="b5b0d-230">次のメッセージは、要求/応答のパターンに従います。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-230">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a><span data-ttu-id="b5b0d-231">CreateCoordinationContext WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="b5b0d-231">CreateCoordinationContext with WSCoor 1.0</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wscoor/CreateCoordinationContext</Action>  
    <a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
    <a:ReplyTo>  
      <Address>https://...</a:Address>  
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security>  
      <u:Timestamp>  
        <wsu:Created>2005-12-15T23:36:09.921Z</wsu:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</wsu:Expires>  
      </u:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:CreateCoordinationContext>  
      <wscoor:CoordinationType>...</wscoor:CoordinationType>  
    </wscoor:CreateCoordinationContext>  
  </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a><span data-ttu-id="b5b0d-232">WSCoor 1.1 での CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="b5b0d-232">CreateCoordinationContext with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>
<s:Header>  
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContext</Action>  
<a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
<a:ReplyTo>
<Address>https://...</a:Address>
</a:ReplyTo>
<a:To>https://...</a:To>
<wsse:Security>  
 <u:Timestamp>  
<wsu:Created>2005-12-15T23:36:09.921Z</wsu:Created>  
<wsu:Expires>2005-12-15T23:41:09.921Z</wsu:Expires>  
</u:Timestamp>
</wsse:Security>
</s:Header>
<s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
<wscoor:CreateCoordinationContext>  
<wscoor:CoordinationType>...</wscoor:CoordinationType>  
</wscoor:CreateCoordinationContext>  
 </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse-with-trust-pre-13-and-wscoor-10"></a><span data-ttu-id="b5b0d-233">Trust Pre-1.3 および WSCoor 1.0 での CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="b5b0d-233">CreateCoordinationContextResponse with Trust Pre-1.3 and WSCoor 1.0</span></span>  
  
```xml  
<s:Envelope>  
  <!-- Data below is shown in the clear for  
       illustration purposes only. -->  
  <s:Header>  
    <a:Action>./ws/2004/10/wscoor/CreateCoordinationContextResponse </a:Action>  
    <a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
    <a:To s:mustUnderstand="1">https://... </a:To>  
    <t:IssuedTokens>  
 <wst:RequestSecurityTokenResponse
    xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
    xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"
    xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"  
    xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
    xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
    <wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
    <wst:RequestedSecurityToken>  
      <wsc:SecurityContextToken>  
        <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
        </wssu:Identifier>  
      </wsc:SecurityContextToken>
    </wst:RequestedSecurityToken>  
    <wsp:AppliesTo>  
        http://fabrikam123.com/CCi  
    </wsp:AppliesTo>
    <wst:RequestedAttachedReference>  
      <wsse:SecurityTokenReference >  
        <wsse:Reference
           ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
           URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedAttachedReference>  
    <wst:RequestedUnattachedReference>  
      <wsse:SecurityTokenReference>  
        <wsse:Reference
          ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
          URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedUnattachedReference>  
    <wst:RequestedProofToken>  
      <wst:BinarySecret
        Type="http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey">  
        <!-- base64 encoded value -->  
      </wst:BinarySecret>  
    </wst:RequestedProofToken>  
    <wst:Lifetime>  
      <wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
      <wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
    </wst:Lifetime>  
    <wst:KeySize>256</wst:KeySize>  
</wst:RequestSecurityTokenResponse>  
    </t:IssuedTokens>  
    <o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="_0">  
        <u:Created>2005-12-15T23:36:12.015Z</u:Created>  
        <u:Expires>2005-12-15T23:41:12.015Z</u:Expires>  
      </u:Timestamp>  
    </o:Security>  
  </s:Header>  
  <s:Body>  
    <wscoor:CreateCoordinationContextResponse>  
      <wscoor:CoordinationContext>  
        <wscoor:Identifier>  
     http://fabrikam123.com/CCi  
      </wscoor:Identifier>  
        <wscoor:Expires>...</wscoor:Expires>  
        <wscoor:CoordinationType>...</wscoor:CoordinationType>  
        <wscoor:RegistrationService>  
          <a:Address>https://...</a:Address>  
          <a:ReferenceParameters>  
             ...  
          </a:ReferenceParameters>  
        </wscoor:RegistrationService>  
      </wscoor:CoordinationContext>  
    </wscoor:CreateCoordinationContextResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a><span data-ttu-id="b5b0d-234">Trust 1.3 および WSCoor 1.1 での CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="b5b0d-234">CreateCoordinationContextResponse with Trust 1.3 and WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<!-- Data below is shown in the clear for illustration purposes only. -->
<s:Header>
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContextResponse </a:Action>  
<a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
<a:To s:mustUnderstand="1">https://... </a:To>
<t:IssuedTokens>
<wst:RequestSecurityTokenResponse
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"
xmlns:wst="http://docs.oasis-open.org/ws-sx/ws-trust/200512"  
xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
<wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
<wst:RequestedSecurityToken>
<wsc:SecurityContextToken>
<wssu:Identifier> http://fabrikam123.com/SCTi  
</wssu:Identifier>
</wsc:SecurityContextToken>
</wst:RequestedSecurityToken>
<wsp:AppliesTo> http://fabrikam123.com/CCi </wsp:AppliesTo>  
<wst:RequestedAttachedReference>
<wsse:SecurityTokenReference >
<wsse:Reference  
  ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
  URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>
</wst:RequestedAttachedReference>
<wst:RequestedUnattachedReference>
<wsse:SecurityTokenReference>
<wsse:Reference  
 ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
 URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>
</wst:RequestedUnattachedReference>
<wst:RequestedProofToken>
<wst:BinarySecret  
  Type="http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey">  
  <!-- base64 encoded value -->
</wst:BinarySecret>
</wst:RequestedProofToken>
<wst:Lifetime>
<wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
<wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
</wst:Lifetime>
<wst:KeySize>256</wst:KeySize>
</wst:RequestSecurityTokenResponse>
</t:IssuedTokens>
<o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
<u:Timestamp u:Id="_0">
<u:Created>2005-12-15T23:36:12.015Z</u:Created>
<u:Expires>2005-12-15T23:41:12.015Z</u:Expires>
</u:Timestamp>
</o:Security>
</s:Header>
<s:Body>
<wscoor:CreateCoordinationContextResponse>
<wscoor:CoordinationContext>
<wscoor:Identifier> http://fabrikam123.com/CCi  
</wscoor:Identifier>
<wscoor:Expires>...</wscoor:Expires>  
<wscoor:CoordinationType>...</wscoor:CoordinationType>  
<wscoor:RegistrationService>
<a:Address>https://...</a:Address>  
<a:ReferenceParameters> ...  
</a:ReferenceParameters>  
</wscoor:RegistrationService>
</wscoor:CoordinationContext>
</wscoor:CreateCoordinationContextResponse>
</s:Body>
</s:Envelope>  
```  
  
### <a name="registration-messages"></a><span data-ttu-id="b5b0d-235">登録メッセージ</span><span class="sxs-lookup"><span data-stu-id="b5b0d-235">Registration Messages</span></span>  

 <span data-ttu-id="b5b0d-236">次のメッセージは、登録メッセージです。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-236">The following messages are registration messages.</span></span>  
  
#### <a name="register-with-wscoor-10"></a><span data-ttu-id="b5b0d-237">WSCoor 1.0 に登録する</span><span class="sxs-lookup"><span data-stu-id="b5b0d-237">Register with WSCoor 1.0</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://schemas.xmlsoap.org/ws/2004/10/wscoor/Register</a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>https://...</a:Address>
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security
      s:mustUnderstand="1"
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsc:SecurityContextToken>  
      <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
      </wssu:Identifier>  
      </wsc:SecurityContextToken>  
      <!-- supporting signature over the timestamp -->  
      <wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
        <ds:SignedInfo>  
          <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
          <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>  
          <ds:Reference URI="#_0">  
            <ds:Transforms>  
              <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
            </ds:Transforms>  
            <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>  
            <ds:DigestValue>  
              alRzyhjLgoUOYoh8cx4n75eTcUk=  
            </ds:DigestValue>  
          </ds:Reference>  
        </ds:SignedInfo>  
        <ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=</ds:SignatureValue>  
        <ds:KeyInfo>  
          <wsse:SecurityTokenReference  
            xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
            <wsse:Reference
              URI="http://fabrikam123.com/SCTi"/>  
          </wsse:SecurityTokenReference>  
        </ds:KeyInfo>  
      </wsse:Signature>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:Register>  
      <wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
      <wscoor:ParticipantProtocolService>  
        <a:Address>https://... </a:Address>  
      </wscoor:ParticipantProtocolService>  
    </wscoor:Register>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-with-wscoor-11"></a><span data-ttu-id="b5b0d-238">WSCoor 1.1 での Register</span><span class="sxs-lookup"><span data-stu-id="b5b0d-238">Register with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/Register</a:Action>
<a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
<a:ReplyTo>
<a:Address>https://...</a:Address>
</a:ReplyTo>  
<a:To>https://...</a:To>
<wsse:Security
s:mustUnderstand="1"
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
<wssu:Timestamp wssu:Id="_0" >
<wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
<wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
</wssu:Timestamp>
<wsc:SecurityContextToken>
<wssu:Identifier> http://fabrikam123.com/SCTi  
</wssu:Identifier>
</wsc:SecurityContextToken>
<!-- supporting signature over the timestamp -->  
<wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
<ds:SignedInfo>
<ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>
<ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>
<ds:Reference URI="#_0">
<ds:Transforms>
<ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>
</ds:Transforms>
<ds:DigestMethod  
Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
<ds:DigestValue> alRzyhjLgoUOYoh8cx4n75eTcUk=  
</ds:DigestValue>
</ds:Reference>
</ds:SignedInfo>  
<ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=  
</ds:SignatureValue>  
<ds:KeyInfo>
<wsse:SecurityTokenReference xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
  <wsse:Reference URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>
</ds:KeyInfo>
</wsse:Signature>
</wsse:Security>
</s:Header>
<s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
<wscoor:Register>
<wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
<wscoor:ParticipantProtocolService>
<a:Address>https://... </a:Address>  
</wscoor:ParticipantProtocolService>
</wscoor:Register>
</s:Body>
</s:Envelope>  
```  
  
#### <a name="register-response-with-wscoor-10"></a><span data-ttu-id="b5b0d-239">WSCoor 1.0 での応答の登録</span><span class="sxs-lookup"><span data-stu-id="b5b0d-239">Register Response with WSCoor 1.0</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>  
      http://schemas.xmlsoap.org/ws/2004/10/wscoor/RegisterResponse  
    </a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
    <a:RelatesTo>  
      urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e
    </a:RelatesTo>  
    <a:To>https://...</a:To>  
    <wsse:Security
      s:mustUnderstand="1"
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp>  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:RegisterResponse>  
      <wscoor:CoordinatorProtocolService>  
        <a:Address>https://...</a:Address>  
        <a:ReferenceParameters>  
          ...  
        </a:ReferenceParameters>  
      </wscoor:CoordinatorProtocolService>  
    </wscoor:RegisterResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-response-with-wscoor-11"></a><span data-ttu-id="b5b0d-240">WSCoor 1.1 での Register Response</span><span class="sxs-lookup"><span data-stu-id="b5b0d-240">Register Response with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>
<a:Action> http://docs.oasis-open.org/ws-tx/wscoor/2006/06/RegisterResponse  
</a:Action>
<a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
<a:RelatesTo> urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e </a:RelatesTo>  
<a:To>https://...</a:To>
<wsse:Security
s:mustUnderstand="1"
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
<wssu:Timestamp>
<wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
<wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
</wssu:Timestamp>
</wsse:Security>
</s:Header>
<s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
<wscoor:RegisterResponse>
<wscoor:CoordinatorProtocolService>  
<a:Address>https://...</a:Address>  
<a:ReferenceParameters> ... </a:ReferenceParameters>  
</wscoor:CoordinatorProtocolService>
</wscoor:RegisterResponse>
</s:Body>
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="b5b0d-241">2 フェーズ コミット プロトコル メッセージ</span><span class="sxs-lookup"><span data-stu-id="b5b0d-241">Two Phase Commit Protocol Messages</span></span>  

 <span data-ttu-id="b5b0d-242">次のメッセージは、2 フェーズ コミット (2PC) プロトコルに関連しています。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-242">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit-with-wsat-10"></a><span data-ttu-id="b5b0d-243">WSAT 1.0 を使用してコミットする</span><span class="sxs-lookup"><span data-stu-id="b5b0d-243">Commit with WSAT 1.0</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wsat/Commit</a:Action>  
    <a:To>https://...</a:To>  
    <wsse:Security
      s:mustUnderstand="1"
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
   </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wsat:Commit />  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="commit-with-wsat-11"></a><span data-ttu-id="b5b0d-244">WSAT 1.1 での Commit</span><span class="sxs-lookup"><span data-stu-id="b5b0d-244">Commit with WSAT 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>
<a:Action>http://docs.oasis-open.org/ws-tx/wsat/2006/06</a:Action>  
<a:To>https://...</a:To>
<wsse:Security
s:mustUnderstand="1"
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
<wssu:Timestamp wssu:Id="_0" >
<wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
<wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
</wssu:Timestamp>
</wsse:Security>
</s:Header>
<s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
<wsat:Commit />
</s:Body>
</s:Envelope>  
```  
  
### <a name="application-messages"></a><span data-ttu-id="b5b0d-245">アプリケーション メッセージ</span><span class="sxs-lookup"><span data-stu-id="b5b0d-245">Application Messages</span></span>  

 <span data-ttu-id="b5b0d-246">次のメッセージは、アプリケーション メッセージです。</span><span class="sxs-lookup"><span data-stu-id="b5b0d-246">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="b5b0d-247">アプリケーション メッセージ (要求)</span><span class="sxs-lookup"><span data-stu-id="b5b0d-247">Application message-Request</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
<!-- Addressing headers, all signed-->  
    <wsse:Security s:mustUnderstand="1">  
      <wssu:Timestamp wssu:Id="timestamp">
        <wssu:Created>2005-10-25T06:29:18.703Z</wssu:Created>  
        <wssu:Expires>2005-10-25T06:34:18.703Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsse:BinarySecurityToken
          wssu:Id="IA_Certificate"
          ValueType="...#X509v3"
          EncodingType="...#Base64Binary">  
        <!-- IA certificate -->  
      </wsse:BinarySecurityToken>  
      <e:EncryptedKey Id="encrypted_key">  
            <!-- ephemeral key encrypted for PA certificate -->
        <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
          <e:DataReference URI="#encrypted_body"/>  
          <e:DataReference URI="#encrypted_CCi"/>  
          <e:DataReference URI="#encrypted_issuedtokens"/>  
        </e:ReferenceList>  
      </e:EncryptedKey>  
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <!-- signature over Addressing headers, Timestamp, and Body -->  
      </Signature>  
    </wsse:Security>  
    <wsse11:EncryptedHeader>  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader>
      <!-- encrypted wst:IssuedTokens header containing SCTi -->  
      <!-- wst:IssuedTokens header is taken verbatim from message #2 above, omitted for brevity -->  
    </wsse11:EncryptedHeader>  
  </s:Header>  
  <s:Body wssu:Id="body">  
    <!-- encrypted content of the Body element of the application message -->
    <e:EncryptedData Id="encrypted_body"
           Type="http://www.w3.org/2001/04/xmlenc#Content"
           xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
...  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
```
