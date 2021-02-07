---
description: '詳細情報: GetSize Memorybuffer:: メソッド'
title: ICorDebugMemoryBuffer::GetSize メソッド
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
ms.openlocfilehash: 7de23dd13a1e0ef841145e3845d7d0052ce3ef9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754041"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="f1761-103">ICorDebugMemoryBuffer::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="f1761-103">ICorDebugMemoryBuffer::GetSize Method</span></span>

<span data-ttu-id="f1761-104">メモリ バッファーのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="f1761-104">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1761-105">構文</span><span class="sxs-lookup"><span data-stu-id="f1761-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1761-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f1761-106">Parameters</span></span>  

 `pcbBufferLength`  
 <span data-ttu-id="f1761-107">[out] メモリ バッファーのサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f1761-107">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1761-108">解説</span><span class="sxs-lookup"><span data-stu-id="f1761-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1761-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f1761-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1761-110">要件</span><span class="sxs-lookup"><span data-stu-id="f1761-110">Requirements</span></span>  

 <span data-ttu-id="f1761-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1761-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1761-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1761-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1761-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1761-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1761-114">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1761-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1761-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1761-115">See also</span></span>

- [<span data-ttu-id="f1761-116">ICorDebugMemoryBuffer インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1761-116">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="f1761-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1761-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
