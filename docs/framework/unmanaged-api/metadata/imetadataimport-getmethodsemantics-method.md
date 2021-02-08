---
description: '詳細について: IMetaDataImport:: GetMethodSemantics メソッド'
title: IMetaDataImport::GetMethodSemantics メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type:
- apiref
ms.openlocfilehash: 2b17e2ffaeef3a451850ce2cc9c4861d68df3a81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783860"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="b7ae3-103">IMetaDataImport::GetMethodSemantics メソッド</span><span class="sxs-lookup"><span data-stu-id="b7ae3-103">IMetaDataImport::GetMethodSemantics Method</span></span>

<span data-ttu-id="b7ae3-104">指定した MethodDef トークンによって参照されるメソッドと、指定した EventProp トークンによって参照されるペアのプロパティおよびイベントの間のリレーションシップを示すフラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="b7ae3-104">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7ae3-105">構文</span><span class="sxs-lookup"><span data-stu-id="b7ae3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7ae3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b7ae3-106">Parameters</span></span>  

 `mb`  
 <span data-ttu-id="b7ae3-107">からセマンティックロール情報を取得するメソッドを表す MethodDef トークン。</span><span class="sxs-lookup"><span data-stu-id="b7ae3-107">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="b7ae3-108">からメソッドのロールを取得するための、ペアのプロパティとイベントを表すトークン。</span><span class="sxs-lookup"><span data-stu-id="b7ae3-108">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="b7ae3-109">入出力関連付けられているセマンティクスフラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b7ae3-109">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="b7ae3-110">この値は、 [CorMethodSemanticsAttr](cormethodsemanticsattr-enumeration.md) 列挙体のビットマスクです。</span><span class="sxs-lookup"><span data-stu-id="b7ae3-110">This value is a bitmask from the [CorMethodSemanticsAttr](cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7ae3-111">解説</span><span class="sxs-lookup"><span data-stu-id="b7ae3-111">Remarks</span></span>  

 <span data-ttu-id="b7ae3-112">[IMetaDataEmit::D efineProperty](imetadataemit-defineproperty-method.md)メソッドは、メソッドのセマンティクスフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="b7ae3-112">The [IMetaDataEmit::DefineProperty](imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7ae3-113">要件</span><span class="sxs-lookup"><span data-stu-id="b7ae3-113">Requirements</span></span>  

 <span data-ttu-id="b7ae3-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7ae3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7ae3-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="b7ae3-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b7ae3-116">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b7ae3-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b7ae3-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7ae3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7ae3-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7ae3-118">See also</span></span>

- [<span data-ttu-id="b7ae3-119">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7ae3-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b7ae3-120">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7ae3-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
