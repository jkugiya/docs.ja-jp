---
description: '詳細情報: LocalServiceSecuritySettings'
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
ms.openlocfilehash: f7220e8253c6ab218414c1be7ed90e5d593b4692
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743942"
---
# <a name="localservicesecuritysettings"></a><span data-ttu-id="ffd0b-103">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ffd0b-103">LocalServiceSecuritySettings</span></span>

<span data-ttu-id="ffd0b-104">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ffd0b-104">LocalServiceSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffd0b-105">構文</span><span class="sxs-lookup"><span data-stu-id="ffd0b-105">Syntax</span></span>  
  
```csharp
class LocalServiceSecuritySettings  
{  
  boolean DetectReplays;  
  datetime InactivityTimeout;  
  datetime IssuedCookieLifetime;  
  sint32 MaxCachedCookies;  
  datetime MaxClockSkew;  
  sint32 MaxPendingSessions;  
  sint32 MaxStatefulNegotiations;  
  datetime NegotiationTimeout;  
  boolean ReconnectTransportOnFailure;  
  sint32 ReplayCacheSize;  
  datetime ReplayWindow;  
  datetime SessionKeyRenewalInterval;  
  datetime SessionKeyRolloverInterval;  
  datetime TimestampValidityDuration;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ffd0b-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="ffd0b-106">Methods</span></span>  

 <span data-ttu-id="ffd0b-107">LocalServiceSecuritySettings クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="ffd0b-107">The LocalServiceSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ffd0b-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ffd0b-108">Properties</span></span>  

 <span data-ttu-id="ffd0b-109">LocalServiceSecuritySettings クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="ffd0b-109">The LocalServiceSecuritySettings class has the following properties:</span></span>  
  
### <a name="detectreplays"></a><span data-ttu-id="ffd0b-110">DetectReplays</span><span class="sxs-lookup"><span data-stu-id="ffd0b-110">DetectReplays</span></span>  

 <span data-ttu-id="ffd0b-111">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="ffd0b-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="ffd0b-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ffd0b-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffd0b-113">チャネルに対するリプレイ攻撃を検出し、自動的に処理するかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="ffd0b-113">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="ffd0b-114">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="ffd0b-114">InactivityTimeout</span></span>  

 <span data-ttu-id="ffd0b-115">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="ffd0b-115">Data type: datetime</span></span>  
  
 <span data-ttu-id="ffd0b-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ffd0b-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffd0b-117">サービスがサポートする保留状態のセキュリティ セッションの最大数。</span><span class="sxs-lookup"><span data-stu-id="ffd0b-117">The maximum number of pending security sessions that the service supports.</span></span>  
  
### <a name="issuedcookielifetime"></a><span data-ttu-id="ffd0b-118">IssuedCookieLifetime</span><span class="sxs-lookup"><span data-stu-id="ffd0b-118">IssuedCookieLifetime</span></span>  

 <span data-ttu-id="ffd0b-119">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="ffd0b-119">Data type: datetime</span></span>  
  
 <span data-ttu-id="ffd0b-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ffd0b-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffd0b-121">すべての新しいセキュリティ クッキーに対して発行する有効期間を指定する TimeSpan です。</span><span class="sxs-lookup"><span data-stu-id="ffd0b-121">A TimeSpan that specifies the lifetime issued to all new security cookies.</span></span>  
  
### <a name="maxcachedcookies"></a><span data-ttu-id="ffd0b-122">MaxCachedCookies</span><span class="sxs-lookup"><span data-stu-id="ffd0b-122">MaxCachedCookies</span></span>  

 <span data-ttu-id="ffd0b-123">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="ffd0b-123">Data type: sint32</span></span>  
  
 <span data-ttu-id="ffd0b-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ffd0b-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffd0b-125">キャッシュできるクッキーの最大数。</span><span class="sxs-lookup"><span data-stu-id="ffd0b-125">The maximum number of cookies that can be cached.</span></span>  
  
### <a name="maxclockskew"></a><span data-ttu-id="ffd0b-126">MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="ffd0b-126">MaxClockSkew</span></span>  

 <span data-ttu-id="ffd0b-127">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="ffd0b-127">Data type: datetime</span></span>  
  
 <span data-ttu-id="ffd0b-128">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ffd0b-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffd0b-129">通信している双方の 2 つのシステム クロックのずれの最長時間を指定する TimeSpan です。</span><span class="sxs-lookup"><span data-stu-id="ffd0b-129">A TimeSpan that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span>  
  
### <a name="maxpendingsessions"></a><span data-ttu-id="ffd0b-130">MaxPendingSessions</span><span class="sxs-lookup"><span data-stu-id="ffd0b-130">MaxPendingSessions</span></span>  

 <span data-ttu-id="ffd0b-131">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="ffd0b-131">Data type: sint32</span></span>  
  
 <span data-ttu-id="ffd0b-132">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ffd0b-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffd0b-133">サービスにおける保留状態の接続の最大数です。</span><span class="sxs-lookup"><span data-stu-id="ffd0b-133">The maximum number of pending connections on the service.</span></span>  
  
### <a name="maxstatefulnegotiations"></a><span data-ttu-id="ffd0b-134">MaxStatefulNegotiations</span><span class="sxs-lookup"><span data-stu-id="ffd0b-134">MaxStatefulNegotiations</span></span>  

 <span data-ttu-id="ffd0b-135">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="ffd0b-135">Data type: sint32</span></span>  
  
 <span data-ttu-id="ffd0b-136">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ffd0b-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffd0b-137">同時にアクティブにできるセキュリティ ネゴシエーションの数。</span><span class="sxs-lookup"><span data-stu-id="ffd0b-137">The number of security negotiations that can be active concurrently.</span></span>  
  
### <a name="negotiationtimeout"></a><span data-ttu-id="ffd0b-138">NegotiationTimeout</span><span class="sxs-lookup"><span data-stu-id="ffd0b-138">NegotiationTimeout</span></span>  

 <span data-ttu-id="ffd0b-139">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="ffd0b-139">Data type: datetime</span></span>  
  
 <span data-ttu-id="ffd0b-140">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ffd0b-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffd0b-141">サーバーとクライアント間のセキュリティ ネゴシエーション フェーズの最大継続時間を指定する TimeSpan です。</span><span class="sxs-lookup"><span data-stu-id="ffd0b-141">A TimeSpan that specifies the maximum duration for the security negotiation phase between server and client.</span></span>  
  
### <a name="reconnecttransportonfailure"></a><span data-ttu-id="ffd0b-142">ReconnectTransportOnFailure</span><span class="sxs-lookup"><span data-stu-id="ffd0b-142">ReconnectTransportOnFailure</span></span>  

 <span data-ttu-id="ffd0b-143">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="ffd0b-143">Data type: boolean</span></span>  
  
 <span data-ttu-id="ffd0b-144">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ffd0b-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffd0b-145">WS-ReliableMessaging を使用した接続が、トランスポート エラーの後再接続を試みるかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="ffd0b-145">A Boolean value that specifies whether connections using WS-Reliable messaging attempt to reconnect after transport failures.</span></span>  
  
### <a name="replaycachesize"></a><span data-ttu-id="ffd0b-146">ReplayCacheSize</span><span class="sxs-lookup"><span data-stu-id="ffd0b-146">ReplayCacheSize</span></span>  

 <span data-ttu-id="ffd0b-147">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="ffd0b-147">Data type: sint32</span></span>  
  
 <span data-ttu-id="ffd0b-148">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ffd0b-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffd0b-149">リプレイ検証で使用されるキャッシュ済みの nonce の数。</span><span class="sxs-lookup"><span data-stu-id="ffd0b-149">The number of cached nonces used for replay detection.</span></span>  
  
### <a name="replaywindow"></a><span data-ttu-id="ffd0b-150">ReplayWindow</span><span class="sxs-lookup"><span data-stu-id="ffd0b-150">ReplayWindow</span></span>  

 <span data-ttu-id="ffd0b-151">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="ffd0b-151">Data type: datetime</span></span>  
  
 <span data-ttu-id="ffd0b-152">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ffd0b-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffd0b-153">個別のメッセージの nonce の有効期間を指定する TimeSpan です。</span><span class="sxs-lookup"><span data-stu-id="ffd0b-153">A TimeSpan that specifies the duration in which individual message nonces are valid.</span></span>  
  
### <a name="sessionkeyrenewalinterval"></a><span data-ttu-id="ffd0b-154">SessionKeyRenewalInterval</span><span class="sxs-lookup"><span data-stu-id="ffd0b-154">SessionKeyRenewalInterval</span></span>  

 <span data-ttu-id="ffd0b-155">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="ffd0b-155">Data type: datetime</span></span>  
  
 <span data-ttu-id="ffd0b-156">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ffd0b-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffd0b-157">イニシエーターがセキュリティ セッションのキーを更新するまでの期間を指定する TimeSpan です。</span><span class="sxs-lookup"><span data-stu-id="ffd0b-157">A TimeSpan that specifies the duration after which the initiator renews the key for the security session.</span></span>  
  
### <a name="sessionkeyrolloverinterval"></a><span data-ttu-id="ffd0b-158">SessionKeyRolloverInterval</span><span class="sxs-lookup"><span data-stu-id="ffd0b-158">SessionKeyRolloverInterval</span></span>  

 <span data-ttu-id="ffd0b-159">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="ffd0b-159">Data type: datetime</span></span>  
  
 <span data-ttu-id="ffd0b-160">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ffd0b-160">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffd0b-161">キーの更新中に、前のセッション キーが受信メッセージで有効な時間間隔を指定する TimeSpan です。</span><span class="sxs-lookup"><span data-stu-id="ffd0b-161">A TimeSpan that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span>  
  
### <a name="timestampvalidityduration"></a><span data-ttu-id="ffd0b-162">TimestampValidityDuration</span><span class="sxs-lookup"><span data-stu-id="ffd0b-162">TimestampValidityDuration</span></span>  

 <span data-ttu-id="ffd0b-163">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="ffd0b-163">Data type: datetime</span></span>  
  
 <span data-ttu-id="ffd0b-164">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ffd0b-164">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffd0b-165">タイムスタンプの有効期間を指定する TimeSpan です。</span><span class="sxs-lookup"><span data-stu-id="ffd0b-165">A TimeSpan that specifies the duration in which a time stamp is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffd0b-166">要件</span><span class="sxs-lookup"><span data-stu-id="ffd0b-166">Requirements</span></span>  
  
|<span data-ttu-id="ffd0b-167">MOF</span><span class="sxs-lookup"><span data-stu-id="ffd0b-167">MOF</span></span>|<span data-ttu-id="ffd0b-168">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="ffd0b-168">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ffd0b-169">名前空間</span><span class="sxs-lookup"><span data-stu-id="ffd0b-169">Namespace</span></span>|<span data-ttu-id="ffd0b-170">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="ffd0b-170">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ffd0b-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="ffd0b-171">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
