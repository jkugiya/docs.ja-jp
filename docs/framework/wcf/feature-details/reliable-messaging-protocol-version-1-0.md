---
description: '詳細情報: Reliable Messaging Protocol version 1.0'
title: 信頼できるメッセージング プロトコル バージョン 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: dbd0184fd6ea9f92c96639d71088ac61bec20f3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793598"
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="afcaa-103">信頼できるメッセージング プロトコル バージョン 1.0</span><span class="sxs-lookup"><span data-stu-id="afcaa-103">Reliable Messaging Protocol version 1.0</span></span>

<span data-ttu-id="afcaa-104">このトピックでは、HTTP トランスポートを使用した相互運用に必要な WS-Reliable Messaging 2005 (バージョン 1.0) プロトコルの Windows Communication Foundation (WCF) 実装の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-104">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="afcaa-105">WCF では、このトピックで説明する制約と説明を使用して、WS-Reliable メッセージング仕様に従います。</span><span class="sxs-lookup"><span data-stu-id="afcaa-105">WCF follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="afcaa-106">WS-ReliableMessaging バージョン1.0 プロトコルは、WinFX 以降で実装されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="afcaa-106">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the WinFX.</span></span>

<span data-ttu-id="afcaa-107">WS-Reliable Messaging 2 月2005プロトコルは、によって WCF に実装され <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-107">The WS-Reliable Messaging February 2005 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>

<span data-ttu-id="afcaa-108">便宜上、ここでは次のロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-108">For convenience, the topic uses the following roles:</span></span>

- <span data-ttu-id="afcaa-109">イニシエーター : WS-Reliable メッセージ シーケンスの作成を開始するクライアント</span><span class="sxs-lookup"><span data-stu-id="afcaa-109">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>

- <span data-ttu-id="afcaa-110">レスポンダー : イニシエーターの要求を受け取るサービス</span><span class="sxs-lookup"><span data-stu-id="afcaa-110">Responder: the service that receives the initiator's requests</span></span>

<span data-ttu-id="afcaa-111">このドキュメントでは、次の表に示すプレフィックスと名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-111">This document uses the prefixes and namespaces in the following table.</span></span>

|<span data-ttu-id="afcaa-112">Prefix</span><span class="sxs-lookup"><span data-stu-id="afcaa-112">Prefix</span></span>|<span data-ttu-id="afcaa-113">名前空間</span><span class="sxs-lookup"><span data-stu-id="afcaa-113">Namespace</span></span>|
|------------|---------------|
|<span data-ttu-id="afcaa-114">wsrm</span><span class="sxs-lookup"><span data-stu-id="afcaa-114">wsrm</span></span>|`http://schemas.xmlsoap.org/ws/2005/02/rm`|
|<span data-ttu-id="afcaa-115">netrm</span><span class="sxs-lookup"><span data-stu-id="afcaa-115">netrm</span></span>|`http://schemas.microsoft.com/ws/2006/05/rm`|
|<span data-ttu-id="afcaa-116">s</span><span class="sxs-lookup"><span data-stu-id="afcaa-116">s</span></span>|`http://www.w3.org/2003/05/soap-envelope`|
|<span data-ttu-id="afcaa-117">wsa</span><span class="sxs-lookup"><span data-stu-id="afcaa-117">wsa</span></span>|`http://schemas.xmlsoap.org/ws/2005/08/addressing`|
|<span data-ttu-id="afcaa-118">wsse</span><span class="sxs-lookup"><span data-stu-id="afcaa-118">wsse</span></span>|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd`|

## <a name="messaging"></a><span data-ttu-id="afcaa-119">メッセージング</span><span class="sxs-lookup"><span data-stu-id="afcaa-119">Messaging</span></span>

### <a name="sequence-establishment-messages"></a><span data-ttu-id="afcaa-120">シーケンス確立メッセージ</span><span class="sxs-lookup"><span data-stu-id="afcaa-120">Sequence Establishment Messages</span></span>

<span data-ttu-id="afcaa-121">WCF `CreateSequence` では、メッセージとメッセージを実装して、 `CreateSequenceResponse` 信頼性の高いメッセージシーケンスを確立します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-121">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="afcaa-122">次の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-122">The following constraints apply:</span></span>

- <span data-ttu-id="afcaa-123">B1101: WCF イニシエーターは、メッセージ内にオプションの Expires 要素を生成しません `CreateSequence` 。また、メッセージに要素が含まれている場合は、 `CreateSequence` `Offer` 要素内の省略可能な要素を生成 `Expires` しません `Offer` 。</span><span class="sxs-lookup"><span data-stu-id="afcaa-123">B1101: The WCF Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>

- <span data-ttu-id="afcaa-124">B1102: メッセージにアクセスするときに、 `CreateSequence` WCF は `Responder` 両方の `Expires` 要素を送受信しますが、これらの要素の値は使用しません。</span><span class="sxs-lookup"><span data-stu-id="afcaa-124">B1102: When accessing the `CreateSequence` message, the WCF`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>

<span data-ttu-id="afcaa-125">WS-ReliableMessaging では、セッションを形成する、相関する 2 つの逆方向シーケンスを確立するために、`Offer` 機構が導入されています。</span><span class="sxs-lookup"><span data-stu-id="afcaa-125">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>

