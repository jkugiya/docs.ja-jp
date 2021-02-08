---
description: '詳細については、次を参照してください: IXCLRDataModule:: GetMethodDefinitionByToken メソッド'
title: 'IXCLRDataModule:: GetMethodDefinitionByToken メソッド'
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetMethodDefinitionByToken Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method
helpviewer.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 1eb1187d09183bfff97324a8032d23cbf471f580
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800774"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="d6c2f-103">IXCLRDataModule:: GetMethodDefinitionByToken メソッド</span><span class="sxs-lookup"><span data-stu-id="d6c2f-103">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="d6c2f-104">指定されたメタデータトークンに対応するメソッド定義を取得します。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-104">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d6c2f-105">構文</span><span class="sxs-lookup"><span data-stu-id="d6c2f-105">Syntax</span></span>

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="d6c2f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d6c2f-106">Parameters</span></span>

`token`\
<span data-ttu-id="d6c2f-107">からメソッドトークン。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-107">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="d6c2f-108">入出力メソッドの定義。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-108">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="d6c2f-109">解説</span><span class="sxs-lookup"><span data-stu-id="d6c2f-109">Remarks</span></span>

<span data-ttu-id="d6c2f-110">指定されたメソッドはインターフェイスの一部で `IXCLRDataModule` あり、仮想メソッドテーブルの26日スロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-110">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="d6c2f-111">要件</span><span class="sxs-lookup"><span data-stu-id="d6c2f-111">Requirements</span></span>

<span data-ttu-id="d6c2f-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6c2f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d6c2f-113">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="d6c2f-113">**Header:** None</span></span>  
<span data-ttu-id="d6c2f-114">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="d6c2f-114">**Library:** None</span></span>  
<span data-ttu-id="d6c2f-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d6c2f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d6c2f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6c2f-116">See also</span></span>

- [<span data-ttu-id="d6c2f-117">デバッグ</span><span class="sxs-lookup"><span data-stu-id="d6c2f-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="d6c2f-118">IXCLRDataModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6c2f-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
