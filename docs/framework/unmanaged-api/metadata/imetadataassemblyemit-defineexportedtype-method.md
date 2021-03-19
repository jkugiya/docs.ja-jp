---
description: '詳細について: IMetaDataAssemblyEmit::D efineExportedType メソッド'
title: IMetaDataAssemblyEmit::DefineExportedType メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
ms.openlocfilehash: 0da1b1eb0880b0ba9df0ba9ad70b460163dffc39
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671114"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="c4768-103">IMetaDataAssemblyEmit::DefineExportedType メソッド</span><span class="sxs-lookup"><span data-stu-id="c4768-103">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>

<span data-ttu-id="c4768-104">指定してエクスポートした型のメタデータが含まれる `ExportedType` 構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="c4768-104">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4768-105">構文</span><span class="sxs-lookup"><span data-stu-id="c4768-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4768-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c4768-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="c4768-107">からエクスポートする型の名前。</span><span class="sxs-lookup"><span data-stu-id="c4768-107">[in] The name of type to be exported.</span></span> <span data-ttu-id="c4768-108">共通言語ランタイムのバージョン1.1 では、エクスポートされた型の名前が、型ので指定された名前と完全に一致している必要があり `TypeDef` ます。</span><span class="sxs-lookup"><span data-stu-id="c4768-108">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="c4768-109">からエクスポートされた型を実装する場所を指定するトークン。</span><span class="sxs-lookup"><span data-stu-id="c4768-109">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="c4768-110">有効な値とそれに関連付けられている意味は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c4768-110">The valid values and their associated meanings are:</span></span>  
  
- <span data-ttu-id="c4768-111">`mdFile` この型は、このアセンブリ内の別のファイルに実装されています。</span><span class="sxs-lookup"><span data-stu-id="c4768-111">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
- <span data-ttu-id="c4768-112">`mdAssemblyRef` 型が別のアセンブリに実装されています。</span><span class="sxs-lookup"><span data-stu-id="c4768-112">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
- <span data-ttu-id="c4768-113">`mdExportedTYpe` 型が他の型の中で入れ子になっています。</span><span class="sxs-lookup"><span data-stu-id="c4768-113">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
- <span data-ttu-id="c4768-114">`mdFileNil` この型はマニフェストと同じファイル内にあり、入れ子にされた型ではありません。</span><span class="sxs-lookup"><span data-stu-id="c4768-114">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="c4768-115">からエクスポートする型を指定するメタデータのトークン。</span><span class="sxs-lookup"><span data-stu-id="c4768-115">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="c4768-116">この値は、型を実装するファイルのテーブルに入力され、 `TypeDef` そのファイルがこのアセンブリ内にある場合にのみ関連します。</span><span class="sxs-lookup"><span data-stu-id="c4768-116">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="c4768-117">からエクスポートされた型のプロパティ設定を定義する [Cortypeattr](cortypeattr-enumeration.md) 列挙値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="c4768-117">[in] A bitwise combination of [CorTypeAttr](cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="c4768-118">入出力エクスポートされた型を示す、返されたメタデータトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c4768-118">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4768-119">解説</span><span class="sxs-lookup"><span data-stu-id="c4768-119">Remarks</span></span>  

 <span data-ttu-id="c4768-120">`ExportedType`このアセンブリによって公開され、マニフェストを含むモジュール以外のモジュールで実装される型ごとに、メタデータ構造を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4768-120">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4768-121">要件</span><span class="sxs-lookup"><span data-stu-id="c4768-121">Requirements</span></span>  

 <span data-ttu-id="c4768-122">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4768-122">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4768-123">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="c4768-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c4768-124">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4768-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c4768-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4768-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4768-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4768-126">See also</span></span>

- [<span data-ttu-id="c4768-127">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c4768-127">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
