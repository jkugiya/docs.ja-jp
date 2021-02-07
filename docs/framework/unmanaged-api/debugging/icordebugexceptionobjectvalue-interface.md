---
description: '詳細については、次の情報を参照してください。: の値インターフェイス'
title: ICorDebugExceptionObjectValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue
helpviewer_keywords:
- ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type:
- apiref
ms.openlocfilehash: 67672f9921bab31019a42b742480176e6d0bf3d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693201"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="d88bd-103">ICorDebugExceptionObjectValue インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d88bd-103">ICorDebugExceptionObjectValue Interface</span></span>

<span data-ttu-id="d88bd-104">"は、マネージ例外オブジェクトからスタックトレース情報を提供するために、" は、"" のような "のインターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="d88bd-104">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d88bd-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d88bd-105">Methods</span></span>  
  
|<span data-ttu-id="d88bd-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="d88bd-106">Method</span></span>|<span data-ttu-id="d88bd-107">説明</span><span class="sxs-lookup"><span data-stu-id="d88bd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d88bd-108">EnumerateExceptionCallStack メソッド</span><span class="sxs-lookup"><span data-stu-id="d88bd-108">EnumerateExceptionCallStack Method</span></span>](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="d88bd-109">例外オブジェクトに埋め込まれている呼び出し履歴に対する列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="d88bd-109">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d88bd-110">解説</span><span class="sxs-lookup"><span data-stu-id="d88bd-110">Remarks</span></span>  

 <span data-ttu-id="d88bd-111">の呼び出しは、 `QueryInterface` から派生したマネージオブジェクトに対して成功し <xref:System.Exception?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="d88bd-111">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d88bd-112">要件</span><span class="sxs-lookup"><span data-stu-id="d88bd-112">Requirements</span></span>  

 <span data-ttu-id="d88bd-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d88bd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d88bd-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d88bd-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d88bd-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d88bd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d88bd-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d88bd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d88bd-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d88bd-117">See also</span></span>

- [<span data-ttu-id="d88bd-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d88bd-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d88bd-119">デバッグ</span><span class="sxs-lookup"><span data-stu-id="d88bd-119">Debugging</span></span>](index.md)
