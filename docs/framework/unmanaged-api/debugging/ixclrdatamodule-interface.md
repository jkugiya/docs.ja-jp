---
description: 詳細については、「IXCLRDataModule インターフェイス」を参照してください。
title: IXCLRDataModule インターフェイス
ms.date: 01/16/2019
api.name:
- IXCLRDataModule Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule Interface
helpviewer.keywords:
- IXCLRDataModule Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 403d4dd3db64f2855347562da7217a3562985c7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800748"
---
# <a name="ixclrdatamodule-interface"></a><span data-ttu-id="3bb7d-103">IXCLRDataModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3bb7d-103">IXCLRDataModule Interface</span></span>

<span data-ttu-id="3bb7d-104">読み込まれたモジュールに関する情報を照会するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="3bb7d-104">Provides methods for querying information about a loaded module.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="3bb7d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3bb7d-105">Methods</span></span>

| <span data-ttu-id="3bb7d-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="3bb7d-106">Method</span></span>                                                                                                                                | <span data-ttu-id="3bb7d-107">説明</span><span class="sxs-lookup"><span data-stu-id="3bb7d-107">Description</span></span>                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="3bb7d-108">GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="3bb7d-108">GetMethodDefinitionByToken</span></span>](ixclrdatamodule-getmethoddefinitionbytoken-method.md) | <span data-ttu-id="3bb7d-109">指定されたメタデータトークンに対応するメソッド定義を取得します。</span><span class="sxs-lookup"><span data-stu-id="3bb7d-109">Gets the method definition corresponding to a given metadata token.</span></span> |
| [<span data-ttu-id="3bb7d-110">Request</span><span class="sxs-lookup"><span data-stu-id="3bb7d-110">Request</span></span>](ixclrdatamodule-request-method.md)                                       | <span data-ttu-id="3bb7d-111">モジュールのデータで指定されたバッファーへの読み込みを要求します。</span><span class="sxs-lookup"><span data-stu-id="3bb7d-111">Requests to populate the buffer given with the module's data.</span></span>       |
| [<span data-ttu-id="3bb7d-112">GetVersionId</span><span class="sxs-lookup"><span data-stu-id="3bb7d-112">GetVersionId</span></span>](ixclrdatamodule-getversionid-method.md)                             | <span data-ttu-id="3bb7d-113">モジュールのバージョン ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="3bb7d-113">Gets the module's version ID.</span></span>                                       |

## <a name="remarks"></a><span data-ttu-id="3bb7d-114">解説</span><span class="sxs-lookup"><span data-stu-id="3bb7d-114">Remarks</span></span>

<span data-ttu-id="3bb7d-115">このインターフェイスはランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="3bb7d-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="3bb7d-116">ただし、これは、 `IUnknown` `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` 通常の com 機構を通じて取得できる GUID を使用してから派生する com インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="3bb7d-116">However, it's a COM interface that derives from `IUnknown` with GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="3bb7d-117">要件</span><span class="sxs-lookup"><span data-stu-id="3bb7d-117">Requirements</span></span>

<span data-ttu-id="3bb7d-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bb7d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="3bb7d-119">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="3bb7d-119">**Header:** None</span></span>  
<span data-ttu-id="3bb7d-120">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="3bb7d-120">**Library:** None</span></span>  
<span data-ttu-id="3bb7d-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3bb7d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3bb7d-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="3bb7d-122">See also</span></span>

- [<span data-ttu-id="3bb7d-123">デバッグ</span><span class="sxs-lookup"><span data-stu-id="3bb7d-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="3bb7d-124">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3bb7d-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
