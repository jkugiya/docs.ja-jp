---
description: '詳細情報: <localServiceSettings> 要素'
title: <localServiceSettings> 要素
ms.date: 03/30/2017
ms.assetid: 0658549c-3f65-46dd-8c5c-9895441ed734
ms.openlocfilehash: ee3306588d6a86ed9ced9c66624cd34f18e2c5c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802204"
---
# <a name="localservicesettings-element"></a><span data-ttu-id="8c67c-103">\<localServiceSettings> 要素</span><span class="sxs-lookup"><span data-stu-id="8c67c-103">\<localServiceSettings> element</span></span>

<span data-ttu-id="8c67c-104">このバインディングのローカル サービスのセキュリティ設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="8c67c-104">Specifies the security settings of a local service for this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localServiceSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="8c67c-105">構文</span><span class="sxs-lookup"><span data-stu-id="8c67c-105">Syntax</span></span>  
  
```xml  
<security>
  <localServiceSettings detectReplays="Boolean"
                        inactivityTimeout="TimeSpan"
                        issuedCookieLifeTime="TimeSpan"
                        maxCachedCookies="Integer"
                        maxClockSkew="TimeSpan"
                        maxPendingSessions="Integer"
                        maxStatefulNegotiations="Integer"
                        negotiationTimeout="TimeSpan"
                        reconnectTransportOnFailure="Boolean"
                        replayCacheSize="Integer"
                        replayWindow="TimeSpan"
                        sessionKeyRenewalInterval="TimeSpan"
                        sessionKeyRolloverInterval="TimeSpan"
                        timestampValidityDuration="TimeSpan" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c67c-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8c67c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="8c67c-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c67c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c67c-108">属性</span><span class="sxs-lookup"><span data-stu-id="8c67c-108">Attributes</span></span>  
  
|<span data-ttu-id="8c67c-109">属性</span><span class="sxs-lookup"><span data-stu-id="8c67c-109">Attribute</span></span>|<span data-ttu-id="8c67c-110">説明</span><span class="sxs-lookup"><span data-stu-id="8c67c-110">Description</span></span>|  
|---------------|-----------------|  
|`detectReplays`|<span data-ttu-id="8c67c-111">チャネルに対するリプレイ攻撃を検出し、自動的に処理するかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="8c67c-111">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="8c67c-112">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="8c67c-112">The default is `false`.</span></span>|  
|`inactivityTimeout`|<span data-ttu-id="8c67c-113"><xref:System.TimeSpan>チャネルがタイムアウトまで待機する非アクティブな時間を指定する正の。既定値は "01:00:00" です。</span><span class="sxs-lookup"><span data-stu-id="8c67c-113">A positive <xref:System.TimeSpan> that specifies the duration of inactivity the channel waits before it times out. The default is "01:00:00".</span></span>|  
|`issuedCookieLifeTime`|<span data-ttu-id="8c67c-114">すべての新しいセキュリティ クッキーに発行される有効期間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="8c67c-114">A <xref:System.TimeSpan> that specifies the lifetime issued to all new security cookies.</span></span> <span data-ttu-id="8c67c-115">有効期間を超えるクッキーは、再利用され、再度ネゴシエートされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c67c-115">Cookies that exceed their lifetime are recycled and need to be negotiated again.</span></span> <span data-ttu-id="8c67c-116">既定値は、"10:00:00" です。</span><span class="sxs-lookup"><span data-stu-id="8c67c-116">The default value is "10:00:00".</span></span>|  
|`maxCachedCookies`|<span data-ttu-id="8c67c-117">キャッシュできるクッキーの最大数を指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="8c67c-117">A positive integer that specifies the maximum number of cookies that can be cached.</span></span> <span data-ttu-id="8c67c-118">既定値は 1000 です。</span><span class="sxs-lookup"><span data-stu-id="8c67c-118">The default is 1000.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="8c67c-119">通信している双方の 2 つのシステム クロックのずれの最長時間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="8c67c-119">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="8c67c-120">既定値は、"00:05:00" です。</span><span class="sxs-lookup"><span data-stu-id="8c67c-120">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="8c67c-121">この値が既定値に設定されている場合、受信側はメッセージが受信された時間より前後最大 5 分間の送信時間タイム スタンプを持つメッセージを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="8c67c-121">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="8c67c-122">送信時間テストにパスしないメッセージは拒否されます。</span><span class="sxs-lookup"><span data-stu-id="8c67c-122">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="8c67c-123">この設定は、`replayWindow` 属性と組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="8c67c-123">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxPendingSessions`|<span data-ttu-id="8c67c-124">サービスがサポートする保留状態のセキュリティ セッションの最大数を指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="8c67c-124">A positive integer that specifies the maximum number of pending security sessions that the service supports.</span></span> <span data-ttu-id="8c67c-125">この制限に達すると、すべての新しいクライアントが SOAP エラーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="8c67c-125">When this limit is reached, all new clients receive SOAP faults.</span></span> <span data-ttu-id="8c67c-126">既定値は 1000 です。</span><span class="sxs-lookup"><span data-stu-id="8c67c-126">The default value is 1000.</span></span>|  
|`maxStatefulNegotiations`|<span data-ttu-id="8c67c-127">同時にアクティブにできるセキュリティ ネゴシエーションの数を指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="8c67c-127">A positive integer that specifies the number of security negotiations that can be active concurrently.</span></span> <span data-ttu-id="8c67c-128">制限を超えるネゴシエーション セッションはキューに置かれ、制限内に空きができた場合にのみ完了できます。</span><span class="sxs-lookup"><span data-stu-id="8c67c-128">Negotiation sessions in excess of the limit are queued and can only be completed when a space below the limit becomes available.</span></span> <span data-ttu-id="8c67c-129">既定値は 1024 です。</span><span class="sxs-lookup"><span data-stu-id="8c67c-129">The default value is 1024.</span></span>|  
|`negotiationTimeout`|<span data-ttu-id="8c67c-130">チャネルによって使用されるセキュリティ ポリシーの有効期間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="8c67c-130">A <xref:System.TimeSpan> that specifies the lifetime of the security policy used by channel.</span></span> <span data-ttu-id="8c67c-131">有効期間が切れると、チャネルは新しいセキュリティ ポリシーについてクライアントと再度ネゴシエートします。</span><span class="sxs-lookup"><span data-stu-id="8c67c-131">When the time expires, the channel renegotiates with the client for a new security policy.</span></span> <span data-ttu-id="8c67c-132">既定値は、"00:02:00" です。</span><span class="sxs-lookup"><span data-stu-id="8c67c-132">The default value is "00:02:00".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="8c67c-133">WS-ReliableMessaging を使用した接続が、トランスポート エラーの後再接続を試みるかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="8c67c-133">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="8c67c-134">既定値は `true` です。これは、再接続の試行が無限に行われることを意味します。</span><span class="sxs-lookup"><span data-stu-id="8c67c-134">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="8c67c-135">循環は非アクティブ タイムアウトにより破棄され、再接続できない場合はチャネルが例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="8c67c-135">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="8c67c-136">リプレイ検証で使用される、キャッシュ済みの nonce 数を指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="8c67c-136">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="8c67c-137">この制限を越えると、最も古い nonce が削除され、新しいメッセージ用に新しい nonce が作成されます。</span><span class="sxs-lookup"><span data-stu-id="8c67c-137">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="8c67c-138">既定値は 500000 です。</span><span class="sxs-lookup"><span data-stu-id="8c67c-138">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="8c67c-139">個別のメッセージ nonce の有効期間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="8c67c-139">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="8c67c-140">この期間が過ぎると、以前に送信されたメッセージと同じ nonce を持つメッセージは受け入れられません。</span><span class="sxs-lookup"><span data-stu-id="8c67c-140">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="8c67c-141">この属性は、リプレイ攻撃を防ぐために `maxClockSkew` 属性と組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="8c67c-141">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="8c67c-142">攻撃者は、メッセージのリプレイ ウィンドウの期限が切れた後にメッセージをリプレイする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8c67c-142">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="8c67c-143">ただし、このメッセージは `maxClockSkew` テストに失敗します。このテストは、メッセージが受信された時間の前後指定時間以内の送信時間タイムスタンプを持つメッセージを拒否します。</span><span class="sxs-lookup"><span data-stu-id="8c67c-143">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="8c67c-144">イニシエーターがセキュリティ セッションのキーを更新するまでの期間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="8c67c-144">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="8c67c-145">既定値は "10:00:00" です。</span><span class="sxs-lookup"><span data-stu-id="8c67c-145">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="8c67c-146">キーの更新中に、前のセッション キーが受信メッセージで有効な時間間隔を指定する <xref:System.TimeSpan> です。</span><span class="sxs-lookup"><span data-stu-id="8c67c-146">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="8c67c-147">既定値は "00:05:00" です。</span><span class="sxs-lookup"><span data-stu-id="8c67c-147">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="8c67c-148">キーの更新中、クライアントおよびサーバーは、常に、利用可能な最新のキーを使用してメッセージを送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c67c-148">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="8c67c-149">どちらのパーティも、ロールオーバー時間に達するまで、前のセッション キーで保護された受信メッセージを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="8c67c-149">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="8c67c-150">タイムスタンプの有効期間を指定する正の <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="8c67c-150">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="8c67c-151">既定値は "00:15:00" です。</span><span class="sxs-lookup"><span data-stu-id="8c67c-151">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c67c-152">子要素</span><span class="sxs-lookup"><span data-stu-id="8c67c-152">Child Elements</span></span>  

 <span data-ttu-id="8c67c-153">なし。</span><span class="sxs-lookup"><span data-stu-id="8c67c-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8c67c-154">親要素</span><span class="sxs-lookup"><span data-stu-id="8c67c-154">Parent Elements</span></span>  
  
