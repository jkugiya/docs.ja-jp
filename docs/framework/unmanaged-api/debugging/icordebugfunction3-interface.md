---
description: 詳細については、「ICorDebugFunction3 インターフェイス」を参照してください。
title: ICorDebugFunction3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
ms.openlocfilehash: f6f3ce78fbb0ca7efb6ba6a95da20f8c698b923c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692070"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="b4d30-103">ICorDebugFunction3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b4d30-103">ICorDebugFunction3 Interface</span></span>

<span data-ttu-id="b4d30-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="b4d30-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b4d30-105">ICorDebugFunction インターフェイスを論理的に拡張して、ReJIT 要求からコードへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="b4d30-105">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b4d30-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="b4d30-106">Methods</span></span>  
  
|<span data-ttu-id="b4d30-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="b4d30-107">Method</span></span>|<span data-ttu-id="b4d30-108">説明</span><span class="sxs-lookup"><span data-stu-id="b4d30-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b4d30-109">GetActiveReJitRequestILCode メソッド</span><span class="sxs-lookup"><span data-stu-id="b4d30-109">GetActiveReJitRequestILCode Method</span></span>](icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="b4d30-110">アクティブな ReJIT 要求から IL を含む、 [コード](icordebugilcode-interface.md) へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="b4d30-110">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4d30-111">解説</span><span class="sxs-lookup"><span data-stu-id="b4d30-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4d30-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="b4d30-112">Requirements</span></span>  

 <span data-ttu-id="b4d30-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4d30-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4d30-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4d30-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4d30-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4d30-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4d30-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4d30-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4d30-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4d30-117">See also</span></span>

- [<span data-ttu-id="b4d30-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b4d30-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b4d30-119">デバッグ</span><span class="sxs-lookup"><span data-stu-id="b4d30-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="b4d30-120">ReJIT: How-To ガイド</span><span class="sxs-lookup"><span data-stu-id="b4d30-120">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
