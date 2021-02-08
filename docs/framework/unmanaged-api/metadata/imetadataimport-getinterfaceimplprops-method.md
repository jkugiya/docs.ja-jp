---
description: '詳細について: IMetaDataImport:: GetInterfaceImplProps メソッド'
title: IMetaDataImport::GetInterfaceImplProps メソッド
ms.date: 02/25/2019
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
ms.openlocfilehash: 6b3c9394bcf37f700c84e1fda0b785dc0c3f4713
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783912"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="fe284-103">IMetaDataImport::GetInterfaceImplProps メソッド</span><span class="sxs-lookup"><span data-stu-id="fe284-103">IMetaDataImport::GetInterfaceImplProps Method</span></span>

<span data-ttu-id="fe284-104">指定したメソッドを実装するのメタデータトークンへのポインター <xref:System.Type> と、そのメソッドを宣言するインターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="fe284-104">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="fe284-105">構文</span><span class="sxs-lookup"><span data-stu-id="fe284-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe284-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fe284-106">Parameters</span></span>  

 `iiImpl`  
 <span data-ttu-id="fe284-107">からクラスとインターフェイストークンを返すメソッドを表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="fe284-107">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="fe284-108">入出力メソッドを実装するクラスを表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="fe284-108">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="fe284-109">入出力実装されたメソッドを定義するインターフェイスを表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="fe284-109">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="fe284-110">解説</span><span class="sxs-lookup"><span data-stu-id="fe284-110">Remarks</span></span>

 <span data-ttu-id="fe284-111">の値を取得する `iImpl` には、 [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="fe284-111">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>

 <span data-ttu-id="fe284-112">たとえば、クラスの `mdTypeDef` トークン値が0x02000007 で、型がトークンを持つ3つのインターフェイスを実装しているとします。</span><span class="sxs-lookup"><span data-stu-id="fe284-112">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span>

- <span data-ttu-id="fe284-113">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="fe284-113">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="fe284-114">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="fe284-114">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="fe284-115">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="fe284-115">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="fe284-116">概念的には、この情報は次のようにインターフェイス実装テーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="fe284-116">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="fe284-117">行番号</span><span class="sxs-lookup"><span data-stu-id="fe284-117">Row number</span></span> | <span data-ttu-id="fe284-118">クラストークン</span><span class="sxs-lookup"><span data-stu-id="fe284-118">Class token</span></span> | <span data-ttu-id="fe284-119">インターフェイストークン</span><span class="sxs-lookup"><span data-stu-id="fe284-119">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="fe284-120">4</span><span class="sxs-lookup"><span data-stu-id="fe284-120">4</span></span>          |             |                 |
| <span data-ttu-id="fe284-121">5</span><span class="sxs-lookup"><span data-stu-id="fe284-121">5</span></span>          | <span data-ttu-id="fe284-122">02000007</span><span class="sxs-lookup"><span data-stu-id="fe284-122">02000007</span></span>    | <span data-ttu-id="fe284-123">02000003</span><span class="sxs-lookup"><span data-stu-id="fe284-123">02000003</span></span>        |
| <span data-ttu-id="fe284-124">6</span><span class="sxs-lookup"><span data-stu-id="fe284-124">6</span></span>          | <span data-ttu-id="fe284-125">02000007</span><span class="sxs-lookup"><span data-stu-id="fe284-125">02000007</span></span>    | <span data-ttu-id="fe284-126">0100000A</span><span class="sxs-lookup"><span data-stu-id="fe284-126">0100000A</span></span>        |
| <span data-ttu-id="fe284-127">7</span><span class="sxs-lookup"><span data-stu-id="fe284-127">7</span></span>          |             |                 |
| <span data-ttu-id="fe284-128">8</span><span class="sxs-lookup"><span data-stu-id="fe284-128">8</span></span>          | <span data-ttu-id="fe284-129">02000007</span><span class="sxs-lookup"><span data-stu-id="fe284-129">02000007</span></span>    | <span data-ttu-id="fe284-130">0200001C</span><span class="sxs-lookup"><span data-stu-id="fe284-130">0200001C</span></span>        |

<span data-ttu-id="fe284-131">これは、トークンが4バイトの値であることを思い出してください。</span><span class="sxs-lookup"><span data-stu-id="fe284-131">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="fe284-132">下位3バイトは、行番号 (RID) を保持します。</span><span class="sxs-lookup"><span data-stu-id="fe284-132">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="fe284-133">上位バイトは、のトークンの種類 (0x09) を保持し `mdtInterfaceImpl` ます。</span><span class="sxs-lookup"><span data-stu-id="fe284-133">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="fe284-134">`GetInterfaceImplProps` 引数で指定したトークンを持つ行に保持されている情報を返し `iImpl` ます。</span><span class="sxs-lookup"><span data-stu-id="fe284-134">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="fe284-135">要件</span><span class="sxs-lookup"><span data-stu-id="fe284-135">Requirements</span></span>  

 <span data-ttu-id="fe284-136">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe284-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe284-137">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="fe284-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fe284-138">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="fe284-138">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fe284-139">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe284-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe284-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe284-140">See also</span></span>

- [<span data-ttu-id="fe284-141">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe284-141">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="fe284-142">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe284-142">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
