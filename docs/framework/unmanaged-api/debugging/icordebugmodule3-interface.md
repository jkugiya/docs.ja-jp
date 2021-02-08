---
description: 詳細については、「ICorDebugModule3 インターフェイス」を参照してください。
title: ICorDebugModule3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugModule3
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3
helpviewer_keywords:
- ICorDebugModule3 interface [.NET Framework debugging]
ms.assetid: 0b69f945-263a-4e11-8512-89d27f6ea296
topic_type:
- apiref
ms.openlocfilehash: 5b47cffb267ab97de2cd225aca2998962ba66d99
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790764"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="410e9-103">ICorDebugModule3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="410e9-103">ICorDebugModule3 Interface</span></span>

<span data-ttu-id="410e9-104">動的モジュールのシンボル リーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="410e9-104">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="410e9-105">構文</span><span class="sxs-lookup"><span data-stu-id="410e9-105">Syntax</span></span>  
  
```cpp  
interface ICorDebugModule3 : IUnknown  
{  
    HRESULT CreateReaderForInMemorySymbols  
      (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **  ppObj  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="410e9-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="410e9-106">Methods</span></span>  
  
|<span data-ttu-id="410e9-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="410e9-107">Method</span></span>|<span data-ttu-id="410e9-108">説明</span><span class="sxs-lookup"><span data-stu-id="410e9-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="410e9-109">ICorDebugModule3::CreateReaderForInMemorySymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="410e9-109">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="410e9-110">動的モジュールのシンボルリーダー (通常は [ISymUnmanagedReader インターフェイス](../diagnostics/isymunmanagedreader-interface.md)) を作成します。</span><span class="sxs-lookup"><span data-stu-id="410e9-110">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="410e9-111">解説</span><span class="sxs-lookup"><span data-stu-id="410e9-111">Remarks</span></span>  

 <span data-ttu-id="410e9-112">このインターフェイスは、"ICorDebugModule2" インターフェイスと "" インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="410e9-112">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="410e9-113">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="410e9-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="410e9-114">要件</span><span class="sxs-lookup"><span data-stu-id="410e9-114">Requirements</span></span>  

 <span data-ttu-id="410e9-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="410e9-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="410e9-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="410e9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="410e9-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="410e9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="410e9-118">**.NET Framework のバージョン:** 4.5、4、3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="410e9-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="410e9-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="410e9-119">See also</span></span>

- [<span data-ttu-id="410e9-120">ICorDebugRemoteTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="410e9-120">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="410e9-121">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="410e9-121">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="410e9-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="410e9-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
