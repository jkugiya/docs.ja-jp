---
description: '詳細については、「IManagedObject:: GetSerializedBuffer メソッド」を参照してください。'
title: IManagedObject::GetSerializedBuffer メソッド
ms.date: 03/30/2017
api_name:
- IManagedObject.GetSerializedBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetSerializedBuffer
helpviewer_keywords:
- IManagedObject::GetSerializedBuffer method [.NET Framework hosting]
- GetSerializedBuffer method [.NET Framework hosting]
ms.assetid: c17105bb-b49f-434e-8f9b-77f8c85b9220
topic_type:
- apiref
ms.openlocfilehash: f324b6ed1e9cea21fec9027a954fbad54174dd0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753771"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="a6ee6-103">IManagedObject::GetSerializedBuffer メソッド</span><span class="sxs-lookup"><span data-stu-id="a6ee6-103">IManagedObject::GetSerializedBuffer Method</span></span>

<span data-ttu-id="a6ee6-104">このマネージオブジェクトの文字列表現を取得します。</span><span class="sxs-lookup"><span data-stu-id="a6ee6-104">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6ee6-105">構文</span><span class="sxs-lookup"><span data-stu-id="a6ee6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6ee6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a6ee6-106">Parameters</span></span>  

 `pBSTR`  
 <span data-ttu-id="a6ee6-107">入出力シリアル化されたオブジェクトである文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a6ee6-107">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6ee6-108">解説</span><span class="sxs-lookup"><span data-stu-id="a6ee6-108">Remarks</span></span>  

 <span data-ttu-id="a6ee6-109">メソッドは、 `GetSerializedBuffer` オブジェクトをシリアル化してクライアントにマーシャリングできるようにします。</span><span class="sxs-lookup"><span data-stu-id="a6ee6-109">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6ee6-110">要件</span><span class="sxs-lookup"><span data-stu-id="a6ee6-110">Requirements</span></span>  

 <span data-ttu-id="a6ee6-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6ee6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6ee6-112">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a6ee6-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a6ee6-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a6ee6-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6ee6-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6ee6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6ee6-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6ee6-115">See also</span></span>

- [<span data-ttu-id="a6ee6-116">IManagedObject インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6ee6-116">IManagedObject Interface</span></span>](imanagedobject-interface.md)
