---
description: '詳細情報: IMetaDataDispenserEx:: FindAssemblyModule メソッド'
title: IMetaDataDispenserEx::FindAssemblyModule メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssemblyModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssemblyModule
helpviewer_keywords:
- FindAssemblyModule method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssemblyModule method [.NET Framework metadata]
ms.assetid: d1fb65e1-7e19-4513-85b1-44f87c294d3e
topic_type:
- apiref
ms.openlocfilehash: 39ea13a2d8f2436e86db513aaa33f990f43d8132
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753576"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="866e9-103">IMetaDataDispenserEx::FindAssemblyModule メソッド</span><span class="sxs-lookup"><span data-stu-id="866e9-103">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>

<span data-ttu-id="866e9-104">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="866e9-104">This method is not implemented.</span></span> <span data-ttu-id="866e9-105">呼び出された場合は E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="866e9-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="866e9-106">構文</span><span class="sxs-lookup"><span data-stu-id="866e9-106">Syntax</span></span>  
  
```cpp  
HRESULT FindAssemblyModule(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [in]  LPCWSTR  szModuleName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="866e9-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="866e9-107">Parameters</span></span>  

 `szAppBase`  
 <span data-ttu-id="866e9-108">から使用しません。</span><span class="sxs-lookup"><span data-stu-id="866e9-108">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="866e9-109">から使用しません。</span><span class="sxs-lookup"><span data-stu-id="866e9-109">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="866e9-110">から使用しません。</span><span class="sxs-lookup"><span data-stu-id="866e9-110">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="866e9-111">からモジュールの名前。</span><span class="sxs-lookup"><span data-stu-id="866e9-111">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="866e9-112">から検索するアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="866e9-112">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="866e9-113">入出力アセンブリの簡易名。</span><span class="sxs-lookup"><span data-stu-id="866e9-113">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="866e9-114">からのサイズ (バイト単位) `szName` 。</span><span class="sxs-lookup"><span data-stu-id="866e9-114">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="866e9-115">入出力で実際に返された文字数 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="866e9-115">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="866e9-116">要件</span><span class="sxs-lookup"><span data-stu-id="866e9-116">Requirements</span></span>  

 <span data-ttu-id="866e9-117">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="866e9-117">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="866e9-118">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="866e9-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="866e9-119">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="866e9-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="866e9-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="866e9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="866e9-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="866e9-121">See also</span></span>

- [<span data-ttu-id="866e9-122">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="866e9-122">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="866e9-123">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="866e9-123">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
