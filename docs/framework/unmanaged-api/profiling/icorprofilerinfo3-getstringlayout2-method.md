---
description: '詳細について: ICorProfilerInfo3:: GetStringLayout2 メソッド'
title: ICorProfilerInfo3::GetStringLayout2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
ms.openlocfilehash: 398d06dc62245e6a2201feacb62ebbb1e4839ccb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646674"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="80ff1-103">ICorProfilerInfo3::GetStringLayout2 メソッド</span><span class="sxs-lookup"><span data-stu-id="80ff1-103">ICorProfilerInfo3::GetStringLayout2 Method</span></span>

<span data-ttu-id="80ff1-104">文字列オブジェクトのレイアウトに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="80ff1-104">Gets information about the layout of a string object.</span></span> <span data-ttu-id="80ff1-105">このメソッドは、 [ICorProfilerInfo2:: GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) メソッドよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="80ff1-105">This method supersedes the [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80ff1-106">構文</span><span class="sxs-lookup"><span data-stu-id="80ff1-106">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80ff1-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="80ff1-107">Parameters</span></span>  

 `pStringLengthOffset`  
 <span data-ttu-id="80ff1-108">入出力 `ObjectID` 文字列自体の長さを格納する、ポインターを基準とした位置のオフセットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="80ff1-108">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="80ff1-109">長さはとして格納され `DWORD` ます。</span><span class="sxs-lookup"><span data-stu-id="80ff1-109">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="80ff1-110">入出力ワイド文字の文字列を格納するポインターを基準とした、バッファーのオフセットへのポインター `ObjectID` 。</span><span class="sxs-lookup"><span data-stu-id="80ff1-110">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80ff1-111">解説</span><span class="sxs-lookup"><span data-stu-id="80ff1-111">Remarks</span></span>  

 <span data-ttu-id="80ff1-112">文字列は、null で終わることができます。</span><span class="sxs-lookup"><span data-stu-id="80ff1-112">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80ff1-113">要件</span><span class="sxs-lookup"><span data-stu-id="80ff1-113">Requirements</span></span>  

 <span data-ttu-id="80ff1-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80ff1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80ff1-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="80ff1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="80ff1-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80ff1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80ff1-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80ff1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ff1-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="80ff1-118">See also</span></span>

- [<span data-ttu-id="80ff1-119">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="80ff1-119">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="80ff1-120">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="80ff1-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
