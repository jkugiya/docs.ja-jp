---
description: '詳細については、「GetSize Module:: メソッド」を参照してください。'
title: ICorDebugModule::GetSize メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetSize method [.NET Framework debugging]
ms.assetid: 5c68375d-145d-46ef-a7c8-2dc4257472de
topic_type:
- apiref
ms.openlocfilehash: b2179c8830911e417ccd482fe72438c4cd7fd3df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660155"
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="083b8-103">ICorDebugModule::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="083b8-103">ICorDebugModule::GetSize Method</span></span>

<span data-ttu-id="083b8-104">モジュールのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="083b8-104">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="083b8-105">構文</span><span class="sxs-lookup"><span data-stu-id="083b8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="083b8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="083b8-106">Parameters</span></span>  

 `pcBytes`  
 <span data-ttu-id="083b8-107">入出力モジュールのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="083b8-107">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="083b8-108">モジュールがネイティブイメージジェネレーター (NGen.exe) から生成された場合、モジュールのサイズはゼロになります。</span><span class="sxs-lookup"><span data-stu-id="083b8-108">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="083b8-109">要件</span><span class="sxs-lookup"><span data-stu-id="083b8-109">Requirements</span></span>  

 <span data-ttu-id="083b8-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="083b8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="083b8-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="083b8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="083b8-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="083b8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="083b8-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="083b8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
