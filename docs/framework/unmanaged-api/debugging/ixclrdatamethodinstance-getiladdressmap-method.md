---
description: '詳細については、「IXCLRDataMethodInstance:: GetILAddressMap メソッド」を参照してください。'
title: 'IXCLRDataMethodInstance:: GetILAddressMap メソッド'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodInstance::GetILAddressMap Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method
helpviewer.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ddddf593c3c18f2b4cd1682b5d6f7c8ff1985ac6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800813"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a><span data-ttu-id="20397-103">IXCLRDataMethodInstance:: GetILAddressMap メソッド</span><span class="sxs-lookup"><span data-stu-id="20397-103">IXCLRDataMethodInstance::GetILAddressMap Method</span></span>

<span data-ttu-id="20397-104">マッピング情報をアドレス付けする IL を取得します。</span><span class="sxs-lookup"><span data-stu-id="20397-104">Gets the IL to address mapping information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="20397-105">構文</span><span class="sxs-lookup"><span data-stu-id="20397-105">Syntax</span></span>

```cpp
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

## <a name="parameters"></a><span data-ttu-id="20397-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="20397-106">Parameters</span></span>

`mapLen`\
<span data-ttu-id="20397-107">から指定されたマップ配列の長さ。</span><span class="sxs-lookup"><span data-stu-id="20397-107">[in] The length of the provided maps array.</span></span>

`mapNeeded`\
<span data-ttu-id="20397-108">入出力メソッドが必要とするマップエントリの数。</span><span class="sxs-lookup"><span data-stu-id="20397-108">[out] The number of map entries that the method needs.</span></span>

`maps`\
<span data-ttu-id="20397-109">[out、size_is (mapLen)]マップエントリを格納するための配列。</span><span class="sxs-lookup"><span data-stu-id="20397-109">[out, size_is(mapLen)] The array for storing the map entries.</span></span>

## <a name="remarks"></a><span data-ttu-id="20397-110">解説</span><span class="sxs-lookup"><span data-stu-id="20397-110">Remarks</span></span>

<span data-ttu-id="20397-111">指定されたメソッドはインターフェイスの一部で `IXCLRDataMethodInstance` あり、仮想メソッドテーブルの15番目のスロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="20397-111">The provided method is part of the `IXCLRDataMethodInstance` interface and corresponds to the 15th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="20397-112">要件</span><span class="sxs-lookup"><span data-stu-id="20397-112">Requirements</span></span>

<span data-ttu-id="20397-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20397-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="20397-114">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="20397-114">**Header:** None</span></span>  
<span data-ttu-id="20397-115">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="20397-115">**Library:** None</span></span>  
<span data-ttu-id="20397-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="20397-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="20397-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="20397-117">See also</span></span>

- [<span data-ttu-id="20397-118">デバッグ</span><span class="sxs-lookup"><span data-stu-id="20397-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="20397-119">IXCLRDataMethodInstance インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20397-119">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
