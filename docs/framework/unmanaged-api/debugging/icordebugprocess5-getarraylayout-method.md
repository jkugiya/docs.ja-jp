---
description: '詳細について: ICorDebugProcess5:: GetArrayLayout メソッド'
title: ICorDebugProcess5::GetArrayLayout メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetArrayLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type:
- apiref
ms.openlocfilehash: c82b296da3a367f5307240225a560af67a56c866
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746400"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="6bad8-103">ICorDebugProcess5::GetArrayLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="6bad8-103">ICorDebugProcess5::GetArrayLayout Method</span></span>

<span data-ttu-id="6bad8-104">配列型のレイアウトに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="6bad8-104">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bad8-105">構文</span><span class="sxs-lookup"><span data-stu-id="6bad8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bad8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6bad8-106">Parameters</span></span>  

 `id`  
 <span data-ttu-id="6bad8-107">からレイアウトが必要な配列を指定する [COR_TYPEID](cor-typeid-structure.md) トークン。</span><span class="sxs-lookup"><span data-stu-id="6bad8-107">[in] A [COR_TYPEID](cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="6bad8-108">入出力メモリ内の配列のレイアウトに関する情報を格納している [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6bad8-108">[out] A pointer to a [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bad8-109">解説</span><span class="sxs-lookup"><span data-stu-id="6bad8-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bad8-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="6bad8-110">Requirements</span></span>  

 <span data-ttu-id="6bad8-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bad8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bad8-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6bad8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bad8-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bad8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bad8-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bad8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bad8-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="6bad8-115">See also</span></span>

- [<span data-ttu-id="6bad8-116">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6bad8-116">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="6bad8-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="6bad8-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
