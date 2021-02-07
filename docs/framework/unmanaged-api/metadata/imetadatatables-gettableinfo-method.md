---
description: '詳細については、次を参照してください: IMetaDataTables 許容:: GetTableInfo メソッド'
title: IMetaDataTables::GetTableInfo メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type:
- apiref
ms.openlocfilehash: 3929f91c15b5c1fc22ac3ad4b17cbaa38a08533a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687650"
---
# <a name="imetadatatablesgettableinfo-method"></a><span data-ttu-id="de044-103">IMetaDataTables::GetTableInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="de044-103">IMetaDataTables::GetTableInfo Method</span></span>

<span data-ttu-id="de044-104">指定されたテーブルの名前、行のサイズ、行数、列の数、およびキー列のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="de044-104">Gets the name, row size, number of rows, number of columns, and key column index of the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de044-105">構文</span><span class="sxs-lookup"><span data-stu-id="de044-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de044-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="de044-106">Parameters</span></span>  

 `ixTbl`  
 <span data-ttu-id="de044-107">から返されるプロパティを持つテーブルの識別子。</span><span class="sxs-lookup"><span data-stu-id="de044-107">[in] The identifier of the table whose properties to return.</span></span>  
  
 `pcbRow`  
 <span data-ttu-id="de044-108">入出力テーブル行のサイズ (バイト単位) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="de044-108">[out] A pointer to the size, in bytes, of a table row.</span></span>  
  
 `pcRows`  
 <span data-ttu-id="de044-109">入出力テーブル内の行の数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="de044-109">[out] A pointer to the number of rows in the table.</span></span>  
  
 `pcCols`  
 <span data-ttu-id="de044-110">入出力テーブル内の列数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="de044-110">[out] A pointer to the number of columns in the table.</span></span>  
  
 `piKey`  
 <span data-ttu-id="de044-111">入出力キー列のインデックスへのポインター。テーブルにキー列がない場合は-1。</span><span class="sxs-lookup"><span data-stu-id="de044-111">[out] A pointer to the index of the key column, or -1 if the table has no key column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="de044-112">入出力テーブル名へのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="de044-112">[out] A pointer to a pointer to the table name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de044-113">要件</span><span class="sxs-lookup"><span data-stu-id="de044-113">Requirements</span></span>  

 <span data-ttu-id="de044-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de044-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de044-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="de044-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="de044-116">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="de044-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="de044-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de044-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de044-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="de044-118">See also</span></span>

- [<span data-ttu-id="de044-119">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="de044-119">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="de044-120">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="de044-120">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
