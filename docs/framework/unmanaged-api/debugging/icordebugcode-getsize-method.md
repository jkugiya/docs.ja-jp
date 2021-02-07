---
description: '詳細情報: 「コード:: GetSize メソッド」を参照してください。'
title: ICorDebugCode::GetSize メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetSize method [.NET Framework debugging]
ms.assetid: 115bc6de-f5e2-4e8e-bb38-c7cf54045434
topic_type:
- apiref
ms.openlocfilehash: 5a244d649cdcf027aea22ab36ff5d39a77a05e1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711181"
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="444b9-103">ICorDebugCode::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="444b9-103">ICorDebugCode::GetSize Method</span></span>

<span data-ttu-id="444b9-104">この "コード" によって表されるバイナリコードのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="444b9-104">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>

## <a name="syntax"></a><span data-ttu-id="444b9-105">構文</span><span class="sxs-lookup"><span data-stu-id="444b9-105">Syntax</span></span>

```cpp
HRESULT GetSize (
    [out] ULONG32    *pcBytes
);
```

## <a name="parameters"></a><span data-ttu-id="444b9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="444b9-106">Parameters</span></span>

`pcBytes`  
<span data-ttu-id="444b9-107">入出力このオブジェクトが表すバイナリコードのサイズ (バイト単位) へのポインター `ICorDebugCode` 。</span><span class="sxs-lookup"><span data-stu-id="444b9-107">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>

## <a name="requirements"></a><span data-ttu-id="444b9-108">要件</span><span class="sxs-lookup"><span data-stu-id="444b9-108">Requirements</span></span>

<span data-ttu-id="444b9-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="444b9-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="444b9-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="444b9-110">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="444b9-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="444b9-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="444b9-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="444b9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
