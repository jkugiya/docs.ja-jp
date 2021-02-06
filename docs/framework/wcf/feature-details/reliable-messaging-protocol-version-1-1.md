---
description: '詳細情報: Reliable Messaging Protocol version 1.1'
title: 信頼できるメッセージング プロトコル バージョン 1.1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 07d1ffb4347c7481944bc5d1c2ccef0940f18071
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632907"
---
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="01508-103">信頼できるメッセージング プロトコル バージョン 1.1</span><span class="sxs-lookup"><span data-stu-id="01508-103">Reliable Messaging Protocol version 1.1</span></span>

<span data-ttu-id="01508-104">このトピックでは、HTTP トランスポートを使用した相互運用に必要な WS-ReliableMessaging 2007 (バージョン 1.1) プロトコルの Windows Communication Foundation (WCF) 実装の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="01508-104">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="01508-105">WCF では、このトピックで説明する制約と説明に従って、WS-ReliableMessaging の仕様に従います。</span><span class="sxs-lookup"><span data-stu-id="01508-105">WCF follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="01508-106">WS-ReliableMessaging バージョン1.1 プロトコルは .NET Framework 3.5 以降で実装されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="01508-106">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with .NET Framework 3.5.</span></span>

<span data-ttu-id="01508-107">WS-ReliableMessaging 2 月2007プロトコルは、によって WCF に実装され <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> ます。</span><span class="sxs-lookup"><span data-stu-id="01508-107">The WS-ReliableMessaging February 2007 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>

<span data-ttu-id="01508-108">便宜上、ここでは次のロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="01508-108">For convenience, the topic uses the following roles:</span></span>

- <span data-ttu-id="01508-109">イニシエーター : WS-Reliable メッセージ シーケンスの作成を開始するクライアント。</span><span class="sxs-lookup"><span data-stu-id="01508-109">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>

- <span data-ttu-id="01508-110">レスポンダー : イニシエーターの要求を受け取るサービス。</span><span class="sxs-lookup"><span data-stu-id="01508-110">Responder: The service that receives the initiator's requests.</span></span>

 <span data-ttu-id="01508-111">このドキュメントでは、次の表に示すプレフィックスと名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="01508-111">This document uses the prefixes and namespaces in the following table.</span></span>

|<span data-ttu-id="01508-112">Prefix</span><span class="sxs-lookup"><span data-stu-id="01508-112">Prefix</span></span>|<span data-ttu-id="01508-113">名前空間</span><span class="sxs-lookup"><span data-stu-id="01508-113">Namespace</span></span>|
|-|-|
|<span data-ttu-id="01508-114">wsrm</span><span class="sxs-lookup"><span data-stu-id="01508-114">wsrm</span></span>|`http://docs.oasis-open.org/ws-rx/wsrm/200702`|
|<span data-ttu-id="01508-115">netrm</span><span class="sxs-lookup"><span data-stu-id="01508-115">netrm</span></span>|`http://schemas.microsoft.com/ws/2006/05/rm`|
|<span data-ttu-id="01508-116">s</span><span class="sxs-lookup"><span data-stu-id="01508-116">s</span></span>|`http://www.w3.org/2003/05/soap-envelope`|
|<span data-ttu-id="01508-117">wsa</span><span class="sxs-lookup"><span data-stu-id="01508-117">wsa</span></span>|`http://schemas.xmlsoap.org/ws/2005/08/addressing`|
|<span data-ttu-id="01508-118">wsse</span><span class="sxs-lookup"><span data-stu-id="01508-118">wsse</span></span>|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd`|
|<span data-ttu-id="01508-119">wsrmp</span><span class="sxs-lookup"><span data-stu-id="01508-119">wsrmp</span></span>|`http://docs.oasis-open.org/ws-rx/wsrmp/200702`|
|<span data-ttu-id="01508-120">netrmp</span><span class="sxs-lookup"><span data-stu-id="01508-120">netrmp</span></span>|`http://schemas.microsoft.com/ws-rx/wsrmp/200702`|
|<span data-ttu-id="01508-121">wsp</span><span class="sxs-lookup"><span data-stu-id="01508-121">wsp</span></span>|<span data-ttu-id="01508-122">(WS-Policy 1.2 または WS-Policy 1.5 のいずれか)</span><span class="sxs-lookup"><span data-stu-id="01508-122">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|

## <a name="messaging"></a><span data-ttu-id="01508-123">メッセージング</span><span class="sxs-lookup"><span data-stu-id="01508-123">Messaging</span></span>

### <a name="sequence-creation"></a><span data-ttu-id="01508-124">シーケンスの作成</span><span class="sxs-lookup"><span data-stu-id="01508-124">Sequence Creation</span></span>

<span data-ttu-id="01508-125">WCF `CreateSequence` では、メッセージとメッセージを実装して、 `CreateSequenceResponse` 信頼できるメッセージシーケンスを確立します。</span><span class="sxs-lookup"><span data-stu-id="01508-125">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="01508-126">次の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="01508-126">The following constraints apply:</span></span>

- <span data-ttu-id="01508-127">B1101: WCF イニシエーターは `CreateSequence` 、メッセージの、、およびと同じエンドポイント参照を使用し `ReplyTo` `AcksTo` `Offer/Endpoint` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-127">B1101: The WCF Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>

- <span data-ttu-id="01508-128">R1102: `AcksTo` メッセージの `ReplyTo`、`Offer/Endpoint`、および `CreateSequence` の各エンドポイント参照には、オクテット単位で一致する同じ文字列表現のアドレス値が必要です。</span><span class="sxs-lookup"><span data-stu-id="01508-128">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>

  - <span data-ttu-id="01508-129">WCF レスポンダーは、 `AcksTo` `ReplyTo` `Endpoint` シーケンスを作成する前に、、、およびの各エンドポイント参照の URI 部分が同一であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="01508-129">The WCF Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>

- <span data-ttu-id="01508-130">R1103: `AcksTo` メッセージの `ReplyTo`、`Offer/Endpoint`、および `CreateSequence` の各エンドポイント参照には、同一の参照パラメーターのセットが必要です。</span><span class="sxs-lookup"><span data-stu-id="01508-130">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>

  - <span data-ttu-id="01508-131">WCF では強制されませんが、の参照パラメーターとの `AcksTo` `ReplyTo` `Offer/Endpoint` エンドポイント参照が同一であることを前提 `CreateSequence` とし、エンドポイント参照の参照パラメーターを使用して `ReplyTo` 受信確認と逆方向シーケンスメッセージを使用します。</span><span class="sxs-lookup"><span data-stu-id="01508-131">WCF does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>

- <span data-ttu-id="01508-132">B1104: WCF イニシエーターは、メッセージ内に省略可能なまたは要素を生成しません `Expires` `Offer/Expires` `CreateSequence` 。</span><span class="sxs-lookup"><span data-stu-id="01508-132">B1104: The WCF Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>

