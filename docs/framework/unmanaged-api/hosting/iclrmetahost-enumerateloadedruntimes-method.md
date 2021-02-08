---
description: '詳細について: ICLRMetaHost:: EnumerateLoadedRuntimes メソッド'
title: ICLRMetaHost::EnumerateLoadedRuntimes メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
ms.openlocfilehash: 508c4daca7e34366e0da35591f4e7a780301e823
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789867"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="3d5be-103">ICLRMetaHost::EnumerateLoadedRuntimes メソッド</span><span class="sxs-lookup"><span data-stu-id="3d5be-103">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>

<span data-ttu-id="3d5be-104">指定されたプロセスに読み込まれる共通言語ランタイム (CLR) の各バージョンの有効な [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスポインターを含む列挙体を返します。</span><span class="sxs-lookup"><span data-stu-id="3d5be-104">Returns an enumeration that includes a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="3d5be-105">このメソッドは、 [Getversionfromprocess](getversionfromprocess-function.md) 関数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="3d5be-105">This method supersedes the [GetVersionFromProcess](getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d5be-106">構文</span><span class="sxs-lookup"><span data-stu-id="3d5be-106">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d5be-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3d5be-107">Parameters</span></span>  

 `hndProcess`  
 <span data-ttu-id="3d5be-108">から読み込まれたランタイムを検査するプロセスのハンドル。</span><span class="sxs-lookup"><span data-stu-id="3d5be-108">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="3d5be-109">入出力 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> プロセスによって読み込まれる各 CLR に対応する [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスの列挙体。</span><span class="sxs-lookup"><span data-stu-id="3d5be-109">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d5be-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="3d5be-110">Return Value</span></span>  

 <span data-ttu-id="3d5be-111">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="3d5be-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3d5be-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3d5be-112">HRESULT</span></span>|<span data-ttu-id="3d5be-113">説明</span><span class="sxs-lookup"><span data-stu-id="3d5be-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3d5be-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="3d5be-114">S_OK</span></span>|<span data-ttu-id="3d5be-115">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="3d5be-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="3d5be-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="3d5be-116">E_POINTER</span></span>|<span data-ttu-id="3d5be-117">`ppEnumerator` が null です。</span><span class="sxs-lookup"><span data-stu-id="3d5be-117">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d5be-118">解説</span><span class="sxs-lookup"><span data-stu-id="3d5be-118">Remarks</span></span>  

 <span data-ttu-id="3d5be-119">このメソッドは、 [Corbindtoruntime](corbindtoruntime-function.md)などの非推奨の関数を使用して読み込まれた場合でも、読み込まれたすべてのランタイムを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="3d5be-119">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d5be-120">要件</span><span class="sxs-lookup"><span data-stu-id="3d5be-120">Requirements</span></span>  

 <span data-ttu-id="3d5be-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d5be-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d5be-122">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="3d5be-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3d5be-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3d5be-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d5be-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d5be-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d5be-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d5be-125">See also</span></span>

- [<span data-ttu-id="3d5be-126">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d5be-126">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="3d5be-127">ホスティング</span><span class="sxs-lookup"><span data-stu-id="3d5be-127">Hosting</span></span>](index.md)
