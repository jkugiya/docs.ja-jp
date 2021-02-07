---
description: '詳細については、「Imetadatatmetadat:: GetNumTables メソッド」を参照してください。'
title: IMetaDataTables::GetNumTables メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNumTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNumTables
helpviewer_keywords:
- GetNumTables method [.NET Framework metadata]
- IMetaDataTables::GetNumTables method [.NET Framework metadata]
ms.assetid: 8196f2a3-bbf2-45d3-a6cd-74502c356644
topic_type:
- apiref
ms.openlocfilehash: 1d1e386b1f1eb0f73fbd0df8ddff9cebc5817692
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687845"
---
# <a name="imetadatatablesgetnumtables-method"></a><span data-ttu-id="58d92-103">IMetaDataTables::GetNumTables メソッド</span><span class="sxs-lookup"><span data-stu-id="58d92-103">IMetaDataTables::GetNumTables Method</span></span>

<span data-ttu-id="58d92-104">現在のインスタンスのスコープ内にあるテーブルの数を取得し `IMetaDataTables` ます。</span><span class="sxs-lookup"><span data-stu-id="58d92-104">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58d92-105">構文</span><span class="sxs-lookup"><span data-stu-id="58d92-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNumTables (  
    [out]  ULONG   *pcTables  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58d92-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="58d92-106">Parameters</span></span>  

 `pcTables`  
 <span data-ttu-id="58d92-107">入出力現在のインスタンススコープ内にあるテーブルの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58d92-107">[out] A pointer to the number of tables in the current instance scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58d92-108">要件</span><span class="sxs-lookup"><span data-stu-id="58d92-108">Requirements</span></span>  

 <span data-ttu-id="58d92-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58d92-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58d92-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="58d92-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="58d92-111">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="58d92-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="58d92-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58d92-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58d92-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="58d92-113">See also</span></span>

- [<span data-ttu-id="58d92-114">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="58d92-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="58d92-115">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="58d92-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
