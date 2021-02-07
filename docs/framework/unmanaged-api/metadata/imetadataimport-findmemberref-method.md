---
description: '詳細について: IMetaDataImport:: FindMemberRef メソッド'
title: IMetaDataImport::FindMemberRef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
ms.openlocfilehash: 301d4dc88b36ca2284ca3b8d70444820befdc0aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745581"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="9fe7e-103">IMetaDataImport::FindMemberRef メソッド</span><span class="sxs-lookup"><span data-stu-id="9fe7e-103">IMetaDataImport::FindMemberRef Method</span></span>

<span data-ttu-id="9fe7e-104">指定した <xref:System.Type> と指定した名前とメタデータシグネチャを持つメンバー参照の MemberRef トークンへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="9fe7e-104">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fe7e-105">構文</span><span class="sxs-lookup"><span data-stu-id="9fe7e-105">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fe7e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9fe7e-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="9fe7e-107">から検索対象のメンバー参照を囲むクラスまたはインターフェイスの TypeRef トークン。</span><span class="sxs-lookup"><span data-stu-id="9fe7e-107">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="9fe7e-108">この値がの場合 `mdTokenNil` 、グローバル変数またはグローバル関数参照に対して参照が行われます。</span><span class="sxs-lookup"><span data-stu-id="9fe7e-108">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="9fe7e-109">から検索対象のメンバー参照の名前。</span><span class="sxs-lookup"><span data-stu-id="9fe7e-109">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="9fe7e-110">からメンバー参照のバイナリメタデータシグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9fe7e-110">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="9fe7e-111">からのサイズ (バイト単位) `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="9fe7e-111">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="9fe7e-112">入出力一致する MemberRef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9fe7e-112">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fe7e-113">解説</span><span class="sxs-lookup"><span data-stu-id="9fe7e-113">Remarks</span></span>  

 <span data-ttu-id="9fe7e-114">メンバーは、外側のクラスまたはインターフェイス ( `td` )、その名前 ( `szName` )、および必要に応じてシグネチャ () を使用して指定し `pvSigBlob` ます。</span><span class="sxs-lookup"><span data-stu-id="9fe7e-114">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="9fe7e-115">署名は特定のスコープにバインドされるため、に渡されるシグネチャは、 `FindMemberRef` 現在のスコープで生成される必要があります。</span><span class="sxs-lookup"><span data-stu-id="9fe7e-115">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="9fe7e-116">署名には、外側のクラスまたは値の型を識別するトークンを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="9fe7e-116">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="9fe7e-117">トークンは、ローカルの TypeDef テーブルのインデックスです。</span><span class="sxs-lookup"><span data-stu-id="9fe7e-117">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="9fe7e-118">現在のスコープのコンテキスト外でランタイムシグネチャを作成し、その署名をへの入力として使用することはできません `FindMemberRef` 。</span><span class="sxs-lookup"><span data-stu-id="9fe7e-118">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="9fe7e-119">`FindMemberRef` クラスまたはインターフェイスで直接定義されたメンバー参照だけを検索します。継承されたメンバー参照は見つかりません。</span><span class="sxs-lookup"><span data-stu-id="9fe7e-119">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fe7e-120">要件</span><span class="sxs-lookup"><span data-stu-id="9fe7e-120">Requirements</span></span>  

 <span data-ttu-id="9fe7e-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9fe7e-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fe7e-122">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="9fe7e-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9fe7e-123">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9fe7e-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9fe7e-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fe7e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fe7e-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="9fe7e-125">See also</span></span>

- [<span data-ttu-id="9fe7e-126">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9fe7e-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="9fe7e-127">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9fe7e-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