- <span data-ttu-id="01508-133">B1105: メッセージにアクセスするとき `CreateSequence` 、WCF レスポンダーは要素の値を `Expires` 要素の `CreateSequence` 値として使用し `Expires` `CreateSequenceResponse` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-133">B1105: When accessing the `CreateSequence` message, the WCF Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="01508-134">それ以外の場合、WCF レスポンダーはとの値を読み取り、無視し `Expires` `Offer/Expires` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-134">Otherwise, the WCF Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>

- <span data-ttu-id="01508-135">B1106: メッセージにアクセスするときに、 `CreateSequenceResponse` WCF イニシエーターは省略可能な値を読み取り `Expires` ますが、使用しません。</span><span class="sxs-lookup"><span data-stu-id="01508-135">B1106: When accessing the `CreateSequenceResponse` message, the WCF Initiator reads the optional `Expires` value but does not use it.</span></span>

- <span data-ttu-id="01508-136">B1107: WCF の開始側と応答側は常に、 `IncompleteSequenceBehavior` 要素と要素にオプションの要素を生成し `CreateSequence/Offer` `CreateSequenceResponse` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-136">B1107: The WCF Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>

- <span data-ttu-id="01508-137">B1108: WCF では、 `DiscardFollowingFirstGap` `NoDiscard` 要素内の値と値のみが使用さ `IncompleteSequenceBehavior` れます。</span><span class="sxs-lookup"><span data-stu-id="01508-137">B1108: WCF uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>

  - <span data-ttu-id="01508-138">WS-ReliableMessaging では、セッションを形成する、相関する 2 つの逆方向シーケンスを確立するために、`Offer` 機構を利用しています。</span><span class="sxs-lookup"><span data-stu-id="01508-138">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>

- <span data-ttu-id="01508-139">B1109: に `CreateSequence` 要素が含まれている場合 `Offer` 、WCF レスポンダーの一方向は、要素のないで応答することによって提供されるシーケンスを拒否し `CreateSequenceResponse` `Accept` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-139">B1109: If `CreateSequence` contains an `Offer` element, the one way WCF Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>

- <span data-ttu-id="01508-140">B1110: 信頼できるメッセージングレスポンダーが提供されたシーケンスを拒否する場合、WCF イニシエーターは新しく確立されたシーケンスをエラーにします。</span><span class="sxs-lookup"><span data-stu-id="01508-140">B1110: If a Reliable Messaging Responder rejects the offered sequence, the WCF Initiator faults the newly established sequence.</span></span>

- <span data-ttu-id="01508-141">B1111: に `CreateSequence` 要素が含まれていない場合 `Offer` 、双方向の WCF レスポンダーは、エラーで応答することによって提供されたシーケンスを拒否し `CreateSequenceRefused` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-141">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way WCF Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>

- <span data-ttu-id="01508-142">R1112: 2 つの逆方向シーケンスが `Offer` 機構を使用して確立された場合、`[address]` エンドポイント参照の `CreateSequenceResponse/Accept/AcksTo` プロパティは、バイト単位で `CreateSequence` メッセージの送信先 URI と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01508-142">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>

- <span data-ttu-id="01508-143">R1113: 2 つの逆方向シーケンスが `Offer` 機構を使用して確立された場合、イニシエーターからレスポンダーに流れる両方のシーケンスにあるすべてのメッセージは、同じエンドポイント参照に送信される必要があります。</span><span class="sxs-lookup"><span data-stu-id="01508-143">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>

<span data-ttu-id="01508-144">WCF では、WS-ReliableMessaging を使用して、発信側と応答側の間の信頼できるセッションを確立します。</span><span class="sxs-lookup"><span data-stu-id="01508-144">WCF uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="01508-145">WCF WS-ReliableMessaging の実装は、一方向、要求/応答、および全二重のメッセージングパターンに対して信頼できるセッションを提供します。</span><span class="sxs-lookup"><span data-stu-id="01508-145">The WCF WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="01508-146">`Offer` および `CreateSequence` で WS-ReliableMessaging の `CreateSequenceResponse` 機構を使用すると、相関する 2 つの逆方向シーケンスを確立できます。また、Offer 機構は、すべてのメッセージ エンドポイントに適したセッション プロトコルを提供します。</span><span class="sxs-lookup"><span data-stu-id="01508-146">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="01508-147">WCF では、セッション整合性に対するエンドツーエンドの保護を含むこのようなセッションに対してセキュリティ保証が提供されるため、同じパーティを対象としたメッセージが同じ送信先に到着することを確認することが実用的です。</span><span class="sxs-lookup"><span data-stu-id="01508-147">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="01508-148">また、これにより、アプリケーション メッセージにシーケンス受信確認を抱き合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="01508-148">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="01508-149">したがって、制約 R1102、R1112、および R1113 は WCF に適用されます。</span><span class="sxs-lookup"><span data-stu-id="01508-149">Therefore, constraints R1102, R1112, and R1113 apply to WCF.</span></span>

<span data-ttu-id="01508-150">`CreateSequence` メッセージの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="01508-150">An example of a `CreateSequence` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:MessageID>
    <wsa:ReplyTo>
        <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequence>
      <wsrm:AcksTo>
        <wsa:Address>http://Business456.com/clientA</wsa:Address>
      </wsrm:AcksTo>
      <wsrm:Offer>
        <wsrm:Identifier>urn:uuid:066b4730-fc82-458a-a5c1-210be4fb4e4e</wsrm:Identifier>
        <wsrm:Endpoint>
          <wsa:Address>http://Business456.com/clientA</wsa:Address>
        </wsrm:Endpoint>
        <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>
      </wsrm:Offer>
    </wsrm:CreateSequence>
  </s:Body>