|<span data-ttu-id="8c67c-155">要素</span><span class="sxs-lookup"><span data-stu-id="8c67c-155">Element</span></span>|<span data-ttu-id="8c67c-156">説明</span><span class="sxs-lookup"><span data-stu-id="8c67c-156">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="8c67c-157">カスタム バインドのセキュリティ オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="8c67c-157">Specifies the security options for a custom binding.</span></span>|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="8c67c-158">セキュリティで保護されたメッセージ交換サービスの開始に使用される既定値を指定します。</span><span class="sxs-lookup"><span data-stu-id="8c67c-158">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c67c-159">解説</span><span class="sxs-lookup"><span data-stu-id="8c67c-159">Remarks</span></span>  

 <span data-ttu-id="8c67c-160">この設定は、サービスのセキュリティ ポリシーの一部として公開されず、クライアントのバインディングには影響を与えないため、ローカルです。</span><span class="sxs-lookup"><span data-stu-id="8c67c-160">The settings are local because they are not published as part of the security policy of the service and do not affect the client's binding.</span></span>  
  
 <span data-ttu-id="8c67c-161">`localServiceSecuritySettings` 要素の以下の属性は、サービス拒否 (DOS) セキュリティ攻撃を軽減するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8c67c-161">The following attributes of the `localServiceSecuritySettings` element can help mitigate a denial-of-service (DOS) security attack:</span></span>  
  
