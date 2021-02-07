---
description: '詳細情報: ChannelPoolSettings'
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: b08c5483e7a0c918393795b4608b9eef16b18341
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757684"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="79546-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="79546-103">ChannelPoolSettings</span></span>

<span data-ttu-id="79546-104">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="79546-104">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79546-105">構文</span><span class="sxs-lookup"><span data-stu-id="79546-105">Syntax</span></span>  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="79546-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="79546-106">Methods</span></span>  

 <span data-ttu-id="79546-107">ChannelPoolSettings クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="79546-107">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="79546-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="79546-108">Properties</span></span>  

 <span data-ttu-id="79546-109">ChannelPoolSettings クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="79546-109">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="79546-110">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="79546-110">IdleTimeout</span></span>  

 <span data-ttu-id="79546-111">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="79546-111">Data type: datetime</span></span>  
  
 <span data-ttu-id="79546-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="79546-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79546-113">接続が切断されるまでの最大アイドル時間。</span><span class="sxs-lookup"><span data-stu-id="79546-113">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="79546-114">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="79546-114">LeaseTimeout</span></span>  

 <span data-ttu-id="79546-115">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="79546-115">Data type: datetime</span></span>  
  
 <span data-ttu-id="79546-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="79546-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79546-117">リース操作の完了がタイムアウトするまでの最大時間。</span><span class="sxs-lookup"><span data-stu-id="79546-117">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="79546-118">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="79546-118">MaxOutboundChannelsPerEndpoint</span></span>  

 <span data-ttu-id="79546-119">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="79546-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="79546-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="79546-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79546-121">各エンドポイントでの送信チャネルの最大数。</span><span class="sxs-lookup"><span data-stu-id="79546-121">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79546-122">要件</span><span class="sxs-lookup"><span data-stu-id="79546-122">Requirements</span></span>  
  
|<span data-ttu-id="79546-123">MOF</span><span class="sxs-lookup"><span data-stu-id="79546-123">MOF</span></span>|<span data-ttu-id="79546-124">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="79546-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="79546-125">名前空間</span><span class="sxs-lookup"><span data-stu-id="79546-125">Namespace</span></span>|<span data-ttu-id="79546-126">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="79546-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79546-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="79546-127">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