</s:Envelope>
```

<span data-ttu-id="01508-151">`CreateSequenceResponse` メッセージの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="01508-151">An example of a `CreateSequenceResponse` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>
      <wsrm:Accept>
        <wsrm:AcksTo>
          <wsa:Address>http://BusinessABC.com/serviceA</wsa:Address>
        </wsrm:AcksTo>
      </wsrm:Accept>
    </wsrm:CreateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="closing-a-sequence"></a><span data-ttu-id="01508-152">シーケンスを閉じる</span><span class="sxs-lookup"><span data-stu-id="01508-152">Closing a Sequence</span></span>

<span data-ttu-id="01508-153">WCF は、メッセージとメッセージを使用して、 `CloseSequence` `CloseSequenceResponse` 信頼性の高いメッセージングソースによるシャットダウンを実行します。</span><span class="sxs-lookup"><span data-stu-id="01508-153">WCF uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="01508-154">WCF の信頼できるメッセージの送信先はシャットダウンを開始せず、WCF Reliable Messaging source は、信頼できるメッセージングの送信先が開始したシャットダウンをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="01508-154">The WCF Reliable Messaging destination does not initiate shutdown and the WCF Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="01508-155">次の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="01508-155">The following constraints apply:</span></span>

- <span data-ttu-id="01508-156">B1201: WCF Reliable Messaging ソースは、シーケンスをシャットダウンするために常にメッセージを送信し `CloseSequence` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-156">B1201: The WCF Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>

- <span data-ttu-id="01508-157">B1202: 信頼できるメッセージの送信元は、`CloseSequence` メッセージを送信する前に、すべてのシーケンス メッセージの受信確認を待機します。</span><span class="sxs-lookup"><span data-stu-id="01508-157">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>

- <span data-ttu-id="01508-158">B1203: 信頼できるメッセージの送信元は、シーケンスにメッセージが含まれない場合を除き、常にオプションの `LastMsgNumber` 要素を含めます。</span><span class="sxs-lookup"><span data-stu-id="01508-158">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>

- <span data-ttu-id="01508-159">R1204: 信頼できるメッセージの送信先は、`CloseSequence` メッセージを送信してシャットダウンを開始することはできません。</span><span class="sxs-lookup"><span data-stu-id="01508-159">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>

- <span data-ttu-id="01508-160">B1205: メッセージを受信する `CloseSequence` と、WCF Reliable Messaging ソースはシーケンスが不完全であると見なし、エラーを送信します。</span><span class="sxs-lookup"><span data-stu-id="01508-160">B1205: Upon receiving a `CloseSequence` message, the WCF Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>

 <span data-ttu-id="01508-161">`CloseSequence` メッセージの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="01508-161">An example of a `CloseSequence` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:MessageID>
    <wsa:ReplyTo>
      <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CloseSequence>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>
    </wsrm:CloseSequence>
  </s:Body>
</s:Envelope>
```

<span data-ttu-id="01508-162">メッセージの例 `CloseSequenceResponse` :</span><span class="sxs-lookup"><span data-stu-id="01508-162">Example `CloseSequenceResponse` message:</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsrm:SequenceAcknowledgement>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>
      <wsrm:Final></wsrm:Final>
      <netrm:BufferRemaining>8</netrm:BufferRemaining>
    </wsrm:SequenceAcknowledgement>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CloseSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    </wsrm:CloseSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequence-termination"></a><span data-ttu-id="01508-163">シーケンスの終了</span><span class="sxs-lookup"><span data-stu-id="01508-163">Sequence Termination</span></span>

<span data-ttu-id="01508-164">WCF は `TerminateSequence/TerminateSequenceResponse` 、ハンドシェイクを完了した後に、主にハンドシェイクを使用し `CloseSequence/CloseSequenceResponse` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-164">WCF primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="01508-165">WCF の信頼できるメッセージの送信先は、終了を開始せず、信頼できるメッセージの送信元は、信頼できるメッセージの送信先が開始した終了をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="01508-165">The WCF Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="01508-166">次の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="01508-166">The following constraints apply:</span></span>

- <span data-ttu-id="01508-167">B1301: WCF イニシエーターは、ハンドシェイクが `TerminateSequence` 正常に完了した後にのみメッセージを送信し `CloseSequence/CloseSequenceResponse` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-167">B1301: The WCF Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>

- <span data-ttu-id="01508-168">R1302: WCF `LastMsgNumber` は、要素が `CloseSequence` 特定のシーケンスのすべてのメッセージとメッセージで一貫していることを検証 `TerminateSequence` します。</span><span class="sxs-lookup"><span data-stu-id="01508-168">R1302: WCF validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="01508-169">つまり、`LastMsgNumber` は、すべての `CloseSequence` メッセージおよび `TerminateSequence` メッセージに存在しないか、すべての `CloseSequence` メッセージおよび `TerminateSequence` メッセージに存在し、同一であるかのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="01508-169">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>

- <span data-ttu-id="01508-170">B1303: `TerminateSequence` ハンドシェイクの後、`CloseSequence/CloseSequenceResponse` メッセージを受け取ると、信頼できるメッセージの送信先が `TerminateSequenceResponse` メッセージで応答します。</span><span class="sxs-lookup"><span data-stu-id="01508-170">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="01508-171">信頼できるメッセージの配信元は、`TerminateSequence` メッセージを送信する前に最終受信確認を受けるため、信頼できるメッセージの送信先ではシーケンスが終了したことが確実にわかり、すぐにリソースを再要求します。</span><span class="sxs-lookup"><span data-stu-id="01508-171">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>

- <span data-ttu-id="01508-172">B1304: ハンドシェイクの前にメッセージを受信すると、 `TerminateSequence` `CloseSequence/CloseSequenceResponse` WCF の信頼できるメッセージの送信先がメッセージで応答し `TerminateSequenceResponse` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-172">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the WCF Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="01508-173">信頼できるメッセージの送信先でシーケンスが一貫していると判断した場合、信頼できるメッセージの送信先は、リソースを再要求する前にアプリケーションの送信先で指定された時間待機し、クライアントが最終受信確認を受け取ることができるようにします。</span><span class="sxs-lookup"><span data-stu-id="01508-173">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="01508-174">それ以外の場合は、信頼できるメッセージの送信先はすぐにリソースを再要求し、`Faulted` イベントを発生させて、不明なシーケンスの終了をアプリケーションの送信先に示します。</span><span class="sxs-lookup"><span data-stu-id="01508-174">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>

<span data-ttu-id="01508-175">`TerminateSequence` メッセージの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="01508-175">An example of a `TerminateSequence` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:MessageID>
    <wsa:ReplyTo>
      <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:TerminateSequence>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>
      </wsrm:TerminateSequence>
  </s:Body>
