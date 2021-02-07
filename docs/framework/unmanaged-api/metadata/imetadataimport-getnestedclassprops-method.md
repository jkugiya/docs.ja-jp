---
description: '詳細について: IMetaDataImport:: GetNestedClassProps メソッド'
title: IMetaDataImport::GetNestedClassProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNestedClassProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNestedClassProps
helpviewer_keywords:
- GetNestedClassProps method [.NET Framework metadata]
- IMetaDataImport::GetNestedClassProps method [.NET Framework metadata]
ms.assetid: 704d19f1-bdef-4745-af8c-6476eb246fb3
topic_type:
- apiref
ms.openlocfilehash: 5fd812bf9b7725d520b14284db400bb50e82c25b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677537"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="3bc44-103">IMetaDataImport::GetNestedClassProps メソッド</span><span class="sxs-lookup"><span data-stu-id="3bc44-103">IMetaDataImport::GetNestedClassProps Method</span></span>

<span data-ttu-id="3bc44-104"><xref:System.Type>指定した入れ子にされた型の親の TypeDef トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="3bc44-104">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bc44-105">構文</span><span class="sxs-lookup"><span data-stu-id="3bc44-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bc44-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3bc44-106">Parameters</span></span>  

 `tdNestedClass`  
 <span data-ttu-id="3bc44-107">から親クラストークンを返すを表す TypeDef トークン <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="3bc44-107">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="3bc44-108">入出力で入れ子になっているの TypeDef トークンへのポインター <xref:System.Type> `tdNestedClass` 。</span><span class="sxs-lookup"><span data-stu-id="3bc44-108">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bc44-109">要件</span><span class="sxs-lookup"><span data-stu-id="3bc44-109">Requirements</span></span>  

 <span data-ttu-id="3bc44-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bc44-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bc44-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="3bc44-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3bc44-112">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3bc44-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3bc44-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bc44-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bc44-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="3bc44-114">See also</span></span>

- [<span data-ttu-id="3bc44-115">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3bc44-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3bc44-116">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3bc44-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
