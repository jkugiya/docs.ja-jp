---
description: '詳細について: ICorDebugProcess4::P rocessStateChanged メソッド'
title: ICorDebugProcess4::P rocessStateChanged メソッド
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4::ProcessStateChanged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4::ProcessStateChanged
helpviewer_keywords:
- ICorDebugProcess4::ProcessStateChanged method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 35a76b3c6dd9b37d3f06f23bc2ffea82f125a29e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746471"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="b1a27-103">ICorDebugProcess4::P rocessStateChanged メソッド</span><span class="sxs-lookup"><span data-stu-id="b1a27-103">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="b1a27-104">アウトプロセスデバッガーがデバッグ対象の実行を継続していることを ICorDebug パイプラインに通知します。</span><span class="sxs-lookup"><span data-stu-id="b1a27-104">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="b1a27-105">構文</span><span class="sxs-lookup"><span data-stu-id="b1a27-105">Syntax</span></span>

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="b1a27-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b1a27-106">Parameters</span></span>

 `eChange`\
<span data-ttu-id="b1a27-107">からプロセスの実行状態の変更を記述する [CorDebugStateChange 列挙体](cordebugstatechange-enumeration.md) のメンバー。</span><span class="sxs-lookup"><span data-stu-id="b1a27-107">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="b1a27-108">解説</span><span class="sxs-lookup"><span data-stu-id="b1a27-108">Remarks</span></span>

<span data-ttu-id="b1a27-109">指定されたメソッドはインターフェイスの一部で `ICorDebugProcess4` あり、仮想メソッドテーブルの4番目のスロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="b1a27-109">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="b1a27-110">要件</span><span class="sxs-lookup"><span data-stu-id="b1a27-110">Requirements</span></span>

 <span data-ttu-id="b1a27-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1a27-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="b1a27-112">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="b1a27-112">**Header:** None</span></span>

 <span data-ttu-id="b1a27-113">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="b1a27-113">**Library:** None</span></span>

 <span data-ttu-id="b1a27-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1a27-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b1a27-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1a27-115">See also</span></span>

- [<span data-ttu-id="b1a27-116">ICorDebugProcess4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b1a27-116">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="b1a27-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b1a27-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b1a27-118">デバッグ</span><span class="sxs-lookup"><span data-stu-id="b1a27-118">Debugging</span></span>](index.md)