</s:Envelope>
```

<span data-ttu-id="01508-176">メッセージの例 `TerminateSequenceResponse` :</span><span class="sxs-lookup"><span data-stu-id="01508-176">Example `TerminateSequenceResponse` message:</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsrm:SequenceAcknowledgement>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>
      <wsrm:Final></wsrm:Final>
      <netrm:BufferRemaining>8</netrm:BufferRemaining>
    </wsrm:SequenceAcknowledgement>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:TerminateSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    </wsrm:TerminateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequences"></a><span data-ttu-id="01508-177">シーケンス</span><span class="sxs-lookup"><span data-stu-id="01508-177">Sequences</span></span>

<span data-ttu-id="01508-178">シーケンスに適用される制約を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="01508-178">The following is a list of constraints that apply to sequences:</span></span>

- <span data-ttu-id="01508-179">B1401: WCF は `xs:long` 、最大値である9223372036854775807を超えるシーケンス番号を生成してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="01508-179">B1401:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>

<span data-ttu-id="01508-180">`Sequence` ヘッダーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="01508-180">An example of a `Sequence` header.</span></span>

```xml
<wsrm:Sequence s:mustUnderstand="1">
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:MessageNumber>1</wsrm:MessageNumber>
</wsrm:Sequence>
```

### <a name="request-acknowledgement"></a><span data-ttu-id="01508-181">受信確認の要求</span><span class="sxs-lookup"><span data-stu-id="01508-181">Request Acknowledgement</span></span>

<span data-ttu-id="01508-182">WCF は、 `AckRequested` キープアライブメカニズムとしてヘッダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="01508-182">WCF uses the `AckRequested` header as a keep-alive mechanism.</span></span>

<span data-ttu-id="01508-183">`AckRequested` ヘッダーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="01508-183">An example of an `AckRequested` header.</span></span>

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement"></a><span data-ttu-id="01508-184">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="01508-184">SequenceAcknowledgement</span></span>

<span data-ttu-id="01508-185">WCF では、WS-Reliable メッセージングで提供されるシーケンス受信確認に "豚" メカニズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="01508-185">WCF uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="01508-186">次の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="01508-186">The following constraints apply:</span></span>

- <span data-ttu-id="01508-187">R1601: 2 つの逆方向シーケンスが機構を使用して確立されると、 `Offer` `SequenceAcknowledgement` 目的の受信者に送信されるアプリケーションメッセージにヘッダーが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="01508-187">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="01508-188">リモートのエンドポイントは、追加された `SequenceAcknowledgement` ヘッダーにアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="01508-188">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="01508-189">B1602: WCF では `SequenceAcknowledgement` 、要素を含むヘッダーは生成されません `Nack` 。</span><span class="sxs-lookup"><span data-stu-id="01508-189">B1602: WCF does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> <span data-ttu-id="01508-190">WCF は、各 `Nack` 要素にシーケンス番号が含まれていることを検証しますが、それ以外の場合は `Nack` 要素と値を無視します。</span><span class="sxs-lookup"><span data-stu-id="01508-190">WCF validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>

 <span data-ttu-id="01508-191">`SequenceAcknowledgement` ヘッダーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="01508-191">An example of a `SequenceAcknowledgement` header.</span></span>

```xml
<wsrm:SequenceAcknowledgement>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>
</wsrm:SequenceAcknowledgement>
```

### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="01508-192">WS-ReliableMessaging エラー</span><span class="sxs-lookup"><span data-stu-id="01508-192">WS-ReliableMessaging Faults</span></span>

<span data-ttu-id="01508-193">WS-ReliableMessaging フォールトの WCF 実装に適用される制約の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="01508-193">The following is a list of constraints that apply to the WCF implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="01508-194">次の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="01508-194">The following constraints apply:</span></span>

- <span data-ttu-id="01508-195">B1701: WCF ではエラーは生成されません `MessageNumberRollover` 。</span><span class="sxs-lookup"><span data-stu-id="01508-195">B1701: WCF does not generate `MessageNumberRollover` faults.</span></span>

- <span data-ttu-id="01508-196">B1702: SOAP 1.2 では、サービスエンドポイントが接続制限に達し、新しい接続を処理できない場合に、 `CreateSequenceRefused` 次の例に示すように、WCF によって入れ子になったエラーサブコードが生成さ `netrm:ConnectionLimitReached` れます。</span><span class="sxs-lookup"><span data-stu-id="01508-196">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, WCF generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action>http://docs.oasis-open.org/ws-rx/wsrm/200702/fault</wsa:Action>
  </s:Header>
  <s:Body>
    <s:Fault>
      <s:Code>
        <s:Value>s:Receiver</s:Value>
        <s:Subcode>
          <s:Value>wsrm:CreateSequenceRefused</s:Value>
          <s:Subcode>
            <s:Value>netrm:ConnectionLimitReached</s:Value>
          </s:Subcode>
        </s:Subcode>
      </s:Code>
      <s:Reason>
        <s:Text xml:lang="en">Server 'http://BusinessABC.com/serviceA' is too busy to process this request. Try again later.</s:Text>
      </s:Reason>
    </s:Fault>
  </s:Body>
</s:Envelope>
```

### <a name="ws-addressing-faults"></a><span data-ttu-id="01508-197">WS-Addressing エラー</span><span class="sxs-lookup"><span data-stu-id="01508-197">WS-Addressing Faults</span></span>

<span data-ttu-id="01508-198">WS-ReliableMessaging は WS-ADDRESSING を使用するため、WCF WS-ReliableMessaging の実装では WS-Addressing エラーが生成され、送信される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="01508-198">Because WS-ReliableMessaging uses WS-Addressing, the WCF WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="01508-199">このセクションでは、WCF によって明示的に生成され、WS-ReliableMessaging レイヤーで送信される WS-Addressing 障害について説明します。</span><span class="sxs-lookup"><span data-stu-id="01508-199">This section covers the WS-Addressing faults that WCF explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>

- <span data-ttu-id="01508-200">B1801: WCF `Message Addressing Header Required` は、次のいずれかに該当する場合にエラーを生成して送信します。</span><span class="sxs-lookup"><span data-stu-id="01508-200">B1801:WCF generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>

  - <span data-ttu-id="01508-201">`CreateSequence`、`CloseSequence`、または `TerminateSequence` メッセージに `MessageId` ヘッダーがない。</span><span class="sxs-lookup"><span data-stu-id="01508-201">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>

  - <span data-ttu-id="01508-202">`CreateSequence`、`CloseSequence`、または `TerminateSequence` メッセージに `ReplyTo` ヘッダーがない。</span><span class="sxs-lookup"><span data-stu-id="01508-202">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>

  - <span data-ttu-id="01508-203">`CreateSequenceResponse`、`CloseSequenceResponse`、または `TerminateSequenceResponse` メッセージに `RelatesTo` ヘッダーがない。</span><span class="sxs-lookup"><span data-stu-id="01508-203">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>

- <span data-ttu-id="01508-204">B1802: WCF は、メッセージの `Endpoint Unavailable` アドレス指定ヘッダーの検査に基づいてシーケンスを処理できるエンドポイントをリッスンしていないことを示すために、エラーを生成して送信します `CreateSequence` 。</span><span class="sxs-lookup"><span data-stu-id="01508-204">B1802:WCF generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>

## <a name="protocol-composition"></a><span data-ttu-id="01508-205">プロトコル コンポジション</span><span class="sxs-lookup"><span data-stu-id="01508-205">Protocol Composition</span></span>

### <a name="composition-with-ws-addressing"></a><span data-ttu-id="01508-206">WS-Addressing によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="01508-206">Composition with WS-Addressing</span></span>

<span data-ttu-id="01508-207">WCF では、2つのバージョンの WS-ADDRESSING をサポートしています。 WS-Addressing 2004/08 [WS-FEDERATION] と W3C WS-Addressing 1.0 の推奨事項 [WS-FEDERATION-CORE] と [WS-FEDERATION-SOAP]。</span><span class="sxs-lookup"><span data-stu-id="01508-207">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>

