---
description: '詳細情報: LockClrVersion 関数'
title: LockClrVersion 関数
ms.date: 03/30/2017
api_name:
- LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LockClrVersion
helpviewer_keywords:
- LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type:
- apiref
ms.openlocfilehash: 268c08cdd24a826ba92cc8865dfd036f544febcd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679916"
---
# <a name="lockclrversion-function"></a><span data-ttu-id="67c6a-103">LockClrVersion 関数</span><span class="sxs-lookup"><span data-stu-id="67c6a-103">LockClrVersion Function</span></span>

<span data-ttu-id="67c6a-104">CLR を明示的に初期化する前に、プロセス内で使用される共通言語ランタイム (CLR) のバージョンをホストが判断できるようにします。</span><span class="sxs-lookup"><span data-stu-id="67c6a-104">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="67c6a-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="67c6a-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67c6a-106">構文</span><span class="sxs-lookup"><span data-stu-id="67c6a-106">Syntax</span></span>  
  
```cpp  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67c6a-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="67c6a-107">Parameters</span></span>  

 `hostCallback`  
 <span data-ttu-id="67c6a-108">から初期化時に CLR によって呼び出される関数。</span><span class="sxs-lookup"><span data-stu-id="67c6a-108">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="67c6a-109">から初期化を開始することを CLR に通知するために、ホストによって呼び出される関数。</span><span class="sxs-lookup"><span data-stu-id="67c6a-109">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="67c6a-110">から初期化が完了したことを CLR に通知するために、ホストによって呼び出される関数。</span><span class="sxs-lookup"><span data-stu-id="67c6a-110">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67c6a-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="67c6a-111">Return Value</span></span>  

 <span data-ttu-id="67c6a-112">このメソッドは、次の値に加えて、Winerror.h で定義されている標準の COM エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="67c6a-112">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="67c6a-113">リターン コード</span><span class="sxs-lookup"><span data-stu-id="67c6a-113">Return code</span></span>|<span data-ttu-id="67c6a-114">説明</span><span class="sxs-lookup"><span data-stu-id="67c6a-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="67c6a-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="67c6a-115">S_OK</span></span>|<span data-ttu-id="67c6a-116">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="67c6a-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="67c6a-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="67c6a-117">E_INVALIDARG</span></span>|<span data-ttu-id="67c6a-118">1つ以上の引数が null です。</span><span class="sxs-lookup"><span data-stu-id="67c6a-118">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67c6a-119">解説</span><span class="sxs-lookup"><span data-stu-id="67c6a-119">Remarks</span></span>  

 <span data-ttu-id="67c6a-120">CLR を初期化する前に、ホストがを呼び出し `LockClrVersion` ます。</span><span class="sxs-lookup"><span data-stu-id="67c6a-120">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="67c6a-121">`LockClrVersion` は、3つのパラメーターを受け取ります。これらはすべて [Flockclrversioncallback](flockclrversioncallback-function-pointer.md)型のコールバックです。</span><span class="sxs-lookup"><span data-stu-id="67c6a-121">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="67c6a-122">この型は次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="67c6a-122">This type is defined as follows.</span></span>  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="67c6a-123">ランタイムの初期化時には、次の手順が実行されます。</span><span class="sxs-lookup"><span data-stu-id="67c6a-123">The following steps occur upon initialization of the runtime:</span></span>  
  
1. <span data-ttu-id="67c6a-124">ホストは [Corbindtoruntimeex](corbindtoruntimeex-function.md) またはその他のランタイム初期化関数のいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="67c6a-124">The host calls [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="67c6a-125">また、ホストは COM オブジェクトアクティベーションを使用してランタイムを初期化することもできます。</span><span class="sxs-lookup"><span data-stu-id="67c6a-125">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2. <span data-ttu-id="67c6a-126">ランタイムは、パラメーターによって指定された関数を呼び出し `hostCallback` ます。</span><span class="sxs-lookup"><span data-stu-id="67c6a-126">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3. <span data-ttu-id="67c6a-127">によって指定された関数は、 `hostCallback` 次の一連の呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="67c6a-127">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    - <span data-ttu-id="67c6a-128">パラメーターによって指定された関数 `pBeginHostSetup` 。</span><span class="sxs-lookup"><span data-stu-id="67c6a-128">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    - <span data-ttu-id="67c6a-129">`CorBindToRuntimeEx` (または別のランタイム初期化関数)。</span><span class="sxs-lookup"><span data-stu-id="67c6a-129">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    - <span data-ttu-id="67c6a-130">[ICLRRuntimeHost:: SetHostControl](iclrruntimehost-sethostcontrol-method.md)。</span><span class="sxs-lookup"><span data-stu-id="67c6a-130">[ICLRRuntimeHost::SetHostControl](iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    - <span data-ttu-id="67c6a-131">[ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md)。</span><span class="sxs-lookup"><span data-stu-id="67c6a-131">[ICLRRuntimeHost::Start](iclrruntimehost-start-method.md).</span></span>  
  
    - <span data-ttu-id="67c6a-132">パラメーターによって指定された関数 `pEndHostSetup` 。</span><span class="sxs-lookup"><span data-stu-id="67c6a-132">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="67c6a-133">からへのすべての呼び出しは、 `pBeginHostSetup` `pEndHostSetup` 同じ論理スタックを持つ1つのスレッドまたはファイバーに対して行われる必要があります。</span><span class="sxs-lookup"><span data-stu-id="67c6a-133">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="67c6a-134">このスレッドは、が呼び出されたときのスレッドとは異なる場合があり `hostCallback` ます。</span><span class="sxs-lookup"><span data-stu-id="67c6a-134">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67c6a-135">要件</span><span class="sxs-lookup"><span data-stu-id="67c6a-135">Requirements</span></span>  

 <span data-ttu-id="67c6a-136">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67c6a-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67c6a-137">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="67c6a-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="67c6a-138">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="67c6a-138">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="67c6a-139">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67c6a-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67c6a-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="67c6a-140">See also</span></span>

- [<span data-ttu-id="67c6a-141">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="67c6a-141">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
