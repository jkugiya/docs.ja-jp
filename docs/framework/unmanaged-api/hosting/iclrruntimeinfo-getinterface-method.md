---
description: '詳細について: ICLRRuntimeInfo:: GetInterface メソッド'
title: ICLRRuntimeInfo::GetInterface メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetInterface
helpviewer_keywords:
- GetInterface method [.NET Framework hosting]
- ICLRRuntimeInfo::GetInterface method [.NET Framework hosting]
ms.assetid: cc7b0e5b-48c3-4509-8ebb-611ddb1f7ec2
topic_type:
- apiref
ms.openlocfilehash: 5a5c55823ff9954735a712423d8aaab1256c947d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637132"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="daecb-103">ICLRRuntimeInfo::GetInterface メソッド</span><span class="sxs-lookup"><span data-stu-id="daecb-103">ICLRRuntimeInfo::GetInterface Method</span></span>

<span data-ttu-id="daecb-104">現在のプロセスに CLR を読み込み、 [ICLRRuntimeHost](iclrruntimehost-interface.md)、 [ICLRStrongName](iclrstrongname-interface.md)、 [IMetaDataDispenserEx](../metadata/imetadatadispenser-interface.md)などのランタイムインターフェイスポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="daecb-104">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md), and [IMetaDataDispenserEx](../metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="daecb-105">このメソッドは、 `CorBindTo` 「 [非推奨の CLR ホスト関数](deprecated-clr-hosting-functions.md) 」セクションのすべての \* 関数を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="daecb-105">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daecb-106">構文</span><span class="sxs-lookup"><span data-stu-id="daecb-106">Syntax</span></span>  
  
```cpp  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="daecb-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="daecb-107">Parameters</span></span>  

 `rclsid`  
 <span data-ttu-id="daecb-108">からコクラスの CLSID インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="daecb-108">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="daecb-109">から要求されたインターフェイスの IID `rclsid` 。</span><span class="sxs-lookup"><span data-stu-id="daecb-109">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="daecb-110">入出力クエリされたインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="daecb-110">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="daecb-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="daecb-111">Return Value</span></span>  

 <span data-ttu-id="daecb-112">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="daecb-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="daecb-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="daecb-113">HRESULT</span></span>|<span data-ttu-id="daecb-114">説明</span><span class="sxs-lookup"><span data-stu-id="daecb-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="daecb-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="daecb-115">S_OK</span></span>|<span data-ttu-id="daecb-116">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="daecb-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="daecb-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="daecb-117">E_POINTER</span></span>|<span data-ttu-id="daecb-118">`ppUnk` が null です。</span><span class="sxs-lookup"><span data-stu-id="daecb-118">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="daecb-119">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="daecb-119">E_OUTOFMEMORY</span></span>|<span data-ttu-id="daecb-120">要求を処理するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="daecb-120">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="daecb-121">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="daecb-121">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="daecb-122">以前の CLR バージョン2のアクティブ化ポリシーに、別のランタイムが既にバインドされています。</span><span class="sxs-lookup"><span data-stu-id="daecb-122">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="daecb-123">解説</span><span class="sxs-lookup"><span data-stu-id="daecb-123">Remarks</span></span>  

 <span data-ttu-id="daecb-124">このメソッドを使用すると、CLR が読み込まれますが、初期化されません。</span><span class="sxs-lookup"><span data-stu-id="daecb-124">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="daecb-125">次の表は、とでサポートされている組み合わせを示して `rclsid` `riid` います。</span><span class="sxs-lookup"><span data-stu-id="daecb-125">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="daecb-126">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="daecb-126">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="daecb-127">IID_IMetaDataDispenser、IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="daecb-127">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="daecb-128">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="daecb-128">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="daecb-129">IID_IMetaDataDispenser、IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="daecb-129">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="daecb-130">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="daecb-130">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="daecb-131">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="daecb-131">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="daecb-132">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="daecb-132">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="daecb-133">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="daecb-133">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="daecb-134">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="daecb-134">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="daecb-135">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="daecb-135">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="daecb-136">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="daecb-136">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="daecb-137">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="daecb-137">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="daecb-138">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="daecb-138">CLSID_CLRStrongName</span></span>|<span data-ttu-id="daecb-139">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="daecb-139">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="daecb-140">要件</span><span class="sxs-lookup"><span data-stu-id="daecb-140">Requirements</span></span>  

 <span data-ttu-id="daecb-141">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="daecb-141">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daecb-142">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="daecb-142">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="daecb-143">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="daecb-143">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="daecb-144">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daecb-144">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daecb-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="daecb-145">See also</span></span>

- [<span data-ttu-id="daecb-146">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="daecb-146">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="daecb-147">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="daecb-147">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="daecb-148">ホスティング</span><span class="sxs-lookup"><span data-stu-id="daecb-148">Hosting</span></span>](index.md)
