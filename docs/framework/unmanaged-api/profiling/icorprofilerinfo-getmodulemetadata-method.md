---
description: '詳細について: ICorProfilerInfo:: GetModuleMetaData メソッド'
title: ICorProfilerInfo::GetModuleMetaData メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
ms.openlocfilehash: ff0fb0563b041fcb3cf63438874724c8236d6081
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647181"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="ae3f7-103">ICorProfilerInfo::GetModuleMetaData メソッド</span><span class="sxs-lookup"><span data-stu-id="ae3f7-103">ICorProfilerInfo::GetModuleMetaData Method</span></span>

<span data-ttu-id="ae3f7-104">指定したモジュールにマップされるメタデータインターフェイスインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="ae3f7-104">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae3f7-105">構文</span><span class="sxs-lookup"><span data-stu-id="ae3f7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae3f7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ae3f7-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="ae3f7-107">からインターフェイスインスタンスのマップ先となるモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="ae3f7-107">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="ae3f7-108">からマニフェストファイルを開くモードを指定する [Coropenflags](../metadata/coropenflags-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="ae3f7-108">[in] A value of the [CorOpenFlags](../metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="ae3f7-109">、、 `ofRead` およびの各 `ofWrite` ビットのみ `ofNoTransform` が有効です。</span><span class="sxs-lookup"><span data-stu-id="ae3f7-109">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="ae3f7-110">からインスタンスを取得するメタデータインターフェイスの参照 ID (GUID)。</span><span class="sxs-lookup"><span data-stu-id="ae3f7-110">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="ae3f7-111">インターフェイスの一覧については、「 [メタデータインターフェイス](../metadata/metadata-interfaces.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae3f7-111">See [Metadata Interfaces](../metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="ae3f7-112">入出力メタデータインターフェイスインスタンスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ae3f7-112">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae3f7-113">解説</span><span class="sxs-lookup"><span data-stu-id="ae3f7-113">Remarks</span></span>  

 <span data-ttu-id="ae3f7-114">メタデータを読み取り/書き込みモードで開くように要求することはできますが、メタデータに対して行われた変更はコンパイラからのものとして最適化できないため、プログラムのメタデータ実行が遅くなります。</span><span class="sxs-lookup"><span data-stu-id="ae3f7-114">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="ae3f7-115">一部のモジュール (リソースモジュールなど) にはメタデータがありません。</span><span class="sxs-lookup"><span data-stu-id="ae3f7-115">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="ae3f7-116">このような場合、 `GetModuleMetaData` は S_FALSE の HRESULT 値を返し、\* では null を返し `ppOut` ます。</span><span class="sxs-lookup"><span data-stu-id="ae3f7-116">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae3f7-117">要件</span><span class="sxs-lookup"><span data-stu-id="ae3f7-117">Requirements</span></span>  

 <span data-ttu-id="ae3f7-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae3f7-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae3f7-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ae3f7-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ae3f7-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae3f7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae3f7-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae3f7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae3f7-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae3f7-122">See also</span></span>

- [<span data-ttu-id="ae3f7-123">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ae3f7-123">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
