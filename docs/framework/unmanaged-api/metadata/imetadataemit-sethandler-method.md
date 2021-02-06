---
description: '詳細について: IMetaDataEmit:: SetHandler メソッド'
title: IMetaDataEmit::SetHandler メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
ms.openlocfilehash: 07ebf8eef816d373e92a82fc84adacfe5a8599fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657868"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="98795-103">IMetaDataEmit::SetHandler メソッド</span><span class="sxs-lookup"><span data-stu-id="98795-103">IMetaDataEmit::SetHandler Method</span></span>

<span data-ttu-id="98795-104">指定したポインターによって参照されるメソッドを、 `IUnknown` トークンリマップの通知コールバックとして設定します。</span><span class="sxs-lookup"><span data-stu-id="98795-104">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98795-105">構文</span><span class="sxs-lookup"><span data-stu-id="98795-105">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98795-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="98795-106">Parameters</span></span>  

 `pUnk`  
 <span data-ttu-id="98795-107">から登録するハンドラー。</span><span class="sxs-lookup"><span data-stu-id="98795-107">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98795-108">解説</span><span class="sxs-lookup"><span data-stu-id="98795-108">Remarks</span></span>  

 <span data-ttu-id="98795-109">メタデータエンジンは、によって提供されるメソッドを使用して、最適化された `SetHandler` 方法でレコードを生成せず、保存されたレコードを最適化するコンパイラに通知を送信します。</span><span class="sxs-lookup"><span data-stu-id="98795-109">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="98795-110">コールバックメソッドがによって提供されていない場合 `SetHandler` 、 `IMapToken` 各スコープに対して merge on merge を使用して複数のインポートスコープがマージされている場合を除き、保存時に最適化は実行されません。</span><span class="sxs-lookup"><span data-stu-id="98795-110">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98795-111">要件</span><span class="sxs-lookup"><span data-stu-id="98795-111">Requirements</span></span>  

 <span data-ttu-id="98795-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98795-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98795-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="98795-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="98795-114">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="98795-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98795-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98795-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98795-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="98795-116">See also</span></span>

- [<span data-ttu-id="98795-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98795-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="98795-118">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98795-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
