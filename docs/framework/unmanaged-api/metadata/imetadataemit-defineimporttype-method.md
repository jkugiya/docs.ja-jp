---
description: '詳細については、次を参照してください: IMetaDataEmit::D efineImportType メソッド'
title: IMetaDataEmit::DefineImportType メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportType
helpviewer_keywords:
- DefineImportType method [.NET Framework metadata]
- IMetaDataEmit::DefineImportType method [.NET Framework metadata]
ms.assetid: 37fd27af-8062-4904-ace4-51bb78ec600a
topic_type:
- apiref
ms.openlocfilehash: 7afe0fe400e4eb6e177a06e00b2d69202820804c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753433"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="de014-103">IMetaDataEmit::DefineImportType メソッド</span><span class="sxs-lookup"><span data-stu-id="de014-103">IMetaDataEmit::DefineImportType Method</span></span>

<span data-ttu-id="de014-104">現在のスコープの外部で定義されている指定した型への参照を作成し、その参照のトークンを定義します。</span><span class="sxs-lookup"><span data-stu-id="de014-104">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de014-105">構文</span><span class="sxs-lookup"><span data-stu-id="de014-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineImportType (
    [in]  IMetaDataAssemblyImport  *pAssemImport,
    [in]  const void               *pbHashValue,
    [in]  ULONG                    cbHashValue,
    [in]  IMetaDataImport          *pImport,
    [in]  mdTypeDef                tdImport,
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,
    [out] mdTypeRef                *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de014-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="de014-106">Parameters</span></span>  

 `pAssemImport`  
 <span data-ttu-id="de014-107">から対象の型のインポート元のアセンブリを表す [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="de014-107">[in] An [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="de014-108">からによって指定されたアセンブリのハッシュを格納している配列 `pAssemImport` 。</span><span class="sxs-lookup"><span data-stu-id="de014-108">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="de014-109">[in] `pbHashValue` 配列のバイト数。</span><span class="sxs-lookup"><span data-stu-id="de014-109">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="de014-110">から対象の型のインポート元のメタデータスコープを表す [IMetaDataImport](imetadataimport-interface.md) インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="de014-110">[in] An [IMetaDataImport](imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="de014-111">から `mdTypeDef` 対象の型を指定するトークンです。</span><span class="sxs-lookup"><span data-stu-id="de014-111">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="de014-112">からターゲット型がインポートされるアセンブリを表す [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="de014-112">[in] An [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="de014-113">入出力 `mdTypeRef` 型参照の現在のスコープで定義されているトークン。</span><span class="sxs-lookup"><span data-stu-id="de014-113">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de014-114">解説</span><span class="sxs-lookup"><span data-stu-id="de014-114">Remarks</span></span>  

 <span data-ttu-id="de014-115">[IMetaDataEmit::D efineImportMember](imetadataemit-defineimportmember-method.md)メソッドを呼び出す前に、メソッドを使用して、 `DefineImportType` メンバーの親クラスまたは親インターフェイスの型参照を現在のスコープ内に作成できます。</span><span class="sxs-lookup"><span data-stu-id="de014-115">Prior to calling the [IMetaDataEmit::DefineImportMember](imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de014-116">要件</span><span class="sxs-lookup"><span data-stu-id="de014-116">Requirements</span></span>  

 <span data-ttu-id="de014-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de014-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de014-118">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="de014-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="de014-119">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="de014-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de014-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de014-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de014-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="de014-121">See also</span></span>

- [<span data-ttu-id="de014-122">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="de014-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="de014-123">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="de014-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
