---
description: '詳細情報: 「コード:: GetVersionNumber メソッド」を参照してください。'
title: ICorDebugCode::GetVersionNumber メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetVersionNumber
helpviewer_keywords:
- GetVersionNumber method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetVersionNumber method [.NET Framework debugging]
ms.assetid: c8e02518-679f-4e9f-8a28-ba4a89a3876f
topic_type:
- apiref
ms.openlocfilehash: 901342333bea3d455407602dde78bdccd0140d77
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764906"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="36d24-103">ICorDebugCode::GetVersionNumber メソッド</span><span class="sxs-lookup"><span data-stu-id="36d24-103">ICorDebugCode::GetVersionNumber Method</span></span>

<span data-ttu-id="36d24-104">この "" コード "が表すコードのバージョンを識別する、1から始まる番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="36d24-104">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>

## <a name="syntax"></a><span data-ttu-id="36d24-105">構文</span><span class="sxs-lookup"><span data-stu-id="36d24-105">Syntax</span></span>

```cpp
HRESULT GetVersionNumber (
    [out] ULONG32    *nVersion
);
```

## <a name="parameters"></a><span data-ttu-id="36d24-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="36d24-106">Parameters</span></span>

 `nVersion`  
 <span data-ttu-id="36d24-107">入出力コードのバージョン番号へのポインター。</span><span class="sxs-lookup"><span data-stu-id="36d24-107">[out] A pointer to the version number of the code.</span></span>

## <a name="remarks"></a><span data-ttu-id="36d24-108">解説</span><span class="sxs-lookup"><span data-stu-id="36d24-108">Remarks</span></span>

 <span data-ttu-id="36d24-109">バージョン番号は、エディットコンティニュ (EnC) 操作がコードで実行されるたびにインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="36d24-109">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>

## <a name="requirements"></a><span data-ttu-id="36d24-110">要件</span><span class="sxs-lookup"><span data-stu-id="36d24-110">Requirements</span></span>

 <span data-ttu-id="36d24-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36d24-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36d24-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36d24-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36d24-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36d24-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36d24-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36d24-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
