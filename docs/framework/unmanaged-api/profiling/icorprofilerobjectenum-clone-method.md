---
description: '詳細情報: ICorProfilerObjectEnum:: Clone メソッド'
title: ICorProfilerObjectEnum::Clone メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type:
- apiref
ms.openlocfilehash: 59971f6f6e7edab4b4c4f796ee7bea3c4d8b4e91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798954"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="795de-103">ICorProfilerObjectEnum::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="795de-103">ICorProfilerObjectEnum::Clone Method</span></span>

<span data-ttu-id="795de-104">この [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) インターフェイスのコピーへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="795de-104">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="795de-105">構文</span><span class="sxs-lookup"><span data-stu-id="795de-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="795de-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="795de-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="795de-107">入出力このインターフェイスのコピーを指すインターフェイスポインターへのポインター `ICorProfilerObjectEnum` 。</span><span class="sxs-lookup"><span data-stu-id="795de-107">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="795de-108">コピーは、このコピーとは別に独自の列挙状態を保持します。</span><span class="sxs-lookup"><span data-stu-id="795de-108">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="795de-109">ただし、コピーの初期カーソル位置は、この列挙子の現在のカーソル位置と同じになります。</span><span class="sxs-lookup"><span data-stu-id="795de-109">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="795de-110">要件</span><span class="sxs-lookup"><span data-stu-id="795de-110">Requirements</span></span>  

 <span data-ttu-id="795de-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="795de-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="795de-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="795de-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="795de-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="795de-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="795de-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="795de-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="795de-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="795de-115">See also</span></span>

- [<span data-ttu-id="795de-116">ICorProfilerObjectEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="795de-116">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
