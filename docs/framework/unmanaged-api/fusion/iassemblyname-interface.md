---
description: 詳細については、「IAssemblyName インターフェイス」を参照してください。
title: IAssemblyName インターフェイス
ms.date: 03/30/2017
api_name:
- IAssemblyName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName
helpviewer_keywords:
- IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type:
- apiref
ms.openlocfilehash: fb5949572adc533bab5ed26ee969267f430f36ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760707"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="978ca-103">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="978ca-103">IAssemblyName Interface</span></span>

<span data-ttu-id="978ca-104">アセンブリの一意の id を記述および操作するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="978ca-104">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="978ca-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="978ca-105">Methods</span></span>  
  
|<span data-ttu-id="978ca-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="978ca-106">Method</span></span>|<span data-ttu-id="978ca-107">説明</span><span class="sxs-lookup"><span data-stu-id="978ca-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="978ca-108">Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="978ca-108">Clone Method</span></span>](iassemblyname-clone-method.md)|<span data-ttu-id="978ca-109">このオブジェクトの簡易コピーを作成し `IAssemblyName` ます。</span><span class="sxs-lookup"><span data-stu-id="978ca-109">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="978ca-110">Finalize メソッド</span><span class="sxs-lookup"><span data-stu-id="978ca-110">Finalize Method</span></span>](iassemblyname-finalize-method.md)|<span data-ttu-id="978ca-111">このオブジェクトが、 `IAssemblyName` デストラクターが呼び出される前にリソースを解放し、その他のクリーンアップ操作を実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="978ca-111">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="978ca-112">GetDisplayName メソッド</span><span class="sxs-lookup"><span data-stu-id="978ca-112">GetDisplayName Method</span></span>](iassemblyname-getdisplayname-method.md)|<span data-ttu-id="978ca-113">このオブジェクトによって参照されるアセンブリの、人間が判読できる名前を取得し `IAssemblyName` ます。</span><span class="sxs-lookup"><span data-stu-id="978ca-113">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="978ca-114">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="978ca-114">GetName Method</span></span>](iassemblyname-getname-method.md)|<span data-ttu-id="978ca-115">このオブジェクトによって参照されるアセンブリの単純な、暗号化されていない名前を取得し `IAssemblyName` ます。</span><span class="sxs-lookup"><span data-stu-id="978ca-115">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="978ca-116">GetProperty メソッド</span><span class="sxs-lookup"><span data-stu-id="978ca-116">GetProperty Method</span></span>](iassemblyname-getproperty-method.md)|<span data-ttu-id="978ca-117">指定したによって参照されるプロパティへのポインターを取得し `PropertyId` ます。</span><span class="sxs-lookup"><span data-stu-id="978ca-117">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="978ca-118">GetVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="978ca-118">GetVersion Method</span></span>](iassemblyname-getversion-method.md)|<span data-ttu-id="978ca-119">このオブジェクトによって参照されるアセンブリのバージョン情報を取得し `IAssemblyName` ます。</span><span class="sxs-lookup"><span data-stu-id="978ca-119">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="978ca-120">IsEqual メソッド</span><span class="sxs-lookup"><span data-stu-id="978ca-120">IsEqual Method</span></span>](iassemblyname-isequal-method.md)|<span data-ttu-id="978ca-121">指定した `IAssemblyName` `IAssemblyName` 比較フラグに基づいて、指定したオブジェクトがこのと等しいかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="978ca-121">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="978ca-122">SetProperty メソッド</span><span class="sxs-lookup"><span data-stu-id="978ca-122">SetProperty Method</span></span>](iassemblyname-setproperty-method.md)|<span data-ttu-id="978ca-123">指定したによって参照されるプロパティの値を設定 `PropertyId` します。</span><span class="sxs-lookup"><span data-stu-id="978ca-123">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="978ca-124">要件</span><span class="sxs-lookup"><span data-stu-id="978ca-124">Requirements</span></span>  

 <span data-ttu-id="978ca-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="978ca-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="978ca-126">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="978ca-126">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="978ca-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="978ca-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="978ca-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="978ca-128">See also</span></span>

- [<span data-ttu-id="978ca-129">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="978ca-129">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="978ca-130">IAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="978ca-130">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
