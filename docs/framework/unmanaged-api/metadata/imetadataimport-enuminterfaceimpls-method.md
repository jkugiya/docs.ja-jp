---
description: '詳細について: IMetaDataImport:: EnumInterfaceImpls メソッド'
title: IMetaDataImport::EnumInterfaceImpls メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
ms.openlocfilehash: 5276d1edb3be0cae76b18a06241dc6b9952e1a72
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649417"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="df71f-103">IMetaDataImport::EnumInterfaceImpls メソッド</span><span class="sxs-lookup"><span data-stu-id="df71f-103">IMetaDataImport::EnumInterfaceImpls Method</span></span>

<span data-ttu-id="df71f-104">指定したによって実装されているすべてのインターフェイスを列挙 `TypeDef` します。</span><span class="sxs-lookup"><span data-stu-id="df71f-104">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="df71f-105">構文</span><span class="sxs-lookup"><span data-stu-id="df71f-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df71f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="df71f-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="df71f-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="df71f-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="df71f-108">からインターフェイスの実装を表す MethodDef トークンを列挙する TypeDef のトークン。</span><span class="sxs-lookup"><span data-stu-id="df71f-108">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="df71f-109">入出力MethodDef トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="df71f-109">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="df71f-110">から配列の最大長 `rImpls` 。</span><span class="sxs-lookup"><span data-stu-id="df71f-110">[in] The maximum length of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="df71f-111">入出力で返されたトークンの実際の数 `rImpls` 。</span><span class="sxs-lookup"><span data-stu-id="df71f-111">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df71f-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="df71f-112">Return Value</span></span>  
  
|<span data-ttu-id="df71f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="df71f-113">HRESULT</span></span>|<span data-ttu-id="df71f-114">説明</span><span class="sxs-lookup"><span data-stu-id="df71f-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="df71f-115">`EnumInterfaceImpls` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="df71f-115">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="df71f-116">列挙する MethodDef トークンがありません。</span><span class="sxs-lookup"><span data-stu-id="df71f-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="df71f-117">この場合、 `pcImpls` は0に設定されます。</span><span class="sxs-lookup"><span data-stu-id="df71f-117">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="df71f-118">解説</span><span class="sxs-lookup"><span data-stu-id="df71f-118">Remarks</span></span>

<span data-ttu-id="df71f-119">列挙体は `mdInterfaceImpl` 、指定したによって実装された各インターフェイスのトークンのコレクションを返し `TypeDef` ます。</span><span class="sxs-lookup"><span data-stu-id="df71f-119">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="df71f-120">インターフェイストークンは、インターフェイスが指定された順序で返され `DefineTypeDef` ます (またはを使用 `SetTypeDefProps` )。</span><span class="sxs-lookup"><span data-stu-id="df71f-120">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="df71f-121">返されたトークンのプロパティは、 `mdInterfaceImpl` [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)を使用して照会できます。</span><span class="sxs-lookup"><span data-stu-id="df71f-121">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="df71f-122">要件</span><span class="sxs-lookup"><span data-stu-id="df71f-122">Requirements</span></span>  

 <span data-ttu-id="df71f-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df71f-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df71f-124">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="df71f-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="df71f-125">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="df71f-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="df71f-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df71f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df71f-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="df71f-127">See also</span></span>

- [<span data-ttu-id="df71f-128">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="df71f-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="df71f-129">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="df71f-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
