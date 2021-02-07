---
description: '詳細については、「ICorDebugValue:: GetAddress メソッド」を参照してください。'
title: ICorDebugValue::GetAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
ms.openlocfilehash: c922388fbab820e50edffc140be94a2c0920099d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690432"
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="65fac-103">ICorDebugValue::GetAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="65fac-103">ICorDebugValue::GetAddress Method</span></span>

<span data-ttu-id="65fac-104">この "ICorDebugValue" オブジェクトのアドレスを取得します。このオブジェクトはデバッグ中です。</span><span class="sxs-lookup"><span data-stu-id="65fac-104">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65fac-105">構文</span><span class="sxs-lookup"><span data-stu-id="65fac-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65fac-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="65fac-106">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="65fac-107">入出力 `CORDB_ADDRESS` この値オブジェクトのアドレスを指定するオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65fac-107">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65fac-108">解説</span><span class="sxs-lookup"><span data-stu-id="65fac-108">Remarks</span></span>  

 <span data-ttu-id="65fac-109">値が使用できない場合は、0 (ゼロ) が返されます。</span><span class="sxs-lookup"><span data-stu-id="65fac-109">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="65fac-110">これは、値がレジスタの少なくとも一部の場合、またはガベージコレクターハンドル () に格納されている場合に発生する可能性が `GCHandle` あります。</span><span class="sxs-lookup"><span data-stu-id="65fac-110">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65fac-111">要件</span><span class="sxs-lookup"><span data-stu-id="65fac-111">Requirements</span></span>  

 <span data-ttu-id="65fac-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65fac-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65fac-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65fac-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65fac-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65fac-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65fac-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65fac-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65fac-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="65fac-116">See also</span></span>
