---
description: '詳細情報: IMetaDataImport:: EnumPermissionSets メソッド'
title: IMetaDataImport::EnumPermissionSets メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumPermissionSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumPermissionSets
helpviewer_keywords:
- EnumPermissionSets method [.NET Framework metadata]
- IMetaDataImport::EnumPermissionSets method [.NET Framework metadata]
ms.assetid: 347d7e5c-c90f-45ad-bd1e-2c7912b0b19c
topic_type:
- apiref
ms.openlocfilehash: 7138cb2a89ecbea1afbf3e9fccfcac26e7e0fd7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688755"
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="96b35-103">IMetaDataImport::EnumPermissionSets メソッド</span><span class="sxs-lookup"><span data-stu-id="96b35-103">IMetaDataImport::EnumPermissionSets Method</span></span>

<span data-ttu-id="96b35-104">指定したメタデータ スコープ内のオブジェクトのアクセス許可を列挙します。</span><span class="sxs-lookup"><span data-stu-id="96b35-104">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96b35-105">構文</span><span class="sxs-lookup"><span data-stu-id="96b35-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,
   [in]      mdToken       tk,
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96b35-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="96b35-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="96b35-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="96b35-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="96b35-108">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="96b35-108">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="96b35-109">から検索範囲を制限するメタデータトークン。または、可能な限り広い範囲を検索する場合は NULL。</span><span class="sxs-lookup"><span data-stu-id="96b35-109">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="96b35-110">から <xref:System.Security.Permissions.SecurityAction> に含める値を表すフラグ `rPermission` 。すべてのアクションを返す場合は0。</span><span class="sxs-lookup"><span data-stu-id="96b35-110">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="96b35-111">入出力アクセス許可トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="96b35-111">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="96b35-112">[in] `rPermission` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="96b35-112">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="96b35-113">入出力で返されたアクセス許可トークンの数 `rPermission` 。</span><span class="sxs-lookup"><span data-stu-id="96b35-113">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96b35-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="96b35-114">Return Value</span></span>  
  
|<span data-ttu-id="96b35-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="96b35-115">HRESULT</span></span>|<span data-ttu-id="96b35-116">説明</span><span class="sxs-lookup"><span data-stu-id="96b35-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="96b35-117">`EnumPermissionSets` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="96b35-117">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="96b35-118">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="96b35-118">There are no tokens to enumerate.</span></span> <span data-ttu-id="96b35-119">この場合、 `pcTokens` は0になります。</span><span class="sxs-lookup"><span data-stu-id="96b35-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="96b35-120">要件</span><span class="sxs-lookup"><span data-stu-id="96b35-120">Requirements</span></span>  

 <span data-ttu-id="96b35-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96b35-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96b35-122">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="96b35-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96b35-123">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="96b35-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96b35-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96b35-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96b35-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="96b35-125">See also</span></span>

- [<span data-ttu-id="96b35-126">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96b35-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="96b35-127">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96b35-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
