---
description: '詳細について: IMetaDataImport:: EnumMembersWithName メソッド'
title: IMetaDataImport::EnumMembersWithName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembersWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembersWithName
helpviewer_keywords:
- IMetaDataImport::EnumMembersWithName method [.NET Framework metadata]
- EnumMembersWithName method [.NET Framework metadata]
ms.assetid: 7c9e9120-3104-42f0-86ce-19a025f20dcc
topic_type:
- apiref
ms.openlocfilehash: bb6d8f0769029dccaf1f52dd211c67d47bf32a73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670763"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="c4163-103">IMetaDataImport::EnumMembersWithName メソッド</span><span class="sxs-lookup"><span data-stu-id="c4163-103">IMetaDataImport::EnumMembersWithName Method</span></span>

<span data-ttu-id="c4163-104">指定した名前を持つ指定した型のメンバーを表す MemberDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="c4163-104">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4163-105">構文</span><span class="sxs-lookup"><span data-stu-id="c4163-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [in]      LPCWSTR     szName,
   [out]     mdToken     rMembers[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4163-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c4163-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="c4163-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c4163-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="c4163-108">から列挙するメンバーを持つ型を表す TypeDef トークン。</span><span class="sxs-lookup"><span data-stu-id="c4163-108">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="c4163-109">から列挙子のスコープを制限するメンバー名。</span><span class="sxs-lookup"><span data-stu-id="c4163-109">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="c4163-110">入出力MemberDef トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="c4163-110">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c4163-111">[in] `rMembers` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="c4163-111">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="c4163-112">入出力で返された MemberDef トークンの実際の数 `rMembers` 。</span><span class="sxs-lookup"><span data-stu-id="c4163-112">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4163-113">解説</span><span class="sxs-lookup"><span data-stu-id="c4163-113">Remarks</span></span>  

 <span data-ttu-id="c4163-114">このメソッドは、フィールドとメソッドを列挙しますが、プロパティやイベントは列挙しません。</span><span class="sxs-lookup"><span data-stu-id="c4163-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="c4163-115">[IMetaDataImport:: EnumMembers](imetadataimport-enummembers-method.md)とは異なり、では、 `EnumMembersWithName` 指定された名前のないすべてのフィールドとメンバートークンが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="c4163-115">Unlike [IMetaDataImport::EnumMembers](imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4163-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="c4163-116">Return Value</span></span>  
  
|<span data-ttu-id="c4163-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c4163-117">HRESULT</span></span>|<span data-ttu-id="c4163-118">説明</span><span class="sxs-lookup"><span data-stu-id="c4163-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c4163-119">`EnumTypeDefs` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="c4163-119">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c4163-120">列挙する MemberDef トークンがありません。</span><span class="sxs-lookup"><span data-stu-id="c4163-120">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="c4163-121">この場合、 `pcTokens` は0になります。</span><span class="sxs-lookup"><span data-stu-id="c4163-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c4163-122">要件</span><span class="sxs-lookup"><span data-stu-id="c4163-122">Requirements</span></span>  

 <span data-ttu-id="c4163-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4163-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4163-124">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="c4163-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c4163-125">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="c4163-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c4163-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4163-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4163-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4163-127">See also</span></span>

- [<span data-ttu-id="c4163-128">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c4163-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c4163-129">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c4163-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
