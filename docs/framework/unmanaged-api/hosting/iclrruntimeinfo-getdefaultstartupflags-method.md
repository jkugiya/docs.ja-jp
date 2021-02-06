---
description: '詳細について: ICLRRuntimeInfo:: GetDefaultStartupFlags メソッド'
title: ICLRRuntimeInfo::GetDefaultStartupFlags メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type:
- apiref
ms.openlocfilehash: c6afb19319fd24d499c2c216f2ce0adc2e7a886c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637177"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="77144-103">ICLRRuntimeInfo::GetDefaultStartupFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="77144-103">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>

<span data-ttu-id="77144-104">ランタイムを開始するために使用されるスタートアップフラグとホスト構成ファイルを取得します。</span><span class="sxs-lookup"><span data-stu-id="77144-104">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77144-105">構文</span><span class="sxs-lookup"><span data-stu-id="77144-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77144-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="77144-106">Parameters</span></span>  

 `pdwStartupFlags`  
 <span data-ttu-id="77144-107">入出力現在設定されているホストのスタートアップフラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="77144-107">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="77144-108">入出力現在のホスト構成ファイルのディレクトリパスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="77144-108">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="77144-109">[入力、出力]入力時には、 `pwzHostConfigFile` バッファーオーバーランを回避するためののサイズ。</span><span class="sxs-lookup"><span data-stu-id="77144-109">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="77144-110">`pwzHostConfigFile`が null の場合、メソッドは、 `pwzHostConfigFile` 事前割り当てのために必要なサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="77144-110">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77144-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="77144-111">Return Value</span></span>  

 <span data-ttu-id="77144-112">このメソッドは、次の特定の HRESULT と、メソッドエラーを示す HRESULT エラーを返します。</span><span class="sxs-lookup"><span data-stu-id="77144-112">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="77144-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77144-113">HRESULT</span></span>|<span data-ttu-id="77144-114">説明</span><span class="sxs-lookup"><span data-stu-id="77144-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77144-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="77144-115">S_OK</span></span>|<span data-ttu-id="77144-116">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="77144-116">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77144-117">解説</span><span class="sxs-lookup"><span data-stu-id="77144-117">Remarks</span></span>  

 <span data-ttu-id="77144-118">このメソッドは、既定のフラグ値 ( `STARTUP_CONCURRENT_GC` および `NULL` )、または [ICLRRuntimeInfo:: SetDefaultStartupFlags メソッド](iclrruntimeinfo-setdefaultstartupflags-method.md)の以前の呼び出しによって提供された値、または `CorBind*` メソッドがこのランタイムにバインドされている場合は、いずれかのメソッドによって設定された値を返します。</span><span class="sxs-lookup"><span data-stu-id="77144-118">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77144-119">要件</span><span class="sxs-lookup"><span data-stu-id="77144-119">Requirements</span></span>  

 <span data-ttu-id="77144-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77144-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77144-121">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="77144-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="77144-122">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="77144-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77144-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77144-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77144-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="77144-124">See also</span></span>

- [<span data-ttu-id="77144-125">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="77144-125">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="77144-126">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="77144-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="77144-127">ホスティング</span><span class="sxs-lookup"><span data-stu-id="77144-127">Hosting</span></span>](index.md)
