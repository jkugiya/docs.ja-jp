---
description: 詳細については、「ICorDebugAppDomain2 インターフェイス」を参照してください。
title: ICorDebugAppDomain2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2
helpviewer_keywords:
- ICorDebugAppDomain2 interface [.NET Framework debugging]
ms.assetid: 314d29f3-feb0-4a92-9530-b569c280cc31
topic_type:
- apiref
ms.openlocfilehash: 2f2fcc4166a0c825abaa04392f9905d17e286803
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754187"
---
# <a name="icordebugappdomain2-interface"></a><span data-ttu-id="8427f-103">ICorDebugAppDomain2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8427f-103">ICorDebugAppDomain2 Interface</span></span>

<span data-ttu-id="8427f-104">配列、ポインター、関数ポインター、および参照型を操作するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="8427f-104">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="8427f-105">このインターフェイスは、の機能を持つ Appdomain インターフェイスの拡張です。</span><span class="sxs-lookup"><span data-stu-id="8427f-105">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8427f-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="8427f-106">Methods</span></span>  
  
|<span data-ttu-id="8427f-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="8427f-107">Method</span></span>|<span data-ttu-id="8427f-108">説明</span><span class="sxs-lookup"><span data-stu-id="8427f-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8427f-109">GetArrayOrPointerType メソッド</span><span class="sxs-lookup"><span data-stu-id="8427f-109">GetArrayOrPointerType Method</span></span>](icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="8427f-110">指定した型、または指定した型へのポインターまたは参照の配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="8427f-110">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="8427f-111">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="8427f-111">GetFunctionPointerType</span></span>](icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="8427f-112">指定されたシグネチャを持つ関数へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="8427f-112">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8427f-113">解説</span><span class="sxs-lookup"><span data-stu-id="8427f-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8427f-114">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="8427f-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8427f-115">要件</span><span class="sxs-lookup"><span data-stu-id="8427f-115">Requirements</span></span>  

 <span data-ttu-id="8427f-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8427f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8427f-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8427f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8427f-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8427f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8427f-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8427f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8427f-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="8427f-120">See also</span></span>

- [<span data-ttu-id="8427f-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8427f-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
