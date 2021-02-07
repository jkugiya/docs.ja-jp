---
description: '詳細については、次を参照してください: GetHandle Method:: メソッド'
title: ICorDebugProcess::GetHandle メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
ms.openlocfilehash: fbc92be53b30d3c70f85fea36e05c6a5514b0f03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722127"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="44468-103">ICorDebugProcess::GetHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="44468-103">ICorDebugProcess::GetHandle Method</span></span>

<span data-ttu-id="44468-104">プロセスを処理するハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="44468-104">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44468-105">構文</span><span class="sxs-lookup"><span data-stu-id="44468-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44468-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="44468-106">Parameters</span></span>  

 `phProcessHandle`  
 <span data-ttu-id="44468-107">入出力プロセスを指すハンドルであるへのポインター `HPROCESS` 。</span><span class="sxs-lookup"><span data-stu-id="44468-107">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44468-108">解説</span><span class="sxs-lookup"><span data-stu-id="44468-108">Remarks</span></span>  

 <span data-ttu-id="44468-109">取得したハンドルは、デバッグインターフェイスによって所有されています。</span><span class="sxs-lookup"><span data-stu-id="44468-109">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="44468-110">デバッガーは、使用する前にハンドルを複製する必要があります。</span><span class="sxs-lookup"><span data-stu-id="44468-110">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44468-111">要件</span><span class="sxs-lookup"><span data-stu-id="44468-111">Requirements</span></span>  

 <span data-ttu-id="44468-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44468-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44468-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44468-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44468-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44468-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44468-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44468-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
