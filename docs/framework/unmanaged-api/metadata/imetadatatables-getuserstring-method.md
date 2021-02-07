---
description: '詳細について: IMetaDataTables:: GetUserString メソッド'
title: IMetaDataTables::GetUserString メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type:
- apiref
ms.openlocfilehash: 0909bfb2dbf4e6a34b746da7397a82845c2129c2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687689"
---
# <a name="imetadatatablesgetuserstring-method"></a><span data-ttu-id="1f43d-103">IMetaDataTables::GetUserString メソッド</span><span class="sxs-lookup"><span data-stu-id="1f43d-103">IMetaDataTables::GetUserString Method</span></span>

<span data-ttu-id="1f43d-104">現在のスコープ内の文字列列にある、指定したインデックス位置にあるハードコーディングされた文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="1f43d-104">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="1f43d-105">構文</span><span class="sxs-lookup"><span data-stu-id="1f43d-105">Syntax</span></span>

```cpp
HRESULT GetUserString (
    [in]  ULONG       ixUserString,
    [out] ULONG       *pcbData,
    [out] const void  **ppData
);
```

## <a name="parameters"></a><span data-ttu-id="1f43d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1f43d-106">Parameters</span></span>

`ixUserString`\
<span data-ttu-id="1f43d-107">からハードコーディングされた文字列の取得元のインデックス値。</span><span class="sxs-lookup"><span data-stu-id="1f43d-107">[in] The index value from which the hard-coded string will be retrieved.</span></span>

`pcbData`\
<span data-ttu-id="1f43d-108">入出力のサイズへのポインター `ppData` 。</span><span class="sxs-lookup"><span data-stu-id="1f43d-108">[out] A pointer to the size of `ppData`.</span></span>

`ppData`\
<span data-ttu-id="1f43d-109">入出力返された文字列へのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1f43d-109">[out] A pointer to a pointer to the returned string.</span></span>

## <a name="requirements"></a><span data-ttu-id="1f43d-110">要件</span><span class="sxs-lookup"><span data-stu-id="1f43d-110">Requirements</span></span>

<span data-ttu-id="1f43d-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f43d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="1f43d-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="1f43d-112">**Header:** Cor.h</span></span>

<span data-ttu-id="1f43d-113">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="1f43d-113">**Library:** Used as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="1f43d-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f43d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1f43d-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f43d-115">See also</span></span>

- [<span data-ttu-id="1f43d-116">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f43d-116">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="1f43d-117">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f43d-117">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