- <span data-ttu-id="afcaa-126">R1103 : `CreateSequence` に `Offer` 要素が含まれている場合、Reliable メッセージング レスポンダーは、シーケンスを受け入れ、`CreateSequenceResponse` 要素を含む `wsrm:Accept` で応答して、相関する 2 つの逆方向シーケンスを形成するか、`CreateSequence` 要求を拒否する必要があります。</span><span class="sxs-lookup"><span data-stu-id="afcaa-126">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>

- <span data-ttu-id="afcaa-127">R1104 : 逆方向シーケンスでフローする `SequenceAcknowledgement` およびアプリケーション メッセージは、`ReplyTo` の `CreateSequence` エンドポイント参照に送信される必要があります。</span><span class="sxs-lookup"><span data-stu-id="afcaa-127">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="afcaa-128">R1105 : `AcksTo` の `ReplyTo` エンドポイント参照と `CreateSequence` エンドポイント参照には、オクテット単位で一致するアドレス値が必要です。</span><span class="sxs-lookup"><span data-stu-id="afcaa-128">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>

  <span data-ttu-id="afcaa-129">WCF レスポンダーは、 `AcksTo` `ReplyTo` シーケンスを作成する前に、と EPR の URI 部分が同一であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-129">The WCF Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>

- <span data-ttu-id="afcaa-130">R1106 : `AcksTo` の `ReplyTo` および `CreateSequence` の各エンドポイント参照は、参照パラメーターの同じセットを持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="afcaa-130">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>

  <span data-ttu-id="afcaa-131">WCF では、との [参照パラメーター] が同じであることを前提としていますが、 `AcksTo` `ReplyTo` 受信確認 `CreateSequence` `ReplyTo` と逆方向シーケンスメッセージのエンドポイント参照から [参照パラメーター] を使用していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="afcaa-131">WCF does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>

- <span data-ttu-id="afcaa-132">R1107 : `Offer` 機構を使用して 2 つの逆方向シーケンスを確立した場合、逆方向シーケンスでフローする `SequenceAcknowledgement` およびアプリケーション メッセージは、`ReplyTo` の `CreateSequence` エンドポイント参照に送信される必要があります。</span><span class="sxs-lookup"><span data-stu-id="afcaa-132">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="afcaa-133">R1108 : Offer 機構を使用して 2 つの逆方向シーケンスを確立した場合、`[address]` の `wsrm:AcksTo` 要素の `wsrm:Accept` エンドポイント参照子要素の `CreateSequenceResponse` プロパティは、`CreateSequence` の送信先 URI とバイト単位で一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="afcaa-133">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>

- <span data-ttu-id="afcaa-134">R1109 : `Offer` 機構を使用して 2 つの逆方向シーケンスを確立した場合、イニシエーターによって送信されたメッセージとレスポンダーによるメッセージの受信確認は、同じエンドポイント参照に送信される必要があります。</span><span class="sxs-lookup"><span data-stu-id="afcaa-134">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>

  <span data-ttu-id="afcaa-135">WCF は WS-Reliable メッセージングを使用して、イニシエーターとレスポンダーの間に信頼できるセッションを確立します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-135">WCF uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> <span data-ttu-id="afcaa-136">WCF の WS-Reliable メッセージング実装は、一方向、要求/応答、および全二重のメッセージングパターンに対して信頼できるセッションを提供します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-136">WCF's WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="afcaa-137">の WS-Reliable メッセージング `Offer` 機構を `CreateSequence` / `CreateSequenceResponse` 使用すると、関連する2つの逆方向シーケンスを確立し、すべてのメッセージエンドポイントに適したセッションプロトコルを提供できます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-137">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="afcaa-138">WCF では、セッション整合性に対するエンドツーエンドの保護を含むこのようなセッションに対してセキュリティ保証が提供されるため、同じパーティを対象としたメッセージが同じ送信先に到着することを確認することが実用的です。</span><span class="sxs-lookup"><span data-stu-id="afcaa-138">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="afcaa-139">また、これにより、アプリケーション メッセージにシーケンス受信確認を抱き合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-139">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="afcaa-140">したがって、制約 R1104、R1105、および R1108 は WCF に適用されます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-140">Therefore, constraints R1104, R1105, and R1108 apply to WCF.</span></span>

<span data-ttu-id="afcaa-141">`CreateSequence` メッセージの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-141">An example of a `CreateSequence` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <a:Action s:mustUnderstand="1">
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequence
    </a:Action>
    <a:ReplyTo>
      <a:Address>
         http://Business456.com/clientA
      </a:Address>
    </a:ReplyTo>
    <a:MessageID>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </a:MessageID>
    <a:To s:mustUnderstand="1">
      http://Business456.com/clientA
    </a:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequence>
      <wsrm:AcksTo>
       <wsa:Address>
         http://Business456.com/clientA
       </wsa:Address>
     </wsrm:AcksTo>
     <wsrm:Offer>
      <wsrm:Identifier>
        urn:uuid:0afb8d36-bf26-4776-b8cf-8c91fddb5496
      </wsrm:Identifier>
     </wsrm:Offer>
   </wsrm:CreateSequence>
  </s:Body>
