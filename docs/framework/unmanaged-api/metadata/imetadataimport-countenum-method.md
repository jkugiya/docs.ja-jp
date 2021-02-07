---
description: '詳細について: IMetaDataImport:: CountEnum メソッド'
title: IMetaDataImport::CountEnum メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CountEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type:
- apiref
ms.openlocfilehash: c579ef7ce440e3552ab28572fc6c96ad12d66400
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677692"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="4d6ed-103">IMetaDataImport::CountEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="4d6ed-103">IMetaDataImport::CountEnum Method</span></span>

<span data-ttu-id="4d6ed-104">指定した列挙子によって取得された列挙体の要素の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="4d6ed-104">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d6ed-105">構文</span><span class="sxs-lookup"><span data-stu-id="4d6ed-105">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d6ed-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4d6ed-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="4d6ed-107">から列挙子のハンドルです。</span><span class="sxs-lookup"><span data-stu-id="4d6ed-107">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="4d6ed-108">入出力列挙された要素の数。</span><span class="sxs-lookup"><span data-stu-id="4d6ed-108">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d6ed-109">解説</span><span class="sxs-lookup"><span data-stu-id="4d6ed-109">Remarks</span></span>  

 <span data-ttu-id="4d6ed-110">によって指定されたハンドル `hEnum` は、前 `Enum` の *名前* の呼び出し (たとえば、 [IMetaDataImport:: enumtypedefs](imetadataimport-enumtypedefs-method.md)) から取得されます。</span><span class="sxs-lookup"><span data-stu-id="4d6ed-110">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d6ed-111">要件</span><span class="sxs-lookup"><span data-stu-id="4d6ed-111">Requirements</span></span>  

 <span data-ttu-id="4d6ed-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d6ed-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d6ed-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="4d6ed-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4d6ed-114">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4d6ed-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4d6ed-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d6ed-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d6ed-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d6ed-116">See also</span></span>

- [<span data-ttu-id="4d6ed-117">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4d6ed-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="4d6ed-118">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4d6ed-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
