---
description: '詳細について: ICLRRuntimeInfo:: GetVersionString メソッド'
title: ICLRRuntimeInfo::GetVersionString メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetVersionString
helpviewer_keywords:
- ICLRRuntimeInfo::GetVersionString method [.NET Framework hosting]
- GetVersionString method, ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 98b097ef-2276-4dd9-8551-b03c972e8179
topic_type:
- apiref
ms.openlocfilehash: 1c7603f4e9bb1142c415ba9da7a05a52d2d5e776
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753875"
---
# <a name="iclrruntimeinfogetversionstring-method"></a><span data-ttu-id="4ca6a-103">ICLRRuntimeInfo::GetVersionString メソッド</span><span class="sxs-lookup"><span data-stu-id="4ca6a-103">ICLRRuntimeInfo::GetVersionString Method</span></span>

<span data-ttu-id="4ca6a-104">指定した [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスに関連付けられている共通言語ランタイム (CLR) のバージョン情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="4ca6a-104">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="4ca6a-105">このメソッドは、次の関数を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="4ca6a-105">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="4ca6a-106">GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="4ca6a-106">GetRequestedRuntimeInfo</span></span>](getrequestedruntimeinfo-function.md)  
  
- [<span data-ttu-id="4ca6a-107">GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="4ca6a-107">GetRequestedRuntimeVersion</span></span>](getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="4ca6a-108">構文</span><span class="sxs-lookup"><span data-stu-id="4ca6a-108">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ca6a-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4ca6a-109">Parameters</span></span>  

 `pwzBuffer`  
 <span data-ttu-id="4ca6a-110">入出力.NET Framework のコンパイルバージョンを "v *A*" という形式で指定します。*B*[.*X*] "</span><span class="sxs-lookup"><span data-stu-id="4ca6a-110">[out] The .NET Framework compilation version in the format "v *A*.*B*[.*X*]".</span></span> <span data-ttu-id="4ca6a-111">*A*、 *B*、および *X* は、メジャーバージョン、マイナーバージョン、およびビルド番号に対応する10進数です。</span><span class="sxs-lookup"><span data-stu-id="4ca6a-111">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="4ca6a-112">*X* は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="4ca6a-112">*X* is optional.</span></span> <span data-ttu-id="4ca6a-113">*X* が存在しない場合、末尾のピリオドはありません。</span><span class="sxs-lookup"><span data-stu-id="4ca6a-113">If *X* is not present, there is no trailing period.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ca6a-114">このパラメーターは、C:\Windows\Microsoft.NET\Framework. の下に表示される .NET Framework バージョンのディレクトリ名と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ca6a-114">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="4ca6a-115">値の例としては、"v v1.0.3705"、"v 1.1.4322"、"v v2.0.50727"、および "v4.0" があります。*x*"。ここで *x* は、インストールされているビルド番号に依存します。</span><span class="sxs-lookup"><span data-stu-id="4ca6a-115">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*x*", where *x* depends on the build number installed.</span></span> <span data-ttu-id="4ca6a-116">"V" プレフィックスが必須であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4ca6a-116">Note that the "v" prefix is mandatory.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="4ca6a-117">[入力、出力] `pwzBuffer` バッファーオーバーランを回避するためののサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="4ca6a-117">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="4ca6a-118">`pwzBuffer`がの場合、は、割り当てを `null` `pchBuffer` 許可するために必要なサイズを返し `pwzBuffer` ます。</span><span class="sxs-lookup"><span data-stu-id="4ca6a-118">If `pwzBuffer` is `null`, `pchBuffer` returns the required size of `pwzBuffer` to allow preallocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ca6a-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="4ca6a-119">Return Value</span></span>  

 <span data-ttu-id="4ca6a-120">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="4ca6a-120">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4ca6a-121">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4ca6a-121">HRESULT</span></span>|<span data-ttu-id="4ca6a-122">説明</span><span class="sxs-lookup"><span data-stu-id="4ca6a-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4ca6a-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="4ca6a-123">S_OK</span></span>|<span data-ttu-id="4ca6a-124">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="4ca6a-124">The method completed successfully.</span></span>|  
|<span data-ttu-id="4ca6a-125">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="4ca6a-125">E_POINTER</span></span>|<span data-ttu-id="4ca6a-126">`pwzBuffer` または `pchBuffer` が null です。</span><span class="sxs-lookup"><span data-stu-id="4ca6a-126">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4ca6a-127">要件</span><span class="sxs-lookup"><span data-stu-id="4ca6a-127">Requirements</span></span>  

 <span data-ttu-id="4ca6a-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ca6a-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ca6a-129">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="4ca6a-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4ca6a-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4ca6a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ca6a-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ca6a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ca6a-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ca6a-132">See also</span></span>

- [<span data-ttu-id="4ca6a-133">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4ca6a-133">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="4ca6a-134">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4ca6a-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="4ca6a-135">.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4ca6a-135">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="4ca6a-136">ホスティング</span><span class="sxs-lookup"><span data-stu-id="4ca6a-136">Hosting</span></span>](index.md)
