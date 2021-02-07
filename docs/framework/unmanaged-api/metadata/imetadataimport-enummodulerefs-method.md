---
description: '詳細について: IMetaDataImport:: EnumModuleRefs メソッド'
title: IMetaDataImport::EnumModuleRefs メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumModuleRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumModuleRefs
helpviewer_keywords:
- EnumModuleRefs method [.NET Framework metadata]
- IMetaDataImport::EnumModuleRefs method [.NET Framework metadata]
ms.assetid: 53441f3a-68d2-477c-906e-37c55dfcfb4d
topic_type:
- apiref
ms.openlocfilehash: 3e12d3da8ff556cb3add73ade77e11a68bf60223
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688820"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="5e9b2-103">IMetaDataImport::EnumModuleRefs メソッド</span><span class="sxs-lookup"><span data-stu-id="5e9b2-103">IMetaDataImport::EnumModuleRefs Method</span></span>

<span data-ttu-id="5e9b2-104">インポートされたモジュールを表す ModuleRef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="5e9b2-104">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e9b2-105">構文</span><span class="sxs-lookup"><span data-stu-id="5e9b2-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e9b2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5e9b2-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="5e9b2-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5e9b2-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="5e9b2-108">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e9b2-108">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="5e9b2-109">入出力ModuleRef トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="5e9b2-109">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5e9b2-110">[in] `rModuleRefs` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="5e9b2-110">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="5e9b2-111">入出力で返された ModuleRef トークンの数 `rModuleRefs` 。</span><span class="sxs-lookup"><span data-stu-id="5e9b2-111">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e9b2-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="5e9b2-112">Return Value</span></span>  
  
|<span data-ttu-id="5e9b2-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5e9b2-113">HRESULT</span></span>|<span data-ttu-id="5e9b2-114">説明</span><span class="sxs-lookup"><span data-stu-id="5e9b2-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5e9b2-115">`EnumModuleRefs` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="5e9b2-115">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5e9b2-116">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="5e9b2-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="5e9b2-117">この場合、 `pcModuleRefs` は0になります。</span><span class="sxs-lookup"><span data-stu-id="5e9b2-117">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5e9b2-118">要件</span><span class="sxs-lookup"><span data-stu-id="5e9b2-118">Requirements</span></span>  

 <span data-ttu-id="5e9b2-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e9b2-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e9b2-120">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="5e9b2-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5e9b2-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="5e9b2-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5e9b2-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e9b2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e9b2-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e9b2-123">See also</span></span>

- [<span data-ttu-id="5e9b2-124">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5e9b2-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="5e9b2-125">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5e9b2-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
