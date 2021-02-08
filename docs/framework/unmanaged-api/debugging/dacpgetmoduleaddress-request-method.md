---
description: '詳細情報: DacpGetModuleAddress:: Request メソッド'
title: DacpGetModuleAddress::Request メソッド
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress::Request Method
helpviewer.keywords:
- DacpGetModuleAddress::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4cdec9cf6b9bd818ce1137fb5b2c691532fab94e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801502"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="871e6-103">DacpGetModuleAddress::Request メソッド</span><span class="sxs-lookup"><span data-stu-id="871e6-103">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="871e6-104">指定されたランタイム構造体を構造体に設定する要求を実行します。</span><span class="sxs-lookup"><span data-stu-id="871e6-104">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="871e6-105">構文</span><span class="sxs-lookup"><span data-stu-id="871e6-105">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="871e6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="871e6-106">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="871e6-107">からシードデータモジュールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="871e6-107">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="871e6-108">解説</span><span class="sxs-lookup"><span data-stu-id="871e6-108">Remarks</span></span>

<span data-ttu-id="871e6-109">この構造体はランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="871e6-109">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="871e6-110">これを使用する最も簡単な方法は、実装を模倣することです。</span><span class="sxs-lookup"><span data-stu-id="871e6-110">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="871e6-111">次のパラメーターを使用して、パラメーターのメソッドの呼び出しから取得した値を返し `Request` `IXCLRDataModule*` ます。 `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="871e6-111">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="871e6-112">要件</span><span class="sxs-lookup"><span data-stu-id="871e6-112">Requirements</span></span>

<span data-ttu-id="871e6-113">**プラットフォーム:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="871e6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md)</span></span>\
<span data-ttu-id="871e6-114">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="871e6-114">**Header:** None\</span></span>
<span data-ttu-id="871e6-115">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="871e6-115">**Library:** None\</span></span>
<span data-ttu-id="871e6-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="871e6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="871e6-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="871e6-117">See also</span></span>

- [<span data-ttu-id="871e6-118">デバッグ</span><span class="sxs-lookup"><span data-stu-id="871e6-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="871e6-119">DacpGetModuleAddress 構造体</span><span class="sxs-lookup"><span data-stu-id="871e6-119">DacpGetModuleAddress structure</span></span>](dacpgetmoduleaddress-structure.md)
