---
description: '詳細について: IMetaDataAssemblyEmit:: SetManifestResourceProps メソッド'
title: IMetaDataAssemblyEmit::SetManifestResourceProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type:
- apiref
ms.openlocfilehash: 0d5022c4acc562f9e77cec4ba080815db410862b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721025"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="50997-103">IMetaDataAssemblyEmit::SetManifestResourceProps メソッド</span><span class="sxs-lookup"><span data-stu-id="50997-103">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>

<span data-ttu-id="50997-104">指定された `ManifestResource` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="50997-104">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50997-105">構文</span><span class="sxs-lookup"><span data-stu-id="50997-105">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50997-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50997-106">Parameters</span></span>  

 `mr`  
 <span data-ttu-id="50997-107">から `ManifestResource` 変更するメタデータ構造を指定するトークン。</span><span class="sxs-lookup"><span data-stu-id="50997-107">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="50997-108">から `File` リソースプロバイダーにマップされる型またはのトークン `AssemblyRef` 。</span><span class="sxs-lookup"><span data-stu-id="50997-108">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="50997-109">からファイル内のリソースの先頭へのオフセット。</span><span class="sxs-lookup"><span data-stu-id="50997-109">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="50997-110">からリソースの属性を指定するフラグ値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="50997-110">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50997-111">解説</span><span class="sxs-lookup"><span data-stu-id="50997-111">Remarks</span></span>  

 <span data-ttu-id="50997-112">メタデータ構造を作成するには `ManifestResource` 、 [IMetaDataAssemblyEmit::D efinemanifestresource](imetadataassemblyemit-definemanifestresource-method.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="50997-112">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50997-113">要件</span><span class="sxs-lookup"><span data-stu-id="50997-113">Requirements</span></span>  

 <span data-ttu-id="50997-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50997-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50997-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="50997-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="50997-116">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="50997-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="50997-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50997-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50997-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="50997-118">See also</span></span>

- [<span data-ttu-id="50997-119">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="50997-119">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
