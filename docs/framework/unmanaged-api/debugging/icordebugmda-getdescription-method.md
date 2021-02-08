---
description: '詳細については、次のページを参照してください: いいね:: GetDescription メソッド'
title: ICorDebugMDA::GetDescription メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetDescription
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetDescription
helpviewer_keywords:
- GetDescription method [.NET Framework debugging]
- ICorDebugMDA::GetDescription method [.NET Framework debugging]
ms.assetid: 01d1b481-ca67-4712-8744-d342ec0df639
topic_type:
- apiref
ms.openlocfilehash: 75ee7d0b912c9f0039acc872173f2cbad25fff38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801203"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="ffba1-103">ICorDebugMDA::GetDescription メソッド</span><span class="sxs-lookup"><span data-stu-id="ffba1-103">ICorDebugMDA::GetDescription Method</span></span>

<span data-ttu-id="ffba1-104">によって表されるマネージデバッグアシスタント (MDA) の説明を含む文字列を [取得します](icordebugmda-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="ffba1-104">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffba1-105">構文</span><span class="sxs-lookup"><span data-stu-id="ffba1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffba1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ffba1-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="ffba1-107">から説明を格納する文字列バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="ffba1-107">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ffba1-108">入出力文字列バッファーで返されたバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ffba1-108">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="ffba1-109">入出力MDA の説明を格納している文字列バッファー。</span><span class="sxs-lookup"><span data-stu-id="ffba1-109">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffba1-110">解説</span><span class="sxs-lookup"><span data-stu-id="ffba1-110">Remarks</span></span>  

 <span data-ttu-id="ffba1-111">文字列の長さは0にすることができます。</span><span class="sxs-lookup"><span data-stu-id="ffba1-111">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffba1-112">要件</span><span class="sxs-lookup"><span data-stu-id="ffba1-112">Requirements</span></span>  

 <span data-ttu-id="ffba1-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffba1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffba1-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ffba1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ffba1-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ffba1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffba1-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffba1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffba1-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="ffba1-117">See also</span></span>

- [<span data-ttu-id="ffba1-118">ICorDebugMDA インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ffba1-118">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="ffba1-119">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="ffba1-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
