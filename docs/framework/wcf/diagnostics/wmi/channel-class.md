---
description: '詳細: Channel クラス'
title: チャネル クラス
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: dcc92f78f09e9a73a24134c6c0685949f46f38dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757723"
---
# <a name="channel-class"></a><span data-ttu-id="de6c1-103">チャネル クラス</span><span class="sxs-lookup"><span data-stu-id="de6c1-103">Channel class</span></span>

<span data-ttu-id="de6c1-104">チャネル</span><span class="sxs-lookup"><span data-stu-id="de6c1-104">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de6c1-105">構文</span><span class="sxs-lookup"><span data-stu-id="de6c1-105">Syntax</span></span>  
  
```csharp
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="de6c1-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="de6c1-106">Methods</span></span>  

 <span data-ttu-id="de6c1-107">チャネル クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="de6c1-107">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="de6c1-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="de6c1-108">Properties</span></span>  

 <span data-ttu-id="de6c1-109">チャネル クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="de6c1-109">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="de6c1-110">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="de6c1-110">LocalAddress</span></span>  

 <span data-ttu-id="de6c1-111">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="de6c1-111">Data type: string</span></span>  
  
 <span data-ttu-id="de6c1-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="de6c1-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de6c1-113">チャネルのローカル エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="de6c1-113">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="de6c1-114">ref</span><span class="sxs-lookup"><span data-stu-id="de6c1-114">ref</span></span>  

 <span data-ttu-id="de6c1-115">データ型 : Endpoint</span><span class="sxs-lookup"><span data-stu-id="de6c1-115">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="de6c1-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="de6c1-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de6c1-117">チャネルが接続するエンドポイントへの参照。</span><span class="sxs-lookup"><span data-stu-id="de6c1-117">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="de6c1-118">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="de6c1-118">RemoteAddress</span></span>  

 <span data-ttu-id="de6c1-119">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="de6c1-119">Data type: string</span></span>  
  
 <span data-ttu-id="de6c1-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="de6c1-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de6c1-121">チャネルに関連するリモート アドレス。</span><span class="sxs-lookup"><span data-stu-id="de6c1-121">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="de6c1-122">SessionId</span><span class="sxs-lookup"><span data-stu-id="de6c1-122">SessionId</span></span>  

 <span data-ttu-id="de6c1-123">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="de6c1-123">Data type: string</span></span>  
  
 <span data-ttu-id="de6c1-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="de6c1-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de6c1-125">現在のセッション ID (存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="de6c1-125">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="de6c1-126">Type</span><span class="sxs-lookup"><span data-stu-id="de6c1-126">Type</span></span>  

 <span data-ttu-id="de6c1-127">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="de6c1-127">Data type: string</span></span>  
  
 <span data-ttu-id="de6c1-128">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="de6c1-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de6c1-129">チャネルの型。</span><span class="sxs-lookup"><span data-stu-id="de6c1-129">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de6c1-130">要件</span><span class="sxs-lookup"><span data-stu-id="de6c1-130">Requirements</span></span>  
  
|<span data-ttu-id="de6c1-131">MOF</span><span class="sxs-lookup"><span data-stu-id="de6c1-131">MOF</span></span>|<span data-ttu-id="de6c1-132">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="de6c1-132">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="de6c1-133">名前空間</span><span class="sxs-lookup"><span data-stu-id="de6c1-133">Namespace</span></span>|<span data-ttu-id="de6c1-134">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="de6c1-134">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de6c1-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="de6c1-135">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelBase>
