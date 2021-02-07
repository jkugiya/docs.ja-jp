---
description: '詳細情報: IMetaDataDispenserEx:: FindAssembly メソッド'
title: IMetaDataDispenserEx::FindAssembly メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssembly
helpviewer_keywords:
- FindAssembly method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssembly method [.NET Framework metadata]
ms.assetid: 3afe7252-5f28-48d9-a74d-1927566c404c
topic_type:
- apiref
ms.openlocfilehash: 6bed016e9235281b42f5a3231ef2aff284b6cc3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753602"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="835aa-103">IMetaDataDispenserEx::FindAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="835aa-103">IMetaDataDispenserEx::FindAssembly Method</span></span>

<span data-ttu-id="835aa-104">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="835aa-104">This method is not implemented.</span></span> <span data-ttu-id="835aa-105">呼び出された場合は E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="835aa-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="835aa-106">構文</span><span class="sxs-lookup"><span data-stu-id="835aa-106">Syntax</span></span>  
  
```cpp  
HRESULT FindAssembly(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="835aa-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="835aa-107">Parameters</span></span>  

 `szAppBase`  
 <span data-ttu-id="835aa-108">から使用しません。</span><span class="sxs-lookup"><span data-stu-id="835aa-108">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="835aa-109">から使用しません。</span><span class="sxs-lookup"><span data-stu-id="835aa-109">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="835aa-110">から使用しません。</span><span class="sxs-lookup"><span data-stu-id="835aa-110">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="835aa-111">から検索するアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="835aa-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="835aa-112">入出力アセンブリの簡易名。</span><span class="sxs-lookup"><span data-stu-id="835aa-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="835aa-113">からのサイズ (バイト単位) `szName` 。</span><span class="sxs-lookup"><span data-stu-id="835aa-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="835aa-114">入出力で実際に返された文字数 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="835aa-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="835aa-115">要件</span><span class="sxs-lookup"><span data-stu-id="835aa-115">Requirements</span></span>  

 <span data-ttu-id="835aa-116">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="835aa-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="835aa-117">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="835aa-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="835aa-118">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="835aa-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="835aa-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="835aa-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="835aa-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="835aa-120">See also</span></span>

- [<span data-ttu-id="835aa-121">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="835aa-121">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="835aa-122">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="835aa-122">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
