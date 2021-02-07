---
description: '詳細情報: ICLRRuntimeInfo:: IsStarted メソッド'
title: ICLRRuntimeInfo::IsStarted メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsStarted
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
ms.openlocfilehash: 22059ecbded9eae9659cdaae8b9b92f2d7df0650
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753849"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="e3677-103">ICLRRuntimeInfo::IsStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="e3677-103">ICLRRuntimeInfo::IsStarted Method</span></span>

<span data-ttu-id="e3677-104">ランタイムが開始されたかどうか (つまり、 [ICLRRuntimeHost:: Start メソッド](iclrruntimehost-start-method.md) が呼び出され、成功したかどうか) を示します。</span><span class="sxs-lookup"><span data-stu-id="e3677-104">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3677-105">構文</span><span class="sxs-lookup"><span data-stu-id="e3677-105">Syntax</span></span>  
  
```cpp  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3677-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e3677-106">Parameters</span></span>  

 `pbStarted`  
 <span data-ttu-id="e3677-107">[出力] `true` このランタイムが開始されている場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="e3677-107">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="e3677-108">入出力ランタイムを開始するために使用されたフラグを返します。</span><span class="sxs-lookup"><span data-stu-id="e3677-108">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3677-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="e3677-109">Return Value</span></span>  

 <span data-ttu-id="e3677-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="e3677-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e3677-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e3677-111">HRESULT</span></span>|<span data-ttu-id="e3677-112">説明</span><span class="sxs-lookup"><span data-stu-id="e3677-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e3677-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e3677-113">S_OK</span></span>|<span data-ttu-id="e3677-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="e3677-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="e3677-115">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="e3677-115">E_NOTIMPL</span></span>|<span data-ttu-id="e3677-116">共通言語ランタイム (CLR) のバージョンは、.NET Framework 4 の CLR バージョンよりも前のバージョンです。</span><span class="sxs-lookup"><span data-stu-id="e3677-116">The common language runtime (CLR) version is earlier than the CLR version in the .NET Framework 4.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3677-117">解説</span><span class="sxs-lookup"><span data-stu-id="e3677-117">Remarks</span></span>  

 <span data-ttu-id="e3677-118">このメソッドは、.NET Framework 4 の CLR バージョンより前の CLR バージョンでは機能しません。</span><span class="sxs-lookup"><span data-stu-id="e3677-118">This method does not work with CLR versions earlier than the CLR version in the .NET Framework 4.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3677-119">要件</span><span class="sxs-lookup"><span data-stu-id="e3677-119">Requirements</span></span>  

 <span data-ttu-id="e3677-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3677-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3677-121">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="e3677-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e3677-122">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="e3677-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3677-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3677-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3677-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3677-124">See also</span></span>

- [<span data-ttu-id="e3677-125">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e3677-125">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="e3677-126">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e3677-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="e3677-127">ホスティング</span><span class="sxs-lookup"><span data-stu-id="e3677-127">Hosting</span></span>](index.md)
