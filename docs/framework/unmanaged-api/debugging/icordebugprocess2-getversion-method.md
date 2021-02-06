---
description: '詳細について: ICorDebugProcess2:: GetVersion メソッド'
title: ICorDebugProcess2::GetVersion メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetVersion
helpviewer_keywords:
- GetVersion method, ICorDebugProcess2 interface [.NET Framework debugging]
- ICorDebugProcess2::GetVersion method [.NET Framework debugging]
ms.assetid: e11d5a75-61d9-4548-aedf-79c26079bd17
topic_type:
- apiref
ms.openlocfilehash: 8472e811ea4df1f99fb4e27b55f3561fae0c8a21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650101"
---
# <a name="icordebugprocess2getversion-method"></a><span data-ttu-id="0d2eb-103">ICorDebugProcess2::GetVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="0d2eb-103">ICorDebugProcess2::GetVersion Method</span></span>

<span data-ttu-id="0d2eb-104">このプロセスで実行されている共通言語ランタイム (CLR) のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="0d2eb-104">Gets the version number of the common language runtime (CLR) that is running in this process.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d2eb-105">構文</span><span class="sxs-lookup"><span data-stu-id="0d2eb-105">Syntax</span></span>

```cpp
HRESULT GetVersion (
    [out] COR_VERSION     *version
);
```

## <a name="parameters"></a><span data-ttu-id="0d2eb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0d2eb-106">Parameters</span></span>

`version`\
<span data-ttu-id="0d2eb-107">入出力ランタイムのバージョン番号を格納する COR_VERSION 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0d2eb-107">[out] A pointer to a COR_VERSION structure that stores the version number of the runtime.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d2eb-108">解説</span><span class="sxs-lookup"><span data-stu-id="0d2eb-108">Remarks</span></span>

<span data-ttu-id="0d2eb-109">`GetVersion`プロセスにランタイムが読み込まれていない場合、メソッドはエラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="0d2eb-109">The `GetVersion` method returns an error code if no runtime has been loaded in the process.</span></span>

## <a name="requirements"></a><span data-ttu-id="0d2eb-110">要件</span><span class="sxs-lookup"><span data-stu-id="0d2eb-110">Requirements</span></span>

<span data-ttu-id="0d2eb-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d2eb-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="0d2eb-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d2eb-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="0d2eb-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d2eb-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="0d2eb-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d2eb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
