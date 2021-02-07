---
description: '詳細について: IMetaDataEmit:: SetClassLayout メソッド'
title: IMetaDataEmit::SetClassLayout メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type:
- apiref
ms.openlocfilehash: e0ce8e93137b9a32a13ca86ead539385523fa8a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706605"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="dc4cf-103">IMetaDataEmit::SetClassLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="dc4cf-103">IMetaDataEmit::SetClassLayout Method</span></span>

<span data-ttu-id="dc4cf-104">以前に呼び出した [Typedef メソッド](imetadataemit-definetypedef-method.md)の呼び出しで定義されたクラスのフィールドのレイアウトを完了します。</span><span class="sxs-lookup"><span data-stu-id="dc4cf-104">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc4cf-105">構文</span><span class="sxs-lookup"><span data-stu-id="dc4cf-105">Syntax</span></span>  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,
    [in]  DWORD               dwPackSize,
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],
    [in]  ULONG               ulClassSize
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc4cf-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dc4cf-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="dc4cf-107">から `mdTypeDef` レイアウトするクラスを指定するトークン。</span><span class="sxs-lookup"><span data-stu-id="dc4cf-107">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="dc4cf-108">からパッキングサイズは1、2、4、8、または16バイトです。</span><span class="sxs-lookup"><span data-stu-id="dc4cf-108">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="dc4cf-109">パッキングサイズは、隣接するフィールド間のバイト数です。</span><span class="sxs-lookup"><span data-stu-id="dc4cf-109">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="dc4cf-110">から [COR_FIELD_OFFSET](cor-field-offset-structure.md) 構造体の配列。各構造体は、クラスのフィールドと、クラス内のフィールドのオフセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="dc4cf-110">[in] An array of [COR_FIELD_OFFSET](cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="dc4cf-111">で配列を終了 `mdTokenNil` します。</span><span class="sxs-lookup"><span data-stu-id="dc4cf-111">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="dc4cf-112">からクラスのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="dc4cf-112">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc4cf-113">解説</span><span class="sxs-lookup"><span data-stu-id="dc4cf-113">Remarks</span></span>  

 <span data-ttu-id="dc4cf-114">クラスを最初に定義するには、 [IMetaDataEmit::D efineTypeDef](imetadataemit-definetypedef-method.md) メソッドを呼び出し、クラスのフィールドに対して3つのレイアウト (automatic、シーケンシャル、explicit) のいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="dc4cf-114">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="dc4cf-115">通常は、自動レイアウトを使用し、フィールドをレイアウトする最適な方法をランタイムが選択できるようにします。</span><span class="sxs-lookup"><span data-stu-id="dc4cf-115">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="dc4cf-116">ただし、アンマネージコードが使用する配置に従って、フィールドをレイアウトすることが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="dc4cf-116">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="dc4cf-117">この場合は、シーケンシャルまたは明示的なレイアウトを選択し、を呼び出して、 `SetClassLayout` フィールドのレイアウトを完成させます。</span><span class="sxs-lookup"><span data-stu-id="dc4cf-117">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
- <span data-ttu-id="dc4cf-118">シーケンシャルレイアウト: パッキングサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="dc4cf-118">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="dc4cf-119">フィールドは、自然サイズまたはパッキングサイズのいずれかに従って整列されます。どちらの場合も、フィールドのオフセットは小さくなります。</span><span class="sxs-lookup"><span data-stu-id="dc4cf-119">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="dc4cf-120">`rFieldOffsets`を `ulClassSize` 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="dc4cf-120">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
- <span data-ttu-id="dc4cf-121">明示的なレイアウト: 各フィールドのオフセットを指定するか、クラスのサイズとパッキングサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="dc4cf-121">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc4cf-122">要件</span><span class="sxs-lookup"><span data-stu-id="dc4cf-122">Requirements</span></span>  

 <span data-ttu-id="dc4cf-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc4cf-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc4cf-124">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="dc4cf-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dc4cf-125">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="dc4cf-125">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc4cf-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc4cf-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc4cf-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc4cf-127">See also</span></span>

- [<span data-ttu-id="dc4cf-128">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dc4cf-128">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="dc4cf-129">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dc4cf-129">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
