---
description: '詳細について: ICLRRuntimeInfo:: LoadErrorString メソッド'
title: ICLRRuntimeInfo::LoadErrorString メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadErrorString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type:
- apiref
ms.openlocfilehash: 0523b5b89072db50c83c52065c22e9df7167a027
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785069"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="81d4c-103">ICLRRuntimeInfo::LoadErrorString メソッド</span><span class="sxs-lookup"><span data-stu-id="81d4c-103">ICLRRuntimeInfo::LoadErrorString Method</span></span>

<span data-ttu-id="81d4c-104">HRESULT 値を、指定したカルチャの適切なエラーメッセージに変換します。</span><span class="sxs-lookup"><span data-stu-id="81d4c-104">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="81d4c-105">このメソッドは、次の関数を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="81d4c-105">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="81d4c-106">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="81d4c-106">LoadStringRC</span></span>](loadstringrc-function.md)  
  
- [<span data-ttu-id="81d4c-107">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="81d4c-107">LoadStringRCEx</span></span>](loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="81d4c-108">構文</span><span class="sxs-lookup"><span data-stu-id="81d4c-108">Syntax</span></span>  
  
```cpp  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81d4c-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81d4c-109">Parameters</span></span>  

 `iResourceID`  
 <span data-ttu-id="81d4c-110">から変換する HRESULT。</span><span class="sxs-lookup"><span data-stu-id="81d4c-110">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="81d4c-111">入出力指定した HRESULT に関連付けられているメッセージ文字列。</span><span class="sxs-lookup"><span data-stu-id="81d4c-111">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="81d4c-112">[入力、出力] `pwzbuffer` バッファーオーバーランを回避するためののサイズ。</span><span class="sxs-lookup"><span data-stu-id="81d4c-112">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="81d4c-113">`pwzbuffer`が null の場合、は、 `pcchBuffer` の予期されるサイズを提供して、事前割り当て `pwzbuffer` を可能にします。</span><span class="sxs-lookup"><span data-stu-id="81d4c-113">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="81d4c-114">からカルチャ識別子。</span><span class="sxs-lookup"><span data-stu-id="81d4c-114">[in] The culture identifier.</span></span> <span data-ttu-id="81d4c-115">既定のカルチャを使用するには、-1 を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81d4c-115">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81d4c-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="81d4c-116">Return Value</span></span>  

 <span data-ttu-id="81d4c-117">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="81d4c-117">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="81d4c-118">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81d4c-118">HRESULT</span></span>|<span data-ttu-id="81d4c-119">説明</span><span class="sxs-lookup"><span data-stu-id="81d4c-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81d4c-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="81d4c-120">S_OK</span></span>|<span data-ttu-id="81d4c-121">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="81d4c-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="81d4c-122">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="81d4c-122">E_POINTER</span></span>|<span data-ttu-id="81d4c-123">`pcchBuffer` が null です。</span><span class="sxs-lookup"><span data-stu-id="81d4c-123">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="81d4c-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="81d4c-124">E_INVALIDARG</span></span>|<span data-ttu-id="81d4c-125">`pwzBuffer` が null です。</span><span class="sxs-lookup"><span data-stu-id="81d4c-125">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="81d4c-126">要件</span><span class="sxs-lookup"><span data-stu-id="81d4c-126">Requirements</span></span>  

 <span data-ttu-id="81d4c-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81d4c-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81d4c-128">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="81d4c-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="81d4c-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="81d4c-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81d4c-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81d4c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81d4c-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="81d4c-131">See also</span></span>

- [<span data-ttu-id="81d4c-132">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="81d4c-132">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="81d4c-133">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="81d4c-133">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="81d4c-134">ホスティング</span><span class="sxs-lookup"><span data-stu-id="81d4c-134">Hosting</span></span>](index.md)
