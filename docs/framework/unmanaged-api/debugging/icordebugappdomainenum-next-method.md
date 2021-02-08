---
description: '詳細情報: ICorDebugAppDomainEnum:: Next メソッド'
title: ICorDebugAppDomainEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum::Next method
helpviewer_keywords:
- ICorDebugAppDomainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: b8d1def7-0ebc-4314-a3a2-fd36a75973e7
topic_type:
- apiref
ms.openlocfilehash: ac5397250e661b4ed380b3272744957f86e1a07b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791531"
---
# <a name="icordebugappdomainenumnext-method"></a><span data-ttu-id="ff561-103">ICorDebugAppDomainEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="ff561-103">ICorDebugAppDomainEnum::Next Method</span></span>

<span data-ttu-id="ff561-104">現在のカーソル位置から開始して、指定した数のアプリケーションドメインをコレクションから取得します。</span><span class="sxs-lookup"><span data-stu-id="ff561-104">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff561-105">構文</span><span class="sxs-lookup"><span data-stu-id="ff561-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff561-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff561-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="ff561-107">から取得するアプリケーションドメインの数。</span><span class="sxs-lookup"><span data-stu-id="ff561-107">[in] The number of application domains to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="ff561-108">入出力ポインターの配列。各ポインターは、アプリケーションドメインを表す、の各オブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="ff561-108">[out] An array of pointers, each of which points to an ICorDebugAppDomain object that represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ff561-109">入出力実際に返されたアプリケーションドメインの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ff561-109">[out] A pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="ff561-110">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="ff561-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff561-111">要件</span><span class="sxs-lookup"><span data-stu-id="ff561-111">Requirements</span></span>  

 <span data-ttu-id="ff561-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff561-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff561-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff561-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff561-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff561-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff561-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff561-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