<span data-ttu-id="01508-208">WS-ReliableMessaging 仕様に記載されているのは、WS-Addressing 2004/08 だけですが、使用する WS-Addressing のバージョンが制限されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="01508-208">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="01508-209">WCF に適用される制約の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="01508-209">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="01508-210">R2101: WS-Addressing 2004/08 と WS-Addressing 1.0 の両方を WS-ReliableMessaging で使用できます。</span><span class="sxs-lookup"><span data-stu-id="01508-210">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>

- <span data-ttu-id="01508-211">R2102: 特定の WS-ReliableMessaging シーケンス、または `Offer` 機構を使用して関連付けられた逆方向シーケンスのペアでは、同じバージョンの WS-Addressing を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01508-211">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>

### <a name="composition-with-soap"></a><span data-ttu-id="01508-212">SOAP によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="01508-212">Composition with SOAP</span></span>

<span data-ttu-id="01508-213">WCF では、SOAP 1.1 と SOAP 1.2 の両方を WS-Reliable メッセージングと共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="01508-213">WCF supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>

### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="01508-214">WS-Security と WS-SecureConversation によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="01508-214">Composition with WS-Security and WS-SecureConversation</span></span>

<span data-ttu-id="01508-215">WCF では、セキュリティで保護されたトランスポート (HTTPS)、WS-SECURITY によるコンポジション、および WS-Secure メッセージ交換による構成を使用して WS-ReliableMessaging シーケンスを保護します。</span><span class="sxs-lookup"><span data-stu-id="01508-215">WCF provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="01508-216">WS-ReliableMessaging 1.1 プロトコル、WS-Security 1.1、および WS-Secure Conversation 1.3 プロトコルは一緒に使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="01508-216">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="01508-217">WCF に適用される制約の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="01508-217">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="01508-218">R2301: 個々のメッセージの整合性と機密性だけでなく、WS-ReliableMessaging シーケンスの整合性を保護するために、WCF では WS-Secure のメッセージ交換を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01508-218">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>

- <span data-ttu-id="01508-219">R2302:WS-ReliableMessaging シーケンスを確立する前に、WS-SecureConversation セッションを確立する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01508-219">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>

- <span data-ttu-id="01508-220">R2303: WS-ReliableMessaging シーケンスの有効期間が WS-SecureConversation セッションの有効期間よりも長い場合は、対応する WS-SecureConversation Renewal バインディングを使用して、WS-SecureConversation によって確立された `SecurityContextToken` を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01508-220">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>

- <span data-ttu-id="01508-221">B2304:WS-ReliableMessaging シーケンスまたは相関する逆方向シーケンスのペアは、必ず同じ WS-SecureConversation セッションにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="01508-221">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>

- <span data-ttu-id="01508-222">R2305: WS-Secure メッセージ交換で構成されている場合、WCF レスポンダーでは、 `CreateSequence` メッセージに要素とヘッダーが含まれている必要があり `wsse:SecurityTokenReference` `wsrm:UsesSequenceSTR` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-222">R2305: When composed with WS-Secure Conversation, the WCF responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>

 <span data-ttu-id="01508-223">`UsesSequenceSTR` ヘッダーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="01508-223">An example of a `UsesSequenceSTR` header.</span></span>

```xml
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>
```

### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="01508-224">SSL/TLS セッションによるコンポジション</span><span class="sxs-lookup"><span data-stu-id="01508-224">Composition with SSL/TLS sessions</span></span>

<span data-ttu-id="01508-225">WCF では、SSL/TLS セッションを使用した構成はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="01508-225">WCF does not support composition with SSL/TLS sessions:</span></span>

- <span data-ttu-id="01508-226">B2401: WCF はヘッダーを生成 `wsrm:UsesSequenceSSL` しません。</span><span class="sxs-lookup"><span data-stu-id="01508-226">B2401: WCF does not generate the `wsrm:UsesSequenceSSL` header.</span></span>

- <span data-ttu-id="01508-227">R2402: 信頼できるメッセージ発信側は、 `CreateSequence` ヘッダーを含むメッセージを `wsrm:UsesSequenceSSL` WCF レスポンダーに送信することはできません。</span><span class="sxs-lookup"><span data-stu-id="01508-227">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a WCF Responder.</span></span>

### <a name="composition-with-ws-policy"></a><span data-ttu-id="01508-228">WS-Policy によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="01508-228">Composition with WS-Policy</span></span>

<span data-ttu-id="01508-229">WCF では、2つのバージョンの WS-POLICY (WS-Policy 1.2 と WS-Policy 1.5) がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="01508-229">WCF supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>

## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="01508-230">WS-ReliableMessaging の WS-Policy アサーション</span><span class="sxs-lookup"><span data-stu-id="01508-230">WS-ReliableMessaging WS-Policy Assertion</span></span>

<span data-ttu-id="01508-231">WCF では、WS-ReliableMessaging WS-Policy アサーションを使用して `wsrm:RMAssertion` 、エンドポイントの機能を記述します。</span><span class="sxs-lookup"><span data-stu-id="01508-231">WCF uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="01508-232">WCF に適用される制約の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="01508-232">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="01508-233">B3001: WCF は `wsrmn:RMAssertion` WS-Policy アサーションを `wsdl:binding` 要素にアタッチします。</span><span class="sxs-lookup"><span data-stu-id="01508-233">B3001: WCF attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="01508-234">WCF では、要素および要素への添付ファイルの両方がサポートさ `wsdl:binding` `wsdl:port` れます。</span><span class="sxs-lookup"><span data-stu-id="01508-234">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>

- <span data-ttu-id="01508-235">B3002: WCF はタグを生成しません `wsp:Optional` 。</span><span class="sxs-lookup"><span data-stu-id="01508-235">B3002: WCF never generates the `wsp:Optional` tag.</span></span>

- <span data-ttu-id="01508-236">B3003: WS-Policy アサーションにアクセスすると `wsrmp:RMAssertion` 、WCF は `wsp:Optional` タグを無視し、ws-federation ポリシーを必須として扱います。</span><span class="sxs-lookup"><span data-stu-id="01508-236">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, WCF ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>

- <span data-ttu-id="01508-237">R3004: WCF は SSL/TLS セッションで構成されないため、WCF はを指定するポリシーを受け入れません `wsrmp:SequenceTransportSecurity` 。</span><span class="sxs-lookup"><span data-stu-id="01508-237">R3004: Because WCF does not compose with SSL/TLS sessions, WCF does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>

- <span data-ttu-id="01508-238">B3005: WCF は常に `wsrmp:DeliveryAssurance` 要素を生成します。</span><span class="sxs-lookup"><span data-stu-id="01508-238">B3005: WCF always generates the `wsrmp:DeliveryAssurance` element.</span></span>

