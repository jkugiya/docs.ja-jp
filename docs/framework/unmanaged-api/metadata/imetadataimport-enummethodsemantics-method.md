---
description: '詳細について: IMetaDataImport:: EnumMethodSemantics メソッド'
title: IMetaDataImport::EnumMethodSemantics メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type:
- apiref
ms.openlocfilehash: 9819afb2d7974e9f705c6ff665d3414eade0ab90
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728251"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="1feb0-103">IMetaDataImport::EnumMethodSemantics メソッド</span><span class="sxs-lookup"><span data-stu-id="1feb0-103">IMetaDataImport::EnumMethodSemantics Method</span></span>

<span data-ttu-id="1feb0-104">指定したメソッドが関連付けられているプロパティおよびプロパティ変更イベントを列挙します。</span><span class="sxs-lookup"><span data-stu-id="1feb0-104">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1feb0-105">構文</span><span class="sxs-lookup"><span data-stu-id="1feb0-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1feb0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1feb0-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="1feb0-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1feb0-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="1feb0-108">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1feb0-108">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="1feb0-109">から列挙型のスコープを制限する MethodDef トークン。</span><span class="sxs-lookup"><span data-stu-id="1feb0-109">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="1feb0-110">入出力イベントまたはプロパティを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="1feb0-110">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1feb0-111">[in] `rEventProp` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="1feb0-111">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="1feb0-112">入出力で返されたイベントまたはプロパティの数 `rEventProp` 。</span><span class="sxs-lookup"><span data-stu-id="1feb0-112">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1feb0-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="1feb0-113">Return Value</span></span>  
  
|<span data-ttu-id="1feb0-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1feb0-114">HRESULT</span></span>|<span data-ttu-id="1feb0-115">説明</span><span class="sxs-lookup"><span data-stu-id="1feb0-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1feb0-116">`EnumMethodSemantics` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="1feb0-116">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1feb0-117">列挙するイベントやプロパティはありません。</span><span class="sxs-lookup"><span data-stu-id="1feb0-117">There are no events or properties to enumerate.</span></span> <span data-ttu-id="1feb0-118">この場合、 `pcEventProp` は0になります。</span><span class="sxs-lookup"><span data-stu-id="1feb0-118">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1feb0-119">解説</span><span class="sxs-lookup"><span data-stu-id="1feb0-119">Remarks</span></span>  

 <span data-ttu-id="1feb0-120">多くの共通言語ランタイム型 `Changed` では、プロパティイベントとプロパティ `On`  `Changed` に関連するプロパティメソッドが定義されています。</span><span class="sxs-lookup"><span data-stu-id="1feb0-120">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="1feb0-121">たとえば、型は、 <xref:System.Windows.Forms.Control?displayProperty=nameWithType> <xref:System.Windows.Forms.Control.Font%2A> プロパティ、 <xref:System.Windows.Forms.Control.FontChanged> イベント、およびメソッドを定義し <xref:System.Windows.Forms.Control.OnFontChanged%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="1feb0-121">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="1feb0-122">プロパティの set アクセサーメソッドは、メソッドを呼び出します。このメソッドは、 <xref:System.Windows.Forms.Control.Font%2A> イベントを発生さ <xref:System.Windows.Forms.Control.OnFontChanged%2A> せ <xref:System.Windows.Forms.Control.FontChanged> ます。</span><span class="sxs-lookup"><span data-stu-id="1feb0-122">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="1feb0-123">`EnumMethodSemantics` <xref:System.Windows.Forms.Control.OnFontChanged%2A> プロパティとイベントへの参照を取得するには、の MethodDef を使用してを呼び出し <xref:System.Windows.Forms.Control.Font%2A> <xref:System.Windows.Forms.Control.FontChanged> ます。</span><span class="sxs-lookup"><span data-stu-id="1feb0-123">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1feb0-124">要件</span><span class="sxs-lookup"><span data-stu-id="1feb0-124">Requirements</span></span>  

 <span data-ttu-id="1feb0-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1feb0-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1feb0-126">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="1feb0-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1feb0-127">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="1feb0-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1feb0-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1feb0-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1feb0-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="1feb0-129">See also</span></span>

- [<span data-ttu-id="1feb0-130">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1feb0-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="1feb0-131">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1feb0-131">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
