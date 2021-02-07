---
description: '詳細情報: GetStartAddress Memorybuffer:: メソッド'
title: ICorDebugMemoryBuffer::GetStartAddress メソッド
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: 46720d70b8a1019e712b577b24dec5d4c3d5a31d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722712"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="e4dca-103">ICorDebugMemoryBuffer::GetStartAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="e4dca-103">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>

<span data-ttu-id="e4dca-104">メモリ バッファーの開始アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="e4dca-104">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4dca-105">構文</span><span class="sxs-lookup"><span data-stu-id="e4dca-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4dca-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4dca-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="e4dca-107">[out] メモリ バッファーの開始アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e4dca-107">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4dca-108">解説</span><span class="sxs-lookup"><span data-stu-id="e4dca-108">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="e4dca-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e4dca-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4dca-110">要件</span><span class="sxs-lookup"><span data-stu-id="e4dca-110">Requirements</span></span>  

 <span data-ttu-id="e4dca-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4dca-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4dca-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4dca-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4dca-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4dca-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4dca-114">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4dca-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4dca-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="e4dca-115">See also</span></span>

- [<span data-ttu-id="e4dca-116">ICorDebugMemoryBuffer インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e4dca-116">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="e4dca-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e4dca-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