- <span data-ttu-id="01508-239">B3006: WCF は常に `wsrmp:ExactlyOnce` 配信保証を指定します。</span><span class="sxs-lookup"><span data-stu-id="01508-239">B3006: WCF always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>

- <span data-ttu-id="01508-240">B3007: WCF は WS-ReliableMessaging アサーションの次のプロパティを生成して読み取り、WCF でそれらを制御し `ReliableSessionBindingElement` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-240">B3007: WCF generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the WCF`ReliableSessionBindingElement`:</span></span>

  - `netrmp:InactivityTimeout`

  - `netrmp:AcknowledgementInterval`

  <span data-ttu-id="01508-241">`RMAssertion` の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="01508-241">An example of a `RMAssertion`.</span></span>

  ```xml
  <wsrmp:RMAssertion>
    <wsp:Policy>
      <wsrmp:SequenceSTR/>
      <wsrmp:DeliveryAssurance>
        <wsp:Policy>
          <wsrmp:ExactlyOnce/>
          <wsrmp:InOrder/>
        </wsp:Policy>
      </wsrmp:DeliveryAssurance>
    </wsp:Policy>
    <netrmp:InactivityTimeout Milliseconds="600000"/>
    <netrmp:AcknowledgementInterval Milliseconds="200"/>
  </wsrmp:RMAssertion>
  ```

## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="01508-242">WS-ReliableMessaging のフロー制御拡張</span><span class="sxs-lookup"><span data-stu-id="01508-242">Flow Control WS-ReliableMessaging Extension</span></span>

<span data-ttu-id="01508-243">WCF は WS-ReliableMessaging 拡張機能を使用して、シーケンスメッセージフローに対してさらに厳密な制御を提供します。</span><span class="sxs-lookup"><span data-stu-id="01508-243">WCF uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>

<span data-ttu-id="01508-244">フロー制御を有効にするには、 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> プロパティをに設定し `true` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-244">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="01508-245">WCF に適用される制約の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="01508-245">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="01508-246">B4001: 信頼できるメッセージングフロー制御が有効になっている場合、WCF は、 `netrm:BufferRemaining` 次の `SequenceAcknowledgement` 例に示すように、ヘッダーの要素拡張に要素を生成します。</span><span class="sxs-lookup"><span data-stu-id="01508-246">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>8</netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="01508-247">B4002: 信頼できるメッセージングフロー制御が有効になっている場合でも、WCF ではヘッダーに要素は必要ありません `netrm:BufferRemaining` `SequenceAcknowledgement` 。</span><span class="sxs-lookup"><span data-stu-id="01508-247">B4002: Even when Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="01508-248">B4003: WCF Reliable Messaging Destination は `netrm:BufferRemaining` 、を使用して、バッファーできる新しいメッセージの数を示します。</span><span class="sxs-lookup"><span data-stu-id="01508-248">B4003: WCF Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>

- <span data-ttu-id="01508-249">B4004: 信頼できるメッセージングフロー制御を有効にすると、WCF Reliable Messaging ソースはの値を使用して `netrm:BufferRemaining` メッセージ転送を調整します。</span><span class="sxs-lookup"><span data-stu-id="01508-249">B4004:When Reliable Messaging Flow Control is enabled, the WCF Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>

- <span data-ttu-id="01508-250">B4005: WCF は 0 ~ 4096 の範囲の `netrm:BufferRemaining` 整数値を生成し、0 ~ の値214748364を含む整数値を読み取り `xs:int` `maxInclusive` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-250">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>

## <a name="message-exchange-patterns"></a><span data-ttu-id="01508-251">メッセージ交換パターン</span><span class="sxs-lookup"><span data-stu-id="01508-251">Message Exchange Patterns</span></span>

<span data-ttu-id="01508-252">このセクションでは、さまざまなメッセージ交換パターンに WS-ReliableMessaging を使用する場合の WCF の動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="01508-252">This section describes WCF's behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="01508-253">各メッセージ交換パターンについて、次の 2 つの展開シナリオを考えます。</span><span class="sxs-lookup"><span data-stu-id="01508-253">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>

- <span data-ttu-id="01508-254">アドレス不可能なイニシエーター : イニシエーターはファイアウォールの内側にあります。レスポンダーは HTTP 応答でのみイニシエーターにメッセージを配信できます。</span><span class="sxs-lookup"><span data-stu-id="01508-254">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>

- <span data-ttu-id="01508-255">アドレス可能なイニシエーター : イニシエーターとレスポンダーの両方に HTTP 要求を送信できます。つまり、逆方向の 2 つの HTTP 接続を確立できます。</span><span class="sxs-lookup"><span data-stu-id="01508-255">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>

### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="01508-256">一方向 : アドレス不可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="01508-256">One-way, Non-addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="01508-257">バインド</span><span class="sxs-lookup"><span data-stu-id="01508-257">Binding</span></span>

<span data-ttu-id="01508-258">WCF は、1つの HTTP チャネルで1つのシーケンスを使用して、一方向のメッセージ交換パターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="01508-258">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="01508-259">WCF は、HTTP 要求を使用して、発信側から応答側にすべてのメッセージを送信し、応答側から発信側にすべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="01508-259">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="01508-260">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="01508-260">CreateSequence Exchange</span></span>

<span data-ttu-id="01508-261">WCF イニシエーターは、 `CreateSequence` http 要求に要素のないメッセージを送信 `Offer` し、 `CreateSequenceResponse` http 応答でメッセージを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="01508-261">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="01508-262">WCF レスポンダーは、シーケンスを作成し、 `CreateSequenceResponse` 要素のないメッセージを `Accept` HTTP 応答に送信します。</span><span class="sxs-lookup"><span data-stu-id="01508-262">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>

#### <a name="sequenceacknowledgement"></a><span data-ttu-id="01508-263">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="01508-263">SequenceAcknowledgement</span></span>

<span data-ttu-id="01508-264">WCF イニシエーターは、メッセージメッセージとエラーメッセージを除くすべてのメッセージの応答で受信確認を処理し `CreateSequence` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-264">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="01508-265">WCF レスポンダーは、すべてのシーケンスとメッセージに対して、HTTP 応答に対してスタンドアロンの受信確認を常に転送し `AckRequested` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-265">The WCF Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>

#### <a name="closesequence-exchange"></a><span data-ttu-id="01508-266">CloseSequence の交換</span><span class="sxs-lookup"><span data-stu-id="01508-266">CloseSequence Exchange</span></span>

<span data-ttu-id="01508-267">WCF イニシエーターは、 `CloseSequence` http 要求でメッセージを送信し、 `CreateSequenceResponse` http 応答でメッセージを要求します。</span><span class="sxs-lookup"><span data-stu-id="01508-267">The WCF Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="01508-268">WCF レスポンダーは、 `CloseSequenceResponse` HTTP 応答でメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="01508-268">The WCF Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="01508-269">TerminateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="01508-269">TerminateSequence Exchange</span></span>

