---
description: '詳細情報: ResolveTypeLib メソッド'
title: ResolveTypeLib メソッド
ms.date: 03/30/2017
api_name:
- ResolveTypeLib
api_location:
- tlbref.dll
f1_keywords:
- ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type:
- apiref
ms.openlocfilehash: ca7f94f630479d30bb9129497b38bcf04e759e5d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646284"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="d581a-103">ResolveTypeLib メソッド</span><span class="sxs-lookup"><span data-stu-id="d581a-103">ResolveTypeLib Method</span></span>

<span data-ttu-id="d581a-104">完全修飾パスを返すことにより、タイプライブラリの簡易名を解決します。</span><span class="sxs-lookup"><span data-stu-id="d581a-104">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d581a-105">構文</span><span class="sxs-lookup"><span data-stu-id="d581a-105">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d581a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d581a-106">Parameters</span></span>  

 `bstrSimpleName`  
 <span data-ttu-id="d581a-107">からタイプライブラリの簡易名を格納している [BSTR](/previous-versions/windows/desktop/automat/bstr) 。</span><span class="sxs-lookup"><span data-stu-id="d581a-107">[in] A [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="d581a-108">からレジストリのタイプライブラリに割り当てられている GUID。</span><span class="sxs-lookup"><span data-stu-id="d581a-108">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="d581a-109">からタイプライブラリのローカライズ ID。</span><span class="sxs-lookup"><span data-stu-id="d581a-109">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="d581a-110">からタイプライブラリのメジャーバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="d581a-110">[in] The major version number of the type library.</span></span> <span data-ttu-id="d581a-111">たとえば、バージョン *x.y* の場合、メジャーバージョン番号は *x* になります。</span><span class="sxs-lookup"><span data-stu-id="d581a-111">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="d581a-112">からタイプライブラリのマイナーバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="d581a-112">[in] The minor version number of the type library.</span></span> <span data-ttu-id="d581a-113">たとえば、バージョン *x.y* の場合、マイナーバージョン番号は *y* になります。</span><span class="sxs-lookup"><span data-stu-id="d581a-113">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="d581a-114">からオペレーティング環境を識別する [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) フラグ。</span><span class="sxs-lookup"><span data-stu-id="d581a-114">[in] A [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the operating environment.</span></span> <span data-ttu-id="d581a-115">共通値は SYS_WIN32 と SYS_WIN64 です。</span><span class="sxs-lookup"><span data-stu-id="d581a-115">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="d581a-116">入出力パラメーターで指定されたタイプライブラリの完全パスを格納する [BSTR](/previous-versions/windows/desktop/automat/bstr) へのポインター `bstrSimpleName` 。</span><span class="sxs-lookup"><span data-stu-id="d581a-116">[out] A pointer to a [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d581a-117">解説</span><span class="sxs-lookup"><span data-stu-id="d581a-117">Remarks</span></span>  

 <span data-ttu-id="d581a-118">`ResolveTypeLib`メソッドは[Tlbexp.exe (タイプライブラリエクスポーター)](../../tools/tlbexp-exe-type-library-exporter.md)の処理中に[LoadTypeLibWithResolver 関数](loadtypelibwithresolver-function.md)によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d581a-118">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="d581a-119">このインターフェイスのカスタム実装では、パラメーターに指定されたタイプライブラリの完全パスを含む [BSTR](/previous-versions/windows/desktop/automat/bstr) を返す必要があり `bstrSimpleName` ます。</span><span class="sxs-lookup"><span data-stu-id="d581a-119">Custom implementations of this interface must return a [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d581a-120">要件</span><span class="sxs-lookup"><span data-stu-id="d581a-120">Requirements</span></span>  

 <span data-ttu-id="d581a-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d581a-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d581a-122">**ヘッダー:** Tlf .idl, Tl. h</span><span class="sxs-lookup"><span data-stu-id="d581a-122">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="d581a-123">**ライブラリ:** Tlf .lib</span><span class="sxs-lookup"><span data-stu-id="d581a-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="d581a-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d581a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d581a-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="d581a-125">See also</span></span>

- [<span data-ttu-id="d581a-126">Tlbexp ヘルパー関数</span><span class="sxs-lookup"><span data-stu-id="d581a-126">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="d581a-127">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="d581a-127">LoadTypeLibEx</span></span>](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
