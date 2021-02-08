---
description: '詳細: CLRCreateInstance 関数'
title: CLRCreateInstance 関数
ms.date: 03/30/2017
api_name:
- CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- CLRCreateInstance
helpviewer_keywords:
- CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type:
- apiref
ms.openlocfilehash: 3b4dd9f07444f3e7ca68af3b85a7a053fc72b772
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799942"
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="5e232-103">CLRCreateInstance 関数</span><span class="sxs-lookup"><span data-stu-id="5e232-103">CLRCreateInstance Function</span></span>

<span data-ttu-id="5e232-104">には、 [ICLRMetaHost](iclrmetahost-interface.md)、 [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md)、または [ICLRDebugging](../debugging/iclrdebugging-interface.md)の3つのインターフェイスのいずれかが用意されています。</span><span class="sxs-lookup"><span data-stu-id="5e232-104">Provides one of three interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e232-105">構文</span><span class="sxs-lookup"><span data-stu-id="5e232-105">Syntax</span></span>  
  
```cpp  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e232-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5e232-106">Parameters</span></span>  

 `clsid`  
 <span data-ttu-id="5e232-107">からCLSID_CLRMetaHost、CLSID_CLRMetaHostPolicy、または CLSID_CLRDebugging の3つのクラス識別子のいずれか。</span><span class="sxs-lookup"><span data-stu-id="5e232-107">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="5e232-108">から3つのインターフェイス識別子 (Iid が) のいずれか。 IID_ICLRMetaHost、IID_ICLRMetaHostPolicy、または IID_ICLRDebugging です。</span><span class="sxs-lookup"><span data-stu-id="5e232-108">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="5e232-109">入出力 [ICLRMetaHost](iclrmetahost-interface.md)、 [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md)、または [ICLRDebugging](../debugging/iclrdebugging-interface.md)の3つのインターフェイスのいずれか。</span><span class="sxs-lookup"><span data-stu-id="5e232-109">[out] One of three interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e232-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="5e232-110">Return Value</span></span>  

 <span data-ttu-id="5e232-111">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="5e232-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5e232-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5e232-112">HRESULT</span></span>|<span data-ttu-id="5e232-113">説明</span><span class="sxs-lookup"><span data-stu-id="5e232-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5e232-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="5e232-114">S_OK</span></span>|<span data-ttu-id="5e232-115">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="5e232-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="5e232-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="5e232-116">E_POINTER</span></span>|<span data-ttu-id="5e232-117">`ppInterface` が null です。</span><span class="sxs-lookup"><span data-stu-id="5e232-117">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e232-118">解説</span><span class="sxs-lookup"><span data-stu-id="5e232-118">Remarks</span></span>  

 <span data-ttu-id="5e232-119">次の表は、とでサポートされている組み合わせを示して `clsid` `riid` います。</span><span class="sxs-lookup"><span data-stu-id="5e232-119">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`clsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="5e232-120">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="5e232-120">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="5e232-121">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="5e232-121">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="5e232-122">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="5e232-122">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="5e232-123">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="5e232-123">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="5e232-124">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="5e232-124">CLSID_CLRDebugging</span></span>|<span data-ttu-id="5e232-125">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="5e232-125">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="5e232-126">次のコードは、を使用して3つすべてのインターフェイスを取得する方法を示してい `CLRCreateInstance` ます。</span><span class="sxs-lookup"><span data-stu-id="5e232-126">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
```cpp  
#include <metahost.h>  
#pragma comment(lib, "mscoree.lib")  
  
ICLRMetaHost       *pMetaHost       = NULL;  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
ICLRDebugging      *pCLRDebugging   = NULL;  
HRESULT hr;  
hr = CLRCreateInstance(CLSID_CLRMetaHost, IID_ICLRMetaHost,  
                    (LPVOID*)&pMetaHost);  
hr = CLRCreateInstance (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  
                    (LPVOID*)&pMetaHostPolicy);  
hr = CLRCreateInstance (CLSID_CLRDebugging, IID_ICLRDebugging,  
                    (LPVOID*)&pCLRDebugging);  
```  
  
## <a name="requirements"></a><span data-ttu-id="5e232-127">要件</span><span class="sxs-lookup"><span data-stu-id="5e232-127">Requirements</span></span>  

 <span data-ttu-id="5e232-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e232-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e232-129">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="5e232-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5e232-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="5e232-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e232-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e232-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e232-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e232-132">See also</span></span>

- [<span data-ttu-id="5e232-133">ホスティング</span><span class="sxs-lookup"><span data-stu-id="5e232-133">Hosting</span></span>](index.md)
