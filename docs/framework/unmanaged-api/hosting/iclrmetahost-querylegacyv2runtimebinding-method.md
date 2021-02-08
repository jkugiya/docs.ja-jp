---
description: '詳細について: ICLRMetaHost:: QueryLegacyV2RuntimeBinding メソッド'
title: ICLRMetaHost::QueryLegacyV2RuntimeBinding メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type:
- apiref
ms.openlocfilehash: ae825c2b2dfe2ce5b75ac9b82511215704fa357f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789854"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="7f452-103">ICLRMetaHost::QueryLegacyV2RuntimeBinding メソッド</span><span class="sxs-lookup"><span data-stu-id="7f452-103">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>

<span data-ttu-id="7f452-104">レガシアクティブ化ポリシーがバインドされているランタイムを表すインターフェイスを返します。たとえば、 `useLegacyV2RuntimeActivationPolicy` [ \<startup> 要素](../../configure-apps/file-schema/startup/startup-element.md)構成ファイルのエントリで属性を使用するか、レガシアクティベーション api を直接使用するか、 [ICLRRuntimeInfo:: BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md)メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7f452-104">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f452-105">構文</span><span class="sxs-lookup"><span data-stu-id="7f452-105">Syntax</span></span>  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f452-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7f452-106">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="7f452-107">から必須。現時点では、このパラメーターの有効な `IID_ICLRRuntimeInfo` 値はのみです。</span><span class="sxs-lookup"><span data-stu-id="7f452-107">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="7f452-108">[out] 必須。</span><span class="sxs-lookup"><span data-stu-id="7f452-108">[out] Required.</span></span> <span data-ttu-id="7f452-109">このメソッドから制御が戻るときに、レガシアクティブ化ポリシーにバインドされているランタイムを表す [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスへのポインターを格納します。</span><span class="sxs-lookup"><span data-stu-id="7f452-109">When this method returns, contains a pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f452-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="7f452-110">Return Value</span></span>  

 <span data-ttu-id="7f452-111">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="7f452-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7f452-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f452-112">HRESULT</span></span>|<span data-ttu-id="7f452-113">説明</span><span class="sxs-lookup"><span data-stu-id="7f452-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f452-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7f452-114">S_OK</span></span>|<span data-ttu-id="7f452-115">メソッドは正常に完了し、レガシ アクティブ化ポリシーにバインドされているランタイムが返されました。</span><span class="sxs-lookup"><span data-stu-id="7f452-115">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="7f452-116">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="7f452-116">S_FALSE</span></span>|<span data-ttu-id="7f452-117">メソッドは正常に完了しましたが、レガシ ランタイムはまだバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="7f452-117">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="7f452-118">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="7f452-118">E_NOINTERFACE</span></span>|<span data-ttu-id="7f452-119">メソッドで、レガシ アクティブ化ポリシーにバインドされているランタイムが見つかりましたが、`riid` はそのランタイムでサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7f452-119">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f452-120">解説</span><span class="sxs-lookup"><span data-stu-id="7f452-120">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f452-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="7f452-121">Requirements</span></span>  

 <span data-ttu-id="7f452-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f452-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f452-123">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="7f452-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7f452-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="7f452-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f452-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f452-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f452-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f452-126">See also</span></span>

- [<span data-ttu-id="7f452-127">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7f452-127">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="7f452-128">ホスティング</span><span class="sxs-lookup"><span data-stu-id="7f452-128">Hosting</span></span>](index.md)
