---
description: 詳細については、「ICorDebugFunction2 インターフェイス」を参照してください。
title: ICorDebugFunction2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2
helpviewer_keywords:
- ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type:
- apiref
ms.openlocfilehash: e5297d46acb9b174537363fc185fa2d540d55a75
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692200"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="2f798-103">ICorDebugFunction2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f798-103">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="2f798-104">マイコードのみのステップスルーデバッグをサポートするように、この関数インターフェイスを論理的に拡張します。これにより、非ユーザーコードがスキップされます。</span><span class="sxs-lookup"><span data-stu-id="2f798-104">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2f798-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="2f798-105">Methods</span></span>  
  
|<span data-ttu-id="2f798-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="2f798-106">Method</span></span>|<span data-ttu-id="2f798-107">説明</span><span class="sxs-lookup"><span data-stu-id="2f798-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2f798-108">EnumerateNativeCode メソッド</span><span class="sxs-lookup"><span data-stu-id="2f798-108">EnumerateNativeCode Method</span></span>](icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="2f798-109">(実装されていません。)この ICorDebugFunction2 オブジェクトによって参照されている関数内のネイティブコードステートメントを含む、コードの型の列挙体へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="2f798-109">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="2f798-110">GetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="2f798-110">GetJMCStatus Method</span></span>](icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="2f798-111">この関数がユーザーコードとしてマークされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="2f798-111">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="2f798-112">GetVersionNumber メソッド</span><span class="sxs-lookup"><span data-stu-id="2f798-112">GetVersionNumber Method</span></span>](icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="2f798-113">この関数のエディットコンティニュバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="2f798-113">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="2f798-114">SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="2f798-114">SetJMCStatus Method</span></span>](icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="2f798-115">マイコードのみのステップ実行のために、この関数をマークします。</span><span class="sxs-lookup"><span data-stu-id="2f798-115">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f798-116">解説</span><span class="sxs-lookup"><span data-stu-id="2f798-116">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f798-117">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="2f798-117">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f798-118">要件</span><span class="sxs-lookup"><span data-stu-id="2f798-118">Requirements</span></span>  

 <span data-ttu-id="2f798-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f798-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f798-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f798-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f798-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f798-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f798-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f798-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f798-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f798-123">See also</span></span>

- [<span data-ttu-id="2f798-124">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f798-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
