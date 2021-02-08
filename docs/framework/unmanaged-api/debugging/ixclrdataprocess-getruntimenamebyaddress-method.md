---
description: '詳細については、「IXCLRDataProcess:: GetRuntimeNameByAddress メソッド」を参照してください。'
title: 'IXCLRDataProcess:: GetRuntimeNameByAddress メソッド'
ms.date: 4/27/2020
api.name:
- IXCLRDataProcess::GetRuntimeNameByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetRuntimeNameByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::GetRuntimeNameByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: tommcdon
ms.author: tommcdon
ms.openlocfilehash: 62d9ae73c216748cc8eb02aedd41cf19f475d071
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800657"
---
# <a name="ixclrdataprocessgetruntimenamebyaddress-method"></a><span data-ttu-id="dc3fd-103">IXCLRDataProcess:: GetRuntimeNameByAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="dc3fd-103">IXCLRDataProcess::GetRuntimeNameByAddress Method</span></span>

<span data-ttu-id="dc3fd-104">指定されたアドレスの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-104">Gets a name for the given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="dc3fd-105">構文</span><span class="sxs-lookup"><span data-stu-id="dc3fd-105">Syntax</span></span>

```cpp
HRESULT GetRuntimeNameByAddress(
    [in] CLRDATA_ADDRESS address,
    [in] ULONG32 flags,
    [in] ULONG32 bufLen,
    [out] ULONG32 *nameLen,
    [out, size_is(bufLen)] WCHAR nameBuf[],
    [out] CLRDATA_ADDRESS* displacement
);
```

## <a name="parameters"></a><span data-ttu-id="dc3fd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dc3fd-106">Parameters</span></span>

`address`\
<span data-ttu-id="dc3fd-107">から `CLRDATA_ADDRESS` コードアドレスを表す値。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-107">[in] A `CLRDATA_ADDRESS` value that represents a code address.</span></span>

`flags`\
<span data-ttu-id="dc3fd-108">からを ' 0 ' に設定します。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-108">[in] Set to '0'.</span></span>

`bufLen`\
<span data-ttu-id="dc3fd-109">からバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-109">[in] The length of the buffer.</span></span>

`namLen`\
<span data-ttu-id="dc3fd-110">入出力返された文字数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-110">[out] A pointer to the number of characters returned.</span></span>

`namBuf`\
<span data-ttu-id="dc3fd-111">[out, size_is ( `bufLen` )] ランタイム名を格納する長さの入力バッファー `bufLen` 。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-111">[out, size_is(`bufLen`)] The input buffer of length `bufLen` that stores the runtime name.</span></span>

`displacement`\
<span data-ttu-id="dc3fd-112">入出力 `CLRDATA_ADDRESS` 返されたシンボルのコードオフセットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-112">[out] A `CLRDATA_ADDRESS` pointer to the code offset of the returned symbol.</span></span>

## <a name="remarks"></a><span data-ttu-id="dc3fd-113">解説</span><span class="sxs-lookup"><span data-stu-id="dc3fd-113">Remarks</span></span>

<span data-ttu-id="dc3fd-114">指定されたメソッドはインターフェイスの一部で `IXCLRDataProcess` あり、仮想メソッドテーブルの16番目のスロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-114">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 16th slot of the virtual-method table.</span></span>

> [!NOTE]
> <span data-ttu-id="dc3fd-115">バッファーが名前に十分な大きさではない場合、このメソッドはを返し、 `S_FALSE` `nameLen` に必要なバッファー長を設定します。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-115">If the buffer is not large enough for the name, this method returns `S_FALSE` and sets `nameLen` to the required buffer length.</span></span>

## <a name="requirements"></a><span data-ttu-id="dc3fd-116">要件</span><span class="sxs-lookup"><span data-stu-id="dc3fd-116">Requirements</span></span>

<span data-ttu-id="dc3fd-117">**プラットフォーム:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md)</span></span>\
<span data-ttu-id="dc3fd-118">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="dc3fd-118">**Header:** None\</span></span>
<span data-ttu-id="dc3fd-119">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="dc3fd-119">**Library:** None\</span></span>
<span data-ttu-id="dc3fd-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dc3fd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="dc3fd-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc3fd-121">See also</span></span>

- [<span data-ttu-id="dc3fd-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="dc3fd-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="dc3fd-123">IXCLRDataProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dc3fd-123">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
