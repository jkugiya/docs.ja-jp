---
description: '詳細について: IMetaDataEmit::D efineUserString メソッド'
title: IMetaDataEmit::DefineUserString メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineUserString
helpviewer_keywords:
- DefineUserString method [.NET Framework metadata]
- IMetaDataEmit::DefineUserString method [.NET Framework metadata]
ms.assetid: 88fb7ef3-bbdf-429c-b678-c9c153456461
topic_type:
- apiref
ms.openlocfilehash: 0d1c376e3f121d35cb9f6c08d7013a3913a8bd49
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784003"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="681cd-103">IMetaDataEmit::DefineUserString メソッド</span><span class="sxs-lookup"><span data-stu-id="681cd-103">IMetaDataEmit::DefineUserString Method</span></span>

<span data-ttu-id="681cd-104">指定されたリテラル文字列のメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="681cd-104">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="681cd-105">構文</span><span class="sxs-lookup"><span data-stu-id="681cd-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineUserString (
    [in]  LPCWSTR     szString,
    [in]  ULONG       cchString,
    [out] mdString    *pstk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="681cd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="681cd-106">Parameters</span></span>  

 `szString`  
 <span data-ttu-id="681cd-107">から格納するユーザー文字列。</span><span class="sxs-lookup"><span data-stu-id="681cd-107">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="681cd-108">からのワイド文字数 `szString` 。</span><span class="sxs-lookup"><span data-stu-id="681cd-108">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="681cd-109">入出力割り当てられた文字列トークン。</span><span class="sxs-lookup"><span data-stu-id="681cd-109">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="681cd-110">要件</span><span class="sxs-lookup"><span data-stu-id="681cd-110">Requirements</span></span>  

 <span data-ttu-id="681cd-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="681cd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="681cd-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="681cd-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="681cd-113">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="681cd-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="681cd-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="681cd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="681cd-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="681cd-115">See also</span></span>

- [<span data-ttu-id="681cd-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="681cd-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="681cd-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="681cd-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
