---
description: '詳細情報: エンドポイント'
title: エンドポイント
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 1c28be37d1b1abfe1813e6da8903809affd309e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757463"
---
# <a name="endpoint"></a><span data-ttu-id="49503-103">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="49503-103">Endpoint</span></span>

<span data-ttu-id="49503-104">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="49503-104">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49503-105">構文</span><span class="sxs-lookup"><span data-stu-id="49503-105">Syntax</span></span>  
  
```csharp
class Endpoint  
{  
  string Address;  
  string AddressHeaders[];  
  string AddressIdentity;  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  Binding Binding;  
  string ContractName;  
  string CounterInstanceName;  
  string ListenUri;  
  string Name;  
  sint32 ProcessId;  
  Contract ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="49503-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="49503-106">Methods</span></span>  

 <span data-ttu-id="49503-107">Endpoint クラスは次のメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="49503-107">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="49503-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="49503-108">Method</span></span>|<span data-ttu-id="49503-109">説明</span><span class="sxs-lookup"><span data-stu-id="49503-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="49503-110">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="49503-110">GetOperationCounterInstanceName</span></span>](getoperationcounterinstancename.md)|<span data-ttu-id="49503-111">操作パフォーマンス カウンターのインスタンスの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="49503-111">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="49503-112">プロパティ</span><span class="sxs-lookup"><span data-stu-id="49503-112">Properties</span></span>  

 <span data-ttu-id="49503-113">Endpoint クラスには次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="49503-113">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="49503-114">Address</span><span class="sxs-lookup"><span data-stu-id="49503-114">Address</span></span>  

 <span data-ttu-id="49503-115">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="49503-115">Data type: string</span></span>  
  
 <span data-ttu-id="49503-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="49503-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49503-117">エンドポイントのアドレスを格納している URI。</span><span class="sxs-lookup"><span data-stu-id="49503-117">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="49503-118">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="49503-118">AddressHeaders</span></span>  

 <span data-ttu-id="49503-119">データ型 : string array</span><span class="sxs-lookup"><span data-stu-id="49503-119">Data type: string array</span></span>  
  
 <span data-ttu-id="49503-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="49503-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49503-121">このエンドポイントに接続しているアドレス ヘッダーのコレクション</span><span class="sxs-lookup"><span data-stu-id="49503-121">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="49503-122">AddressIdentity</span><span class="sxs-lookup"><span data-stu-id="49503-122">AddressIdentity</span></span>  

 <span data-ttu-id="49503-123">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="49503-123">Data type: string</span></span>  
  
 <span data-ttu-id="49503-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="49503-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49503-125">エンドポイントの ID</span><span class="sxs-lookup"><span data-stu-id="49503-125">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="49503-126">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="49503-126">AppDomainId</span></span>  

 <span data-ttu-id="49503-127">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="49503-127">Data type: sint32</span></span>  
  
 <span data-ttu-id="49503-128">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="49503-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49503-129">エンドポイントをホストする appdomain の appdomain ID</span><span class="sxs-lookup"><span data-stu-id="49503-129">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="49503-130">動作</span><span class="sxs-lookup"><span data-stu-id="49503-130">Behaviors</span></span>  

 <span data-ttu-id="49503-131">データ型 : Behavior array</span><span class="sxs-lookup"><span data-stu-id="49503-131">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="49503-132">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="49503-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49503-133">このエンドポイントが実装する動作のコレクション</span><span class="sxs-lookup"><span data-stu-id="49503-133">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="49503-134">バインド</span><span class="sxs-lookup"><span data-stu-id="49503-134">Binding</span></span>  

 <span data-ttu-id="49503-135">データ型 : Binding</span><span class="sxs-lookup"><span data-stu-id="49503-135">Data type: Binding</span></span>  
  
 <span data-ttu-id="49503-136">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="49503-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49503-137">このエンドポイントが使用するバインディング</span><span class="sxs-lookup"><span data-stu-id="49503-137">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="49503-138">ContractName</span><span class="sxs-lookup"><span data-stu-id="49503-138">ContractName</span></span>  

 <span data-ttu-id="49503-139">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="49503-139">Data type: string</span></span>  
  
 <span data-ttu-id="49503-140">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="49503-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49503-141">このエンドポイントが公開するコントラクトを指定する文字列</span><span class="sxs-lookup"><span data-stu-id="49503-141">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="49503-142">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="49503-142">CounterInstanceName</span></span>  

 <span data-ttu-id="49503-143">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="49503-143">Data type: string</span></span>  
  
 <span data-ttu-id="49503-144">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="49503-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49503-145">エンドポイントのパフォーマンス カウンターのインスタンス名</span><span class="sxs-lookup"><span data-stu-id="49503-145">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="49503-146">ListenUri</span><span class="sxs-lookup"><span data-stu-id="49503-146">ListenUri</span></span>  

 <span data-ttu-id="49503-147">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="49503-147">Data type: string</span></span>  
  
 <span data-ttu-id="49503-148">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="49503-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49503-149">エンドポイントがリッスンする URI</span><span class="sxs-lookup"><span data-stu-id="49503-149">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="49503-150">名前</span><span class="sxs-lookup"><span data-stu-id="49503-150">Name</span></span>  

 <span data-ttu-id="49503-151">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="49503-151">Data type: string</span></span>  
  
 <span data-ttu-id="49503-152">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="49503-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49503-153">このエンドポイントの一意の名前</span><span class="sxs-lookup"><span data-stu-id="49503-153">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="49503-154">ProcessId</span><span class="sxs-lookup"><span data-stu-id="49503-154">ProcessId</span></span>  

 <span data-ttu-id="49503-155">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="49503-155">Data type: sint32</span></span>  
  
 <span data-ttu-id="49503-156">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="49503-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49503-157">エンドポイントをホストするプロセスのプロセス ID</span><span class="sxs-lookup"><span data-stu-id="49503-157">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="49503-158">ref</span><span class="sxs-lookup"><span data-stu-id="49503-158">ref</span></span>  

 <span data-ttu-id="49503-159">データ型 : Contract</span><span class="sxs-lookup"><span data-stu-id="49503-159">Data type: Contract</span></span>  
  
 <span data-ttu-id="49503-160">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="49503-160">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49503-161">このエンドポイントが公開しているコントラクト。</span><span class="sxs-lookup"><span data-stu-id="49503-161">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49503-162">要件</span><span class="sxs-lookup"><span data-stu-id="49503-162">Requirements</span></span>  
  
|<span data-ttu-id="49503-163">MOF</span><span class="sxs-lookup"><span data-stu-id="49503-163">MOF</span></span>|<span data-ttu-id="49503-164">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="49503-164">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="49503-165">名前空間</span><span class="sxs-lookup"><span data-stu-id="49503-165">Namespace</span></span>|<span data-ttu-id="49503-166">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="49503-166">Defined in root\ServiceModel</span></span>|
