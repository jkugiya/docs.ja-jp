---
description: '詳細について: IMetaDataImport:: EnumMemberRefs メソッド'
title: IMetaDataImport::EnumMemberRefs メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMemberRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMemberRefs
helpviewer_keywords:
- EnumMemberRefs method [.NET Framework metadata]
- IMetaDataImport::EnumMemberRefs method [.NET Framework metadata]
ms.assetid: e97c97a6-6e4f-41f5-9af1-9b3cf3bdbd6b
topic_type:
- apiref
ms.openlocfilehash: 0c9b10342f73ae5b604ac25b6ff8ccec58deb5ab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670945"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="9b7db-103">IMetaDataImport::EnumMemberRefs メソッド</span><span class="sxs-lookup"><span data-stu-id="9b7db-103">IMetaDataImport::EnumMemberRefs Method</span></span>

<span data-ttu-id="9b7db-104">指定した型のメンバーを表す MemberRef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="9b7db-104">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b7db-105">構文</span><span class="sxs-lookup"><span data-stu-id="9b7db-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,
   [in]   mdToken        tkParent,
   [out]  mdMemberRef    rMemberRefs[],
   [in]   ULONG          cMax,
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b7db-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9b7db-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="9b7db-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9b7db-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="9b7db-108">からメンバーを列挙する型の TypeDef、TypeRef、MethodDef、または ModuleRef トークン。</span><span class="sxs-lookup"><span data-stu-id="9b7db-108">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="9b7db-109">入出力MemberRef トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="9b7db-109">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9b7db-110">[in] `rMemberRefs` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="9b7db-110">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="9b7db-111">入出力で返された MemberRef トークンの実際の数 `rMemberRefs` 。</span><span class="sxs-lookup"><span data-stu-id="9b7db-111">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b7db-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="9b7db-112">Return Value</span></span>  
  
|<span data-ttu-id="9b7db-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9b7db-113">HRESULT</span></span>|<span data-ttu-id="9b7db-114">説明</span><span class="sxs-lookup"><span data-stu-id="9b7db-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9b7db-115">`EnumMemberRefs` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="9b7db-115">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9b7db-116">列挙する MemberRef トークンがありません。</span><span class="sxs-lookup"><span data-stu-id="9b7db-116">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="9b7db-117">この場合、 `pcTokens` はゼロになります。</span><span class="sxs-lookup"><span data-stu-id="9b7db-117">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9b7db-118">要件</span><span class="sxs-lookup"><span data-stu-id="9b7db-118">Requirements</span></span>  

 <span data-ttu-id="9b7db-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b7db-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b7db-120">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="9b7db-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9b7db-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9b7db-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9b7db-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b7db-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b7db-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b7db-123">See also</span></span>

- [<span data-ttu-id="9b7db-124">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b7db-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="9b7db-125">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b7db-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
