---
description: '詳細情報: 「コード:: IsIL メソッド」を参照してください。'
title: ICorDebugCode::IsIL メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode.IsIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type:
- apiref
ms.openlocfilehash: db41f9ebaa6a6403b21e10d1daa0e8b167c7cb96
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711127"
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="06a6f-103">ICorDebugCode::IsIL メソッド</span><span class="sxs-lookup"><span data-stu-id="06a6f-103">ICorDebugCode::IsIL Method</span></span>

<span data-ttu-id="06a6f-104">この "コードが、Microsoft 中間言語 (MSIL) でコンパイルされたコードを表しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="06a6f-104">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>

## <a name="syntax"></a><span data-ttu-id="06a6f-105">構文</span><span class="sxs-lookup"><span data-stu-id="06a6f-105">Syntax</span></span>

```cpp
HRESULT IsIL (
    [out] BOOL       *pbIL
);
```

## <a name="parameters"></a><span data-ttu-id="06a6f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="06a6f-106">Parameters</span></span>

`pbIL`  
<span data-ttu-id="06a6f-107">[出力] `true` このが `ICorDebugCode` MSIL でコンパイルされたコードを表す場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="06a6f-107">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="06a6f-108">要件</span><span class="sxs-lookup"><span data-stu-id="06a6f-108">Requirements</span></span>

<span data-ttu-id="06a6f-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06a6f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="06a6f-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06a6f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="06a6f-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06a6f-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="06a6f-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06a6f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
