---
description: '詳細については、次の情報を参照してください: の値インターフェイス'
title: ICorDebugHeapValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
ms.openlocfilehash: 7c65cbce530f0d1f00d8610031fb604a0118ee29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803686"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="88677-103">ICorDebugHeapValue インターフェイス</span><span class="sxs-lookup"><span data-stu-id="88677-103">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="88677-104">共通言語ランタイム (CLR) ガベージコレクターによって収集されたオブジェクトを表す "ICorDebugValue" のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="88677-104">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="88677-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="88677-105">Methods</span></span>  
  
|<span data-ttu-id="88677-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="88677-106">Method</span></span>|<span data-ttu-id="88677-107">説明</span><span class="sxs-lookup"><span data-stu-id="88677-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="88677-108">CreateRelocBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="88677-108">CreateRelocBreakpoint Method</span></span>](icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="88677-109">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="88677-109">Not implemented.</span></span>|  
|[<span data-ttu-id="88677-110">IsValid メソッド</span><span class="sxs-lookup"><span data-stu-id="88677-110">IsValid Method</span></span>](icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="88677-111">このによって表されるオブジェクトが有効かどうか、 `ICorDebugHeapValue` またはガベージコレクターによって解放されたかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="88677-111">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="88677-112">このメソッドは .NET Framework バージョン2.0 では非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="88677-112">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88677-113">解説</span><span class="sxs-lookup"><span data-stu-id="88677-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88677-114">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="88677-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88677-115">要件</span><span class="sxs-lookup"><span data-stu-id="88677-115">Requirements</span></span>  

 <span data-ttu-id="88677-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88677-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88677-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88677-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88677-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88677-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88677-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88677-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88677-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="88677-120">See also</span></span>

- [<span data-ttu-id="88677-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="88677-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
