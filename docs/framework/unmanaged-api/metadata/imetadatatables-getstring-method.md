---
description: '詳細については、「IMetaDataTables:: メソッド」を参照してください。'
title: IMetaDataTables::GetString メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type:
- apiref
ms.openlocfilehash: 2104e30657a152d1b9a2ace743da9b126fb15d60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687793"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="f09be-103">IMetaDataTables::GetString メソッド</span><span class="sxs-lookup"><span data-stu-id="f09be-103">IMetaDataTables::GetString Method</span></span>

<span data-ttu-id="f09be-104">現在の参照スコープのテーブル列から、指定したインデックス位置にある文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="f09be-104">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f09be-105">構文</span><span class="sxs-lookup"><span data-stu-id="f09be-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f09be-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f09be-106">Parameters</span></span>  

 `ixString`  
 <span data-ttu-id="f09be-107">から次の値の検索を開始する位置のインデックス。</span><span class="sxs-lookup"><span data-stu-id="f09be-107">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="f09be-108">入出力返された文字列値へのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f09be-108">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f09be-109">要件</span><span class="sxs-lookup"><span data-stu-id="f09be-109">Requirements</span></span>  

 <span data-ttu-id="f09be-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f09be-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f09be-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="f09be-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f09be-112">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="f09be-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f09be-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f09be-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f09be-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f09be-114">See also</span></span>

- [<span data-ttu-id="f09be-115">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f09be-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="f09be-116">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f09be-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
