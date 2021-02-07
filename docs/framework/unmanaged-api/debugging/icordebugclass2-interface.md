---
description: 詳細については、「ICorDebugClass2 インターフェイス」を参照してください。
title: ICorDebugClass2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugClass2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2
helpviewer_keywords:
- ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type:
- apiref
ms.openlocfilehash: 80aa8e59ccc774141e7fcea130d1fc6a38fa37da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711472"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="27099-103">ICorDebugClass2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="27099-103">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="27099-104">ジェネリック、または <xref:System.Type> 型のメソッド パラメーターを持つクラスを表します。</span><span class="sxs-lookup"><span data-stu-id="27099-104">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="27099-105">このインターフェイスは [、を](icordebugclass-interface.md)拡張します。</span><span class="sxs-lookup"><span data-stu-id="27099-105">This interface extends [ICorDebugClass](icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27099-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="27099-106">Methods</span></span>  
  
|<span data-ttu-id="27099-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="27099-107">Method</span></span>|<span data-ttu-id="27099-108">説明</span><span class="sxs-lookup"><span data-stu-id="27099-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="27099-109">GetParameterizedType メソッド</span><span class="sxs-lookup"><span data-stu-id="27099-109">GetParameterizedType Method</span></span>](icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="27099-110">このクラスの型宣言を取得します。</span><span class="sxs-lookup"><span data-stu-id="27099-110">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="27099-111">SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="27099-111">SetJMCStatus Method</span></span>](icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="27099-112">このクラスの各メソッドについて、メソッドがユーザー定義のコードかどうかを示す値を設定します。</span><span class="sxs-lookup"><span data-stu-id="27099-112">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27099-113">解説</span><span class="sxs-lookup"><span data-stu-id="27099-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="27099-114">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="27099-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27099-115">要件</span><span class="sxs-lookup"><span data-stu-id="27099-115">Requirements</span></span>  

 <span data-ttu-id="27099-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27099-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27099-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27099-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27099-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27099-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27099-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27099-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27099-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="27099-120">See also</span></span>

- [<span data-ttu-id="27099-121">ICorDebugClass インターフェイス</span><span class="sxs-lookup"><span data-stu-id="27099-121">ICorDebugClass Interface</span></span>](icordebugclass-interface.md)
- [<span data-ttu-id="27099-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="27099-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
