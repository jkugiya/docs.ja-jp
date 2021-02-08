---
description: '詳細については、次を参照してください: いいね。'
title: ICorDebugMDA インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
ms.openlocfilehash: 8e6e779c58d71b07edc9b63dff72aef728ebe050
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801125"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="862bc-103">ICorDebugMDA インターフェイス</span><span class="sxs-lookup"><span data-stu-id="862bc-103">ICorDebugMDA Interface</span></span>

<span data-ttu-id="862bc-104">マネージド デバッグ アシスタント (MDA) メッセージを表します。</span><span class="sxs-lookup"><span data-stu-id="862bc-104">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="862bc-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="862bc-105">Methods</span></span>  
  
|<span data-ttu-id="862bc-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="862bc-106">Method</span></span>|<span data-ttu-id="862bc-107">説明</span><span class="sxs-lookup"><span data-stu-id="862bc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="862bc-108">GetDescription メソッド</span><span class="sxs-lookup"><span data-stu-id="862bc-108">GetDescription Method</span></span>](icordebugmda-getdescription-method.md)|<span data-ttu-id="862bc-109">この MDA の説明を格納している文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="862bc-109">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="862bc-110">GetFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="862bc-110">GetFlags Method</span></span>](icordebugmda-getflags-method.md)|<span data-ttu-id="862bc-111">この MDA に関連付けられているフラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="862bc-111">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="862bc-112">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="862bc-112">GetName Method</span></span>](icordebugmda-getname-method.md)|<span data-ttu-id="862bc-113">この MDA の名前を格納している文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="862bc-113">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="862bc-114">GetOSThreadId メソッド</span><span class="sxs-lookup"><span data-stu-id="862bc-114">GetOSThreadId Method</span></span>](icordebugmda-getosthreadid-method.md)|<span data-ttu-id="862bc-115">この MDA が実行されているオペレーティングシステムのスレッド id を取得します。</span><span class="sxs-lookup"><span data-stu-id="862bc-115">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="862bc-116">GetXML メソッド</span><span class="sxs-lookup"><span data-stu-id="862bc-116">GetXML Method</span></span>](icordebugmda-getxml-method.md)|<span data-ttu-id="862bc-117">この MDA に関連付けられている XML の完全ストリームを取得します。</span><span class="sxs-lookup"><span data-stu-id="862bc-117">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="862bc-118">解説</span><span class="sxs-lookup"><span data-stu-id="862bc-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="862bc-119">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="862bc-119">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="862bc-120">要件</span><span class="sxs-lookup"><span data-stu-id="862bc-120">Requirements</span></span>  

 <span data-ttu-id="862bc-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="862bc-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="862bc-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="862bc-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="862bc-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="862bc-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="862bc-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="862bc-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="862bc-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="862bc-125">See also</span></span>

- [<span data-ttu-id="862bc-126">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="862bc-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="862bc-127">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="862bc-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
