---
description: '詳細については、次を参照してください: IMetaDataTables 許容:: GetColumn メソッド'
title: IMetaDataTables::GetColumn メソッド
ms.date: 02/25/2019
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
ms.openlocfilehash: 4c4cec7216f93783b34b594330358d1e6036ed40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688274"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="846ff-103">IMetaDataTables::GetColumn メソッド</span><span class="sxs-lookup"><span data-stu-id="846ff-103">IMetaDataTables::GetColumn Method</span></span>

<span data-ttu-id="846ff-104">指定したテーブル内の指定した列および行のセルに格納されている値へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="846ff-104">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="846ff-105">構文</span><span class="sxs-lookup"><span data-stu-id="846ff-105">Syntax</span></span>  
  
```cpp  
HRESULT GetColumn (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="846ff-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="846ff-106">Parameters</span></span>

 `ixTbl`  
 <span data-ttu-id="846ff-107">からテーブルのインデックス。</span><span class="sxs-lookup"><span data-stu-id="846ff-107">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="846ff-108">からテーブル内の列のインデックス。</span><span class="sxs-lookup"><span data-stu-id="846ff-108">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="846ff-109">からテーブル内の行のインデックス。</span><span class="sxs-lookup"><span data-stu-id="846ff-109">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="846ff-110">入出力セル内の値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="846ff-110">[out] A pointer to the value in the cell.</span></span>  

## <a name="remarks"></a><span data-ttu-id="846ff-111">解説</span><span class="sxs-lookup"><span data-stu-id="846ff-111">Remarks</span></span>

<span data-ttu-id="846ff-112">によって返される値の interpretion は、 `pVal` 列の型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="846ff-112">The interpretion of the value returned through `pVal` depends on the column's type.</span></span> <span data-ttu-id="846ff-113">列の型は、 [GetColumnInfo](imetadatatables-getcolumninfo-method.md)を呼び出すことによって決定できます。</span><span class="sxs-lookup"><span data-stu-id="846ff-113">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span></span>

- <span data-ttu-id="846ff-114">**Getcolumn** メソッドは、 **Rid** または **codedtoken** 型の列を、完全な32ビット値に自動的に変換し `mdToken` ます。</span><span class="sxs-lookup"><span data-stu-id="846ff-114">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span></span>
- <span data-ttu-id="846ff-115">また、8ビットまたは16ビットの値を完全な32ビット値に自動的に変換します。</span><span class="sxs-lookup"><span data-stu-id="846ff-115">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span></span>
- <span data-ttu-id="846ff-116">*ヒープ* 型の列の場合、返される *pVal* は、対応するヒープのインデックスになります。</span><span class="sxs-lookup"><span data-stu-id="846ff-116">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span></span>

| <span data-ttu-id="846ff-117">列の型</span><span class="sxs-lookup"><span data-stu-id="846ff-117">Column type</span></span>              | <span data-ttu-id="846ff-118">pVal を含む</span><span class="sxs-lookup"><span data-stu-id="846ff-118">pVal contains</span></span> | <span data-ttu-id="846ff-119">解説</span><span class="sxs-lookup"><span data-stu-id="846ff-119">Comment</span></span>                          |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="846ff-120">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="846ff-120">`0`..`iRidMax`</span></span><br><span data-ttu-id="846ff-121">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="846ff-121">(0..63)</span></span>  | <span data-ttu-id="846ff-122">mdToken</span><span class="sxs-lookup"><span data-stu-id="846ff-122">mdToken</span></span>     | <span data-ttu-id="846ff-123">*pVal* には完全なトークンが含まれます。</span><span class="sxs-lookup"><span data-stu-id="846ff-123">*pVal* will contain a full Token.</span></span> <span data-ttu-id="846ff-124">関数は、自動的に Rid を完全なトークンに変換します。</span><span class="sxs-lookup"><span data-stu-id="846ff-124">The function automatically converts the Rid into a full token.</span></span> |
| <span data-ttu-id="846ff-125">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="846ff-125">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="846ff-126">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="846ff-126">(64..95)</span></span> | <span data-ttu-id="846ff-127">mdToken</span><span class="sxs-lookup"><span data-stu-id="846ff-127">mdToken</span></span> | <span data-ttu-id="846ff-128">返されると、 *pVal* には完全なトークンが含まれます。</span><span class="sxs-lookup"><span data-stu-id="846ff-128">Upon return, *pVal* will contain a full Token.</span></span> <span data-ttu-id="846ff-129">関数は、CodedToken を完全なトークンに自動的に圧縮解除します。</span><span class="sxs-lookup"><span data-stu-id="846ff-129">The function automatically decompresses the CodedToken into a full token.</span></span> |
| <span data-ttu-id="846ff-130">`iSHORT` (96)</span><span class="sxs-lookup"><span data-stu-id="846ff-130">`iSHORT` (96)</span></span>            | <span data-ttu-id="846ff-131">Int16</span><span class="sxs-lookup"><span data-stu-id="846ff-131">Int16</span></span>         | <span data-ttu-id="846ff-132">32ビットに自動的に拡張されます。</span><span class="sxs-lookup"><span data-stu-id="846ff-132">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="846ff-133">`iUSHORT` (97)</span><span class="sxs-lookup"><span data-stu-id="846ff-133">`iUSHORT` (97)</span></span>           | <span data-ttu-id="846ff-134">UInt16</span><span class="sxs-lookup"><span data-stu-id="846ff-134">UInt16</span></span>        | <span data-ttu-id="846ff-135">32ビットに自動的に拡張されます。</span><span class="sxs-lookup"><span data-stu-id="846ff-135">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="846ff-136">`iLONG` (98)</span><span class="sxs-lookup"><span data-stu-id="846ff-136">`iLONG` (98)</span></span>             | <span data-ttu-id="846ff-137">Int32</span><span class="sxs-lookup"><span data-stu-id="846ff-137">Int32</span></span>         |                                        |
| <span data-ttu-id="846ff-138">`iULONG` (99)</span><span class="sxs-lookup"><span data-stu-id="846ff-138">`iULONG` (99)</span></span>            | <span data-ttu-id="846ff-139">UInt32</span><span class="sxs-lookup"><span data-stu-id="846ff-139">UInt32</span></span>        |                                        |
| <span data-ttu-id="846ff-140">`iBYTE` (100)</span><span class="sxs-lookup"><span data-stu-id="846ff-140">`iBYTE` (100)</span></span>            | <span data-ttu-id="846ff-141">Byte</span><span class="sxs-lookup"><span data-stu-id="846ff-141">Byte</span></span>          | <span data-ttu-id="846ff-142">32ビットに自動的に拡張されます。</span><span class="sxs-lookup"><span data-stu-id="846ff-142">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="846ff-143">`iSTRING` (101)</span><span class="sxs-lookup"><span data-stu-id="846ff-143">`iSTRING` (101)</span></span>          | <span data-ttu-id="846ff-144">文字列ヒープインデックス</span><span class="sxs-lookup"><span data-stu-id="846ff-144">String heap index</span></span> | <span data-ttu-id="846ff-145">*pVal* は、文字列ヒープのインデックスです。</span><span class="sxs-lookup"><span data-stu-id="846ff-145">*pVal* is an index into the String heap.</span></span> <span data-ttu-id="846ff-146">実際の列文字列値を取得するには、 [Imetadatatables::](imetadatatables-getstring-method.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="846ff-146">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span></span> |
| <span data-ttu-id="846ff-147">`iGUID` (102)</span><span class="sxs-lookup"><span data-stu-id="846ff-147">`iGUID` (102)</span></span>            | <span data-ttu-id="846ff-148">Guid ヒープインデックス</span><span class="sxs-lookup"><span data-stu-id="846ff-148">Guid heap index</span></span> | <span data-ttu-id="846ff-149">*pVal* は、Guid ヒープのインデックスです。</span><span class="sxs-lookup"><span data-stu-id="846ff-149">*pVal* is an index into the Guid heap.</span></span> <span data-ttu-id="846ff-150">実際の列の Guid 値を取得するには、 [Imetadatatables 指定できる:: GetGuid](imetadatatables-getguid-method.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="846ff-150">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span></span> |
| <span data-ttu-id="846ff-151">`iBLOB` (103)</span><span class="sxs-lookup"><span data-stu-id="846ff-151">`iBLOB` (103)</span></span>            | <span data-ttu-id="846ff-152">Blob ヒープインデックス</span><span class="sxs-lookup"><span data-stu-id="846ff-152">Blob heap index</span></span> | <span data-ttu-id="846ff-153">*pVal* は、Blob ヒープのインデックスです。</span><span class="sxs-lookup"><span data-stu-id="846ff-153">*pVal* is an index into the Blob heap.</span></span> <span data-ttu-id="846ff-154">実際の列の Blob 値を取得するには、 [Imetadatatables 指定できる:: GetBlob](imetadatatables-getblob-method.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="846ff-154">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span></span> |
  
## <a name="requirements"></a><span data-ttu-id="846ff-155">要件</span><span class="sxs-lookup"><span data-stu-id="846ff-155">Requirements</span></span>  

 <span data-ttu-id="846ff-156">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="846ff-156">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="846ff-157">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="846ff-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="846ff-158">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="846ff-158">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="846ff-159">**.NET Framework のバージョン**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="846ff-159">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="846ff-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="846ff-160">See also</span></span>

- [<span data-ttu-id="846ff-161">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="846ff-161">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="846ff-162">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="846ff-162">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
