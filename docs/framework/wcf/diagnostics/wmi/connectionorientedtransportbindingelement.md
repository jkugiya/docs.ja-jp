---
description: '詳細情報: ConnectionOrientedTransportBindingElement'
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: bd0c05fc86ad7bc95837cee7e22ea83975369b62
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757580"
---
# <a name="connectionorientedtransportbindingelement"></a><span data-ttu-id="07488-103">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="07488-103">ConnectionOrientedTransportBindingElement</span></span>

<span data-ttu-id="07488-104">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="07488-104">ConnectionOrientedTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07488-105">構文</span><span class="sxs-lookup"><span data-stu-id="07488-105">Syntax</span></span>  
  
```csharp
class ConnectionOrientedTransportBindingElement : TransportBindingElement  
{  
  datetime ChannelInitializationTimeout;  
  sint32 ConnectionBufferSize;  
  string HostNameComparisonMode;  
  sint32 MaxBufferSize;  
  datetime MaxOutputDelay;  
  sint32 MaxPendingAccepts;  
  sint32 MaxPendingConnections;  
  string TransferMode;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="07488-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="07488-106">Methods</span></span>  

 <span data-ttu-id="07488-107">ConnectionOrientedTransportBindingElement クラスで定義されているメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="07488-107">The ConnectionOrientedTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="07488-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="07488-108">Properties</span></span>  

 <span data-ttu-id="07488-109">ConnectionOrientedTransportBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="07488-109">The ConnectionOrientedTransportBindingElement class has the following properties:</span></span>  
  
### <a name="channelinitializationtimeout"></a><span data-ttu-id="07488-110">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="07488-110">ChannelInitializationTimeout</span></span>  

 <span data-ttu-id="07488-111">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="07488-111">Data type: datetime</span></span>  
  
 <span data-ttu-id="07488-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="07488-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07488-113">チャネルの初期化が開始されてからタイムアウトになるまでの時間の長さを示す期間。</span><span class="sxs-lookup"><span data-stu-id="07488-113">The timespan that specifies how long the channel initialization has to complete before timing out.</span></span>  
  
### <a name="connectionbuffersize"></a><span data-ttu-id="07488-114">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="07488-114">ConnectionBufferSize</span></span>  

 <span data-ttu-id="07488-115">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="07488-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="07488-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="07488-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07488-117">クライアントまたサービスからネットワークでシリアル化されたメッセージのチャンクを転送するために使用されるバッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="07488-117">The size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="07488-118">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="07488-118">HostNameComparisonMode</span></span>  

 <span data-ttu-id="07488-119">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="07488-119">Data type: string</span></span>  
  
 <span data-ttu-id="07488-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="07488-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07488-121">URI の照合時にサービスに到達するため、ホスト名が使用されたかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="07488-121">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="07488-122">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="07488-122">MaxBufferSize</span></span>  

 <span data-ttu-id="07488-123">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="07488-123">Data type: sint32</span></span>  
  
 <span data-ttu-id="07488-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="07488-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07488-125">使用するバッファーの最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="07488-125">The maximum size of the buffer to use.</span></span>  
  
### <a name="maxoutputdelay"></a><span data-ttu-id="07488-126">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="07488-126">MaxOutputDelay</span></span>  

 <span data-ttu-id="07488-127">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="07488-127">Data type: datetime</span></span>  
  
 <span data-ttu-id="07488-128">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="07488-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07488-129">メッセージのチャンクまたは完全なメッセージを、送信前にメモリ内のバッファーに残したままにできる最長期間。</span><span class="sxs-lookup"><span data-stu-id="07488-129">The maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>  
  
### <a name="maxpendingaccepts"></a><span data-ttu-id="07488-130">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="07488-130">MaxPendingAccepts</span></span>  

 <span data-ttu-id="07488-131">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="07488-131">Data type: sint32</span></span>  
  
 <span data-ttu-id="07488-132">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="07488-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07488-133">サービスでの着信接続処理に使用できる保留中の非同期受け入れスレッドの最大数。</span><span class="sxs-lookup"><span data-stu-id="07488-133">The maximum number of pending asynchronous accept threads that are available for processing incoming connections on the service.</span></span>  
  
### <a name="maxpendingconnections"></a><span data-ttu-id="07488-134">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="07488-134">MaxPendingConnections</span></span>  

 <span data-ttu-id="07488-135">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="07488-135">Data type: sint32</span></span>  
  
 <span data-ttu-id="07488-136">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="07488-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07488-137">保留状態の接続の最大数。</span><span class="sxs-lookup"><span data-stu-id="07488-137">The maximum number of pending connections.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="07488-138">TransferMode</span><span class="sxs-lookup"><span data-stu-id="07488-138">TransferMode</span></span>  

 <span data-ttu-id="07488-139">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="07488-139">Data type: string</span></span>  
  
 <span data-ttu-id="07488-140">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="07488-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07488-141">接続指向トランスポートを使用して、メッセージをバッファーするかまたはストリームするかを指定する値。</span><span class="sxs-lookup"><span data-stu-id="07488-141">A value that specifies whether the messages are buffered or streamed with the connection-oriented transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07488-142">要件</span><span class="sxs-lookup"><span data-stu-id="07488-142">Requirements</span></span>  
  
|<span data-ttu-id="07488-143">MOF</span><span class="sxs-lookup"><span data-stu-id="07488-143">MOF</span></span>|<span data-ttu-id="07488-144">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="07488-144">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="07488-145">名前空間</span><span class="sxs-lookup"><span data-stu-id="07488-145">Namespace</span></span>|<span data-ttu-id="07488-146">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="07488-146">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07488-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="07488-147">See also</span></span>

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
