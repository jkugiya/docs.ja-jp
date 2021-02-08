---
description: '詳細について: IMetaDataImport:: GetMemberProps メソッド'
title: IMetaDataImport::GetMemberProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
ms.openlocfilehash: 073c8fae06c3df69f0b3152b109417b818637d1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783899"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="3db16-103">IMetaDataImport::GetMemberProps メソッド</span><span class="sxs-lookup"><span data-stu-id="3db16-103">IMetaDataImport::GetMemberProps Method</span></span>

<span data-ttu-id="3db16-104">指定された <xref:System.Type> メタデータトークンによって参照されるメンバーの、名前、バイナリ署名、相対仮想アドレスなど、指定されたメンバー定義のメタデータに格納されている情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="3db16-104">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="3db16-105">これは単純なヘルパーメソッドです。 *mb* が MethodDef の場合は、 **getmethodprops** が呼び出されます。 *mb* が FieldDef の場合は、 **getfieldprops** が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3db16-105">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="3db16-106">詳細については、これらの他の方法を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3db16-106">See these other methods for details.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="3db16-107">構文</span><span class="sxs-lookup"><span data-stu-id="3db16-107">Syntax</span></span>  
  
```cpp  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,
   [in]  ULONG             cchMember,
   [out] ULONG             *pchMember,
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] ULONG             *pulCodeRVA,
   [out] DWORD             *pdwImplFlags,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3db16-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3db16-108">Parameters</span></span>  

 `mb`  
 <span data-ttu-id="3db16-109">から関連付けられているメタデータを取得するメンバーを参照するトークン。</span><span class="sxs-lookup"><span data-stu-id="3db16-109">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="3db16-110">入出力メンバーのクラスを表すメタデータトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3db16-110">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="3db16-111">入出力メンバーの名前。</span><span class="sxs-lookup"><span data-stu-id="3db16-111">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="3db16-112">からバッファーのサイズ (ワイド文字単位) `szMember` 。</span><span class="sxs-lookup"><span data-stu-id="3db16-112">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="3db16-113">入出力返される名前のワイド文字単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="3db16-113">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="3db16-114">入出力メンバーに適用されるフラグ値。</span><span class="sxs-lookup"><span data-stu-id="3db16-114">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="3db16-115">入出力メンバーのバイナリメタデータシグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3db16-115">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="3db16-116">入出力のサイズ (バイト単位) `ppvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="3db16-116">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="3db16-117">入出力メンバーの相対仮想アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3db16-117">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="3db16-118">入出力メンバーに関連付けられているメソッド実装フラグ。</span><span class="sxs-lookup"><span data-stu-id="3db16-118">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="3db16-119">入出力をマークするフラグ <xref:System.ValueType> 。</span><span class="sxs-lookup"><span data-stu-id="3db16-119">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="3db16-120">値の1つです `ELEMENT_TYPE_*` 。</span><span class="sxs-lookup"><span data-stu-id="3db16-120">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="3db16-121">入出力このメンバーによって返される定数文字列値。</span><span class="sxs-lookup"><span data-stu-id="3db16-121">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="3db16-122">入出力の文字数のサイズ `ppValue` `ppValue` 。が文字列を保持しない場合は0。</span><span class="sxs-lookup"><span data-stu-id="3db16-122">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3db16-123">要件</span><span class="sxs-lookup"><span data-stu-id="3db16-123">Requirements</span></span>  

 <span data-ttu-id="3db16-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3db16-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3db16-125">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="3db16-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3db16-126">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3db16-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3db16-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3db16-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3db16-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="3db16-128">See also</span></span>

- [<span data-ttu-id="3db16-129">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3db16-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3db16-130">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3db16-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
