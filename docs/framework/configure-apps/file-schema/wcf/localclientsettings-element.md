---
description: '詳細情報: <localClientSettings> 要素'
title: <localClientSettings> 要素
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: 6393a460b5a58ab9bf7933df8643df3530da5f14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802217"
---
# <a name="localclientsettings-element"></a><span data-ttu-id="c3d2d-103">\<localClientSettings> 要素</span><span class="sxs-lookup"><span data-stu-id="c3d2d-103">\<localClientSettings> element</span></span>

<span data-ttu-id="c3d2d-104">このバインディングのローカル クライアントのセキュリティ設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-104">Specifies the security settings of a local client for this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="c3d2d-105">構文</span><span class="sxs-lookup"><span data-stu-id="c3d2d-105">Syntax</span></span>  
  
```xml  
<security>
   <localClientSettings cacheCookies="Boolean"
                        cookieRenewalThresholdPercentage="Integer"
                        detectReplays="Boolean"
                        maxClockSkew="TimeSpan"
                        maxCookieCachingTime="TimeSpan"
                        reconnectTransportOnFailure="Boolean"
                        replayCacheSize="Integer"
                        replayWindow="TimeSpan"
                        sessionKeyRenewalInterval="TimeSpan"
                        sessionKeyRolloverInterval="TimeSpan"
                        timestampValidityDuration="TimeSpan" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3d2d-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c3d2d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c3d2d-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3d2d-108">属性</span><span class="sxs-lookup"><span data-stu-id="c3d2d-108">Attributes</span></span>  
  
|<span data-ttu-id="c3d2d-109">属性</span><span class="sxs-lookup"><span data-stu-id="c3d2d-109">Attribute</span></span>|<span data-ttu-id="c3d2d-110">説明</span><span class="sxs-lookup"><span data-stu-id="c3d2d-110">Description</span></span>|  
|---------------|-----------------|  
|`cacheCookies`|<span data-ttu-id="c3d2d-111">クッキーのキャッシュが有効かどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-111">A Boolean value that specifies whether cookie caching is enabled.</span></span> <span data-ttu-id="c3d2d-112">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-112">The default is `false`.</span></span>|  
|`cookieRenewalThresholdPercentage`|<span data-ttu-id="c3d2d-113">更新できるクッキーの最大パーセンテージを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-113">An integer that specifies the maximum percentage of cookies that can be renewed.</span></span> <span data-ttu-id="c3d2d-114">この値は、0 ～ 100 (0 と 100を含む) のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-114">This value should be between 0 and 100 inclusively.</span></span> <span data-ttu-id="c3d2d-115">既定値は 90 です。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-115">The default is 90.</span></span>|  
|`detectReplays`|<span data-ttu-id="c3d2d-116">チャネルに対するリプレイ攻撃を検出し、自動的に処理するかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-116">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="c3d2d-117">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-117">The default is `false`.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="c3d2d-118">通信している双方の 2 つのシステム クロックのずれの最長時間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-118">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="c3d2d-119">既定値は、"00:05:00" です。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-119">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="c3d2d-120">この値が既定値に設定されている場合、受信側はメッセージが受信された時間より前後最大 5 分間の送信時間タイム スタンプを持つメッセージを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-120">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="c3d2d-121">送信時間テストにパスしないメッセージは拒否されます。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-121">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="c3d2d-122">この設定は、`replayWindow` 属性と組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-122">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxCookieCachingTime`|<span data-ttu-id="c3d2d-123">クッキーの最長有効期間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-123">A <xref:System.TimeSpan> that specifies the maximum lifetime of cookies.</span></span> <span data-ttu-id="c3d2d-124">デフォルト値は "10675199.02:48:05.4775807" です。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-124">The default value is "10675199.02:48:05.4775807".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="c3d2d-125">WS-ReliableMessaging を使用した接続が、トランスポート エラーの後再接続を試みるかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-125">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="c3d2d-126">既定値は `true` です。これは、再接続の試行が無限に行われることを意味します。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-126">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="c3d2d-127">循環は非アクティブ タイムアウトにより破棄され、再接続できない場合はチャネルが例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-127">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="c3d2d-128">リプレイ検証で使用される、キャッシュ済みの nonce 数を指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-128">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="c3d2d-129">この制限を越えると、最も古い nonce が削除され、新しいメッセージ用に新しい nonce が作成されます。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-129">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="c3d2d-130">既定値は 500000 です。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-130">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="c3d2d-131">個別のメッセージ nonce の有効期間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-131">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="c3d2d-132">この期間が過ぎると、以前に送信されたメッセージと同じ nonce を持つメッセージは受け入れられません。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-132">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="c3d2d-133">この属性は、リプレイ攻撃を防ぐために `maxClockSkew` 属性と組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-133">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="c3d2d-134">攻撃者は、メッセージのリプレイ ウィンドウの期限が切れた後にメッセージをリプレイする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-134">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="c3d2d-135">ただし、このメッセージは `maxClockSkew` テストに失敗します。このテストは、メッセージが受信された時間の前後指定時間以内の送信時間タイムスタンプを持つメッセージを拒否します。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-135">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="c3d2d-136">イニシエーターがセキュリティ セッションのキーを更新するまでの期間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-136">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="c3d2d-137">既定値は "10:00:00" です。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-137">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="c3d2d-138">キーの更新中に、前のセッション キーが受信メッセージで有効な時間間隔を指定する <xref:System.TimeSpan> です。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-138">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="c3d2d-139">既定値は "00:05:00" です。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-139">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="c3d2d-140">キーの更新中、クライアントおよびサーバーは、常に、利用可能な最新のキーを使用してメッセージを送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-140">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="c3d2d-141">どちらのパーティも、ロールオーバー時間に達するまで、前のセッション キーで保護された受信メッセージを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-141">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="c3d2d-142">タイムスタンプの有効期間を指定する正の <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-142">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="c3d2d-143">既定値は "00:15:00" です。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-143">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c3d2d-144">子要素</span><span class="sxs-lookup"><span data-stu-id="c3d2d-144">Child Elements</span></span>  

 <span data-ttu-id="c3d2d-145">なし</span><span class="sxs-lookup"><span data-stu-id="c3d2d-145">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c3d2d-146">親要素</span><span class="sxs-lookup"><span data-stu-id="c3d2d-146">Parent Elements</span></span>  
  
