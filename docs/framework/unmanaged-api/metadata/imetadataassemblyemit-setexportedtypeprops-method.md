---
description: '詳細について: IMetaDataAssemblyEmit:: SetExportedTypeProps メソッド'
title: IMetaDataAssemblyEmit::SetExportedTypeProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
ms.openlocfilehash: 61032abd7b049af29c583e9aee126184af3c78f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678108"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="f4476-103">IMetaDataAssemblyEmit::SetExportedTypeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="f4476-103">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>

<span data-ttu-id="f4476-104">指定された `ExportedType` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="f4476-104">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4476-105">構文</span><span class="sxs-lookup"><span data-stu-id="f4476-105">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4476-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f4476-106">Parameters</span></span>  

 `ct`  
 <span data-ttu-id="f4476-107">から変更するメタデータ構造を指定するメタデータトークン `ExportedType` 。</span><span class="sxs-lookup"><span data-stu-id="f4476-107">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="f4476-108">から `File` `AssemblyRef` `ExportedType` この型の実装方法を指定する、、、または型のトークン。</span><span class="sxs-lookup"><span data-stu-id="f4476-108">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="f4476-109">から `TypeDef` コードファイルで参照されるトークン。</span><span class="sxs-lookup"><span data-stu-id="f4476-109">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="f4476-110">から型の属性を指定する値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="f4476-110">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4476-111">解説</span><span class="sxs-lookup"><span data-stu-id="f4476-111">Remarks</span></span>  

 <span data-ttu-id="f4476-112">メタデータ構造を作成するには `ExportedType` 、 [IMetaDataAssemblyEmit::D efineExportedType](imetadataassemblyemit-defineexportedtype-method.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f4476-112">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4476-113">要件</span><span class="sxs-lookup"><span data-stu-id="f4476-113">Requirements</span></span>  

 <span data-ttu-id="f4476-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4476-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4476-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="f4476-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f4476-116">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="f4476-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f4476-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4476-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4476-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4476-118">See also</span></span>

- [<span data-ttu-id="f4476-119">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4476-119">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