</s:Envelope>
```

 <span data-ttu-id="afcaa-142">`CreateSequenceResponse` メッセージの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-142">An example of a `CreateSequenceResponse` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <a:Action s:mustUnderstand="1">
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequenceResponse
    </a:Action>
    <a:RelatesTo>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </a:RelatesTo>
    <a:To s:mustUnderstand="1">
      http://Business456.com/clientA
    </a:To>
  </s:Header>
  <s:Body>
   <wsrm:CreateSequenceResponse>
    <Identifier>
     urn:uuid:eea0a36c-b38a-43e8-8c76-2fabe2d76386
    </Identifier>
    <Accept>
    <AcksTo>
      <a:Address>
        http://BusinessABC.com/serviceA
      </a:Address>
    </AcksTo>
    </Accept>
   </wsrm:CreateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequence"></a><span data-ttu-id="afcaa-143">Sequence</span><span class="sxs-lookup"><span data-stu-id="afcaa-143">Sequence</span></span>

<span data-ttu-id="afcaa-144">シーケンスに適用される制約を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-144">The following is a list of constraints that apply to sequences:</span></span>

- <span data-ttu-id="afcaa-145">B1201: WCF は `xs:long` 、最大値である9223372036854775807を超えるシーケンス番号を生成してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="afcaa-145">B1201:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>

- <span data-ttu-id="afcaa-146">B1202: WCF は、アクション URI がである空の最後のメッセージを常に生成 `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-146">B1202:WCF always generates an empty-bodied last message with the action URI of `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

- <span data-ttu-id="afcaa-147">B1203: WCF は `LastMessage` 、アクション URI がでない限り、要素を含むシーケンスヘッダーを含むメッセージを受信して配信し `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-147">B1203: WCF receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

<span data-ttu-id="afcaa-148">シーケンス ヘッダーのサンプル</span><span class="sxs-lookup"><span data-stu-id="afcaa-148">An example of a Sequence Header.</span></span>

```xml
<wsrm:Sequence>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
  <wsrm:MessageNumber>
    10
  </wsrm:MessageNumber>
  <wsrm:LastMessage/>
 </wsrm:Sequence>
