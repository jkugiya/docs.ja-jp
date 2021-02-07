---
description: '詳細について: 「コード:: GetAddress メソッド」を参照してください。'
title: ICorDebugCode::GetAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetAddress
helpviewer_keywords:
- GetAddress method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetAddress method [.NET Framework debugging]
ms.assetid: cc507cb0-df2e-49c2-b32e-0c3271a8df9a
topic_type:
- apiref
ms.openlocfilehash: 4c074a407d8153703fd92aeddb53e9fa05b0ef01
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711337"
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="31855-103">ICorDebugCode::GetAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="31855-103">ICorDebugCode::GetAddress Method</span></span>

<span data-ttu-id="31855-104">この "" コード "インターフェイスが表すコードセグメントの相対仮想アドレス (RVA) を取得します。</span><span class="sxs-lookup"><span data-stu-id="31855-104">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31855-105">構文</span><span class="sxs-lookup"><span data-stu-id="31855-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31855-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="31855-106">Parameters</span></span>  

 `pStart`  
 <span data-ttu-id="31855-107">入出力コードセグメントの RVA へのポインター。</span><span class="sxs-lookup"><span data-stu-id="31855-107">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31855-108">要件</span><span class="sxs-lookup"><span data-stu-id="31855-108">Requirements</span></span>  

 <span data-ttu-id="31855-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31855-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31855-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="31855-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31855-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31855-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31855-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31855-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
