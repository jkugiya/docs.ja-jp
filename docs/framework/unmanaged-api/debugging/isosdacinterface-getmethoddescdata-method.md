---
description: ': ISOSDacInterface:: GetMethodDescData メソッドの詳細について説明します。'
title: 'ISOSDacInterface:: GetMethodDescData メソッド'
ms.date: 01/16/2019
api.name:
- ISOSDacInterface::GetMethodDescData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescData Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescData Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a1284aa4d810ed9d6db7ad3c1b471702b1dad54d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790426"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="fc837-103">ISOSDacInterface:: GetMethodDescData メソッド</span><span class="sxs-lookup"><span data-stu-id="fc837-103">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="fc837-104">指定された MethodDesc ポインターのデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="fc837-104">Gets the data for the given MethodDesc pointer.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="fc837-105">構文</span><span class="sxs-lookup"><span data-stu-id="fc837-105">Syntax</span></span>

```cpp
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a><span data-ttu-id="fc837-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fc837-106">Parameters</span></span>

`methodDesc`\
<span data-ttu-id="fc837-107">からMethodDesc のアドレス。</span><span class="sxs-lookup"><span data-stu-id="fc837-107">[in] The address of the MethodDesc.</span></span>

`ip`\
<span data-ttu-id="fc837-108">からメソッドの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="fc837-108">[in] The IP address of the method.</span></span>

`data`\
<span data-ttu-id="fc837-109">入出力内部 Api から返される MethodDesc に関連付けられたデータ。</span><span class="sxs-lookup"><span data-stu-id="fc837-109">[out] The data associated with the MethodDesc as returned from the internal APIs.</span></span>

`cRevertedRejitVersions`\
<span data-ttu-id="fc837-110">入出力戻された再 jit バージョンの数。</span><span class="sxs-lookup"><span data-stu-id="fc837-110">[out] The number of reverted rejit versions.</span></span>

`rgRevertedRejitData`\
<span data-ttu-id="fc837-111">入出力内部 Api から返された、元に戻された rejit バージョンに関連付けられたデータ。</span><span class="sxs-lookup"><span data-stu-id="fc837-111">[out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span>

`pcNeededRevertedRejitData`\
<span data-ttu-id="fc837-112">入出力戻された ReJit バージョンに関連付けられたデータを格納するために必要なバイト数。</span><span class="sxs-lookup"><span data-stu-id="fc837-112">[out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc837-113">解説</span><span class="sxs-lookup"><span data-stu-id="fc837-113">Remarks</span></span>

<span data-ttu-id="fc837-114">指定されたメソッドはインターフェイスの一部で `ISOSDacInterface` あり、仮想メソッドテーブルの21スロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="fc837-114">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 21st slot of the virtual method table.</span></span> <span data-ttu-id="fc837-115">これらを使用できるようにするには、を [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) 64 ビット符号なし整数として定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc837-115">To be able to use them, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) must be defined as a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="fc837-116">要件</span><span class="sxs-lookup"><span data-stu-id="fc837-116">Requirements</span></span>

<span data-ttu-id="fc837-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc837-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="fc837-118">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="fc837-118">**Header:** None</span></span>  
<span data-ttu-id="fc837-119">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="fc837-119">**Library:** None</span></span>  
<span data-ttu-id="fc837-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fc837-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="fc837-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc837-121">See also</span></span>

- [<span data-ttu-id="fc837-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="fc837-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="fc837-123">ISOSDacInterface インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc837-123">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
