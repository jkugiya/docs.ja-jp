---
description: '詳細について: ICorDebugCode2:: GetCompilerFlags メソッド'
title: ICorDebugCode2::GetCompilerFlags メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCompilerFlags
helpviewer_keywords:
- GetCompilerFlags method [.NET Framework debugging]
- ICorDebugCode2::GetCompilerFlags method [.NET Framework debugging]
ms.assetid: 532e9dfd-d114-4c75-b952-1accce102643
topic_type:
- apiref
ms.openlocfilehash: 820b6d2392b2b91bbfc8a85b165c4d73a2546859
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711119"
---
# <a name="icordebugcode2getcompilerflags-method"></a><span data-ttu-id="8449b-103">ICorDebugCode2::GetCompilerFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="8449b-103">ICorDebugCode2::GetCompilerFlags Method</span></span>

<span data-ttu-id="8449b-104">このコード オブジェクトが Just-In-Time (JIT) コンパイルされたとき、またはネイティブ イメージ ジェネレーター (Ngen.exe) を使用して生成されたときの条件を指定するフラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="8449b-104">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>

## <a name="syntax"></a><span data-ttu-id="8449b-105">構文</span><span class="sxs-lookup"><span data-stu-id="8449b-105">Syntax</span></span>

```cpp
HRESULT GetCompilerFlags (
    [out] DWORD *pdwFlags
);
```

## <a name="parameters"></a><span data-ttu-id="8449b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8449b-106">Parameters</span></span>

`pdwFlags`  
<span data-ttu-id="8449b-107">入出力JIT コンパイラまたはネイティブイメージジェネレーターの動作を指定する [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) 列挙値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8449b-107">[out] A pointer to a value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that specifies the behavior of the JIT compiler or the native image generator.</span></span>

## <a name="requirements"></a><span data-ttu-id="8449b-108">要件</span><span class="sxs-lookup"><span data-stu-id="8449b-108">Requirements</span></span>

<span data-ttu-id="8449b-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8449b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="8449b-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8449b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="8449b-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8449b-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="8449b-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8449b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
