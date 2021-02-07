---
description: '詳細情報: サービス'
title: サービス
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: e66f9a23f8c182327899904c26ff6a6368b9bdc6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715627"
---
# <a name="service"></a><span data-ttu-id="8e3a2-103">サービス</span><span class="sxs-lookup"><span data-stu-id="8e3a2-103">Service</span></span>

<span data-ttu-id="8e3a2-104">サービス</span><span class="sxs-lookup"><span data-stu-id="8e3a2-104">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e3a2-105">構文</span><span class="sxs-lookup"><span data-stu-id="8e3a2-105">Syntax</span></span>  
  
```csharp
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8e3a2-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="8e3a2-106">Methods</span></span>  

 <span data-ttu-id="8e3a2-107">Service クラスで定義されているメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="8e3a2-107">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8e3a2-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8e3a2-108">Properties</span></span>  

 <span data-ttu-id="8e3a2-109">Service クラスには次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="8e3a2-109">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="8e3a2-110">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="8e3a2-110">BaseAddresses</span></span>  

 <span data-ttu-id="8e3a2-111">データ型 : string array</span><span class="sxs-lookup"><span data-stu-id="8e3a2-111">Data type: string array</span></span>  
  
 <span data-ttu-id="8e3a2-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8e3a2-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e3a2-113">サービスによって使用されるベース アドレスです。</span><span class="sxs-lookup"><span data-stu-id="8e3a2-113">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="8e3a2-114">動作</span><span class="sxs-lookup"><span data-stu-id="8e3a2-114">Behaviors</span></span>  

 <span data-ttu-id="8e3a2-115">データ型 : Behavior array</span><span class="sxs-lookup"><span data-stu-id="8e3a2-115">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="8e3a2-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8e3a2-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e3a2-117">このサービスに関連付けられている動作です。</span><span class="sxs-lookup"><span data-stu-id="8e3a2-117">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="8e3a2-118">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="8e3a2-118">ConfigurationName</span></span>  

 <span data-ttu-id="8e3a2-119">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="8e3a2-119">Data type: string</span></span>  
  
 <span data-ttu-id="8e3a2-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8e3a2-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e3a2-121">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="8e3a2-121">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="8e3a2-122">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="8e3a2-122">CounterInstanceName</span></span>  

 <span data-ttu-id="8e3a2-123">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="8e3a2-123">Data type: string</span></span>  
  
 <span data-ttu-id="8e3a2-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8e3a2-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e3a2-125">サービスのパフォーマンス カウンターのインスタンスのインスタンス名です。</span><span class="sxs-lookup"><span data-stu-id="8e3a2-125">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="8e3a2-126">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="8e3a2-126">DistinguishedName</span></span>  

 <span data-ttu-id="8e3a2-127">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="8e3a2-127">Data type: string</span></span>  
  
 <span data-ttu-id="8e3a2-128">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8e3a2-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e3a2-129">アドレスでのサービス名です。</span><span class="sxs-lookup"><span data-stu-id="8e3a2-129">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="8e3a2-130">Extensions</span><span class="sxs-lookup"><span data-stu-id="8e3a2-130">Extensions</span></span>  

 <span data-ttu-id="8e3a2-131">データ型 : string array</span><span class="sxs-lookup"><span data-stu-id="8e3a2-131">Data type: string array</span></span>  
  
 <span data-ttu-id="8e3a2-132">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8e3a2-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e3a2-133">サービス インスタンスの拡張に対するインスタンス コンテキストです。</span><span class="sxs-lookup"><span data-stu-id="8e3a2-133">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="8e3a2-134">メタデータ</span><span class="sxs-lookup"><span data-stu-id="8e3a2-134">Metadata</span></span>  

 <span data-ttu-id="8e3a2-135">データ型 : string array</span><span class="sxs-lookup"><span data-stu-id="8e3a2-135">Data type: string array</span></span>  
  
 <span data-ttu-id="8e3a2-136">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8e3a2-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e3a2-137">サービス メタデータの設定です。</span><span class="sxs-lookup"><span data-stu-id="8e3a2-137">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="8e3a2-138">名前</span><span class="sxs-lookup"><span data-stu-id="8e3a2-138">Name</span></span>  

 <span data-ttu-id="8e3a2-139">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="8e3a2-139">Data type: string</span></span>  
  
 <span data-ttu-id="8e3a2-140">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8e3a2-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e3a2-141">このサービスの一意の名前。</span><span class="sxs-lookup"><span data-stu-id="8e3a2-141">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="8e3a2-142">名前空間</span><span class="sxs-lookup"><span data-stu-id="8e3a2-142">Namespace</span></span>  

 <span data-ttu-id="8e3a2-143">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="8e3a2-143">Data type: string</span></span>  
  
 <span data-ttu-id="8e3a2-144">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8e3a2-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e3a2-145">サービスの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="8e3a2-145">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="8e3a2-146">開始済み</span><span class="sxs-lookup"><span data-stu-id="8e3a2-146">Opened</span></span>  

 <span data-ttu-id="8e3a2-147">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="8e3a2-147">Data type: datetime</span></span>  
  
 <span data-ttu-id="8e3a2-148">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8e3a2-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e3a2-149">サービスが開かれた時刻です。</span><span class="sxs-lookup"><span data-stu-id="8e3a2-149">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="8e3a2-150">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="8e3a2-150">OutgoingChannels</span></span>  

 <span data-ttu-id="8e3a2-151">データ型 : Channel 配列</span><span class="sxs-lookup"><span data-stu-id="8e3a2-151">Data type: Channel array</span></span>  
  
 <span data-ttu-id="8e3a2-152">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8e3a2-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e3a2-153">サービス インスタンスから送信しているチャネルです。</span><span class="sxs-lookup"><span data-stu-id="8e3a2-153">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="8e3a2-154">ProcessId</span><span class="sxs-lookup"><span data-stu-id="8e3a2-154">ProcessId</span></span>  

 <span data-ttu-id="8e3a2-155">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="8e3a2-155">Data type: sint32</span></span>  
  
 <span data-ttu-id="8e3a2-156">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8e3a2-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e3a2-157">サービスをホストするプロセスのプロセス ID です。</span><span class="sxs-lookup"><span data-stu-id="8e3a2-157">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e3a2-158">要件</span><span class="sxs-lookup"><span data-stu-id="8e3a2-158">Requirements</span></span>  
  
|<span data-ttu-id="8e3a2-159">MOF</span><span class="sxs-lookup"><span data-stu-id="8e3a2-159">MOF</span></span>|<span data-ttu-id="8e3a2-160">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="8e3a2-160">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8e3a2-161">名前空間</span><span class="sxs-lookup"><span data-stu-id="8e3a2-161">Namespace</span></span>|<span data-ttu-id="8e3a2-162">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="8e3a2-162">Defined in root\ServiceModel</span></span>|
