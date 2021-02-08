---
description: ': ISOSDacInterface:: GetModuleData メソッドの詳細について説明します。'
title: 'ISOSDacInterface:: GetModuleData メソッド'
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetModuleData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetModuleData Method
helpviewer.keywords:
- ISOSDacInterface::GetModuleData Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: c01f55d55d5ee9082dee4b3adb3022bb17807aa2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790387"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="40a2c-103">ISOSDacInterface:: GetModuleData メソッド</span><span class="sxs-lookup"><span data-stu-id="40a2c-103">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="40a2c-104">指定したアドレスに読み込まれたモジュールに対応するデータをフェッチします。</span><span class="sxs-lookup"><span data-stu-id="40a2c-104">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="40a2c-105">構文</span><span class="sxs-lookup"><span data-stu-id="40a2c-105">Syntax</span></span>

```cpp
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a><span data-ttu-id="40a2c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="40a2c-106">Parameters</span></span>

`moduleAddr`\
<span data-ttu-id="40a2c-107">から情報を取得するモジュールのアドレス。</span><span class="sxs-lookup"><span data-stu-id="40a2c-107">[in] The address of the module to retrieve information for.</span></span>

`data`\
<span data-ttu-id="40a2c-108">入出力読み込まれたモジュールの情報を保持する [Dacpmoduledata 構造体](dacpmoduledata-structure.md) 。</span><span class="sxs-lookup"><span data-stu-id="40a2c-108">[out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>

## <a name="remarks"></a><span data-ttu-id="40a2c-109">解説</span><span class="sxs-lookup"><span data-stu-id="40a2c-109">Remarks</span></span>

<span data-ttu-id="40a2c-110">指定されたメソッドはインターフェイスの一部で `ISOSDacInterface` あり、仮想メソッドテーブルの14番目のスロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="40a2c-110">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 14th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="40a2c-111">要件</span><span class="sxs-lookup"><span data-stu-id="40a2c-111">Requirements</span></span>

<span data-ttu-id="40a2c-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40a2c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="40a2c-113">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="40a2c-113">**Header:** None</span></span>  
<span data-ttu-id="40a2c-114">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="40a2c-114">**Library:** None</span></span>  
<span data-ttu-id="40a2c-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="40a2c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="40a2c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="40a2c-116">See also</span></span>

- [<span data-ttu-id="40a2c-117">デバッグ</span><span class="sxs-lookup"><span data-stu-id="40a2c-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="40a2c-118">ISOSDacInterface インターフェイス</span><span class="sxs-lookup"><span data-stu-id="40a2c-118">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
