---
description: '詳細については、「IMetaDataTables:: メソッド」を参照してください。'
title: IMetaDataTables::GetNextString メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextString
helpviewer_keywords:
- IMetaDataTables::GetNextString method [.NET Framework metadata]
- GetNextString method [.NET Framework metadata]
ms.assetid: d9720428-c353-4f07-a7e8-899e106a1b37
topic_type:
- apiref
ms.openlocfilehash: b3c4f94a2659b83c89bef322517465a585b63ddc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688014"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="f3240-103">IMetaDataTables::GetNextString メソッド</span><span class="sxs-lookup"><span data-stu-id="f3240-103">IMetaDataTables::GetNextString Method</span></span>

<span data-ttu-id="f3240-104">現在のテーブル列の次の文字列のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="f3240-104">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3240-105">構文</span><span class="sxs-lookup"><span data-stu-id="f3240-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNextString (
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3240-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f3240-106">Parameters</span></span>  

 `ixString`  
 <span data-ttu-id="f3240-107">から文字列テーブル列からのインデックス値。</span><span class="sxs-lookup"><span data-stu-id="f3240-107">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="f3240-108">入出力列内の次の文字列のインデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f3240-108">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3240-109">要件</span><span class="sxs-lookup"><span data-stu-id="f3240-109">Requirements</span></span>  

 <span data-ttu-id="f3240-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3240-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3240-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="f3240-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3240-112">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="f3240-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3240-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3240-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3240-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3240-114">See also</span></span>

- [<span data-ttu-id="f3240-115">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f3240-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="f3240-116">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f3240-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