```

### <a name="ackrequested-header"></a><span data-ttu-id="afcaa-149">AckRequested ヘッダー</span><span class="sxs-lookup"><span data-stu-id="afcaa-149">AckRequested Header</span></span>

<span data-ttu-id="afcaa-150">WCF は `AckRequested` 、キープアライブメカニズムとしてヘッダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-150">WCF uses `AckRequested` Header as a keep-alive mechanism.</span></span> <span data-ttu-id="afcaa-151">WCF では、省略可能な要素は生成されません `MessageNumber` 。</span><span class="sxs-lookup"><span data-stu-id="afcaa-151">WCF does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="afcaa-152">要素を含むヘッダーを含むメッセージを受信すると `AckRequested` `MessageNumber` 、 `MessageNumber` 次の例に示すように、WCF は要素の値を無視します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-152">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, WCF ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="afcaa-153">SequenceAcknowledgement ヘッダー</span><span class="sxs-lookup"><span data-stu-id="afcaa-153">SequenceAcknowledgement Header</span></span>

<span data-ttu-id="afcaa-154">WCF では、WS-Reliable メッセージングに用意されているシーケンス受信確認に豚メカニズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-154">WCF uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>

- <span data-ttu-id="afcaa-155">R1401 : `Offer` 機構を使用して 2 つの逆方向シーケンスを確立した場合、目的の受信者に送信されるアプリケーション メッセージに、`SequenceAcknowledgement` ヘッダーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-155">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>

- <span data-ttu-id="afcaa-156">B1402: WCF は、シーケンスメッセージを受信する前に受信確認を生成する必要があります (たとえば、メッセージを満たすには、 `AckRequested` `SequenceAcknowledgement` 次の例に示すように、wcf は範囲0-0 を含むヘッダーを生成します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-156">B1402: When WCF must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), WCF generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="0" Lower="0"/>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="afcaa-157">B1403: WCF は `SequenceAcknowledgement` 要素を含むヘッダーを生成 `Nack` しませんが、要素をサポート `Nack` します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-157">B1403: WCF does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>

### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="afcaa-158">WS-ReliableMessaging エラー</span><span class="sxs-lookup"><span data-stu-id="afcaa-158">WS-ReliableMessaging Faults</span></span>

<span data-ttu-id="afcaa-159">WS-Reliable メッセージングエラーの WCF 実装に適用される制約の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-159">The following is a list of constraints that apply to the WCF implementation of WS-Reliable Messaging faults:</span></span>

- <span data-ttu-id="afcaa-160">B1501: WCF ではエラーは生成されません `MessageNumberRollover` 。</span><span class="sxs-lookup"><span data-stu-id="afcaa-160">B1501: WCF does not generate `MessageNumberRollover` faults.</span></span>

- <span data-ttu-id="afcaa-161">B1502: WCF エンドポイントは `CreateSequenceRefused` 、仕様で説明されているようにエラーを生成する場合があります。</span><span class="sxs-lookup"><span data-stu-id="afcaa-161">B1502:WCF endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>

- <span data-ttu-id="afcaa-162">B1503: サービスエンドポイントが接続制限に達し、新しい接続を処理できない場合、WCF は `CreateSequenceRefused` 次の `netrm:ConnectionLimitReached` 例に示すように、追加のエラーサブコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-162">B1503:When the service endpoint reaches its connection limit and cannot process new connections, WCF generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>

  ```xml
  <s:Envelope>
    <s:Header>
      <wsa:Action>
        http://schemas.xmlsoap.org/ws/2005/08/addressing/fault
      </wsa:Action>
    </s:Header>
    <s:Body>
      <s:Fault>
        <s:Code>
          <s:Value>
            s:Receiver
          </s:Value>
          <s:Subcode>
            <s:Value>
              wsrm:CreateSequenceRefused
            </s:Value>
            <s:Subcode>
              <s:Value>
                netrm:ConnectionLimitReached
              </s:Value>
            </s:Subcode>
          </s:Subcode>
        </s:Code>
        <s:Reason>
          <s:Text xml:lang="en">
            [Reason]
          </s:Text>
        </s:Reason>
      </s:Fault>
    </s:Body>
  </s:Envelope>
  ```

### <a name="ws-addressing-faults"></a><span data-ttu-id="afcaa-163">WS-Addressing エラー</span><span class="sxs-lookup"><span data-stu-id="afcaa-163">WS-Addressing Faults</span></span>

<span data-ttu-id="afcaa-164">WS-Reliable メッセージングでは WS-ADDRESSING を使用するため、WCF WS-Reliable メッセージングを実装すると WS-Addressing エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="afcaa-164">Because WS-Reliable Messaging uses WS-Addressing, WCF WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="afcaa-165">このセクションでは、WCF が WS-Reliable メッセージングレイヤーで明示的に生成する WS-Addressing エラーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-165">This section covers the WS-Addressing faults that WCF explicitly generates at the WS-Reliable Messaging layer:</span></span>

- <span data-ttu-id="afcaa-166">B1601: WCF では、次のいずれかに該当する場合に、必要なエラーメッセージのアドレス指定ヘッダーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-166">B1601:WCF generates the fault Message Addressing Header Required when one of the following is true:</span></span>

  - <span data-ttu-id="afcaa-167">メッセージに `Sequence` ヘッダーと `Action` ヘッダーがない。</span><span class="sxs-lookup"><span data-stu-id="afcaa-167">A message is missing a `Sequence` header and an `Action` header.</span></span>

  - <span data-ttu-id="afcaa-168">`CreateSequence` メッセージに `MessageId` ヘッダーがない。</span><span class="sxs-lookup"><span data-stu-id="afcaa-168">A `CreateSequence` message is missing a `MessageId` header.</span></span>

  - <span data-ttu-id="afcaa-169">`CreateSequence` メッセージに `ReplyTo` ヘッダーがない。</span><span class="sxs-lookup"><span data-stu-id="afcaa-169">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>

- <span data-ttu-id="afcaa-170">B1602: WCF は、ヘッダーが欠落していて、 `Sequence` `Action` WS-Reliable メッセージング仕様で認識されていないヘッダーを持つメッセージに対して、応答でサポートされていないエラーアクションを生成します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-170">B1602:WCF generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>

- <span data-ttu-id="afcaa-171">B1603: WCF は、 `CreateSequence` メッセージのアドレス指定ヘッダーの検査に基づいて、エンドポイントがシーケンスを処理しないことを示すために、使用できない障害エンドポイントを生成します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-171">B1603:WCF generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>

## <a name="protocol-composition"></a><span data-ttu-id="afcaa-172">プロトコル コンポジション</span><span class="sxs-lookup"><span data-stu-id="afcaa-172">Protocol Composition</span></span>

### <a name="composition-with-ws-addressing"></a><span data-ttu-id="afcaa-173">WS-Addressing によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="afcaa-173">Composition with WS-Addressing</span></span>

<span data-ttu-id="afcaa-174">WCF では、2つのバージョンの WS-ADDRESSING をサポートしています。 WS-Addressing 2004/08 [WS-FEDERATION] と W3C WS-Addressing 1.0 の推奨事項 [WS-FEDERATION-CORE] と [WS-FEDERATION-SOAP]。</span><span class="sxs-lookup"><span data-stu-id="afcaa-174">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>

<span data-ttu-id="afcaa-175">WS-ReliableMessaging 仕様に記載されているのは、WS-Addressing 2004/08 だけですが、使用する WS-Addressing のバージョンが制限されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="afcaa-175">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="afcaa-176">WCF に適用される制約の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-176">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="afcaa-177">R2101 :WS-Addressing 2004/08 と WS-Addressing 1.0 の両方を WS-ReliableMessaging で使用できます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-177">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>

- <span data-ttu-id="afcaa-178">R2102: 1 つのバージョンの WS-Addressing は、特定の WS-Reliable メッセージングシーケンス、またはメカニズムを使用して関連付けられた逆方向シーケンスのペア全体で使用する必要があり `wsrm:Offer` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-178">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>

### <a name="composition-with-soap"></a><span data-ttu-id="afcaa-179">SOAP によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="afcaa-179">Composition with SOAP</span></span>

<span data-ttu-id="afcaa-180">WCF では、SOAP 1.1 と SOAP 1.2 の両方を WS-Reliable メッセージングと共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-180">WCF supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>

### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="afcaa-181">WS-Security と WS-SecureConversation によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="afcaa-181">Composition with WS-Security and WS-SecureConversation</span></span>

<span data-ttu-id="afcaa-182">WCF では、セキュリティで保護されたトランスポート (HTTPS)、WS-SECURITY によるコンポジション、および WS-Secure メッセージ交換による構成を使用して、WS-Reliable メッセージングシーケンスを保護します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-182">WCF provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="afcaa-183">WCF に適用される制約の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-183">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="afcaa-184">R2301: 個々のメッセージの整合性と機密性だけでなく、WS-Reliable メッセージングシーケンスの整合性を保護するために、WCF では WS-Secure のメッセージ交換を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="afcaa-184">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>

- <span data-ttu-id="afcaa-185">R2302 :WS-ReliableMessaging シーケンスを確立する前に、WS-SecureConversation セッションを確立する必要があります。</span><span class="sxs-lookup"><span data-stu-id="afcaa-185">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>

- <span data-ttu-id="afcaa-186">R2303 : WS-ReliableMessaging シーケンスの有効期間が WS-SecureConversation セッションの有効期間よりも長い場合は、対応する WS-SecureConversation Renewal バインディングを使用して、WS-SecureConversation によって確立された `SecurityContextToken` を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="afcaa-186">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>

- <span data-ttu-id="afcaa-187">B2304 :WS-ReliableMessaging シーケンスまたは相関する逆方向シーケンスのペアは、必ず同じ WS-SecureConversation セッションにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-187">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>

  <span data-ttu-id="afcaa-188">WCF ソースによって、 `wsse:SecurityTokenReference` メッセージの要素拡張セクションに要素が生成され `CreateSequence` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-188">The WCF source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>

- <span data-ttu-id="afcaa-189">R2305: WS-Secure メッセージ交換で構成される場合、メッセージには `CreateSequence` 要素が含まれている必要があり `wsse:SecurityTokenReference` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-189">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>

## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="afcaa-190">WS-ReliableMessaging の WS-Policy アサーション</span><span class="sxs-lookup"><span data-stu-id="afcaa-190">WS-Reliable Messaging WS-Policy Assertion</span></span>

<span data-ttu-id="afcaa-191">WCF では、WS-Reliable のメッセージング WS-Policy アサーションを使用して `wsrm:RMAssertion` 、エンドポイントの機能を記述します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-191">WCF uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="afcaa-192">WCF に適用される制約の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-192">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="afcaa-193">B3001: WCF は `wsrm:RMAssertion` WS-Policy アサーションを `wsdl:binding` 要素にアタッチします。</span><span class="sxs-lookup"><span data-stu-id="afcaa-193">B3001: WCF attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="afcaa-194">WCF では、要素および要素への添付ファイルの両方がサポートさ `wsdl:binding` `wsdl:port` れます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-194">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>

- <span data-ttu-id="afcaa-195">B3002: WCF では、WS-Reliable メッセージングアサーションの次の省略可能なプロパティがサポートされており、WCF でこれらのプロパティを制御でき `ReliableMessagingBindingElement` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-195">B3002: WCF supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the WCF`ReliableMessagingBindingElement`:</span></span>

  - `wsrm:InactivityTimeout`

  - `wsrm:AcknowledgementInterval`

  <span data-ttu-id="afcaa-196">以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-196">The following is an example.</span></span>

  ```xml
  <wsrm:RMAssertion>
    <wsrm:InactivityTimeout Milliseconds="600000" />
    <wsrm:AcknowledgementInterval Milliseconds="200" />
  </wsrm:RMAssertion>
  ```

## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="afcaa-197">WS-ReliableMessaging のフロー制御拡張</span><span class="sxs-lookup"><span data-stu-id="afcaa-197">Flow Control WS-Reliable Messaging Extension</span></span>

<span data-ttu-id="afcaa-198">WCF は WS-Reliable メッセージング拡張機能を使用して、シーケンスメッセージフローに対してさらに厳密な制御を提供します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-198">WCF uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>

<span data-ttu-id="afcaa-199">フロー制御を有効にするには、 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> プロパティをに設定し `true` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-199">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="afcaa-200">WCF に適用される制約の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-200">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="afcaa-201">B4001: 信頼できるメッセージングフロー制御を有効にすると、WCF は `netrm:BufferRemaining` ヘッダーの要素拡張に要素を生成し `SequenceAcknowledgement` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-201">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="afcaa-202">B4002: 信頼できるメッセージングフロー制御を有効にすると、次の `netrm:BufferRemaining` `SequenceAcknowledgement` 例に示すように、WCF では要素がヘッダーに存在する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="afcaa-202">B4002: When Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      http://fabrikam123.com/abc
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>
      8
    </netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="afcaa-203">B4003: WCF では `netrm:BufferRemaining` 、を使用して、信頼できるメッセージの送信先がバッファーできる新しいメッセージの数を示します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-203">B4003: WCF uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>

- <span data-ttu-id="afcaa-204">B4004: WCF Reliable Messaging サービスは、信頼できるメッセージングの送信先アプリケーションがメッセージを迅速に受信できない場合に送信されるメッセージの数を調整します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-204">B4004:The WCF Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="afcaa-205">信頼できるメッセージングの送信先がメッセージをバッファーに保持する場合、要素の値が 0 になります。</span><span class="sxs-lookup"><span data-stu-id="afcaa-205">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>

- <span data-ttu-id="afcaa-206">B4005: WCF は 0 ~ 4096 の範囲の `netrm:BufferRemaining` 整数値を生成し、0 ~ の値214748364を含む整数値を読み取り `xs:int` `maxInclusive` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-206">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>

## <a name="message-exchange-patterns"></a><span data-ttu-id="afcaa-207">メッセージ交換パターン</span><span class="sxs-lookup"><span data-stu-id="afcaa-207">Message Exchange Patterns</span></span>

<span data-ttu-id="afcaa-208">このセクションでは、さまざまなメッセージ交換パターンに WS-Reliable メッセージングを使用する場合の WCF の動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-208">This section describes WCF's behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="afcaa-209">各メッセージ交換パターンについて、次の 2 つの展開シナリオを考えます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-209">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>

- <span data-ttu-id="afcaa-210">アドレス不可能なイニシエーター : イニシエーターはファイアウォールの内側にあります。レスポンダーは HTTP 応答でのみイニシエーターにメッセージを配信できます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-210">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>

- <span data-ttu-id="afcaa-211">アドレス可能なイニシエーター : イニシエーターとレスポンダーの両方に HTTP 要求を送信できます。つまり、逆方向の 2 つの HTTP 接続を確立できます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-211">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>

### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="afcaa-212">一方向 : アドレス不可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="afcaa-212">One-way, Non-addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="afcaa-213">バインド</span><span class="sxs-lookup"><span data-stu-id="afcaa-213">Binding</span></span>

<span data-ttu-id="afcaa-214">WCF は、1つの HTTP チャネルで1つのシーケンスを使用して、一方向のメッセージ交換パターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-214">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="afcaa-215">WCF は、HTTP 要求を使用して RMS から RMD にすべてのメッセージを転送し、HTTP 応答を使用して、RMD から RMS にすべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-215">WCF uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="afcaa-216">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="afcaa-216">CreateSequence Exchange</span></span>

<span data-ttu-id="afcaa-217">WCF イニシエーターは、オファーのないメッセージを生成し `CreateSequence` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-217">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="afcaa-218">WCF レスポンダーは、 `CreateSequence` シーケンスを作成する前に、にオファーがないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-218">The WCF Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="afcaa-219">WCF レスポンダーは、 `CreateSequence` メッセージと共に要求に応答し `CreateSequenceResponse` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-219">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="sequenceacknowledgement"></a><span data-ttu-id="afcaa-220">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="afcaa-220">SequenceAcknowledgement</span></span>

<span data-ttu-id="afcaa-221">WCF イニシエーターは、メッセージメッセージとエラーメッセージを除くすべてのメッセージの応答で受信確認を処理し `CreateSequence` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-221">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="afcaa-222">WCF レスポンダーは、シーケンスとメッセージの両方に対する応答で、スタンドアロンの受信確認を常に生成し `AckRequested` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-222">The WCF Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>

#### <a name="terminatesequence-message"></a><span data-ttu-id="afcaa-223">TerminateSequence メッセージ</span><span class="sxs-lookup"><span data-stu-id="afcaa-223">TerminateSequence message</span></span>

<span data-ttu-id="afcaa-224">WCF は、 `TerminateSequence` 一方向の操作として処理します。つまり、http 応答には、空の本文と http 202 ステータスコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-224">WCF treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>

### <a name="one-way-addressable-initiator"></a><span data-ttu-id="afcaa-225">一方向 : アドレス可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="afcaa-225">One Way, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="afcaa-226">バインド</span><span class="sxs-lookup"><span data-stu-id="afcaa-226">Binding</span></span>

<span data-ttu-id="afcaa-227">WCF は、受信および送信 Http チャネルで1つのシーケンスを使用して、一方向のメッセージ交換パターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-227">WCF provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> <span data-ttu-id="afcaa-228">WCF は、HTTP 要求を使用してすべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-228">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="afcaa-229">すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-229">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="afcaa-230">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="afcaa-230">CreateSequence Exchange</span></span>

<span data-ttu-id="afcaa-231">WCF イニシエーターは、オファーのないメッセージを生成し `CreateSequence` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-231">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="afcaa-232">WCF レスポンダーは、 `CreateSequence` シーケンスを作成する前に、にオファーがないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-232">The WCF Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="afcaa-233">WCF レスポンダーは、 `CreateSequenceResponse` エンドポイント参照でアドレス指定された HTTP 要求でメッセージを送信し `ReplyTo` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-233">The WCF Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>

### <a name="duplex-addressable-initiator"></a><span data-ttu-id="afcaa-234">双方向 : アドレス可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="afcaa-234">Duplex, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="afcaa-235">バインド</span><span class="sxs-lookup"><span data-stu-id="afcaa-235">Binding</span></span>

<span data-ttu-id="afcaa-236">WCF は、受信と送信の HTTP チャネルで2つのシーケンスを使用して、完全に非同期の双方向メッセージ交換パターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-236">WCF provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="afcaa-237">WCF は、HTTP 要求を使用してすべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-237">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="afcaa-238">すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-238">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="afcaa-239">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="afcaa-239">CreateSequence Exchange</span></span>

<span data-ttu-id="afcaa-240">WCF イニシエーターは、オファーを使用してメッセージを生成し `CreateSequence` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-240">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="afcaa-241">WCF レスポンダーは、 `CreateSequence` シーケンスを作成する前に、にオファーがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-241">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="afcaa-242">WCF は、 `CreateSequenceResponse` `CreateSequence` のエンドポイント参照にアドレス指定された HTTP 要求でを送信し `ReplyTo` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-242">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="sequence-lifetime"></a><span data-ttu-id="afcaa-243">シーケンスの有効期間</span><span class="sxs-lookup"><span data-stu-id="afcaa-243">Sequence Lifetime</span></span>

<span data-ttu-id="afcaa-244">WCF では、2つのシーケンスが1つの完全な二重セッションとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-244">WCF treats the two sequences as one fully duplex session.</span></span>

<span data-ttu-id="afcaa-245">1つのシーケンスに障害が発生したエラーが生成されると、WCF は、リモートエンドポイントが両方のシーケンスをフォールトすることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="afcaa-245">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="afcaa-246">1つのシーケンスで障害が発生したエラーを読み取ると、WCF は両方のシーケンスをエラーにします。</span><span class="sxs-lookup"><span data-stu-id="afcaa-246">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>

<span data-ttu-id="afcaa-247">WCF は、その送信シーケンスを終了し、受信シーケンスでメッセージを処理し続けることができます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-247">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="afcaa-248">逆に、WCF では、受信シーケンスの終了を処理し、送信シーケンスでメッセージを送信し続けることができます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-248">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>

### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="afcaa-249">要求/応答 : アドレス不可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="afcaa-249">Request-Reply, Non-Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="afcaa-250">バインド</span><span class="sxs-lookup"><span data-stu-id="afcaa-250">Binding</span></span>

<span data-ttu-id="afcaa-251">WCF は、1つの HTTP チャネルで2つのシーケンスを使用して、一方向および要求/応答メッセージ交換パターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-251">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="afcaa-252">WCF は、HTTP 要求を使用して要求シーケンスのメッセージを送信し、HTTP 応答を使用して応答シーケンスのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-252">WCF uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="afcaa-253">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="afcaa-253">CreateSequence Exchange</span></span>

<span data-ttu-id="afcaa-254">WCF イニシエーターは、オファーを使用してメッセージを生成し `CreateSequence` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-254">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="afcaa-255">WCF レスポンダーは、 `CreateSequence` シーケンスを作成する前に、にオファーがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-255">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="afcaa-256">WCF レスポンダーは、 `CreateSequence` メッセージと共に要求に応答し `CreateSequenceResponse` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-256">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="afcaa-257">一方向のメッセージ</span><span class="sxs-lookup"><span data-stu-id="afcaa-257">One-way Message</span></span>

<span data-ttu-id="afcaa-258">一方向メッセージ交換プロトコルを正常に完了するために、WCF イニシエーターは HTTP 要求で要求シーケンスメッセージを送信し、HTTP 応答でスタンドアロンメッセージを受信し `SequenceAcknowledgement` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-258">To complete a one-way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="afcaa-259">`SequenceAcknowledgement` は、送信されたメッセージの受信確認を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="afcaa-259">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>

<span data-ttu-id="afcaa-260">WCF レスポンダーは、受信確認、エラー、または空の本文と HTTP 202 ステータスコードを持つ応答を使用して、要求に応答できます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-260">The WCF Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>

#### <a name="two-way-messages"></a><span data-ttu-id="afcaa-261">双方向のメッセージ</span><span class="sxs-lookup"><span data-stu-id="afcaa-261">Two Way Messages</span></span>

<span data-ttu-id="afcaa-262">双方向メッセージ交換プロトコルを正常に完了するために、WCF イニシエーターは HTTP 要求で要求シーケンスメッセージを送信し、HTTP 応答で応答シーケンスメッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-262">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="afcaa-263">応答では、送信された要求シーケンス メッセージの受信確認を行う `SequenceAcknowledgement` を送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="afcaa-263">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>

<span data-ttu-id="afcaa-264">WCF レスポンダーは、アプリケーション応答、エラー、または空の本文と HTTP 202 ステータスコードを含む応答を使用して、要求に応答できます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-264">The WCF Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>

<span data-ttu-id="afcaa-265">一方向のメッセージが存在することと、アプリケーション応答のタイミングもあるため、要求シーケンス メッセージのシーケンス番号と応答メッセージのシーケンス番号には相関関係はありません。</span><span class="sxs-lookup"><span data-stu-id="afcaa-265">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>

#### <a name="retrying-replies"></a><span data-ttu-id="afcaa-266">応答の再試行</span><span class="sxs-lookup"><span data-stu-id="afcaa-266">Retrying Replies</span></span>

<span data-ttu-id="afcaa-267">WCF は、双方向のメッセージ交換プロトコルの相関関係について、HTTP 要求/応答の相関関係に依存します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-267">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="afcaa-268">このため、要求シーケンスメッセージが受信確認された場合でも、HTTP 応答が受信確認、ユーザーメッセージ、またはエラーを受信する場合、WCF イニシエーターは要求シーケンスメッセージの再試行を停止しません。</span><span class="sxs-lookup"><span data-stu-id="afcaa-268">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="afcaa-269">WCF レスポンダーは、応答が関連付けられている要求の HTTP 要求レッグで応答を再試行します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-269">The WCF Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>

#### <a name="lastmessage-exchange"></a><span data-ttu-id="afcaa-270">LastMessage の交換</span><span class="sxs-lookup"><span data-stu-id="afcaa-270">LastMessage Exchange</span></span>

<span data-ttu-id="afcaa-271">WCF イニシエーターは、HTTP 要求レッグで空の本文の最後のメッセージを生成して送信します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-271">The WCF Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> <span data-ttu-id="afcaa-272">WCF には応答が必要ですが、実際の応答メッセージは無視されます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-272">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="afcaa-273">WCF レスポンダーは、応答シーケンスの空の最後のメッセージと共に、要求シーケンスの空のメッセージに応答します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-273">The WCF Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>

<span data-ttu-id="afcaa-274">WCF レスポンダーが、アクション URI がではない最後のメッセージを受信すると `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` 、wcf は最後のメッセージを返します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-274">If the WCF Responder receives a last message in which the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, WCF replies with a last message.</span></span> <span data-ttu-id="afcaa-275">双方向メッセージ交換プロトコルの場合、最後のメッセージでアプリケーション メッセージが送信されます。一方向メッセージ交換プロトコルの場合、最後のメッセージは空です。</span><span class="sxs-lookup"><span data-stu-id="afcaa-275">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>

<span data-ttu-id="afcaa-276">WCF レスポンダーは、応答シーケンスの空の最後のメッセージに対する受信確認を必要としません。</span><span class="sxs-lookup"><span data-stu-id="afcaa-276">The WCF Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="afcaa-277">TerminateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="afcaa-277">TerminateSequence Exchange</span></span>

<span data-ttu-id="afcaa-278">すべての要求が有効な応答を受信すると、WCF イニシエーターは、HTTP 要求レッグで要求シーケンスのメッセージを生成して送信し `TerminateSequence` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-278">When all requests have received a valid reply, the WCF Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> <span data-ttu-id="afcaa-279">WCF には応答が必要ですが、実際の応答メッセージは無視されます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-279">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="afcaa-280">WCF レスポンダーは、 `TerminateSequence` 応答シーケンスのメッセージと共に、要求シーケンスのメッセージに応答し `TerminateSequence` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-280">The WCF Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>

<span data-ttu-id="afcaa-281">通常のシャットダウン シーケンスでは、両方の `TerminateSequence` メッセージで完全な `SequenceAcknowledgement` を送信します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-281">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>

### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="afcaa-282">要求/応答 : アドレス可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="afcaa-282">Request/Reply, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="afcaa-283">バインド</span><span class="sxs-lookup"><span data-stu-id="afcaa-283">Binding</span></span>

<span data-ttu-id="afcaa-284">WCF は、受信と送信の HTTP チャネルで2つのシーケンスを使用して、要求/応答メッセージ交換パターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-284">WCF provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="afcaa-285">WCF は、HTTP 要求を使用してすべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-285">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="afcaa-286">すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-286">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="afcaa-287">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="afcaa-287">CreateSequence Exchange</span></span>

<span data-ttu-id="afcaa-288">WCF イニシエーターは、オファーを使用してメッセージを生成し `CreateSequence` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-288">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="afcaa-289">WCF レスポンダーは、 `CreateSequence` シーケンスを作成する前に、にオファーがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-289">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="afcaa-290">WCF は、 `CreateSequenceResponse` `CreateSequence` のエンドポイント参照にアドレス指定された HTTP 要求でを送信し `ReplyTo` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-290">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="requestreply-correlation"></a><span data-ttu-id="afcaa-291">要求/応答の相関関係</span><span class="sxs-lookup"><span data-stu-id="afcaa-291">Request/Reply Correlation</span></span>

<span data-ttu-id="afcaa-292">WCF イニシエーターは、すべてのアプリケーション要求メッセージに `MessageId` およびエンドポイント参照を保持することを保証し `ReplyTo` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-292">The WCF Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="afcaa-293">WCF イニシエーターは、 `CreateSequence` `ReplyTo` 各アプリケーション要求メッセージに対してメッセージのエンドポイント参照を適用します。</span><span class="sxs-lookup"><span data-stu-id="afcaa-293">The WCF Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="afcaa-294">WCF レスポンダーでは、受信要求メッセージにとがあることが必要です `MessageId` `ReplyTo` 。</span><span class="sxs-lookup"><span data-stu-id="afcaa-294">The WCF Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="afcaa-295">WCF レスポンダーは、とすべてのアプリケーション要求メッセージのエンドポイント参照の URI が同一であることを保証し `CreateSequence` ます。</span><span class="sxs-lookup"><span data-stu-id="afcaa-295">The WCF Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>
