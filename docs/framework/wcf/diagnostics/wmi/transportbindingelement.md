---
description: '詳細情報: TransportBindingElement'
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: de08feaf8abec3a0dfee97e92d68d5223cd0de44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757112"
---
# <a name="transportbindingelement"></a><span data-ttu-id="ebfd9-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="ebfd9-103">TransportBindingElement</span></span>

<span data-ttu-id="ebfd9-104">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="ebfd9-104">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebfd9-105">構文</span><span class="sxs-lookup"><span data-stu-id="ebfd9-105">Syntax</span></span>  
  
```csharp
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ebfd9-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="ebfd9-106">Methods</span></span>  

 <span data-ttu-id="ebfd9-107">TransportBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="ebfd9-107">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ebfd9-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ebfd9-108">Properties</span></span>  

 <span data-ttu-id="ebfd9-109">TransportBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="ebfd9-109">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="ebfd9-110">ManualAddressing</span><span class="sxs-lookup"><span data-stu-id="ebfd9-110">ManualAddressing</span></span>  

 <span data-ttu-id="ebfd9-111">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="ebfd9-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="ebfd9-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ebfd9-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebfd9-113">メッセージのアドレス指定をユーザーが制御するかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="ebfd9-113">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="ebfd9-114">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="ebfd9-114">MaxBufferPoolSize</span></span>  

 <span data-ttu-id="ebfd9-115">データ型 : sint64</span><span class="sxs-lookup"><span data-stu-id="ebfd9-115">Data type: sint64</span></span>  
  
 <span data-ttu-id="ebfd9-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ebfd9-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebfd9-117">バインディングに使用するバッファー プールの最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="ebfd9-117">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="ebfd9-118">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="ebfd9-118">MaxReceivedMessageSize</span></span>  

 <span data-ttu-id="ebfd9-119">データ型 : sint64</span><span class="sxs-lookup"><span data-stu-id="ebfd9-119">Data type: sint64</span></span>  
  
 <span data-ttu-id="ebfd9-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ebfd9-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebfd9-121">このバインディングで処理されるメッセージの最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="ebfd9-121">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="ebfd9-122">Scheme</span><span class="sxs-lookup"><span data-stu-id="ebfd9-122">Scheme</span></span>  

 <span data-ttu-id="ebfd9-123">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="ebfd9-123">Data type: string</span></span>  
  
 <span data-ttu-id="ebfd9-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ebfd9-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebfd9-125">トランスポートの URI スキーム。</span><span class="sxs-lookup"><span data-stu-id="ebfd9-125">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebfd9-126">要件</span><span class="sxs-lookup"><span data-stu-id="ebfd9-126">Requirements</span></span>  
  
|<span data-ttu-id="ebfd9-127">MOF</span><span class="sxs-lookup"><span data-stu-id="ebfd9-127">MOF</span></span>|<span data-ttu-id="ebfd9-128">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="ebfd9-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ebfd9-129">名前空間</span><span class="sxs-lookup"><span data-stu-id="ebfd9-129">Namespace</span></span>|<span data-ttu-id="ebfd9-130">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="ebfd9-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ebfd9-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="ebfd9-131">See also</span></span>

- <xref:System.ServiceModel.Channels.TransportBindingElement>
