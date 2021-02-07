---
description: '詳細について: IMetaDataImport:: GetParamProps メソッド'
title: IMetaDataImport::GetParamProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
ms.openlocfilehash: 2c48215836dfb3ae44edc9a2bf10d4028fd82bb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728120"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="4cd00-103">IMetaDataImport::GetParamProps メソッド</span><span class="sxs-lookup"><span data-stu-id="4cd00-103">IMetaDataImport::GetParamProps Method</span></span>

<span data-ttu-id="4cd00-104">指定した ParamDef トークンによって参照されるパラメーターのメタデータ値を取得します。</span><span class="sxs-lookup"><span data-stu-id="4cd00-104">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cd00-105">構文</span><span class="sxs-lookup"><span data-stu-id="4cd00-105">Syntax</span></span>  
  
```cpp  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cd00-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4cd00-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="4cd00-107">からメタデータを返すパラメーターを表す ParamDef トークン。</span><span class="sxs-lookup"><span data-stu-id="4cd00-107">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="4cd00-108">入出力パラメーターを受け取るメソッドを表す MethodDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4cd00-108">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="4cd00-109">入出力メソッド引数リスト内のパラメーターの序数位置。</span><span class="sxs-lookup"><span data-stu-id="4cd00-109">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="4cd00-110">入出力パラメーターの名前を保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="4cd00-110">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="4cd00-111">からのワイド文字で要求されたサイズ `szName` 。</span><span class="sxs-lookup"><span data-stu-id="4cd00-111">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="4cd00-112">入出力のワイド文字で返されたサイズ `szName` 。</span><span class="sxs-lookup"><span data-stu-id="4cd00-112">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="4cd00-113">入出力パラメーターに関連付けられているすべての属性フラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4cd00-113">[out] A pointer to any attribute flags associated with the parameter.</span></span> <span data-ttu-id="4cd00-114">これは、値のビットマスクです `CorParamAttr` 。</span><span class="sxs-lookup"><span data-stu-id="4cd00-114">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="4cd00-115">入出力パラメーターがであることを示すフラグへのポインター <xref:System.ValueType> 。</span><span class="sxs-lookup"><span data-stu-id="4cd00-115">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="4cd00-116">入出力パラメーターによって返される定数文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="4cd00-116">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="4cd00-117">入出力のサイズ `ppValue` 。ワイド文字の場合は `ppValue` 。が文字列を保持しない場合は0。</span><span class="sxs-lookup"><span data-stu-id="4cd00-117">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cd00-118">解説</span><span class="sxs-lookup"><span data-stu-id="4cd00-118">Remarks</span></span>

<span data-ttu-id="4cd00-119">パラメーターの場合、のシーケンス値は `pulSequence` 1 から始まります。</span><span class="sxs-lookup"><span data-stu-id="4cd00-119">The sequence values in `pulSequence` begin with 1 for parameters.</span></span> <span data-ttu-id="4cd00-120">戻り値のシーケンス番号は0です。</span><span class="sxs-lookup"><span data-stu-id="4cd00-120">A return value has a sequence number of 0.</span></span>

## <a name="requirements"></a><span data-ttu-id="4cd00-121">要件</span><span class="sxs-lookup"><span data-stu-id="4cd00-121">Requirements</span></span>  

 <span data-ttu-id="4cd00-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4cd00-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cd00-123">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="4cd00-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4cd00-124">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4cd00-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4cd00-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cd00-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cd00-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="4cd00-126">See also</span></span>

- [<span data-ttu-id="4cd00-127">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4cd00-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="4cd00-128">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4cd00-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