<span data-ttu-id="01508-270">WCF イニシエーターは、 `TerminateSequence` http 要求でメッセージを送信し、 `TerminateSequenceResponse` http 応答でメッセージを要求します。</span><span class="sxs-lookup"><span data-stu-id="01508-270">The WCF Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="01508-271">WCF レスポンダーは、 `TerminateSequenceResponse` HTTP 応答でメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="01508-271">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>

### <a name="one-way-addressable-initiator"></a><span data-ttu-id="01508-272">一方向 : アドレス可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="01508-272">One Way, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="01508-273">バインド</span><span class="sxs-lookup"><span data-stu-id="01508-273">Binding</span></span>

<span data-ttu-id="01508-274">WCF では、1つの受信と送信の HTTP チャネルを1つのシーケンスを使用して、一方向のメッセージ交換パターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="01508-274">WCF provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="01508-275">WCF は、HTTP 要求を使用してすべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="01508-275">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="01508-276">すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="01508-276">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="01508-277">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="01508-277">CreateSequence Exchange</span></span>

<span data-ttu-id="01508-278">WCF イニシエーターは、 `CreateSequence` HTTP 要求に要素のないメッセージを送信し `Offer` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-278">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="01508-279">WCF レスポンダーは、シーケンスを作成し、 `CreateSequenceResponse` 要素のないメッセージを `Accept` HTTP 要求に送信します。</span><span class="sxs-lookup"><span data-stu-id="01508-279">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>

### <a name="duplex-addressable-initiator"></a><span data-ttu-id="01508-280">双方向 : アドレス可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="01508-280">Duplex, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="01508-281">バインド</span><span class="sxs-lookup"><span data-stu-id="01508-281">Binding</span></span>

<span data-ttu-id="01508-282">WCF は、1つの受信と1つの送信 HTTP チャネルに対して2つのシーケンスを使用して、完全に非同期の双方向メッセージ交換パターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="01508-282">WCF provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="01508-283">このメッセージ交換パターンは、限定された方法で `Request/Reply`、`Addressable` イニシエーター メッセージ交換パターンに組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="01508-283">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="01508-284">WCF では、HTTP 要求を使用してすべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="01508-284">WCF uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="01508-285">すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="01508-285">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="01508-286">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="01508-286">CreateSequence Exchange</span></span>

<span data-ttu-id="01508-287">WCF イニシエーターは、 `CreateSequence` HTTP 要求の要素を使用してメッセージを送信し `Offer` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-287">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="01508-288">WCF レスポンダーは、に要素があることを確認し、 `CreateSequence` `Offer` シーケンスを作成し、要素を使用してメッセージを送信し `CreateSequenceResponse` `Accept` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-288">The WCF Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>

#### <a name="sequence-lifetime"></a><span data-ttu-id="01508-289">シーケンスの有効期間</span><span class="sxs-lookup"><span data-stu-id="01508-289">Sequence Lifetime</span></span>

<span data-ttu-id="01508-290">WCF では、2つのシーケンスが1つの完全な二重セッションとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="01508-290">WCF treats the two sequences as one fully-duplex session.</span></span>

<span data-ttu-id="01508-291">1つのシーケンスに障害が発生したエラーが生成されると、WCF は、リモートエンドポイントが両方のシーケンスをフォールトすることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="01508-291">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="01508-292">1つのシーケンスで障害が発生したエラーを読み取ると、WCF は両方のシーケンスをエラーにします。</span><span class="sxs-lookup"><span data-stu-id="01508-292">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>

<span data-ttu-id="01508-293">WCF は、その送信シーケンスを終了し、受信シーケンスでメッセージを処理し続けることができます。</span><span class="sxs-lookup"><span data-stu-id="01508-293">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="01508-294">逆に、WCF では、受信シーケンスの終了を処理し、送信シーケンスでメッセージを送信し続けることができます。</span><span class="sxs-lookup"><span data-stu-id="01508-294">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>

### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="01508-295">要求/応答および一方向のアドレス不可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="01508-295">Request-Reply and One-Way, Non-Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="01508-296">バインド</span><span class="sxs-lookup"><span data-stu-id="01508-296">Binding</span></span>

<span data-ttu-id="01508-297">WCF は、1つの HTTP チャネルで2つのシーケンスを使用して、一方向および要求/応答メッセージ交換パターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="01508-297">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="01508-298">WCF は、HTTP 要求を使用して、発信側から応答側にすべてのメッセージを送信し、応答側から発信側にすべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="01508-298">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="01508-299">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="01508-299">CreateSequence Exchange</span></span>

<span data-ttu-id="01508-300">WCF イニシエーターは、 `CreateSequence` http 要求で要素を含むメッセージを送信 `Offer` し、 `CreateSequenceResponse` http 応答でメッセージを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="01508-300">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="01508-301">WCF レスポンダーは、シーケンスを作成し、 `CreateSequenceResponse` HTTP 応答の要素を使用してメッセージを送信し `Accept` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-301">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="01508-302">一方向のメッセージ</span><span class="sxs-lookup"><span data-stu-id="01508-302">One-way Message</span></span>

<span data-ttu-id="01508-303">一方向メッセージ交換を正常に完了するために、WCF イニシエーターは HTTP 要求で要求シーケンスメッセージを送信し、HTTP 応答でスタンドアロンメッセージを受信し `SequenceAcknowledgement` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-303">To complete a one-way message exchange successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="01508-304">`SequenceAcknowledgement` は、送信されたメッセージの受信確認を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="01508-304">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>

<span data-ttu-id="01508-305">WCF レスポンダーは、受信確認、エラー、または空の本文と HTTP 202 状態コードを持つ応答で要求に応答できます。</span><span class="sxs-lookup"><span data-stu-id="01508-305">The WCF Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>

#### <a name="two-way-messages"></a><span data-ttu-id="01508-306">双方向のメッセージ</span><span class="sxs-lookup"><span data-stu-id="01508-306">Two Way Messages</span></span>

<span data-ttu-id="01508-307">双方向メッセージ交換プロトコルを正常に完了するために、WCF イニシエーターは HTTP 要求で要求シーケンスメッセージを送信し、HTTP 応答で応答シーケンスメッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="01508-307">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="01508-308">応答では、送信された要求シーケンス メッセージの受信確認を行う `SequenceAcknowledgement` を送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01508-308">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>

<span data-ttu-id="01508-309">WCF レスポンダーは、アプリケーション応答、エラー、または空の本文と HTTP 202 状態コードを持つ応答で要求に応答できます。</span><span class="sxs-lookup"><span data-stu-id="01508-309">The WCF Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>

