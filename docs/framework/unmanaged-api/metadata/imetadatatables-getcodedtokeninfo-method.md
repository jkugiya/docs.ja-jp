---
description: '詳細については、次を参照してください: IMetaDataTables 許容:: GetCodedTokenInfo メソッド'
title: IMetaDataTables::GetCodedTokenInfo メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetCodedTokenInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetCodedTokenInfo
helpviewer_keywords:
- GetCodedTokenInfo method [.NET Framework metadata]
- IMetaDataTables::GetCodedTokenInfo method [.NET Framework metadata]
ms.assetid: 31214d3a-715e-49af-92b3-0fd11e4f218a
topic_type:
- apiref
ms.openlocfilehash: 982a13636d8b4572113038eaa658158e6c2ca966
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688287"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="9cd33-103">IMetaDataTables::GetCodedTokenInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="9cd33-103">IMetaDataTables::GetCodedTokenInfo Method</span></span>

<span data-ttu-id="9cd33-104">指定した行インデックスに関連付けられているトークンの配列へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="9cd33-104">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cd33-105">構文</span><span class="sxs-lookup"><span data-stu-id="9cd33-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cd33-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9cd33-106">Parameters</span></span>  

 `ixCdTkn`  
 <span data-ttu-id="9cd33-107">から返されるコード化されたトークンの種類。</span><span class="sxs-lookup"><span data-stu-id="9cd33-107">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="9cd33-108">入出力の長さへのポインター `ppTokens` 。</span><span class="sxs-lookup"><span data-stu-id="9cd33-108">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="9cd33-109">入出力返されたトークンのリストを格納する配列へのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9cd33-109">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="9cd33-110">入出力にあるトークンの名前へのポインターへのポインター `ixCdTkn` 。</span><span class="sxs-lookup"><span data-stu-id="9cd33-110">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cd33-111">要件</span><span class="sxs-lookup"><span data-stu-id="9cd33-111">Requirements</span></span>  

 <span data-ttu-id="9cd33-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9cd33-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cd33-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="9cd33-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9cd33-114">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="9cd33-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9cd33-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cd33-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cd33-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="9cd33-116">See also</span></span>

- [<span data-ttu-id="9cd33-117">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9cd33-117">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="9cd33-118">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9cd33-118">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
