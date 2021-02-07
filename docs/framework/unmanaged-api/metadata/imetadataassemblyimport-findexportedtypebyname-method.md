---
description: '詳細について: IMetaDataAssemblyImport:: FindExportedTypeByName メソッド'
title: IMetaDataAssemblyImport::FindExportedTypeByName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindExportedTypeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindExportedTypeByName
helpviewer_keywords:
- FindExportedTypeByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindExportedTypeByName method [.NET Framework metadata]
ms.assetid: 46264b2c-574d-4dde-aafc-77187a104fdd
topic_type:
- apiref
ms.openlocfilehash: 4a2dc2b65b7f7fe6d5f2e120c635214d457991bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677991"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="dedc0-103">IMetaDataAssemblyImport::FindExportedTypeByName メソッド</span><span class="sxs-lookup"><span data-stu-id="dedc0-103">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>

<span data-ttu-id="dedc0-104">名前と外側の型を指定して、エクスポートされた型へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="dedc0-104">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dedc0-105">構文</span><span class="sxs-lookup"><span data-stu-id="dedc0-105">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dedc0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dedc0-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="dedc0-107">からエクスポートされた型の名前。</span><span class="sxs-lookup"><span data-stu-id="dedc0-107">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="dedc0-108">からエクスポートする型の外側のクラスのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="dedc0-108">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="dedc0-109">要求されたエクスポート型が入れ子にされた型では `mdExportedTypeNil` ない場合、この値はです。</span><span class="sxs-lookup"><span data-stu-id="dedc0-109">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="dedc0-110">入出力エクスポートされた `mdExportedType` 型を表すトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dedc0-110">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dedc0-111">解説</span><span class="sxs-lookup"><span data-stu-id="dedc0-111">Remarks</span></span>  

 <span data-ttu-id="dedc0-112">メソッドは、 `FindExportedTypeByName` 参照を解決するために共通言語ランタイムによって採用されている標準の規則を使用します。</span><span class="sxs-lookup"><span data-stu-id="dedc0-112">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dedc0-113">要件</span><span class="sxs-lookup"><span data-stu-id="dedc0-113">Requirements</span></span>  

 <span data-ttu-id="dedc0-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dedc0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dedc0-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="dedc0-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dedc0-116">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="dedc0-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dedc0-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dedc0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dedc0-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="dedc0-118">See also</span></span>

- [<span data-ttu-id="dedc0-119">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dedc0-119">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="dedc0-120">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="dedc0-120">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
