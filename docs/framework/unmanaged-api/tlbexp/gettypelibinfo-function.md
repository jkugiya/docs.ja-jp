---
description: '詳細情報: GetTypeLibInfo 関数'
title: GetTypeLibInfo 関数
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
ms.openlocfilehash: 61a830f3ce81345634da377f6fc815a307700e9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794469"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="e69b7-103">GetTypeLibInfo 関数</span><span class="sxs-lookup"><span data-stu-id="e69b7-103">GetTypeLibInfo Function</span></span>

<span data-ttu-id="e69b7-104">指定したタイプライブラリに関する情報を返します。そのためには、その [Tlibattr](/windows/win32/api/oaidl/ns-oaidl-tlibattr) 構造体を調べます。</span><span class="sxs-lookup"><span data-stu-id="e69b7-104">Returns information about the specified type library by examining its [TLIBATTR](/windows/win32/api/oaidl/ns-oaidl-tlibattr) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e69b7-105">構文</span><span class="sxs-lookup"><span data-stu-id="e69b7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e69b7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e69b7-106">Parameters</span></span>  

 `szFile`  
 <span data-ttu-id="e69b7-107">からタイプライブラリのファイル名。</span><span class="sxs-lookup"><span data-stu-id="e69b7-107">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="e69b7-108">入出力タイプライブラリの GUID。</span><span class="sxs-lookup"><span data-stu-id="e69b7-108">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="e69b7-109">入出力タイプライブラリのローカライズ ID。</span><span class="sxs-lookup"><span data-stu-id="e69b7-109">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="e69b7-110">入出力タイプライブラリのターゲットオペレーティングシステムを識別する [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) フラグ。</span><span class="sxs-lookup"><span data-stu-id="e69b7-110">[out] A [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="e69b7-111">共通値は SYS_WIN32 と SYS_WIN64 です。</span><span class="sxs-lookup"><span data-stu-id="e69b7-111">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="e69b7-112">入出力タイプライブラリのメジャーバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="e69b7-112">[out] The major version number of the type library.</span></span> <span data-ttu-id="e69b7-113">たとえば、バージョン *x.y* の場合、メジャーバージョン番号は *x* になります。</span><span class="sxs-lookup"><span data-stu-id="e69b7-113">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="e69b7-114">入出力タイプライブラリのマイナーバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="e69b7-114">[out] The minor version number of the type library.</span></span> <span data-ttu-id="e69b7-115">たとえば、バージョン *x.y* の場合、マイナーバージョン番号は *y* になります。</span><span class="sxs-lookup"><span data-stu-id="e69b7-115">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e69b7-116">解説</span><span class="sxs-lookup"><span data-stu-id="e69b7-116">Remarks</span></span>  

 <span data-ttu-id="e69b7-117">`GetTypeLibInfo`関数は、 [Tlbexp.exe (タイプライブラリエクスポーター)](../../tools/tlbexp-exe-type-library-exporter.md)によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e69b7-117">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="e69b7-118">このツールは、共通言語ランタイム (CLR) アセンブリ内の型を記述するタイプライブラリを生成します。</span><span class="sxs-lookup"><span data-stu-id="e69b7-118">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="e69b7-119">いずれかのパラメーターが null の場合、関数はのを返し `HRESULT` `E_POINTER` ます。</span><span class="sxs-lookup"><span data-stu-id="e69b7-119">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="e69b7-120">それ以外の場合は `S_OK`を返します。</span><span class="sxs-lookup"><span data-stu-id="e69b7-120">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e69b7-121">要件</span><span class="sxs-lookup"><span data-stu-id="e69b7-121">Requirements</span></span>  

 <span data-ttu-id="e69b7-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e69b7-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e69b7-123">**ヘッダー:** Tlf .h</span><span class="sxs-lookup"><span data-stu-id="e69b7-123">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="e69b7-124">**ライブラリ:** Tlf .lib</span><span class="sxs-lookup"><span data-stu-id="e69b7-124">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="e69b7-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e69b7-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e69b7-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="e69b7-126">See also</span></span>

- [<span data-ttu-id="e69b7-127">Tlbexp ヘルパー関数</span><span class="sxs-lookup"><span data-stu-id="e69b7-127">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="e69b7-128">LoadTypeLibEx 関数</span><span class="sxs-lookup"><span data-stu-id="e69b7-128">LoadTypeLibEx Function</span></span>](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
