---
description: 詳細については、「ICorDebugProcess4 インターフェイス」を参照してください。
title: ICorDebugProcess4 インターフェイス
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4
helpviewer_keywords:
- ICorDebugProcess4 interface [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 16c7f3fbd1a79b1406fe0c19a9d922964667a2a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650002"
---
# <a name="icordebugprocess4-interface"></a><span data-ttu-id="21871-103">ICorDebugProcess4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="21871-103">ICorDebugProcess4 Interface</span></span>

<span data-ttu-id="21871-104">アウトプロセス実行制御のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="21871-104">Provides support for out of process execution control.</span></span>

## <a name="methods"></a><span data-ttu-id="21871-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="21871-105">Methods</span></span>

| <span data-ttu-id="21871-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="21871-106">Method</span></span>                                                                 | <span data-ttu-id="21871-107">説明</span><span class="sxs-lookup"><span data-stu-id="21871-107">Description</span></span>                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="21871-108">ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="21871-108">ProcessStateChanged</span></span>](icordebugprocess4-processstatechanged-method.md) | <span data-ttu-id="21871-109">アウトプロセスデバッガーがデバッグ対象の実行を継続していることを ICorDebug パイプラインに通知します。</span><span class="sxs-lookup"><span data-stu-id="21871-109">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span> |

## <a name="remarks"></a><span data-ttu-id="21871-110">解説</span><span class="sxs-lookup"><span data-stu-id="21871-110">Remarks</span></span>

<span data-ttu-id="21871-111">このインターフェイスはランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="21871-111">This interface lives inside the runtime and isn't exposed through any headers or library files.</span></span> <span data-ttu-id="21871-112">ただし、これは、 `IUnknown` `E930C679-78AF-4953-8AB7-B0AABF0F9F80` 通常の com 機構を通じて取得できる GUID を使用してから派生する com インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="21871-112">However, it's a COM interface that derives from `IUnknown` with GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="21871-113">要件</span><span class="sxs-lookup"><span data-stu-id="21871-113">Requirements</span></span>

<span data-ttu-id="21871-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21871-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="21871-115">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="21871-115">**Header:** None</span></span>

<span data-ttu-id="21871-116">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="21871-116">**Library:** None</span></span>

<span data-ttu-id="21871-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21871-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="21871-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="21871-118">See also</span></span>

- [<span data-ttu-id="21871-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="21871-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="21871-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="21871-120">Debugging</span></span>](index.md)
