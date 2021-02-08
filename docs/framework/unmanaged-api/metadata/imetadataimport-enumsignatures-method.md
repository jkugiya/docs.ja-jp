---
description: '詳細について: IMetaDataImport:: EnumSignatures メソッド'
title: IMetaDataImport::EnumSignatures メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumSignatures
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type:
- apiref
ms.openlocfilehash: ed41dd42151791e3d27950f30b10d91217ad7e7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771627"
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="39c9e-103">IMetaDataImport::EnumSignatures メソッド</span><span class="sxs-lookup"><span data-stu-id="39c9e-103">IMetaDataImport::EnumSignatures Method</span></span>

<span data-ttu-id="39c9e-104">現在のスコープ内のスタンドアロン シグネチャを表す Signature トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="39c9e-104">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39c9e-105">構文</span><span class="sxs-lookup"><span data-stu-id="39c9e-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39c9e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="39c9e-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="39c9e-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="39c9e-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="39c9e-108">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="39c9e-108">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="39c9e-109">入出力署名トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="39c9e-109">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="39c9e-110">[in] `rSignatures` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="39c9e-110">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="39c9e-111">入出力で返された署名トークンの数 `rSignatures` 。</span><span class="sxs-lookup"><span data-stu-id="39c9e-111">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39c9e-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="39c9e-112">Return Value</span></span>  
  
|<span data-ttu-id="39c9e-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="39c9e-113">HRESULT</span></span>|<span data-ttu-id="39c9e-114">説明</span><span class="sxs-lookup"><span data-stu-id="39c9e-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="39c9e-115">`EnumSignatures` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="39c9e-115">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="39c9e-116">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="39c9e-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="39c9e-117">この場合、 `pcSignatures` は0になります。</span><span class="sxs-lookup"><span data-stu-id="39c9e-117">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39c9e-118">解説</span><span class="sxs-lookup"><span data-stu-id="39c9e-118">Remarks</span></span>  

 <span data-ttu-id="39c9e-119">署名トークンは、 [IMetaDataEmit:: GetTokenFromSig](imetadataemit-gettokenfromsig-method.md) メソッドによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="39c9e-119">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39c9e-120">要件</span><span class="sxs-lookup"><span data-stu-id="39c9e-120">Requirements</span></span>  

 <span data-ttu-id="39c9e-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39c9e-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39c9e-122">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="39c9e-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="39c9e-123">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="39c9e-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="39c9e-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39c9e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39c9e-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="39c9e-125">See also</span></span>

- [<span data-ttu-id="39c9e-126">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="39c9e-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="39c9e-127">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="39c9e-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
