---
description: '詳細情報: ReliableSessionBindingElement'
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: 582fd62a8751a31c2834b7d81219a237c9887236
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743864"
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="b53d0-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="b53d0-103">ReliableSessionBindingElement</span></span>

<span data-ttu-id="b53d0-104">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="b53d0-104">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b53d0-105">構文</span><span class="sxs-lookup"><span data-stu-id="b53d0-105">Syntax</span></span>  
  
```csharp
class ReliableSessionBindingElement : BindingElement  
{  
  datetime AcknowledgementInterval;  
  boolean FlowControlEnabled;  
  datetime InactivityTimeout;  
  sint32 MaxPendingChannels;  
  sint32 MaxRetryCount;  
  sint32 MaxTransferWindowSize;  
  boolean Ordered;  
  integer ReliableMessagingVersion;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b53d0-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="b53d0-106">Methods</span></span>  

 <span data-ttu-id="b53d0-107">ReliableSessionBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="b53d0-107">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b53d0-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b53d0-108">Properties</span></span>  

 <span data-ttu-id="b53d0-109">ReliableSessionBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="b53d0-109">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="b53d0-110">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="b53d0-110">AcknowledgementInterval</span></span>  

 <span data-ttu-id="b53d0-111">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="b53d0-111">Data type: datetime</span></span>  
  
 <span data-ttu-id="b53d0-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="b53d0-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b53d0-113">ファクトリによって作成された信頼できるチャネルで、メッセージの送信元に受信確認を送信するまで送信先が待機する時間</span><span class="sxs-lookup"><span data-stu-id="b53d0-113">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="b53d0-114">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="b53d0-114">FlowControlEnabled</span></span>  

 <span data-ttu-id="b53d0-115">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="b53d0-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="b53d0-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="b53d0-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b53d0-117">フロー制御を有効にするかどうかを示すブール値</span><span class="sxs-lookup"><span data-stu-id="b53d0-117">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="b53d0-118">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="b53d0-118">InactivityTimeout</span></span>  

 <span data-ttu-id="b53d0-119">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="b53d0-119">Data type: datetime</span></span>  
  
 <span data-ttu-id="b53d0-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="b53d0-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b53d0-121">他の通信相手がチャネルにメッセージを送信せずにいられる最長期間を指定します。他の通信相手がメッセージを送信しない期間がこの値を超えると、チャネルでエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="b53d0-121">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="b53d0-122">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="b53d0-122">MaxPendingChannels</span></span>  

 <span data-ttu-id="b53d0-123">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="b53d0-123">Data type: sint32</span></span>  
  
 <span data-ttu-id="b53d0-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="b53d0-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b53d0-125">リスナーで受け入れを待機できるチャネルの最大数。</span><span class="sxs-lookup"><span data-stu-id="b53d0-125">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="b53d0-126">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="b53d0-126">MaxRetryCount</span></span>  

 <span data-ttu-id="b53d0-127">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="b53d0-127">Data type: sint32</span></span>  
  
 <span data-ttu-id="b53d0-128">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="b53d0-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b53d0-129">基になるチャネルで `Send` を呼び出すことで、信頼できるチャネルが受信確認を受信していないメッセージの再転送を試みる最大回数</span><span class="sxs-lookup"><span data-stu-id="b53d0-129">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="b53d0-130">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="b53d0-130">MaxTransferWindowSize</span></span>  

 <span data-ttu-id="b53d0-131">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="b53d0-131">Data type: sint32</span></span>  
  
 <span data-ttu-id="b53d0-132">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="b53d0-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b53d0-133">信頼できるセッションの転送ウィンドウの最大サイズ</span><span class="sxs-lookup"><span data-stu-id="b53d0-133">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="b53d0-134">注文済み</span><span class="sxs-lookup"><span data-stu-id="b53d0-134">Ordered</span></span>  

 <span data-ttu-id="b53d0-135">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="b53d0-135">Data type: boolean</span></span>  
  
 <span data-ttu-id="b53d0-136">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="b53d0-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b53d0-137">メッセージが送信された順序で到着されることを保証するかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="b53d0-137">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="b53d0-138">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="b53d0-138">ReliableMessagingVersion</span></span>  

 <span data-ttu-id="b53d0-139">データ型 : integer</span><span class="sxs-lookup"><span data-stu-id="b53d0-139">Data type: integer</span></span>  
  
 <span data-ttu-id="b53d0-140">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="b53d0-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b53d0-141">信頼できるセッションで使用される WS-ReliableMessaging プロトコルのバージョンを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="b53d0-141">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b53d0-142">要件</span><span class="sxs-lookup"><span data-stu-id="b53d0-142">Requirements</span></span>  
  
|<span data-ttu-id="b53d0-143">MOF</span><span class="sxs-lookup"><span data-stu-id="b53d0-143">MOF</span></span>|<span data-ttu-id="b53d0-144">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="b53d0-144">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b53d0-145">名前空間</span><span class="sxs-lookup"><span data-stu-id="b53d0-145">Namespace</span></span>|<span data-ttu-id="b53d0-146">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="b53d0-146">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b53d0-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="b53d0-147">See also</span></span>

- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
