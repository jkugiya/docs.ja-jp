---
description: '詳細について: ICorDebugProcess5:: GetTypeID メソッド'
title: ICorDebugProcess5::GetTypeID メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess5.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeID
helpviewer_keywords:
- ICorDebugProcess5::GetTypeID method [.NET Framework debugging]
- GetTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 47dbaea4-8857-462e-93ba-fff880fc9e50
topic_type:
- apiref
ms.openlocfilehash: 564fc2819c9c370844111cf497d62e6d89cb28b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649703"
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="e4d4a-103">ICorDebugProcess5::GetTypeID メソッド</span><span class="sxs-lookup"><span data-stu-id="e4d4a-103">ICorDebugProcess5::GetTypeID Method</span></span>

<span data-ttu-id="e4d4a-104">オブジェクトのアドレスを [COR_TYPEID](cor-typeid-structure.md) 識別子に変換します。</span><span class="sxs-lookup"><span data-stu-id="e4d4a-104">Converts an object address to a [COR_TYPEID](cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4d4a-105">構文</span><span class="sxs-lookup"><span data-stu-id="e4d4a-105">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4d4a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4d4a-106">Parameters</span></span>  

 `obj`  
 <span data-ttu-id="e4d4a-107">からオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="e4d4a-107">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="e4d4a-108">オブジェクトを識別する [COR_TYPEID](cor-typeid-structure.md) 値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e4d4a-108">A pointer to the [COR_TYPEID](cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4d4a-109">解説</span><span class="sxs-lookup"><span data-stu-id="e4d4a-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4d4a-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="e4d4a-110">Requirements</span></span>  

 <span data-ttu-id="e4d4a-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4d4a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4d4a-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4d4a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4d4a-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4d4a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4d4a-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4d4a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4d4a-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="e4d4a-115">See also</span></span>

- [<span data-ttu-id="e4d4a-116">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e4d4a-116">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="e4d4a-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e4d4a-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
