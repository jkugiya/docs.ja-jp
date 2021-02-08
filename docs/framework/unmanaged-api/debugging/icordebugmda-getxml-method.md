---
description: '詳細については、次の情報を参照してください: いいね:: GetXML メソッド'
title: ICorDebugMDA::GetXML メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
ms.openlocfilehash: fa506e6e8f306271f10a7a715af9b8bc6a80c1d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801138"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="ed20f-103">ICorDebugMDA::GetXML メソッド</span><span class="sxs-lookup"><span data-stu-id="ed20f-103">ICorDebugMDA::GetXML Method</span></span>

<span data-ttu-id="ed20f-104">[によって](icordebugmda-interface.md)表されるマネージデバッグアシスタント (MDA) に関連付けられた完全な XML ストリームを取得します。</span><span class="sxs-lookup"><span data-stu-id="ed20f-104">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed20f-105">構文</span><span class="sxs-lookup"><span data-stu-id="ed20f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed20f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ed20f-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="ed20f-107">[in] `szName` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="ed20f-107">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ed20f-108">入出力XML ストリームの長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ed20f-108">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="ed20f-109">入出力XML ストリームを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="ed20f-109">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="ed20f-110">配列が空である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ed20f-110">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed20f-111">解説</span><span class="sxs-lookup"><span data-stu-id="ed20f-111">Remarks</span></span>  

 <span data-ttu-id="ed20f-112">メソッドは、 `GetXML` 関連付けられている XML ストリームのサイズによっては、パフォーマンスに影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ed20f-112">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed20f-113">要件</span><span class="sxs-lookup"><span data-stu-id="ed20f-113">Requirements</span></span>  

 <span data-ttu-id="ed20f-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed20f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed20f-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ed20f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed20f-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed20f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed20f-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed20f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed20f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="ed20f-118">See also</span></span>

- [<span data-ttu-id="ed20f-119">ICorDebugMDA インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ed20f-119">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="ed20f-120">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="ed20f-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
