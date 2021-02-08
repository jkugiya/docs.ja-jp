---
description: '詳細については、「IXCLRDataMethodDefinition:: EndEnumInstances メソッド」を参照してください。'
title: 'IXCLRDataMethodDefinition:: EndEnumInstances メソッド'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EndEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: bfdcb9046b4983e6686410bf2ceadf7119b89e74
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790374"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="a5434-103">IXCLRDataMethodDefinition:: EndEnumInstances メソッド</span><span class="sxs-lookup"><span data-stu-id="a5434-103">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="a5434-104">インスタンスの列挙中に使用される内部反復子によって使用されるリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="a5434-104">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a5434-105">構文</span><span class="sxs-lookup"><span data-stu-id="a5434-105">Syntax</span></span>

```cpp
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="a5434-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a5434-106">Parameters</span></span>

`handle`\
<span data-ttu-id="a5434-107">入出力インスタンスを列挙するハンドル。</span><span class="sxs-lookup"><span data-stu-id="a5434-107">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="a5434-108">解説</span><span class="sxs-lookup"><span data-stu-id="a5434-108">Remarks</span></span>

<span data-ttu-id="a5434-109">指定されたメソッドはインターフェイスの一部で `IXCLRDataMethodDefinition` あり、仮想メソッドテーブルの7番目のスロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="a5434-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 7th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="a5434-110">要件</span><span class="sxs-lookup"><span data-stu-id="a5434-110">Requirements</span></span>

<span data-ttu-id="a5434-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5434-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a5434-112">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="a5434-112">**Header:** None</span></span>  
<span data-ttu-id="a5434-113">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="a5434-113">**Library:** None</span></span>  
<span data-ttu-id="a5434-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a5434-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a5434-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5434-115">See also</span></span>

- [<span data-ttu-id="a5434-116">デバッグ</span><span class="sxs-lookup"><span data-stu-id="a5434-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="a5434-117">IXCLRDataMethodDefinition インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5434-117">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
