---
description: '詳細について: IMetaDataImport:: GetClassLayout メソッド'
title: IMetaDataImport::GetClassLayout メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
ms.openlocfilehash: 74a3170e40a7f857b9150f2d0048af3eac0f2cbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745425"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="7f7a5-103">IMetaDataImport::GetClassLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="7f7a5-103">IMetaDataImport::GetClassLayout Method</span></span>

<span data-ttu-id="7f7a5-104">指定した TypeDef トークンによって参照されるクラスのレイアウト情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="7f7a5-104">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f7a5-105">構文</span><span class="sxs-lookup"><span data-stu-id="7f7a5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout  (
   [in]  mdTypeDef          td,
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f7a5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7f7a5-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="7f7a5-107">から返されるレイアウトを持つクラスの TypeDef トークン。</span><span class="sxs-lookup"><span data-stu-id="7f7a5-107">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="7f7a5-108">入出力クラスのパックサイズを表す1、2、4、8、または16のいずれかの値。</span><span class="sxs-lookup"><span data-stu-id="7f7a5-108">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="7f7a5-109">入出力 [COR_FIELD_OFFSET](cor-field-offset-structure.md) 値の配列。</span><span class="sxs-lookup"><span data-stu-id="7f7a5-109">[out] An array of [COR_FIELD_OFFSET](cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7f7a5-110">[in] `rFieldOffset` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="7f7a5-110">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="7f7a5-111">入出力で返される要素の数 `rFieldOffset` 。</span><span class="sxs-lookup"><span data-stu-id="7f7a5-111">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="7f7a5-112">入出力によって表されるクラスのサイズ (バイト単位) `td` 。</span><span class="sxs-lookup"><span data-stu-id="7f7a5-112">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f7a5-113">要件</span><span class="sxs-lookup"><span data-stu-id="7f7a5-113">Requirements</span></span>  

 <span data-ttu-id="7f7a5-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f7a5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f7a5-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="7f7a5-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f7a5-116">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="7f7a5-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7f7a5-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f7a5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f7a5-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f7a5-118">See also</span></span>

- [<span data-ttu-id="7f7a5-119">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7f7a5-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="7f7a5-120">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7f7a5-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
