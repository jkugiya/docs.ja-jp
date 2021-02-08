---
description: '詳細について: IXCLRDataModule:: GetVersionId メソッド'
title: 'IXCLRDataModule:: GetVersionId メソッド'
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetVersionId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetVersionId Method
helpviewer.keywords:
- IXCLRDataModule::GetVersionId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 1b924757f43d106df555ea028270ac873f8f4558
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800761"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="66195-103">IXCLRDataModule:: GetVersionId メソッド</span><span class="sxs-lookup"><span data-stu-id="66195-103">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="66195-104">モジュールのバージョン識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="66195-104">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="66195-105">構文</span><span class="sxs-lookup"><span data-stu-id="66195-105">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="66195-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="66195-106">Parameters</span></span>

`vid`\
<span data-ttu-id="66195-107">入出力モジュールのバージョン識別子。</span><span class="sxs-lookup"><span data-stu-id="66195-107">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="66195-108">解説</span><span class="sxs-lookup"><span data-stu-id="66195-108">Remarks</span></span>

<span data-ttu-id="66195-109">指定されたメソッドはインターフェイスの一部で `IXCLRDataModule` あり、仮想メソッドテーブルの4番目のスロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="66195-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 41st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="66195-110">要件</span><span class="sxs-lookup"><span data-stu-id="66195-110">Requirements</span></span>

<span data-ttu-id="66195-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66195-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="66195-112">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="66195-112">**Header:** None</span></span>  
<span data-ttu-id="66195-113">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="66195-113">**Library:** None</span></span>  
<span data-ttu-id="66195-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="66195-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="66195-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="66195-115">See also</span></span>

- [<span data-ttu-id="66195-116">デバッグ</span><span class="sxs-lookup"><span data-stu-id="66195-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="66195-117">IXCLRDataModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="66195-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
