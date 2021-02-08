---
description: '詳細については、「GetBaseAddress Module:: メソッド」を参照してください。'
title: ICorDebugModule::GetBaseAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetBaseAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetBaseAddress
helpviewer_keywords:
- GetBaseAddress method [.NET Framework debugging]
- ICorDebugModule::GetBaseAddress method [.NET Framework debugging]
ms.assetid: 26a82815-1982-4eb7-92d1-5c3d318d5be4
topic_type:
- apiref
ms.openlocfilehash: bdfa4aeac3a9c06f666d56f1ee08ec503626ce7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790816"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="b8385-103">ICorDebugModule::GetBaseAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="b8385-103">ICorDebugModule::GetBaseAddress Method</span></span>

<span data-ttu-id="b8385-104">モジュールのベースアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="b8385-104">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8385-105">構文</span><span class="sxs-lookup"><span data-stu-id="b8385-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8385-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b8385-106">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="b8385-107">入出力 `CORDB_ADDRESS` モジュールのベースアドレスを指定する。</span><span class="sxs-lookup"><span data-stu-id="b8385-107">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8385-108">解説</span><span class="sxs-lookup"><span data-stu-id="b8385-108">Remarks</span></span>  

 <span data-ttu-id="b8385-109">モジュールがネイティブイメージの場合 (つまり、モジュールがネイティブイメージジェネレーターによって生成された場合は、NGen.exe)、そのベースアドレスはゼロになります。</span><span class="sxs-lookup"><span data-stu-id="b8385-109">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8385-110">要件</span><span class="sxs-lookup"><span data-stu-id="b8385-110">Requirements</span></span>  

 <span data-ttu-id="b8385-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8385-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8385-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8385-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8385-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8385-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8385-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8385-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8385-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8385-115">See also</span></span>
