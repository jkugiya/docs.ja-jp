---
description: '詳細について: ICLRRuntimeInfo:: GetProcAddress メソッド'
title: ICLRRuntimeInfo::GetProcAddress メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetProcAddress
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type:
- apiref
ms.openlocfilehash: 1e5d08ed118930418106b28541b4081d6acad927
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637145"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="ffc54-103">ICLRRuntimeInfo::GetProcAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="ffc54-103">ICLRRuntimeInfo::GetProcAddress Method</span></span>

<span data-ttu-id="ffc54-104">このインターフェイスに関連付けられている共通言語ランタイム (CLR) からエクスポートされた、指定された関数のアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="ffc54-104">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="ffc54-105">このメソッドは、 [GetRealProcAddress](getrealprocaddress-function.md) 関数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="ffc54-105">This method supersedes the [GetRealProcAddress](getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffc54-106">構文</span><span class="sxs-lookup"><span data-stu-id="ffc54-106">Syntax</span></span>  
  
```cpp  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffc54-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ffc54-107">Parameters</span></span>  

 `pszProcName`  
 <span data-ttu-id="ffc54-108">からエクスポートされた関数の名前。</span><span class="sxs-lookup"><span data-stu-id="ffc54-108">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="ffc54-109">入出力エクスポートされた関数のアドレス。</span><span class="sxs-lookup"><span data-stu-id="ffc54-109">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ffc54-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="ffc54-110">Return Value</span></span>  

 <span data-ttu-id="ffc54-111">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="ffc54-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ffc54-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ffc54-112">HRESULT</span></span>|<span data-ttu-id="ffc54-113">説明</span><span class="sxs-lookup"><span data-stu-id="ffc54-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ffc54-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ffc54-114">S_OK</span></span>|<span data-ttu-id="ffc54-115">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="ffc54-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="ffc54-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="ffc54-116">E_POINTER</span></span>|<span data-ttu-id="ffc54-117">`pszProcName` または `ppProc` が null です。</span><span class="sxs-lookup"><span data-stu-id="ffc54-117">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="ffc54-118">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="ffc54-118">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="ffc54-119">指定された関数はエクスポートされた関数ではありません。</span><span class="sxs-lookup"><span data-stu-id="ffc54-119">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffc54-120">解説</span><span class="sxs-lookup"><span data-stu-id="ffc54-120">Remarks</span></span>  

 <span data-ttu-id="ffc54-121">このメソッドを使用すると、CLR が読み込まれますが、初期化されません。</span><span class="sxs-lookup"><span data-stu-id="ffc54-121">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffc54-122">要件</span><span class="sxs-lookup"><span data-stu-id="ffc54-122">Requirements</span></span>  

 <span data-ttu-id="ffc54-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffc54-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffc54-124">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="ffc54-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ffc54-125">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ffc54-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ffc54-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffc54-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffc54-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="ffc54-127">See also</span></span>

- [<span data-ttu-id="ffc54-128">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ffc54-128">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="ffc54-129">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ffc54-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="ffc54-130">ホスティング</span><span class="sxs-lookup"><span data-stu-id="ffc54-130">Hosting</span></span>](index.md)
