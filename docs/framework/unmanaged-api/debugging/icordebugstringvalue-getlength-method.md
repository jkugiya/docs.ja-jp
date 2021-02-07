---
description: '詳細については、次を参照してください: GetLength メソッド'
title: ICorDebugStringValue::GetLength メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetLength
helpviewer_keywords:
- ICorDebugStringValue::GetLength method [.NET Framework debugging]
- GetLength method [.NET Framework debugging]
ms.assetid: a1ebfc69-46a6-4225-8788-b7cfb2f15e1d
topic_type:
- apiref
ms.openlocfilehash: ae4d42b5b65e5f80e884415a5acfc7f894ffe11e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717382"
---
# <a name="icordebugstringvaluegetlength-method"></a><span data-ttu-id="c6e89-103">ICorDebugStringValue::GetLength メソッド</span><span class="sxs-lookup"><span data-stu-id="c6e89-103">ICorDebugStringValue::GetLength Method</span></span>

<span data-ttu-id="c6e89-104">このによって参照される文字列の文字数を取得します。</span><span class="sxs-lookup"><span data-stu-id="c6e89-104">Gets the number of characters in the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6e89-105">構文</span><span class="sxs-lookup"><span data-stu-id="c6e89-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLength (  
    [out] ULONG32   *pcchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6e89-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c6e89-106">Parameters</span></span>  

 `pcchString`  
 <span data-ttu-id="c6e89-107">入出力このオブジェクトによって参照される文字列の長さを指定する値へのポインター `ICorDebugStringValue` 。</span><span class="sxs-lookup"><span data-stu-id="c6e89-107">[out] A pointer to a value that specifies the length of the string referenced by this `ICorDebugStringValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6e89-108">要件</span><span class="sxs-lookup"><span data-stu-id="c6e89-108">Requirements</span></span>  

 <span data-ttu-id="c6e89-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6e89-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6e89-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6e89-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6e89-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6e89-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6e89-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6e89-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