- <span data-ttu-id="8c67c-162">`maxCachedCookies`: SPNEGO または SSL の各ネゴシエーションの実行後にサーバーによってキャッシュされる、期限付きの SecurityContextTokens の最大数を制御します。</span><span class="sxs-lookup"><span data-stu-id="8c67c-162">`maxCachedCookies`: controls the maximum number of time-bounded SecurityContextTokens that are cached by the server after doing SPNEGO or SSL negotiation.</span></span>  
  
- <span data-ttu-id="8c67c-163">`issuedCookieLifetime`: SPNEGO または SSL の各ネゴシエーションに続いてサーバーが発行する SecurityContextTokens の有効期限を制御します。</span><span class="sxs-lookup"><span data-stu-id="8c67c-163">`issuedCookieLifetime`: controls the lifetime of the SecurityContextTokens that are issued by the server following SPNEGO or SSL negotiation.</span></span> <span data-ttu-id="8c67c-164">サーバーは、この期間だけ SecurityContextTokens をキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="8c67c-164">The server caches the SecurityContextTokens for this period of time.</span></span>  
  
- <span data-ttu-id="8c67c-165">`maxPendingSessions`: サーバーで確立されているが、そのアプリケーション メッセージが処理されていない、セキュリティで保護されたメッセージ交換の最大数を制御します。</span><span class="sxs-lookup"><span data-stu-id="8c67c-165">`maxPendingSessions`: controls the maximum number of secure conversations that are established at the server but for which no application messages have been processed.</span></span> <span data-ttu-id="8c67c-166">このクォータは、クライアントが、セキュリティで保護されたメッセージ交換をサービスで確立しないようにします。それによって、サービスはクライアントごとの状態を保持できますが、それらの状態を使用することはありません。</span><span class="sxs-lookup"><span data-stu-id="8c67c-166">This quota prevents clients from establishing secure conversations at the service, thereby causing the service to maintain state for each client, but never using them.</span></span>  
  
- <span data-ttu-id="8c67c-167">`inactivityTimeout`: サービスが、セキュリティで保護されたメッセージ交換を、それに対するアプリケーション メッセージを受信しなくても維持する最長時間を制御します。</span><span class="sxs-lookup"><span data-stu-id="8c67c-167">`inactivityTimeout`: controls the maximum time that the service keeps a secure conversation alive without ever receiving an application message on it.</span></span> <span data-ttu-id="8c67c-168">このクォータは、クライアントが、セキュリティで保護されたメッセージ交換をサービスで確立しないようにします。それによって、サービスはクライアントごとの状態を保持できますが、それらの状態を使用することはありません。</span><span class="sxs-lookup"><span data-stu-id="8c67c-168">This quota prevents clients from establishing secure conversations at the service, thereby causing the service to maintain state for each client, but never using them.</span></span>  
  
 <span data-ttu-id="8c67c-169">セキュリティで保護されたメッセージ交換セッションでは、バインディングの `inactivityTimeout` 属性および `receiveTimeout` 属性の両方が、セッション タイムアウトに影響します。</span><span class="sxs-lookup"><span data-stu-id="8c67c-169">In a secure conversation session, note that both `inactivityTimeout` and the `receiveTimeout` attributes on the binding affect session timeout.</span></span> <span data-ttu-id="8c67c-170">2 つのうち短い方が、タイムアウトが発生する時間を決定します。</span><span class="sxs-lookup"><span data-stu-id="8c67c-170">The shorter of the two determines when timeouts occur.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c67c-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c67c-171">See also</span></span>

- <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="8c67c-172">バインド</span><span class="sxs-lookup"><span data-stu-id="8c67c-172">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8c67c-173">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="8c67c-173">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8c67c-174">カスタムバインド</span><span class="sxs-lookup"><span data-stu-id="8c67c-174">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="8c67c-175">方法: SecurityBindingElement を使用してカスタム バインドを作成する</span><span class="sxs-lookup"><span data-stu-id="8c67c-175">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="8c67c-176">カスタム バインディング セキュリティ</span><span class="sxs-lookup"><span data-stu-id="8c67c-176">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
