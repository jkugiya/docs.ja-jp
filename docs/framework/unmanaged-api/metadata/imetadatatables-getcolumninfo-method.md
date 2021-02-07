---
description: '詳細については、「IMetaDataTables:: メソッド」を参照してください。'
title: IMetaDataTables::GetColumnInfo メソッド
ms.date: 10/10/2019
api_name:
- IMetaDataTables.GetColumnInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type:
- apiref
ms.openlocfilehash: 21980567c5f9b364362f7e3ff02ee3a5e60b01ee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688235"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="c0bcf-103">IMetaDataTables::GetColumnInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="c0bcf-103">IMetaDataTables::GetColumnInfo Method</span></span>

<span data-ttu-id="c0bcf-104">指定されたテーブル内の指定された列に関するデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="c0bcf-104">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0bcf-105">構文</span><span class="sxs-lookup"><span data-stu-id="c0bcf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetColumnInfo (
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0bcf-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c0bcf-106">Parameters</span></span>

=======

 `ixTbl`  
 <span data-ttu-id="c0bcf-107">から目的のテーブルのインデックス。</span><span class="sxs-lookup"><span data-stu-id="c0bcf-107">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="c0bcf-108">から目的の列のインデックス。</span><span class="sxs-lookup"><span data-stu-id="c0bcf-108">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="c0bcf-109">入出力行内の列のオフセットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c0bcf-109">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="c0bcf-110">入出力列のサイズ (バイト単位) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c0bcf-110">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="c0bcf-111">入出力列内の値の型へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c0bcf-111">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="c0bcf-112">入出力列名へのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c0bcf-112">[out] A pointer to a pointer to the column name.</span></span>  

## <a name="remarks"></a><span data-ttu-id="c0bcf-113">解説</span><span class="sxs-lookup"><span data-stu-id="c0bcf-113">Remarks</span></span>

<span data-ttu-id="c0bcf-114">返される列の型は、値の範囲内にあります。</span><span class="sxs-lookup"><span data-stu-id="c0bcf-114">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="c0bcf-115">pType</span><span class="sxs-lookup"><span data-stu-id="c0bcf-115">pType</span></span>                    | <span data-ttu-id="c0bcf-116">説明</span><span class="sxs-lookup"><span data-stu-id="c0bcf-116">Description</span></span>   | <span data-ttu-id="c0bcf-117">ヘルパー関数</span><span class="sxs-lookup"><span data-stu-id="c0bcf-117">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="c0bcf-118">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="c0bcf-118">`0`..`iRidMax`</span></span><br><span data-ttu-id="c0bcf-119">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="c0bcf-119">(0..63)</span></span>   | <span data-ttu-id="c0bcf-120">Rid</span><span class="sxs-lookup"><span data-stu-id="c0bcf-120">Rid</span></span>           | <span data-ttu-id="c0bcf-121">**IsRidType**</span><span class="sxs-lookup"><span data-stu-id="c0bcf-121">**IsRidType**</span></span><br><span data-ttu-id="c0bcf-122">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="c0bcf-122">**IsRidOrToken**</span></span> |
| <span data-ttu-id="c0bcf-123">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="c0bcf-123">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="c0bcf-124">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="c0bcf-124">(64..95)</span></span> | <span data-ttu-id="c0bcf-125">コード化されたトークン</span><span class="sxs-lookup"><span data-stu-id="c0bcf-125">Coded token</span></span> | <span data-ttu-id="c0bcf-126">**IsCodedTokenType**</span><span class="sxs-lookup"><span data-stu-id="c0bcf-126">**IsCodedTokenType**</span></span> <br><span data-ttu-id="c0bcf-127">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="c0bcf-127">**IsRidOrToken**</span></span> |
| <span data-ttu-id="c0bcf-128">`iSHORT` (96)</span><span class="sxs-lookup"><span data-stu-id="c0bcf-128">`iSHORT` (96)</span></span>            | <span data-ttu-id="c0bcf-129">Int16</span><span class="sxs-lookup"><span data-stu-id="c0bcf-129">Int16</span></span>         | <span data-ttu-id="c0bcf-130">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="c0bcf-130">**IsFixedType**</span></span>                   |
| <span data-ttu-id="c0bcf-131">`iUSHORT` (97)</span><span class="sxs-lookup"><span data-stu-id="c0bcf-131">`iUSHORT` (97)</span></span>           | <span data-ttu-id="c0bcf-132">UInt16</span><span class="sxs-lookup"><span data-stu-id="c0bcf-132">UInt16</span></span>        | <span data-ttu-id="c0bcf-133">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="c0bcf-133">**IsFixedType**</span></span>                   |
| <span data-ttu-id="c0bcf-134">`iLONG` (98)</span><span class="sxs-lookup"><span data-stu-id="c0bcf-134">`iLONG` (98)</span></span>             | <span data-ttu-id="c0bcf-135">Int32</span><span class="sxs-lookup"><span data-stu-id="c0bcf-135">Int32</span></span>         | <span data-ttu-id="c0bcf-136">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="c0bcf-136">**IsFixedType**</span></span>                   |
| <span data-ttu-id="c0bcf-137">`iULONG` (99)</span><span class="sxs-lookup"><span data-stu-id="c0bcf-137">`iULONG` (99)</span></span>            | <span data-ttu-id="c0bcf-138">UInt32</span><span class="sxs-lookup"><span data-stu-id="c0bcf-138">UInt32</span></span>        | <span data-ttu-id="c0bcf-139">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="c0bcf-139">**IsFixedType**</span></span>                   |
| <span data-ttu-id="c0bcf-140">`iBYTE` (100)</span><span class="sxs-lookup"><span data-stu-id="c0bcf-140">`iBYTE` (100)</span></span>            | <span data-ttu-id="c0bcf-141">Byte</span><span class="sxs-lookup"><span data-stu-id="c0bcf-141">Byte</span></span>          | <span data-ttu-id="c0bcf-142">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="c0bcf-142">**IsFixedType**</span></span>                   |
| <span data-ttu-id="c0bcf-143">`iSTRING` (101)</span><span class="sxs-lookup"><span data-stu-id="c0bcf-143">`iSTRING` (101)</span></span>          | <span data-ttu-id="c0bcf-144">String</span><span class="sxs-lookup"><span data-stu-id="c0bcf-144">String</span></span>        | <span data-ttu-id="c0bcf-145">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="c0bcf-145">**IsHeapType**</span></span>                    |
| <span data-ttu-id="c0bcf-146">`iGUID` (102)</span><span class="sxs-lookup"><span data-stu-id="c0bcf-146">`iGUID` (102)</span></span>            | <span data-ttu-id="c0bcf-147">Guid</span><span class="sxs-lookup"><span data-stu-id="c0bcf-147">Guid</span></span>          | <span data-ttu-id="c0bcf-148">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="c0bcf-148">**IsHeapType**</span></span>                    |
| <span data-ttu-id="c0bcf-149">`iBLOB` (103)</span><span class="sxs-lookup"><span data-stu-id="c0bcf-149">`iBLOB` (103)</span></span>            | <span data-ttu-id="c0bcf-150">BLOB</span><span class="sxs-lookup"><span data-stu-id="c0bcf-150">Blob</span></span>          | <span data-ttu-id="c0bcf-151">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="c0bcf-151">**IsHeapType**</span></span>                    |

<span data-ttu-id="c0bcf-152">*ヒープ* に格納されている値 (つまり、 `IsHeapType == true` ) は次を使用して読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="c0bcf-152">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="c0bcf-153">`iSTRING`: **Imetadatatables**</span><span class="sxs-lookup"><span data-stu-id="c0bcf-153">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="c0bcf-154">`iGUID`: **Imetadatatables 実行できます。 GetGUID**</span><span class="sxs-lookup"><span data-stu-id="c0bcf-154">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="c0bcf-155">`iBLOB`: **Imetadatatables 実行できます。 GetBlob**</span><span class="sxs-lookup"><span data-stu-id="c0bcf-155">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c0bcf-156">上の表で定義されている定数を使用するには、 `#define _DEFINE_META_DATA_META_CONSTANTS` *cor* ヘッダーファイルによって提供されるディレクティブをインクルードします。</span><span class="sxs-lookup"><span data-stu-id="c0bcf-156">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="c0bcf-157">要件</span><span class="sxs-lookup"><span data-stu-id="c0bcf-157">Requirements</span></span>  

 <span data-ttu-id="c0bcf-158">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0bcf-158">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0bcf-159">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="c0bcf-159">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c0bcf-160">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="c0bcf-160">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c0bcf-161">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0bcf-161">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0bcf-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0bcf-162">See also</span></span>

- [<span data-ttu-id="c0bcf-163">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c0bcf-163">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="c0bcf-164">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c0bcf-164">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