|<span data-ttu-id="c3d2d-147">要素</span><span class="sxs-lookup"><span data-stu-id="c3d2d-147">Element</span></span>|<span data-ttu-id="c3d2d-148">説明</span><span class="sxs-lookup"><span data-stu-id="c3d2d-148">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="c3d2d-149">カスタム バインドのセキュリティ オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-149">Specifies the security options for a custom binding.</span></span>|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="c3d2d-150">セキュリティで保護されたメッセージ交換サービスの開始に使用される既定値を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-150">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3d2d-151">解説</span><span class="sxs-lookup"><span data-stu-id="c3d2d-151">Remarks</span></span>  

 <span data-ttu-id="c3d2d-152">この設定は、サービスのセキュリティ ポリシーから派生する設定ではないという点でローカルです。</span><span class="sxs-lookup"><span data-stu-id="c3d2d-152">The settings are local in the sense that they are not settings derived from the security policy of the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3d2d-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="c3d2d-153">See also</span></span>

- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="c3d2d-154">バインド</span><span class="sxs-lookup"><span data-stu-id="c3d2d-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c3d2d-155">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="c3d2d-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c3d2d-156">カスタムバインド</span><span class="sxs-lookup"><span data-stu-id="c3d2d-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="c3d2d-157">方法: SecurityBindingElement を使用してカスタム バインドを作成する</span><span class="sxs-lookup"><span data-stu-id="c3d2d-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="c3d2d-158">カスタム バインディング セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c3d2d-158">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
