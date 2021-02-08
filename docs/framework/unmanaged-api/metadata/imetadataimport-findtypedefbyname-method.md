---
description: '詳細について: IMetaDataImport:: FindTypeDefByName メソッド'
title: IMetaDataImport::FindTypeDefByName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeDefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type:
- apiref
ms.openlocfilehash: 083f786cc03b83cda54497937e376baa4a2cbee3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789230"
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="ecbf8-103">IMetaDataImport::FindTypeDefByName メソッド</span><span class="sxs-lookup"><span data-stu-id="ecbf8-103">IMetaDataImport::FindTypeDefByName Method</span></span>

<span data-ttu-id="ecbf8-104">指定した名前を持つの TypeDef メタデータトークンへのポインターを取得し <xref:System.Type> ます。</span><span class="sxs-lookup"><span data-stu-id="ecbf8-104">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecbf8-105">構文</span><span class="sxs-lookup"><span data-stu-id="ecbf8-105">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecbf8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ecbf8-106">Parameters</span></span>  

 `szTypeDef`  
 <span data-ttu-id="ecbf8-107">からTypeDef トークンを取得する型の名前。</span><span class="sxs-lookup"><span data-stu-id="ecbf8-107">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="ecbf8-108">から外側のクラスを表す TypeDef または TypeRef トークン。</span><span class="sxs-lookup"><span data-stu-id="ecbf8-108">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="ecbf8-109">検索する型が入れ子になったクラスでない場合は、この値を NULL に設定します。</span><span class="sxs-lookup"><span data-stu-id="ecbf8-109">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="ecbf8-110">入出力一致する TypeDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ecbf8-110">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecbf8-111">要件</span><span class="sxs-lookup"><span data-stu-id="ecbf8-111">Requirements</span></span>  

 <span data-ttu-id="ecbf8-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ecbf8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecbf8-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="ecbf8-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ecbf8-114">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ecbf8-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ecbf8-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecbf8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecbf8-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="ecbf8-116">See also</span></span>

- [<span data-ttu-id="ecbf8-117">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ecbf8-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ecbf8-118">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ecbf8-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
