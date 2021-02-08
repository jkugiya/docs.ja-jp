---
description: '詳細については、「IXCLRDataProcess:: EndEnumMethodInstancesByAddress メソッド」を参照してください。'
title: 'IXCLRDataProcess:: EndEnumMethodInstancesByAddress メソッド'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 2e01fe0737319a7b336d9f6992bf81b2c57f9e70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800722"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="fc14e-103">IXCLRDataProcess:: EndEnumMethodInstancesByAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="fc14e-103">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="fc14e-104">インスタンスの列挙中に使用される内部反復子によって使用されるリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="fc14e-104">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="fc14e-105">構文</span><span class="sxs-lookup"><span data-stu-id="fc14e-105">Syntax</span></span>

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="fc14e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fc14e-106">Parameters</span></span>

`handle`\
<span data-ttu-id="fc14e-107">入出力メソッドインスタンスを列挙するハンドル。</span><span class="sxs-lookup"><span data-stu-id="fc14e-107">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc14e-108">解説</span><span class="sxs-lookup"><span data-stu-id="fc14e-108">Remarks</span></span>

<span data-ttu-id="fc14e-109">指定されたメソッドはインターフェイスの一部で `IXCLRDataProcess` あり、仮想メソッドテーブルの30スロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="fc14e-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 30th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="fc14e-110">要件</span><span class="sxs-lookup"><span data-stu-id="fc14e-110">Requirements</span></span>

<span data-ttu-id="fc14e-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc14e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="fc14e-112">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="fc14e-112">**Header:** None</span></span>  
<span data-ttu-id="fc14e-113">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="fc14e-113">**Library:** None</span></span>  
<span data-ttu-id="fc14e-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fc14e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="fc14e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc14e-115">See also</span></span>

- [<span data-ttu-id="fc14e-116">CLRDataSourceType 列挙型</span><span class="sxs-lookup"><span data-stu-id="fc14e-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="fc14e-117">デバッグ</span><span class="sxs-lookup"><span data-stu-id="fc14e-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="fc14e-118">IXCLRDataProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc14e-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
