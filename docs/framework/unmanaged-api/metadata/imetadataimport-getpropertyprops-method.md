---
description: '詳細について: IMetaDataImport:: GetPropertyProps メソッド'
title: IMetaDataImport::GetPropertyProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
ms.openlocfilehash: 25fae4488117a35d94479ce501154679b6b536ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789178"
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="347b9-103">IMetaDataImport::GetPropertyProps メソッド</span><span class="sxs-lookup"><span data-stu-id="347b9-103">IMetaDataImport::GetPropertyProps Method</span></span>

<span data-ttu-id="347b9-104">指定したトークンによって表されるプロパティのメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="347b9-104">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="347b9-105">構文</span><span class="sxs-lookup"><span data-stu-id="347b9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,
   [out] LPCWSTR           szProperty,
   [in]  ULONG             cchProperty,
   [out] ULONG             *pchProperty,
   [out] DWORD             *pdwPropFlags,
   [out] PCCOR_SIGNATURE   *ppvSig,
   [out] ULONG             *pbSig,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,
   [out] mdMethodDef       *pmdGetter,
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,
   [out] ULONG             *pcOtherMethod
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="347b9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="347b9-106">Parameters</span></span>  

 `prop`  
 <span data-ttu-id="347b9-107">からメタデータを返すプロパティを表すトークン。</span><span class="sxs-lookup"><span data-stu-id="347b9-107">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="347b9-108">入出力プロパティを実装する型を表す TypeDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="347b9-108">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="347b9-109">入出力プロパティ名を保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="347b9-109">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="347b9-110">からのワイド文字のサイズ `szProperty` 。</span><span class="sxs-lookup"><span data-stu-id="347b9-110">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="347b9-111">入出力で返されたワイド文字の数 `szProperty` 。</span><span class="sxs-lookup"><span data-stu-id="347b9-111">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="347b9-112">入出力プロパティに適用されている属性フラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="347b9-112">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="347b9-113">この値は、 [Corpropertyattr](corpropertyattr-enumeration.md) 列挙子のビットマスクです。</span><span class="sxs-lookup"><span data-stu-id="347b9-113">This value is a bitmask from the [CorPropertyAttr](corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="347b9-114">入出力プロパティのメタデータシグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="347b9-114">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="347b9-115">入出力で返されたバイト数 `ppvSig` 。</span><span class="sxs-lookup"><span data-stu-id="347b9-115">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="347b9-116">入出力プロパティの既定値である定数の型を指定するフラグ。</span><span class="sxs-lookup"><span data-stu-id="347b9-116">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="347b9-117">この値は CorElementType 列挙子からのものです。</span><span class="sxs-lookup"><span data-stu-id="347b9-117">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="347b9-118">入出力このプロパティの既定値を格納するバイトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="347b9-118">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="347b9-119">入出力が ELEMENT_TYPE_STRING の場合は、のワイド文字のサイズ `ppDefaultValue` `pdwCPlusTypeFlag` 。それ以外の場合、この値は関係ありません。</span><span class="sxs-lookup"><span data-stu-id="347b9-119">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="347b9-120">この場合、の長さは、 `ppDefaultValue` によって指定された型から推論され `pdwCPlusTypeFlag` ます。</span><span class="sxs-lookup"><span data-stu-id="347b9-120">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="347b9-121">入出力プロパティの set アクセサーメソッドを表す MethodDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="347b9-121">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="347b9-122">入出力プロパティの get アクセサーメソッドを表す MethodDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="347b9-122">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="347b9-123">入出力プロパティに関連付けられている他のメソッドを表す MethodDef トークンの配列。</span><span class="sxs-lookup"><span data-stu-id="347b9-123">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="347b9-124">[in] `rmdOtherMethod` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="347b9-124">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="347b9-125">すべてのメソッドを保持するのに十分な大きさの配列を指定しなかった場合、警告なしにスキップされます。</span><span class="sxs-lookup"><span data-stu-id="347b9-125">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="347b9-126">入出力で返される MethodDef トークンの数 `rmdOtherMethod` 。</span><span class="sxs-lookup"><span data-stu-id="347b9-126">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="347b9-127">要件</span><span class="sxs-lookup"><span data-stu-id="347b9-127">Requirements</span></span>  

 <span data-ttu-id="347b9-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="347b9-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="347b9-129">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="347b9-129">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="347b9-130">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="347b9-130">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="347b9-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="347b9-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="347b9-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="347b9-132">See also</span></span>

- [<span data-ttu-id="347b9-133">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="347b9-133">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="347b9-134">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="347b9-134">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
