---
description: '詳細について: ICorProfilerInfo2:: EnumModuleFrozenObjects メソッド'
title: ICorProfilerInfo2::EnumModuleFrozenObjects メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.EnumModuleFrozenObjects
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::EnumModuleFrozenObjects
helpviewer_keywords:
- EnumModuleFrozenObjects method [.NET Framework profiling]
- ICorProfilerInfo2::EnumModuleFrozenObjects method [.NET Framework profiling]
ms.assetid: 920b6483-7064-4d64-8613-fcc38ccf9b1e
topic_type:
- apiref
ms.openlocfilehash: b68571544c00c8c234a73404a95433e91f0cfdcf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753212"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="c3268-103">ICorProfilerInfo2::EnumModuleFrozenObjects メソッド</span><span class="sxs-lookup"><span data-stu-id="c3268-103">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>

<span data-ttu-id="c3268-104">指定したモジュール内の固定されたオブジェクトを反復処理できる列挙子を取得します。このメソッドは互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="c3268-104">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3268-105">構文</span><span class="sxs-lookup"><span data-stu-id="c3268-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3268-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c3268-106">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="c3268-107">から列挙される固定オブジェクトを含むモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="c3268-107">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="c3268-108">入出力固定されたオブジェクトを列挙する [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) インターフェイスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c3268-108">[out] A pointer to the address of an [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3268-109">要件</span><span class="sxs-lookup"><span data-stu-id="c3268-109">Requirements</span></span>  

 <span data-ttu-id="c3268-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3268-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3268-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c3268-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c3268-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3268-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3268-113">**.NET Framework のバージョン:** 3.5、3.0 SP1、3.0、2.0 SP1、2.0</span><span class="sxs-lookup"><span data-stu-id="c3268-113">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3268-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="c3268-114">See also</span></span>

- [<span data-ttu-id="c3268-115">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c3268-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="c3268-116">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c3268-116">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
