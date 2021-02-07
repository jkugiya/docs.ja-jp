---
description: '詳細情報: バインド'
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: 36887a9296bfafd0790105e7f4d513efc3009bf8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757788"
---
# <a name="binding"></a><span data-ttu-id="7cf8a-103">バインド</span><span class="sxs-lookup"><span data-stu-id="7cf8a-103">Binding</span></span>

<span data-ttu-id="7cf8a-104">wmi バインディング</span><span class="sxs-lookup"><span data-stu-id="7cf8a-104">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cf8a-105">構文</span><span class="sxs-lookup"><span data-stu-id="7cf8a-105">Syntax</span></span>  
  
```csharp
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7cf8a-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="7cf8a-106">Methods</span></span>  

 <span data-ttu-id="7cf8a-107">Binding クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="7cf8a-107">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7cf8a-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7cf8a-108">Properties</span></span>  

 <span data-ttu-id="7cf8a-109">Binding クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="7cf8a-109">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="7cf8a-110">BindingElements</span><span class="sxs-lookup"><span data-stu-id="7cf8a-110">BindingElements</span></span>  

 <span data-ttu-id="7cf8a-111">データ型 : BindingElement 配列</span><span class="sxs-lookup"><span data-stu-id="7cf8a-111">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="7cf8a-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7cf8a-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7cf8a-113">バインディングによって実装されるバインド要素のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="7cf8a-113">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="7cf8a-114">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="7cf8a-114">CloseTimeout</span></span>  

 <span data-ttu-id="7cf8a-115">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="7cf8a-115">Data type: datetime</span></span>  
  
 <span data-ttu-id="7cf8a-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7cf8a-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7cf8a-117">クローズ操作が完了するまで待機する時間です。</span><span class="sxs-lookup"><span data-stu-id="7cf8a-117">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="7cf8a-118">名前</span><span class="sxs-lookup"><span data-stu-id="7cf8a-118">Name</span></span>  

 <span data-ttu-id="7cf8a-119">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="7cf8a-119">Data type: string</span></span>  
  
 <span data-ttu-id="7cf8a-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7cf8a-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7cf8a-121">バインディングの名前。</span><span class="sxs-lookup"><span data-stu-id="7cf8a-121">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="7cf8a-122">名前空間</span><span class="sxs-lookup"><span data-stu-id="7cf8a-122">Namespace</span></span>  

 <span data-ttu-id="7cf8a-123">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="7cf8a-123">Data type: string</span></span>  
  
 <span data-ttu-id="7cf8a-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7cf8a-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7cf8a-125">バインディングの XML 名前空間。</span><span class="sxs-lookup"><span data-stu-id="7cf8a-125">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="7cf8a-126">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="7cf8a-126">OpenTimeout</span></span>  

 <span data-ttu-id="7cf8a-127">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="7cf8a-127">Data type: datetime</span></span>  
  
 <span data-ttu-id="7cf8a-128">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7cf8a-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7cf8a-129">オープン操作が完了するまで待機する時間です。</span><span class="sxs-lookup"><span data-stu-id="7cf8a-129">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="7cf8a-130">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="7cf8a-130">ReceiveTimeout</span></span>  

 <span data-ttu-id="7cf8a-131">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="7cf8a-131">Data type: datetime</span></span>  
  
 <span data-ttu-id="7cf8a-132">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7cf8a-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7cf8a-133">受信操作が完了するまで待機する時間です。</span><span class="sxs-lookup"><span data-stu-id="7cf8a-133">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="7cf8a-134">Scheme</span><span class="sxs-lookup"><span data-stu-id="7cf8a-134">Scheme</span></span>  

 <span data-ttu-id="7cf8a-135">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="7cf8a-135">Data type: string</span></span>  
  
 <span data-ttu-id="7cf8a-136">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7cf8a-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7cf8a-137">このバインディングに組み込まれているチャネルおよびリスナー ファクトリによって使用される URI トランスポート スキームです。</span><span class="sxs-lookup"><span data-stu-id="7cf8a-137">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="7cf8a-138">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="7cf8a-138">SendTimeout</span></span>  

 <span data-ttu-id="7cf8a-139">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="7cf8a-139">Data type: datetime</span></span>  
  
 <span data-ttu-id="7cf8a-140">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7cf8a-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7cf8a-141">送信操作が完了するまで待機する時間です。</span><span class="sxs-lookup"><span data-stu-id="7cf8a-141">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cf8a-142">要件</span><span class="sxs-lookup"><span data-stu-id="7cf8a-142">Requirements</span></span>  
  
|<span data-ttu-id="7cf8a-143">MOF</span><span class="sxs-lookup"><span data-stu-id="7cf8a-143">MOF</span></span>|<span data-ttu-id="7cf8a-144">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="7cf8a-144">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7cf8a-145">名前空間</span><span class="sxs-lookup"><span data-stu-id="7cf8a-145">Namespace</span></span>|<span data-ttu-id="7cf8a-146">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="7cf8a-146">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7cf8a-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="7cf8a-147">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
