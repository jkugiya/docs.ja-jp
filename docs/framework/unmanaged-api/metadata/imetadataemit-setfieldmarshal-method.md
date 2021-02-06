---
description: '詳細について: IMetaDataEmit:: SetFieldMarshal メソッド'
title: IMetaDataEmit::SetFieldMarshal メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type:
- apiref
ms.openlocfilehash: 4694487479b0249e875abfd9ecd963a5dc404d46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658049"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="370ca-103">IMetaDataEmit::SetFieldMarshal メソッド</span><span class="sxs-lookup"><span data-stu-id="370ca-103">IMetaDataEmit::SetFieldMarshal Method</span></span>

<span data-ttu-id="370ca-104">指定したトークンによって参照されるフィールド、メソッドの戻り値、またはメソッドパラメーターの PInvoke マーシャリング情報を設定します。</span><span class="sxs-lookup"><span data-stu-id="370ca-104">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="370ca-105">構文</span><span class="sxs-lookup"><span data-stu-id="370ca-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,
    [in]  PCCOR_SIGNATURE  pvNativeType,
    [in]  ULONG            cbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="370ca-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="370ca-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="370ca-107">からターゲットデータ項目のトークン。</span><span class="sxs-lookup"><span data-stu-id="370ca-107">[in] The token for target data item.</span></span> <span data-ttu-id="370ca-108">これは、 `mdFieldDef` またはトークンのいずれか `mdParamDef` です。</span><span class="sxs-lookup"><span data-stu-id="370ca-108">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="370ca-109">からアンマネージ型のシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="370ca-109">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="370ca-110">からのバイト数 `pvNativeType` 。</span><span class="sxs-lookup"><span data-stu-id="370ca-110">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="370ca-111">要件</span><span class="sxs-lookup"><span data-stu-id="370ca-111">Requirements</span></span>  

 <span data-ttu-id="370ca-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="370ca-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="370ca-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="370ca-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="370ca-114">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="370ca-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="370ca-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="370ca-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="370ca-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="370ca-116">See also</span></span>

- [<span data-ttu-id="370ca-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="370ca-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="370ca-118">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="370ca-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