<span data-ttu-id="01508-310">一方向のメッセージが存在することと、アプリケーション応答のタイミングもあるため、要求シーケンス メッセージのシーケンス番号と応答メッセージのシーケンス番号には相関関係はありません。</span><span class="sxs-lookup"><span data-stu-id="01508-310">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>

#### <a name="retrying-replies"></a><span data-ttu-id="01508-311">応答の再試行</span><span class="sxs-lookup"><span data-stu-id="01508-311">Retrying Replies</span></span>

<span data-ttu-id="01508-312">WCF は、双方向のメッセージ交換プロトコルの相関関係について、HTTP 要求/応答の相関関係に依存します。</span><span class="sxs-lookup"><span data-stu-id="01508-312">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="01508-313">このため、要求シーケンスメッセージが受信確認されたときに、HTTP 応答で `SequenceAcknowledgement` 、アプリケーション応答、またはエラーが発生した場合、WCF イニシエーターは要求シーケンスメッセージの再試行を停止しません。</span><span class="sxs-lookup"><span data-stu-id="01508-313">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="01508-314">WCF レスポンダーは、応答が関連付けられている要求の HTTP 応答で応答を再試行します。</span><span class="sxs-lookup"><span data-stu-id="01508-314">The WCF Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>

#### <a name="closesequence-exchange"></a><span data-ttu-id="01508-315">CloseSequence の交換</span><span class="sxs-lookup"><span data-stu-id="01508-315">CloseSequence Exchange</span></span>

<span data-ttu-id="01508-316">WCF イニシエーターは、すべての一方向の要求シーケンスメッセージのすべての応答シーケンスメッセージと受信確認を受信した後、 `CloseSequence` http 要求で要求シーケンスのメッセージを送信し、 `CloseSequenceResponse` http 応答でを想定します。</span><span class="sxs-lookup"><span data-stu-id="01508-316">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the WCF Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>

<span data-ttu-id="01508-317">要求シーケンスを終了すると、暗黙的に応答シーケンスが終了します。</span><span class="sxs-lookup"><span data-stu-id="01508-317">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="01508-318">つまり、WCF イニシエーターは、メッセージに応答シーケンスの最終的なを含め、 `SequenceAcknowledgement` `CloseSequence` 応答シーケンスには交換がありません `CloseSequence` 。</span><span class="sxs-lookup"><span data-stu-id="01508-318">This means the WCF Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>

<span data-ttu-id="01508-319">WCF レスポンダーは、すべての応答が確認され、HTTP 応答でメッセージを送信することを保証し `CloseSequenceResponse` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-319">The WCF Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="01508-320">TerminateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="01508-320">TerminateSequence Exchange</span></span>

<span data-ttu-id="01508-321">`CloseSequenceResponse`WCF イニシエーターは、メッセージを受信すると、 `TerminateSequence` http 要求で要求シーケンスのメッセージを送信し、 `TerminateSequenceResponse` http 応答でを想定します。</span><span class="sxs-lookup"><span data-stu-id="01508-321">After receiving the `CloseSequenceResponse` message, the WCF Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>

<span data-ttu-id="01508-322">`CloseSequence` 交換と同じように、要求シーケンスを終了すると、暗黙的に応答シーケンスが終了します。</span><span class="sxs-lookup"><span data-stu-id="01508-322">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="01508-323">つまり、WCF イニシエーターは、メッセージに応答シーケンスの最終的なを含め、 `SequenceAcknowledgement` `TerminateSequence` 応答シーケンスには交換がありません `TerminateSequence` 。</span><span class="sxs-lookup"><span data-stu-id="01508-323">This means the WCF Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>

<span data-ttu-id="01508-324">WCF レスポンダーは、 `TerminateSequenceResponse` HTTP 応答でメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="01508-324">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>

### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="01508-325">要求/応答 : アドレス可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="01508-325">Request/Reply, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="01508-326">バインド</span><span class="sxs-lookup"><span data-stu-id="01508-326">Binding</span></span>

<span data-ttu-id="01508-327">WCF は、1つの受信および1つの送信 HTTP チャネルに対して2つのシーケンスを使用して、要求/応答メッセージ交換パターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="01508-327">WCF provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="01508-328">このメッセージ交換パターンは、限定された方法で `Duplex, Addressable` イニシエーター メッセージ交換パターンに組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="01508-328">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="01508-329">WCF は、HTTP 要求を使用してすべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="01508-329">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="01508-330">すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="01508-330">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="01508-331">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="01508-331">CreateSequence Exchange</span></span>

<span data-ttu-id="01508-332">WCF イニシエーターは、 `CreateSequence` HTTP 要求の要素を使用してメッセージを送信し `Offer` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-332">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="01508-333">WCF レスポンダーは、に要素があることを確認し、 `CreateSequence` `Offer` シーケンスを作成し、要素を使用してメッセージを送信し `CreateSequenceResponse` `Accept` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-333">The WCF Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>

#### <a name="requestreply-correlation"></a><span data-ttu-id="01508-334">要求/応答の相関関係</span><span class="sxs-lookup"><span data-stu-id="01508-334">Request/Reply Correlation</span></span>

<span data-ttu-id="01508-335">次の状況は、すべての相関関係にある要求/応答で発生します。</span><span class="sxs-lookup"><span data-stu-id="01508-335">The following applies to all correlated requests and replies:</span></span>

- <span data-ttu-id="01508-336">WCF は、すべてのアプリケーション要求メッセージに `ReplyTo` エンドポイント参照とがあることを保証し `MessageId` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-336">WCF ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>

- <span data-ttu-id="01508-337">WCF は、各アプリケーション要求メッセージのとしてローカルエンドポイント参照を適用し `ReplyTo` ます。</span><span class="sxs-lookup"><span data-stu-id="01508-337">WCF applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="01508-338">ローカル エンドポイント参照は、イニシエーターの `CreateSequence` メッセージの `ReplyTo` であり、レスポンダーの `CreateSequence` メッセージの `To` です。</span><span class="sxs-lookup"><span data-stu-id="01508-338">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>

- <span data-ttu-id="01508-339">WCF では、受信要求メッセージにとが確実に送信さ `MessageId` `ReplyTo` れます。</span><span class="sxs-lookup"><span data-stu-id="01508-339">WCF ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>

- <span data-ttu-id="01508-340">WCF は、 `ReplyTo` すべてのアプリケーション要求メッセージのエンドポイント参照の URI が、前に定義したローカルエンドポイント参照と一致することを保証します。</span><span class="sxs-lookup"><span data-stu-id="01508-340">WCF ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>

- <span data-ttu-id="01508-341">WCF では、 `RelatesTo` `To` 要求/応答の相関関係規則に従って、すべての応答が正しいとヘッダーを持つことが保証さ `wsa` れます。</span><span class="sxs-lookup"><span data-stu-id="01508-341">WCF ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>
