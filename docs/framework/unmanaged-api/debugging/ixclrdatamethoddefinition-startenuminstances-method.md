---
description: '詳細については、「IXCLRDataMethodDefinition:: StartEnumInstances メソッド」を参照してください。'
title: 'IXCLRDataMethodDefinition:: StartEnumInstances メソッド'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::StartEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 74de6360c90766cfec17e6b88a495fe2a70858b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800826"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="383f8-103">IXCLRDataMethodDefinition:: StartEnumInstances メソッド</span><span class="sxs-lookup"><span data-stu-id="383f8-103">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="383f8-104">指定されたのメソッドインスタンスの列挙体のハンドルを提供 `IXCLRDataAppDomain` します。</span><span class="sxs-lookup"><span data-stu-id="383f8-104">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="383f8-105">構文</span><span class="sxs-lookup"><span data-stu-id="383f8-105">Syntax</span></span>

```cpp
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="383f8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="383f8-106">Parameters</span></span>

`appDomain`\
<span data-ttu-id="383f8-107">から列挙型の AppDomain。</span><span class="sxs-lookup"><span data-stu-id="383f8-107">[in] An AppDomain for the enumeration.</span></span>

`handle`\
<span data-ttu-id="383f8-108">入出力インスタンスを列挙するハンドル。</span><span class="sxs-lookup"><span data-stu-id="383f8-108">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="383f8-109">解説</span><span class="sxs-lookup"><span data-stu-id="383f8-109">Remarks</span></span>

<span data-ttu-id="383f8-110">指定されたメソッドはインターフェイスの一部で `IXCLRDataMethodDefinition` あり、仮想メソッドテーブルの5番目のスロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="383f8-110">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 5th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="383f8-111">要件</span><span class="sxs-lookup"><span data-stu-id="383f8-111">Requirements</span></span>

<span data-ttu-id="383f8-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="383f8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="383f8-113">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="383f8-113">**Header:** None</span></span>  
<span data-ttu-id="383f8-114">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="383f8-114">**Library:** None</span></span>  
<span data-ttu-id="383f8-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="383f8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="383f8-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="383f8-116">See also</span></span>

- [<span data-ttu-id="383f8-117">CLRDataSourceType 列挙型</span><span class="sxs-lookup"><span data-stu-id="383f8-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="383f8-118">デバッグ</span><span class="sxs-lookup"><span data-stu-id="383f8-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="383f8-119">IXCLRDataMethodDefinition インターフェイス</span><span class="sxs-lookup"><span data-stu-id="383f8-119">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
