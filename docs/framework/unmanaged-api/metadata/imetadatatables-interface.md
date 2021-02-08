---
description: 詳細については、「IMetaDataTables インターフェイス」を参照してください。
title: IMetaDataTables インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables
helpviewer_keywords:
- IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type:
- apiref
ms.openlocfilehash: c3edf504586bad1252c36d6e8254193eaf9cc26d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799271"
---
# <a name="imetadatatables-interface"></a><span data-ttu-id="f564c-103">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f564c-103">IMetaDataTables Interface</span></span>

<span data-ttu-id="f564c-104">テーブル内のメタデータ情報の格納と取得のためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f564c-104">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f564c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-105">Methods</span></span>  
  
|<span data-ttu-id="f564c-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-106">Method</span></span>|<span data-ttu-id="f564c-107">説明</span><span class="sxs-lookup"><span data-stu-id="f564c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f564c-108">GetBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-108">GetBlob Method</span></span>](imetadatatables-getblob-method.md)|<span data-ttu-id="f564c-109">指定した列インデックスにあるバイナリラージオブジェクト (BLOB) へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="f564c-109">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>|  
|[<span data-ttu-id="f564c-110">GetBlobHeapSize メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-110">GetBlobHeapSize Method</span></span>](imetadatatables-getblobheapsize-method.md)|<span data-ttu-id="f564c-111">BLOB ヒープのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="f564c-111">Gets the size, in bytes, of the BLOB heap.</span></span>|  
|[<span data-ttu-id="f564c-112">GetCodedTokenInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-112">GetCodedTokenInfo Method</span></span>](imetadatatables-getcodedtokeninfo-method.md)|<span data-ttu-id="f564c-113">指定した行インデックスに関連付けられているトークンの配列へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="f564c-113">Gets a pointer to an array of tokens associated with the specified row index.</span></span>|  
|[<span data-ttu-id="f564c-114">GetColumn メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-114">GetColumn Method</span></span>](imetadatatables-getcolumn-method.md)|<span data-ttu-id="f564c-115">指定したテーブルインデックスにあるテーブル内の、指定した列インデックスにある列に格納されている値へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="f564c-115">Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="f564c-116">GetColumnInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-116">GetColumnInfo Method</span></span>](imetadatatables-getcolumninfo-method.md)|<span data-ttu-id="f564c-117">指定されたテーブル内の指定された列に関するデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="f564c-117">Gets data about the specified column in the specified table.</span></span>|  
|[<span data-ttu-id="f564c-118">GetGuid メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-118">GetGuid Method</span></span>](imetadatatables-getguid-method.md)|<span data-ttu-id="f564c-119">指定したインデックス位置にある行から GUID を取得します。</span><span class="sxs-lookup"><span data-stu-id="f564c-119">Gets a GUID from the row at the specified index.</span></span>|  
|[<span data-ttu-id="f564c-120">GetGuidHeapSize メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-120">GetGuidHeapSize Method</span></span>](imetadatatables-getguidheapsize-method.md)|<span data-ttu-id="f564c-121">GUID ヒープのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="f564c-121">Gets the size, in bytes, of the GUID heap.</span></span>|  
|[<span data-ttu-id="f564c-122">GetNextBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-122">GetNextBlob Method</span></span>](imetadatatables-getnextblob-method.md)|<span data-ttu-id="f564c-123">テーブル内の次の BLOB のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="f564c-123">Gets the index of the next BLOB in the table.</span></span>|  
|[<span data-ttu-id="f564c-124">GetNextGuid メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-124">GetNextGuid Method</span></span>](imetadatatables-getnextguid-method.md)|<span data-ttu-id="f564c-125">現在のテーブル列の次の GUID 値のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="f564c-125">Gets the index of the next GUID value in the current table column.</span></span>|  
|[<span data-ttu-id="f564c-126">GetNextString メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-126">GetNextString Method</span></span>](imetadatatables-getnextstring-method.md)|<span data-ttu-id="f564c-127">現在のテーブル列の次の文字列のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="f564c-127">Gets the index of the next string in the current table column.</span></span>|  
|[<span data-ttu-id="f564c-128">GetNextUserString メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-128">GetNextUserString Method</span></span>](imetadatatables-getnextuserstring-method.md)|<span data-ttu-id="f564c-129">現在のテーブル列の次のハードコーディングされた文字列を含む行のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="f564c-129">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>|  
|[<span data-ttu-id="f564c-130">GetNumTables メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-130">GetNumTables Method</span></span>](imetadatatables-getnumtables-method.md)|<span data-ttu-id="f564c-131">現在のインスタンスのスコープ内にあるテーブルの数を取得し `IMetaDataTables` ます。</span><span class="sxs-lookup"><span data-stu-id="f564c-131">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>|  
|[<span data-ttu-id="f564c-132">GetRow メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-132">GetRow Method</span></span>](imetadatatables-getrow-method.md)|<span data-ttu-id="f564c-133">指定したテーブルインデックスにあるテーブル内の指定した行インデックスにある行を取得します。</span><span class="sxs-lookup"><span data-stu-id="f564c-133">Gets the row at the specified row index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="f564c-134">GetString メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-134">GetString Method</span></span>](imetadatatables-getstring-method.md)|<span data-ttu-id="f564c-135">現在の参照スコープのテーブル列から、指定したインデックス位置にある文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="f564c-135">Gets the string at the specified index from the table column in the current reference scope.</span></span>|  
|[<span data-ttu-id="f564c-136">GetStringHeapSize メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-136">GetStringHeapSize Method</span></span>](imetadatatables-getstringheapsize-method.md)|<span data-ttu-id="f564c-137">文字列ヒープのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="f564c-137">Gets the size, in bytes, of the string heap.</span></span>|  
|[<span data-ttu-id="f564c-138">GetTableIndex メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-138">GetTableIndex Method</span></span>](imetadatatables-gettableindex-method.md)|<span data-ttu-id="f564c-139">指定したトークンによって参照されるテーブルのインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="f564c-139">Gets the index for the table referenced by the specified token.</span></span>|  
|[<span data-ttu-id="f564c-140">GetTableInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-140">GetTableInfo Method</span></span>](imetadatatables-gettableinfo-method.md)|<span data-ttu-id="f564c-141">指定されたテーブルインデックスにあるテーブルの名前、行のサイズ、行数、列の数、およびキー列のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="f564c-141">Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.</span></span>|  
|[<span data-ttu-id="f564c-142">GetUserString メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-142">GetUserString Method</span></span>](imetadatatables-getuserstring-method.md)|<span data-ttu-id="f564c-143">現在のスコープ内の文字列列にある、指定したインデックス位置にあるハードコーディングされた文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="f564c-143">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>|  
|[<span data-ttu-id="f564c-144">GetUserStringHeapSize メソッド</span><span class="sxs-lookup"><span data-stu-id="f564c-144">GetUserStringHeapSize Method</span></span>](imetadatatables-getuserstringheapsize-method.md)|<span data-ttu-id="f564c-145">ユーザー文字列ヒープのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="f564c-145">Gets the size, in bytes, of the user string heap.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f564c-146">要件</span><span class="sxs-lookup"><span data-stu-id="f564c-146">Requirements</span></span>  

 <span data-ttu-id="f564c-147">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f564c-147">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f564c-148">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="f564c-148">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f564c-149">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="f564c-149">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f564c-150">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f564c-150">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f564c-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="f564c-151">See also</span></span>

- [<span data-ttu-id="f564c-152">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f564c-152">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="f564c-153">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f564c-153">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
