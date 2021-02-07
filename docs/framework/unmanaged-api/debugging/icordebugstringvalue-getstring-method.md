---
description: '詳細については、次を参照してください: GetString メソッド'
title: ICorDebugStringValue::GetString メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetString
helpviewer_keywords:
- ICorDebugStringValue::GetString method [.NET Framework debugging]
- GetString method, ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: 2b94bda7-09ee-435d-91b9-c4e31af1896c
topic_type:
- apiref
ms.openlocfilehash: 06e8e039c8b0afb7753a398302a9b32eb3ba7213
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717343"
---
# <a name="icordebugstringvaluegetstring-method"></a><span data-ttu-id="5ea0b-103">ICorDebugStringValue::GetString メソッド</span><span class="sxs-lookup"><span data-stu-id="5ea0b-103">ICorDebugStringValue::GetString Method</span></span>

<span data-ttu-id="5ea0b-104">このによって参照される文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="5ea0b-104">Gets the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ea0b-105">構文</span><span class="sxs-lookup"><span data-stu-id="5ea0b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]
        WCHAR       szString[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ea0b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5ea0b-106">Parameters</span></span>  

 `cchString`  
 <span data-ttu-id="5ea0b-107">[in] `szString` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="5ea0b-107">[in] The size of the `szString` array.</span></span>  
  
 `pcchString`  
 <span data-ttu-id="5ea0b-108">入出力配列で返された文字数へのポインター `szString` 。</span><span class="sxs-lookup"><span data-stu-id="5ea0b-108">[out] A pointer to the number of characters returned in the `szString` array.</span></span>  
  
 `szString`  
 <span data-ttu-id="5ea0b-109">入出力取得した文字列を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="5ea0b-109">[out] An array that stores the retrieved string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ea0b-110">要件</span><span class="sxs-lookup"><span data-stu-id="5ea0b-110">Requirements</span></span>  

 <span data-ttu-id="5ea0b-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ea0b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ea0b-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ea0b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ea0b-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ea0b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ea0b-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ea0b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
