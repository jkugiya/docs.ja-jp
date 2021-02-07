---
description: '詳細情報: コントラクト'
title: コントラクト
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 3443a7d2eed1a34f07495bd3ceb98c1ba997fabf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757554"
---
# <a name="contract"></a><span data-ttu-id="eef7c-103">コントラクト</span><span class="sxs-lookup"><span data-stu-id="eef7c-103">Contract</span></span>

<span data-ttu-id="eef7c-104">コントラクト</span><span class="sxs-lookup"><span data-stu-id="eef7c-104">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eef7c-105">構文</span><span class="sxs-lookup"><span data-stu-id="eef7c-105">Syntax</span></span>  
  
```csharp
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="eef7c-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="eef7c-106">Methods</span></span>  

 <span data-ttu-id="eef7c-107">Contract クラスで定義されているメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="eef7c-107">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="eef7c-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="eef7c-108">Properties</span></span>  

 <span data-ttu-id="eef7c-109">Contract クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="eef7c-109">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="eef7c-110">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="eef7c-110">AppDomainId</span></span>  

 <span data-ttu-id="eef7c-111">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="eef7c-111">Data type: sint32</span></span>  
  
 <span data-ttu-id="eef7c-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="eef7c-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eef7c-113">コントラクトをホストする appdomain の appdomain ID。</span><span class="sxs-lookup"><span data-stu-id="eef7c-113">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="eef7c-114">動作</span><span class="sxs-lookup"><span data-stu-id="eef7c-114">Behaviors</span></span>  

 <span data-ttu-id="eef7c-115">データ型 : Behavior array</span><span class="sxs-lookup"><span data-stu-id="eef7c-115">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="eef7c-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="eef7c-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eef7c-117">このコントラクトに関連付けられている動作。</span><span class="sxs-lookup"><span data-stu-id="eef7c-117">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="eef7c-118">名前</span><span class="sxs-lookup"><span data-stu-id="eef7c-118">Name</span></span>  

 <span data-ttu-id="eef7c-119">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="eef7c-119">Data type: string</span></span>  
  
 <span data-ttu-id="eef7c-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="eef7c-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eef7c-121">WSDL でのコントラクトの名前。</span><span class="sxs-lookup"><span data-stu-id="eef7c-121">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="eef7c-122">名前空間</span><span class="sxs-lookup"><span data-stu-id="eef7c-122">Namespace</span></span>  

 <span data-ttu-id="eef7c-123">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="eef7c-123">Data type: string</span></span>  
  
 <span data-ttu-id="eef7c-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="eef7c-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eef7c-125">WSDL での `portType` 要素の名前空間。</span><span class="sxs-lookup"><span data-stu-id="eef7c-125">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="eef7c-126">操作</span><span class="sxs-lookup"><span data-stu-id="eef7c-126">Operations</span></span>  

 <span data-ttu-id="eef7c-127">データ型 : Operation 配列</span><span class="sxs-lookup"><span data-stu-id="eef7c-127">Data type: Operation array</span></span>  
  
 <span data-ttu-id="eef7c-128">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="eef7c-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eef7c-129">このコントラクトの操作。</span><span class="sxs-lookup"><span data-stu-id="eef7c-129">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="eef7c-130">ProcessId</span><span class="sxs-lookup"><span data-stu-id="eef7c-130">ProcessId</span></span>  

 <span data-ttu-id="eef7c-131">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="eef7c-131">Data type: sint32</span></span>  
  
 <span data-ttu-id="eef7c-132">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="eef7c-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eef7c-133">コントラクトをホストするプロセスのプロセス ID。</span><span class="sxs-lookup"><span data-stu-id="eef7c-133">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="eef7c-134">ref</span><span class="sxs-lookup"><span data-stu-id="eef7c-134">ref</span></span>  

 <span data-ttu-id="eef7c-135">データ型 : Contract</span><span class="sxs-lookup"><span data-stu-id="eef7c-135">Data type: Contract</span></span>  
  
 <span data-ttu-id="eef7c-136">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="eef7c-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eef7c-137">コントラクトが双方向コントラクトのときのコールバックの型。</span><span class="sxs-lookup"><span data-stu-id="eef7c-137">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="eef7c-138">SessionMode</span><span class="sxs-lookup"><span data-stu-id="eef7c-138">SessionMode</span></span>  

 <span data-ttu-id="eef7c-139">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="eef7c-139">Data type: string</span></span>  
  
 <span data-ttu-id="eef7c-140">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="eef7c-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eef7c-141">コントラクトでチャネル セッションを使用するために、このコントラクトに関連付けられたバインディングが必要かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="eef7c-141">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="eef7c-142">Type</span><span class="sxs-lookup"><span data-stu-id="eef7c-142">Type</span></span>  

 <span data-ttu-id="eef7c-143">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="eef7c-143">Data type: string</span></span>  
  
 <span data-ttu-id="eef7c-144">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="eef7c-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eef7c-145">コントラクトの型。</span><span class="sxs-lookup"><span data-stu-id="eef7c-145">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eef7c-146">要件</span><span class="sxs-lookup"><span data-stu-id="eef7c-146">Requirements</span></span>  
  
|<span data-ttu-id="eef7c-147">MOF</span><span class="sxs-lookup"><span data-stu-id="eef7c-147">MOF</span></span>|<span data-ttu-id="eef7c-148">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="eef7c-148">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="eef7c-149">名前空間</span><span class="sxs-lookup"><span data-stu-id="eef7c-149">Namespace</span></span>|<span data-ttu-id="eef7c-150">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="eef7c-150">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eef7c-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="eef7c-151">See also</span></span>

- <xref:System.ServiceModel.Description.ContractDescription>
