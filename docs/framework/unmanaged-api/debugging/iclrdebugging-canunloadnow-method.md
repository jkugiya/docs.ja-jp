---
description: '詳細について: ICLRDebugging:: CanUnloadNow メソッド'
title: ICLRDebugging::CanUnloadNow メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebugging.CanUnloadNow Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::CanUnloadNow
helpviewer_keywords:
- CanUnloadNow method [.NET Framework debugging]
- ICLRDebugging::CanUnloadNow method [.NET Framework debugging]
ms.assetid: 62e0630c-8cb7-45d2-b622-5a472abfd8cf
topic_type:
- apiref
ms.openlocfilehash: 537494fe862c58aa8a8768dd5ce2abc8ca94f87d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723375"
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="511a6-103">ICLRDebugging::CanUnloadNow メソッド</span><span class="sxs-lookup"><span data-stu-id="511a6-103">ICLRDebugging::CanUnloadNow Method</span></span>

<span data-ttu-id="511a6-104">[ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)インターフェイスによって提供されたライブラリがまだ使用中であるか、またはアンロードできるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="511a6-104">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="511a6-105">構文</span><span class="sxs-lookup"><span data-stu-id="511a6-105">Syntax</span></span>  
  
```cpp  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="511a6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="511a6-106">Parameters</span></span>  

 `hmodule`  
 <span data-ttu-id="511a6-107">からターゲットプロセス内のモジュールのベースアドレス。</span><span class="sxs-lookup"><span data-stu-id="511a6-107">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="511a6-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="511a6-108">Return Value</span></span>  

 <span data-ttu-id="511a6-109">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="511a6-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="511a6-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="511a6-110">HRESULT</span></span>|<span data-ttu-id="511a6-111">説明</span><span class="sxs-lookup"><span data-stu-id="511a6-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="511a6-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="511a6-112">S_OK</span></span>|<span data-ttu-id="511a6-113">によって参照されているモジュールは、 `hmodule` アンロードできます。</span><span class="sxs-lookup"><span data-stu-id="511a6-113">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="511a6-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="511a6-114">S_FALSE</span></span>|<span data-ttu-id="511a6-115">によって参照されているモジュール `hmodule` は、引き続き使用されています。</span><span class="sxs-lookup"><span data-stu-id="511a6-115">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="511a6-116">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="511a6-116">COR_E_NOT_CLR</span></span>|<span data-ttu-id="511a6-117">指定されたモジュールは CLR モジュールではありません。</span><span class="sxs-lookup"><span data-stu-id="511a6-117">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="511a6-118">例外</span><span class="sxs-lookup"><span data-stu-id="511a6-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="511a6-119">解説</span><span class="sxs-lookup"><span data-stu-id="511a6-119">Remarks</span></span>  

 <span data-ttu-id="511a6-120">このメソッドは、インターフェイスのすべてのインスタンスが解放されているかどうかを確認し、 `ICorDebug*` 現在 [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) メソッドの呼び出し内にスレッドが存在しないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="511a6-120">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="511a6-121">要件</span><span class="sxs-lookup"><span data-stu-id="511a6-121">Requirements</span></span>  

 <span data-ttu-id="511a6-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="511a6-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="511a6-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="511a6-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="511a6-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="511a6-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="511a6-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="511a6-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="511a6-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="511a6-126">See also</span></span>

- [<span data-ttu-id="511a6-127">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="511a6-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="511a6-128">デバッグ</span><span class="sxs-lookup"><span data-stu-id="511a6-128">Debugging</span></span>](index.md)
