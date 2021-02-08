---
description: '詳細については、次のページを参照してください: いいね:: GetName メソッド'
title: ICorDebugMDA::GetName メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetName
helpviewer_keywords:
- ICorDebugMDA::GetName method [.NET Framework debugging]
- GetName method, ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 885bf5e8-00b7-4cd7-9d8d-e720d47918c4
topic_type:
- apiref
ms.openlocfilehash: 4ea39f062071073684a20d8f60875fbaaab43a2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801167"
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="6a6ec-103">ICorDebugMDA::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="6a6ec-103">ICorDebugMDA::GetName Method</span></span>

<span data-ttu-id="6a6ec-104">によって表されるマネージデバッグアシスタント (MDA) の名前を含む文字列を [取得します](icordebugmda-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="6a6ec-104">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a6ec-105">構文</span><span class="sxs-lookup"><span data-stu-id="6a6ec-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a6ec-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6a6ec-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="6a6ec-107">[in] `szName` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="6a6ec-107">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="6a6ec-108">入出力名前の長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6a6ec-108">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="6a6ec-109">入出力名前を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="6a6ec-109">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a6ec-110">解説</span><span class="sxs-lookup"><span data-stu-id="6a6ec-110">Remarks</span></span>  

 <span data-ttu-id="6a6ec-111">MDA 名は一意の値です。</span><span class="sxs-lookup"><span data-stu-id="6a6ec-111">MDA names are unique values.</span></span> <span data-ttu-id="6a6ec-112">この `GetName` メソッドは、XML ストリームを取得し、そのスキーマに基づいてストリームから名前を抽出する場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="6a6ec-112">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a6ec-113">要件</span><span class="sxs-lookup"><span data-stu-id="6a6ec-113">Requirements</span></span>  

 <span data-ttu-id="6a6ec-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a6ec-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a6ec-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a6ec-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a6ec-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a6ec-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a6ec-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a6ec-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a6ec-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="6a6ec-118">See also</span></span>

- [<span data-ttu-id="6a6ec-119">ICorDebugMDA インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6a6ec-119">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="6a6ec-120">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="6a6ec-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
