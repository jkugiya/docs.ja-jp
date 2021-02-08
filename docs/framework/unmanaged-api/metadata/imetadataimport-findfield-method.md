---
description: '詳細情報: IMetaDataImport:: FindField メソッド'
title: IMetaDataImport::FindField メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
ms.openlocfilehash: b8041a37b91f22722a05aec99c92c4f17c2b0610
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799305"
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="d689a-103">IMetaDataImport::FindField メソッド</span><span class="sxs-lookup"><span data-stu-id="d689a-103">IMetaDataImport::FindField Method</span></span>

<span data-ttu-id="d689a-104">指定した <xref:System.Type> と指定した名前とメタデータシグネチャを持つフィールドの FieldDef トークンへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="d689a-104">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d689a-105">構文</span><span class="sxs-lookup"><span data-stu-id="d689a-105">Syntax</span></span>  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d689a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d689a-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="d689a-107">から検索対象のフィールドを囲むクラスまたはインターフェイスの TypeDef トークン。</span><span class="sxs-lookup"><span data-stu-id="d689a-107">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="d689a-108">この値がの場合 `mdTokenNil` 、グローバル変数に対して参照が行われます。</span><span class="sxs-lookup"><span data-stu-id="d689a-108">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="d689a-109">から検索するフィールドの名前。</span><span class="sxs-lookup"><span data-stu-id="d689a-109">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="d689a-110">からフィールドのバイナリメタデータシグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d689a-110">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="d689a-111">からのサイズ (バイト単位) `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="d689a-111">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="d689a-112">入出力一致する FieldDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d689a-112">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d689a-113">解説</span><span class="sxs-lookup"><span data-stu-id="d689a-113">Remarks</span></span>  

 <span data-ttu-id="d689a-114">フィールドは、外側のクラスまたはインターフェイス ( `td` )、その名前 ( `szName` )、および必要に応じてシグネチャ () を使用して指定し `pvSigBlob` ます。</span><span class="sxs-lookup"><span data-stu-id="d689a-114">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="d689a-115">署名は特定のスコープにバインドされるため、に渡されるシグネチャは、 `FindField` 現在のスコープで生成される必要があります。</span><span class="sxs-lookup"><span data-stu-id="d689a-115">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="d689a-116">署名には、外側のクラスまたは値の型を識別するトークンを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="d689a-116">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="d689a-117">(トークンは、ローカルの TypeDef テーブルのインデックスです)。</span><span class="sxs-lookup"><span data-stu-id="d689a-117">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="d689a-118">現在のスコープのコンテキスト外でランタイムシグネチャを作成し、その署名をへの入力として使用することはできません `FindField` 。</span><span class="sxs-lookup"><span data-stu-id="d689a-118">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="d689a-119">`FindField` クラスまたはインターフェイスで直接定義されたフィールドのみを検索します。継承されたフィールドは見つかりません。</span><span class="sxs-lookup"><span data-stu-id="d689a-119">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d689a-120">要件</span><span class="sxs-lookup"><span data-stu-id="d689a-120">Requirements</span></span>  

 <span data-ttu-id="d689a-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d689a-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d689a-122">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="d689a-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d689a-123">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d689a-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d689a-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d689a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d689a-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="d689a-125">See also</span></span>

- [<span data-ttu-id="d689a-126">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d689a-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d689a-127">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d689a-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
