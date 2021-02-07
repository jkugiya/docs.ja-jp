---
description: '詳細については、「IMetaDataTables:: メソッド」を参照してください。'
title: IMetaDataTables::GetNextBlob メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextBlob
helpviewer_keywords:
- IMetaDataTables::GetNextBlob method [.NET Framework metadata]
- GetNextBlob method [.NET Framework metadata]
ms.assetid: 017c8ab4-4c09-4754-9935-5b0b49cabecb
topic_type:
- apiref
ms.openlocfilehash: 99126ab5c3891ee09346bb54096a4fce3ca44bc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688131"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="fe020-103">IMetaDataTables::GetNextBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="fe020-103">IMetaDataTables::GetNextBlob Method</span></span>

<span data-ttu-id="fe020-104">テーブル内の次のバイナリラージオブジェクト (BLOB) のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="fe020-104">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe020-105">構文</span><span class="sxs-lookup"><span data-stu-id="fe020-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe020-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fe020-106">Parameters</span></span>  

 `ixBlob`  
 <span data-ttu-id="fe020-107">からBlob の列から返されるインデックス。</span><span class="sxs-lookup"><span data-stu-id="fe020-107">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="fe020-108">入出力次の BLOB のインデックスを指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="fe020-108">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe020-109">要件</span><span class="sxs-lookup"><span data-stu-id="fe020-109">Requirements</span></span>  

 <span data-ttu-id="fe020-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe020-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe020-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="fe020-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fe020-112">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="fe020-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fe020-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe020-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe020-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe020-114">See also</span></span>

- [<span data-ttu-id="fe020-115">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe020-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="fe020-116">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe020-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
