---
description: '詳細について: ICorProfilerInfo:: GetTokenAndMetadataFromFunction メソッド'
title: ICorProfilerInfo::GetTokenAndMetadataFromFunction メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetTokenAndMetadataFromFunction
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction
helpviewer_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction method [.NET Framework profiling]
- GetTokenAndMetadataFromFunction method [.NET Framework profiling]
ms.assetid: e525aa16-c923-4b16-833b-36f1f0dd70fc
topic_type:
- apiref
ms.openlocfilehash: 0cea6564df15c7a7f4c46097714cc0956002599b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783847"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="3c938-103">ICorProfilerInfo::GetTokenAndMetadataFromFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="3c938-103">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>

<span data-ttu-id="3c938-104">指定された関数のトークンに対して使用できるメタデータトークンとメタデータインターフェイスインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="3c938-104">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c938-105">構文</span><span class="sxs-lookup"><span data-stu-id="3c938-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c938-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3c938-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="3c938-107">からメタデータトークンとメタデータインターフェイスを取得する対象の関数の ID。</span><span class="sxs-lookup"><span data-stu-id="3c938-107">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="3c938-108">からインスタンスを取得するメタデータインターフェイスの参照 ID。</span><span class="sxs-lookup"><span data-stu-id="3c938-108">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="3c938-109">入出力指定された関数のトークンに対して使用できるメタデータインターフェイスインスタンスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3c938-109">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="3c938-110">入出力指定された関数のメタデータトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3c938-110">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c938-111">要件</span><span class="sxs-lookup"><span data-stu-id="3c938-111">Requirements</span></span>  

 <span data-ttu-id="3c938-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c938-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c938-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3c938-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3c938-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c938-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c938-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c938-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c938-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c938-116">See also</span></span>

- [<span data-ttu-id="3c938-117">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3c938-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
