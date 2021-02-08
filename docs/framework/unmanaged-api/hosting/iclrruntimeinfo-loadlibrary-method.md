---
description: '詳細について: ICLRRuntimeInfo:: LoadLibrary メソッド'
title: ICLRRuntimeInfo::LoadLibrary メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadLibrary
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadLibrary
helpviewer_keywords:
- ICLRRuntimeInfo::LoadLibrary method [.NET Framework hosting]
- LoadLibrary method [.NET Framework hosting]
ms.assetid: 4517ada3-4417-4ac5-a150-73da7a87c686
topic_type:
- apiref
ms.openlocfilehash: 47557934868c7c1b68b23bf4eded0e90705d7252
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785056"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="7fe21-103">ICLRRuntimeInfo::LoadLibrary メソッド</span><span class="sxs-lookup"><span data-stu-id="7fe21-103">ICLRRuntimeInfo::LoadLibrary Method</span></span>

<span data-ttu-id="7fe21-104">[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)インターフェイスによって表される共通言語ランタイム (CLR) から .NET Framework ライブラリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="7fe21-104">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="7fe21-105">このメソッドは、 [LoadLibraryShim](loadlibraryshim-function.md) 関数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="7fe21-105">This method supersedes the [LoadLibraryShim](loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fe21-106">構文</span><span class="sxs-lookup"><span data-stu-id="7fe21-106">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fe21-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7fe21-107">Parameters</span></span>  

 `pwzDllName`  
 <span data-ttu-id="7fe21-108">から読み込むアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="7fe21-108">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="7fe21-109">入出力読み込まれたアセンブリへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="7fe21-109">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7fe21-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="7fe21-110">Return Value</span></span>  

 <span data-ttu-id="7fe21-111">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="7fe21-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7fe21-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7fe21-112">HRESULT</span></span>|<span data-ttu-id="7fe21-113">説明</span><span class="sxs-lookup"><span data-stu-id="7fe21-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7fe21-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7fe21-114">S_OK</span></span>|<span data-ttu-id="7fe21-115">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="7fe21-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="7fe21-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="7fe21-116">E_POINTER</span></span>|<span data-ttu-id="7fe21-117">`pwzDllName` または `phndModule` が null です。</span><span class="sxs-lookup"><span data-stu-id="7fe21-117">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="7fe21-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7fe21-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7fe21-119">要求を処理するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="7fe21-119">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fe21-120">解説</span><span class="sxs-lookup"><span data-stu-id="7fe21-120">Remarks</span></span>  

 <span data-ttu-id="7fe21-121">このメソッドは、.NET Framework 再頒布可能パッケージに含まれている Dll のみを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="7fe21-121">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="7fe21-122">ユーザーが生成したアセンブリを読み込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="7fe21-122">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fe21-123">要件</span><span class="sxs-lookup"><span data-stu-id="7fe21-123">Requirements</span></span>  

 <span data-ttu-id="7fe21-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fe21-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fe21-125">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="7fe21-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7fe21-126">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="7fe21-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7fe21-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fe21-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe21-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="7fe21-128">See also</span></span>

- [<span data-ttu-id="7fe21-129">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7fe21-129">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="7fe21-130">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7fe21-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="7fe21-131">ホスティング</span><span class="sxs-lookup"><span data-stu-id="7fe21-131">Hosting</span></span>](index.md)
