---
description: '詳細については、「IXCLRDataMethodDefinition:: EnumInstance メソッド」を参照してください。'
title: 'IXCLRDataMethodDefinition:: EnumInstance メソッド'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EnumInstance Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4038dc4706b8362acaf9c13abd9c7326cce376a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790361"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="3236e-103">IXCLRDataMethodDefinition:: EnumInstance メソッド</span><span class="sxs-lookup"><span data-stu-id="3236e-103">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="3236e-104">このメソッド定義のインスタンスを列挙します。</span><span class="sxs-lookup"><span data-stu-id="3236e-104">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="3236e-105">構文</span><span class="sxs-lookup"><span data-stu-id="3236e-105">Syntax</span></span>

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="3236e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3236e-106">Parameters</span></span>

`handle`\
<span data-ttu-id="3236e-107">[入力、出力]インスタンスを列挙するハンドル。</span><span class="sxs-lookup"><span data-stu-id="3236e-107">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="3236e-108">入出力列挙されたインスタンス。</span><span class="sxs-lookup"><span data-stu-id="3236e-108">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="3236e-109">解説</span><span class="sxs-lookup"><span data-stu-id="3236e-109">Remarks</span></span>

<span data-ttu-id="3236e-110">指定されたメソッドはインターフェイスの一部で `IXCLRDataMethodDefinition` あり、仮想メソッドテーブルの6番目のスロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="3236e-110">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 6th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="3236e-111">要件</span><span class="sxs-lookup"><span data-stu-id="3236e-111">Requirements</span></span>

<span data-ttu-id="3236e-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3236e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="3236e-113">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="3236e-113">**Header:** None</span></span>  
<span data-ttu-id="3236e-114">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="3236e-114">**Library:** None</span></span>  
<span data-ttu-id="3236e-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3236e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3236e-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="3236e-116">See also</span></span>

- [<span data-ttu-id="3236e-117">CLRDataSourceType 列挙型</span><span class="sxs-lookup"><span data-stu-id="3236e-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="3236e-118">デバッグ</span><span class="sxs-lookup"><span data-stu-id="3236e-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="3236e-119">IXCLRDataMethodDefinition インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3236e-119">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="3236e-120">IXCLRDataMethodInstance インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3236e-120">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
