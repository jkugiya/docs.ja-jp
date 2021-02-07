---
description: '詳細について: ICorDebugProcess5:: GetObject メソッド'
title: ICorDebugProcess5::GetObject メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetObject method [.NET Framework debugging]
ms.assetid: c8111502-5a20-447f-9dc2-76e8acd7ed5a
topic_type:
- apiref
ms.openlocfilehash: 4e295e1afc19cc5b9ca763b04b05097d48f0302c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746361"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="c30b1-103">ICorDebugProcess5::GetObject メソッド</span><span class="sxs-lookup"><span data-stu-id="c30b1-103">ICorDebugProcess5::GetObject Method</span></span>

<span data-ttu-id="c30b1-104">オブジェクトのアドレスを "の値" オブジェクトに変換します。</span><span class="sxs-lookup"><span data-stu-id="c30b1-104">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c30b1-105">構文</span><span class="sxs-lookup"><span data-stu-id="c30b1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c30b1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c30b1-106">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="c30b1-107">からオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="c30b1-107">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="c30b1-108">入出力"の値" オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c30b1-108">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c30b1-109">解説</span><span class="sxs-lookup"><span data-stu-id="c30b1-109">Remarks</span></span>  

 <span data-ttu-id="c30b1-110">`addr`が有効なマネージオブジェクトを指していない場合、 `GetObject` メソッドはを返し `E_FAIL` ます。</span><span class="sxs-lookup"><span data-stu-id="c30b1-110">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c30b1-111">要件</span><span class="sxs-lookup"><span data-stu-id="c30b1-111">Requirements</span></span>  

 <span data-ttu-id="c30b1-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c30b1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c30b1-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c30b1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c30b1-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c30b1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c30b1-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c30b1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c30b1-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="c30b1-116">See also</span></span>

- [<span data-ttu-id="c30b1-117">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c30b1-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="c30b1-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c30b1-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
