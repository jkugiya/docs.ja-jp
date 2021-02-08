---
description: 詳細については、「GetRequestedRuntimeVersionForCLSID 関数」を参照してください。
title: GetRequestedRuntimeVersionForCLSID 関数
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersionForCLSID
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersionForCLSID
helpviewer_keywords:
- GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type:
- apiref
ms.openlocfilehash: 10fdc947181d3f1fa12b33f11cf31b68fc4285cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785264"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="846c4-103">GetRequestedRuntimeVersionForCLSID 関数</span><span class="sxs-lookup"><span data-stu-id="846c4-103">GetRequestedRuntimeVersionForCLSID Function</span></span>

<span data-ttu-id="846c4-104">指定したを使用して、クラスの適切な共通言語ランタイム (CLR) バージョン情報を取得し `CLSID` ます。</span><span class="sxs-lookup"><span data-stu-id="846c4-104">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="846c4-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="846c4-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="846c4-106">構文</span><span class="sxs-lookup"><span data-stu-id="846c4-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,
    [out]  LPWSTR     pVersion,
    [in]  DWORD      cchBuffer,
    [out] DWORD*     dwLength,
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="846c4-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="846c4-107">Parameters</span></span>  

 `rclsid`  
 <span data-ttu-id="846c4-108">から `CLSID` コンポーネントの。</span><span class="sxs-lookup"><span data-stu-id="846c4-108">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="846c4-109">入出力 正常に完了したときのバージョン番号の文字列を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="846c4-109">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="846c4-110">から バッファーのサイズ (ワイド文字単位) `pVersion` 。</span><span class="sxs-lookup"><span data-stu-id="846c4-110">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="846c4-111">入出力返されたバッファーの長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="846c4-111">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="846c4-112">から CLSID_RESOLUTION_FLAGS 値の1つ。</span><span class="sxs-lookup"><span data-stu-id="846c4-112">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="846c4-113">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="846c4-113">The following values are supported:</span></span>  
  
- <span data-ttu-id="846c4-114">CLSID_RESOLUTION_DEFAULT: (0x0) 既定の相互運用動作を使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="846c4-114">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
- <span data-ttu-id="846c4-115">CLSID_RESOLUTION_REGISTERED: (0x1) は、レジストリを検索する必要があり、shim ポリシーを適用する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="846c4-115">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="846c4-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="846c4-116">Return Value</span></span>  
  
|<span data-ttu-id="846c4-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="846c4-117">HRESULT</span></span>|<span data-ttu-id="846c4-118">説明</span><span class="sxs-lookup"><span data-stu-id="846c4-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="846c4-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="846c4-119">S_OK</span></span>|<span data-ttu-id="846c4-120">関数が正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="846c4-120">The function returned successfully.</span></span>|  
|<span data-ttu-id="846c4-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="846c4-121">E_INVALIDARG</span></span>|<span data-ttu-id="846c4-122">パラメーターの1つに無効な型または形式が指定されています。</span><span class="sxs-lookup"><span data-stu-id="846c4-122">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="846c4-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="846c4-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="846c4-124">`pVersion`バッファーのサイズが、バージョン文字列全体を保持するのに十分ではありません。</span><span class="sxs-lookup"><span data-stu-id="846c4-124">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="846c4-125">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="846c4-125">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="846c4-126">指定されたに登録されているクラスがありません `CLSID` 。</span><span class="sxs-lookup"><span data-stu-id="846c4-126">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="846c4-127">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="846c4-127">E_POINTER</span></span>|<span data-ttu-id="846c4-128">`dwLength` が null であるか、または `cchBuffer` バージョン文字列を保持するのに十分な大きさですが、が `pVersion` null です。</span><span class="sxs-lookup"><span data-stu-id="846c4-128">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="846c4-129">要件</span><span class="sxs-lookup"><span data-stu-id="846c4-129">Requirements</span></span>  

 <span data-ttu-id="846c4-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="846c4-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="846c4-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="846c4-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="846c4-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="846c4-132">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="846c4-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="846c4-133">See also</span></span>

- [<span data-ttu-id="846c4-134">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="846c4-134">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
