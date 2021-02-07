---
description: '詳細について: IMetaDataImport:: FindTypeRef メソッド'
title: IMetaDataImport::FindTypeRef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type:
- apiref
ms.openlocfilehash: 11e966256b5e75c1acff0bf1e6de0c96dc03e6aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745568"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="17e51-103">IMetaDataImport::FindTypeRef メソッド</span><span class="sxs-lookup"><span data-stu-id="17e51-103">IMetaDataImport::FindTypeRef Method</span></span>

<span data-ttu-id="17e51-104">指定したスコープ内にあり、指定した名前を持つ参照の TypeRef トークンへのポインターを取得し <xref:System.Type> ます。</span><span class="sxs-lookup"><span data-stu-id="17e51-104">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17e51-105">構文</span><span class="sxs-lookup"><span data-stu-id="17e51-105">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17e51-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="17e51-106">Parameters</span></span>  

 `tkResolutionScope`  
 <span data-ttu-id="17e51-107">から型参照が定義されているモジュール、アセンブリ、または型をそれぞれ指定する ModuleRef、AssemblyRef、または TypeRef トークン。</span><span class="sxs-lookup"><span data-stu-id="17e51-107">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="17e51-108">から検索する型参照の名前。</span><span class="sxs-lookup"><span data-stu-id="17e51-108">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="17e51-109">入出力一致する TypeRef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="17e51-109">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17e51-110">要件</span><span class="sxs-lookup"><span data-stu-id="17e51-110">Requirements</span></span>  

 <span data-ttu-id="17e51-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17e51-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17e51-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="17e51-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="17e51-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="17e51-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="17e51-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17e51-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17e51-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="17e51-115">See also</span></span>

- [<span data-ttu-id="17e51-116">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17e51-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="17e51-117">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17e51-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
