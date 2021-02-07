---
description: 詳細については、「ICorDebugValue2 インターフェイス」を参照してください。
title: ICorDebugValue2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugValue2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2
helpviewer_keywords:
- ICorDebugValue2 interface [.NET Framework debugging]
ms.assetid: 3ff2ad2a-da5a-461b-8627-1a8eba49df9c
topic_type:
- apiref
ms.openlocfilehash: b408bb5d1732a60fc9aa8ffb93321d3542f2cab7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690263"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="cffe8-103">ICorDebugValue2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cffe8-103">ICorDebugValue2 Interface</span></span>

<span data-ttu-id="cffe8-104">"ICorDebugValue" インターフェイスを拡張して "テキスト" オブジェクトのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="cffe8-104">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cffe8-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="cffe8-105">Methods</span></span>  
  
|<span data-ttu-id="cffe8-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="cffe8-106">Method</span></span>|<span data-ttu-id="cffe8-107">説明</span><span class="sxs-lookup"><span data-stu-id="cffe8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cffe8-108">GetExactType メソッド</span><span class="sxs-lookup"><span data-stu-id="cffe8-108">GetExactType Method</span></span>](icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="cffe8-109">この値のを表すオブジェクトへのインターフェイスポインターを取得し `ICorDebugType` <xref:System.Type> ます。</span><span class="sxs-lookup"><span data-stu-id="cffe8-109">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cffe8-110">解説</span><span class="sxs-lookup"><span data-stu-id="cffe8-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cffe8-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="cffe8-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cffe8-112">要件</span><span class="sxs-lookup"><span data-stu-id="cffe8-112">Requirements</span></span>  

 <span data-ttu-id="cffe8-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cffe8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cffe8-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cffe8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cffe8-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cffe8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cffe8-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cffe8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cffe8-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="cffe8-117">See also</span></span>

- [<span data-ttu-id="cffe8-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cffe8-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

- [<span data-ttu-id="cffe8-119">ICorDebugValue3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cffe8-119">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
