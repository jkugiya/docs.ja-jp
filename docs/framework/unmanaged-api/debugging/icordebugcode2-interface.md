---
description: 詳細については、「ICorDebugCode2 インターフェイス」を参照してください。
title: ICorDebugCode2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugCode2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2
helpviewer_keywords:
- ICorDebugCode2 interface [.NET Framework debugging]
ms.assetid: 9321903b-7dea-40d8-ba32-99016c00cc46
topic_type:
- apiref
ms.openlocfilehash: 29fd657ec56993d47ee57aa41c81b45e75352697
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765049"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="9dd50-103">ICorDebugCode2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9dd50-103">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="9dd50-104">"コード例" の機能を拡張するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9dd50-104">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9dd50-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9dd50-105">Methods</span></span>  
  
|<span data-ttu-id="9dd50-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="9dd50-106">Method</span></span>|<span data-ttu-id="9dd50-107">説明</span><span class="sxs-lookup"><span data-stu-id="9dd50-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9dd50-108">GetCodeChunks メソッド</span><span class="sxs-lookup"><span data-stu-id="9dd50-108">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="9dd50-109">このコード オブジェクトを構成しているコード チャンクを取得します。</span><span class="sxs-lookup"><span data-stu-id="9dd50-109">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="9dd50-110">GetCompilerFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="9dd50-110">GetCompilerFlags Method</span></span>](icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="9dd50-111">このコード オブジェクトが Just-In-Time (JIT) コンパイルされたとき、またはネイティブ イメージ ジェネレーター (Ngen.exe) を使用して生成されたときの条件を指定するフラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="9dd50-111">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9dd50-112">解説</span><span class="sxs-lookup"><span data-stu-id="9dd50-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9dd50-113">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="9dd50-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dd50-114">要件</span><span class="sxs-lookup"><span data-stu-id="9dd50-114">Requirements</span></span>  

 <span data-ttu-id="9dd50-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9dd50-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dd50-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9dd50-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9dd50-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9dd50-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9dd50-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dd50-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dd50-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="9dd50-119">See also</span></span>

- [<span data-ttu-id="9dd50-120">ICorDebugCode3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9dd50-120">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="9dd50-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9dd50-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
