---
description: '詳細について: ICorProfilerInfo2:: GetStringLayout メソッド'
title: ICorProfilerInfo2::GetStringLayout メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
ms.openlocfilehash: 145d748d756fd30ef0522d1c516f8f63ca604545
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716368"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="80020-103">ICorProfilerInfo2::GetStringLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="80020-103">ICorProfilerInfo2::GetStringLayout Method</span></span>

<span data-ttu-id="80020-104">文字列オブジェクトのレイアウトに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="80020-104">Gets information about the layout of a string object.</span></span> <span data-ttu-id="80020-105">このメソッドは .NET Framework 4 では非推奨とされており、 [ICorProfilerInfo3:: GetStringLayout2](icorprofilerinfo3-getstringlayout2-method.md) メソッドに置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="80020-105">This method is deprecated in the .NET Framework 4, and is superseded by the [ICorProfilerInfo3::GetStringLayout2](icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80020-106">構文</span><span class="sxs-lookup"><span data-stu-id="80020-106">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80020-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="80020-107">Parameters</span></span>  

 `pBufferLengthOffset`  
 <span data-ttu-id="80020-108">入出力文字列の長さを格納する、ポインターを基準とした位置のオフセットへのポインター `ObjectID` 。</span><span class="sxs-lookup"><span data-stu-id="80020-108">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="80020-109">長さはとして格納され `DWORD` ます。</span><span class="sxs-lookup"><span data-stu-id="80020-109">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80020-110">このパラメーターは、バッファーの長さではなく、文字列自体の長さを返します。</span><span class="sxs-lookup"><span data-stu-id="80020-110">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="80020-111">バッファーの長さは使用できなくなりました。</span><span class="sxs-lookup"><span data-stu-id="80020-111">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="80020-112">入出力 `ObjectID` 文字列自体の長さを格納する、ポインターを基準とした位置のオフセットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="80020-112">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="80020-113">長さはとして格納され `DWORD` ます。</span><span class="sxs-lookup"><span data-stu-id="80020-113">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="80020-114">入出力 `ObjectID` ワイド文字の文字列を格納する、ポインターを基準としたバッファーのオフセットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="80020-114">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80020-115">解説</span><span class="sxs-lookup"><span data-stu-id="80020-115">Remarks</span></span>  

 <span data-ttu-id="80020-116">メソッドは、ポインターを基準として、 `GetStringLayout` `ObjectID` 次のが格納されている位置のオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="80020-116">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="80020-117">文字列のバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="80020-117">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="80020-118">文字列自体の長さ。</span><span class="sxs-lookup"><span data-stu-id="80020-118">The length of the string itself.</span></span>  
  
- <span data-ttu-id="80020-119">ワイド文字の実際の文字列を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="80020-119">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="80020-120">文字列は null で終わる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="80020-120">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80020-121">要件</span><span class="sxs-lookup"><span data-stu-id="80020-121">Requirements</span></span>  

 <span data-ttu-id="80020-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80020-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80020-123">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="80020-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="80020-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80020-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80020-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80020-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80020-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="80020-126">See also</span></span>

- [<span data-ttu-id="80020-127">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="80020-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="80020-128">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="80020-128">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
