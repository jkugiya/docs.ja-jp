---
description: 詳細については、「ICorDebugMetaDataLocator インターフェイス」を参照してください。
title: ICorDebugMetaDataLocator インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator
helpviewer_keywords:
- ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: 287f5ecd-863f-4090-a615-077859f0257b
topic_type:
- apiref
ms.openlocfilehash: 7b87527d4d0b98fc97631fb47184665daaf39edb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790829"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="8d09a-103">ICorDebugMetaDataLocator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d09a-103">ICorDebugMetaDataLocator Interface</span></span>

<span data-ttu-id="8d09a-104">デバッガーにメタデータ情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="8d09a-104">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8d09a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8d09a-105">Methods</span></span>  
  
|<span data-ttu-id="8d09a-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="8d09a-106">Method</span></span>|<span data-ttu-id="8d09a-107">説明</span><span class="sxs-lookup"><span data-stu-id="8d09a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8d09a-108">GetMetaData メソッド</span><span class="sxs-lookup"><span data-stu-id="8d09a-108">GetMetaData Method</span></span>](icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="8d09a-109">デバッガーが要求した操作を完了するために必要となるメタデータが含まれているモジュールの完全パスを返すように、デバッガーに求めます。</span><span class="sxs-lookup"><span data-stu-id="8d09a-109">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d09a-110">解説</span><span class="sxs-lookup"><span data-stu-id="8d09a-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d09a-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="8d09a-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d09a-112">要件</span><span class="sxs-lookup"><span data-stu-id="8d09a-112">Requirements</span></span>  

 <span data-ttu-id="8d09a-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d09a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d09a-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d09a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d09a-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d09a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d09a-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d09a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d09a-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d09a-117">See also</span></span>

- [<span data-ttu-id="8d09a-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d09a-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8d09a-119">デバッグ</span><span class="sxs-lookup"><span data-stu-id="8d09a-119">Debugging</span></span>](index.md)
