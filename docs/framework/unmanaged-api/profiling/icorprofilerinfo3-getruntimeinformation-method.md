---
description: '詳細について: ICorProfilerInfo3:: GetRuntimeInformation メソッド'
title: ICorProfilerInfo3::GetRuntimeInformation メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
ms.openlocfilehash: f615cc54e12b6f2f6eaa7335353f2f5f6a8ecfce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646713"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="d14cf-103">ICorProfilerInfo3::GetRuntimeInformation メソッド</span><span class="sxs-lookup"><span data-stu-id="d14cf-103">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>

<span data-ttu-id="d14cf-104">プロファイリングされている共通言語ランタイム (CLR) に関するバージョン情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="d14cf-104">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d14cf-105">構文</span><span class="sxs-lookup"><span data-stu-id="d14cf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d14cf-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d14cf-106">Parameters</span></span>  

 `pClrInstanceId`  
 <span data-ttu-id="d14cf-107">入出力プロセス内で実行されている CLR インスタンスの代表 ID。</span><span class="sxs-lookup"><span data-stu-id="d14cf-107">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="d14cf-108">これは、 `ClrInstanceID` event tracing For Windows (ETW) のスタートアップイベントによって報告されると同じです。</span><span class="sxs-lookup"><span data-stu-id="d14cf-108">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="d14cf-109">入出力ランタイム型。</span><span class="sxs-lookup"><span data-stu-id="d14cf-109">[out] The runtime type.</span></span> <span data-ttu-id="d14cf-110">このパラメーター `COR_PRF_DESKTOP_CLR` は、clr のデスクトップバージョンに対して、または `COR_PRF_CORE_CLR` Silverlight で使用される clr のコアバージョンに対してを返します。</span><span class="sxs-lookup"><span data-stu-id="d14cf-110">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="d14cf-111">入出力CLR のメジャーバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="d14cf-111">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="d14cf-112">入出力CLR のマイナーバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="d14cf-112">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="d14cf-113">入出力CLR のビルドバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="d14cf-113">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="d14cf-114">入出力ソフトウェア更新プログラムに関連付けられている CLR のバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="d14cf-114">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="d14cf-115">からが指すバッファーの長さ (文字数) `szVersionString` 。</span><span class="sxs-lookup"><span data-stu-id="d14cf-115">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="d14cf-116">入出力の長さ (文字数) `szVersionString` 。</span><span class="sxs-lookup"><span data-stu-id="d14cf-116">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="d14cf-117">入出力CLR のバージョン文字列。</span><span class="sxs-lookup"><span data-stu-id="d14cf-117">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d14cf-118">解説</span><span class="sxs-lookup"><span data-stu-id="d14cf-118">Remarks</span></span>  

 <span data-ttu-id="d14cf-119">任意のパラメーターに null を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="d14cf-119">You may pass null for any parameter.</span></span> <span data-ttu-id="d14cf-120">ただし、が null の場合を除き、を `pcchVersionString` null にすることはできません `szVersionString` 。</span><span class="sxs-lookup"><span data-stu-id="d14cf-120">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d14cf-121">要件</span><span class="sxs-lookup"><span data-stu-id="d14cf-121">Requirements</span></span>  

 <span data-ttu-id="d14cf-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d14cf-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d14cf-123">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d14cf-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d14cf-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d14cf-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d14cf-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d14cf-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d14cf-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="d14cf-126">See also</span></span>

- [<span data-ttu-id="d14cf-127">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d14cf-127">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="d14cf-128">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d14cf-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="d14cf-129">プロファイル</span><span class="sxs-lookup"><span data-stu-id="d14cf-129">Profiling</span></span>](index.md)
