---
description: '詳細については、「IXCLRDataMethodInstance:: GetRepresentativeEntryAddress メソッド」を参照してください。'
title: 'IXCLRDataMethodInstance:: GetRepresentativeEntryAddress メソッド'
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
helpviewer.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 21cc6c50ab460c0e3a3a92c11fcfe51d4a2a4606
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800800"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a><span data-ttu-id="798ae-103">IXCLRDataMethodInstance:: GetRepresentativeEntryAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="798ae-103">IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method</span></span>

<span data-ttu-id="798ae-104">メソッドに対して使用可能なすべてのエントリポイントのネイティブコンパイルを行うための最も代表的なエントリポイントアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="798ae-104">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="798ae-105">構文</span><span class="sxs-lookup"><span data-stu-id="798ae-105">Syntax</span></span>

```cpp
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

## <a name="parameters"></a><span data-ttu-id="798ae-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="798ae-106">Parameters</span></span>

`addr`\
<span data-ttu-id="798ae-107">入出力メソッドの最も代表的なネイティブエントリポイントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="798ae-107">[out] The address of the most representative native entry point for the method.</span></span>

## <a name="remarks"></a><span data-ttu-id="798ae-108">解説</span><span class="sxs-lookup"><span data-stu-id="798ae-108">Remarks</span></span>

<span data-ttu-id="798ae-109">指定されたメソッドは[ `IXCLRDataMethodInstance` インターフェイス](ixclrdatamethodinstance-interface.md)の一部であり、仮想メソッドテーブルの20番目のスロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="798ae-109">The provided method is part of the [`IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) and corresponds to the 20th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="798ae-110">要件</span><span class="sxs-lookup"><span data-stu-id="798ae-110">Requirements</span></span>

<span data-ttu-id="798ae-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="798ae-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="798ae-112">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="798ae-112">**Header:** None</span></span>  
<span data-ttu-id="798ae-113">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="798ae-113">**Library:** None</span></span>  
<span data-ttu-id="798ae-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="798ae-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="798ae-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="798ae-115">See also</span></span>

- [<span data-ttu-id="798ae-116">デバッグ</span><span class="sxs-lookup"><span data-stu-id="798ae-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="798ae-117">IXCLRDataMethodInstance インターフェイス</span><span class="sxs-lookup"><span data-stu-id="798ae-117">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
