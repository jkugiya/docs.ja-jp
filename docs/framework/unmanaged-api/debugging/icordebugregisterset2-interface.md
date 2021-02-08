---
description: 詳細については、「ICorDebugRegisterSet2 インターフェイス」を参照してください。
title: ICorDebugRegisterSet2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2
helpviewer_keywords:
- ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type:
- apiref
ms.openlocfilehash: 3501325df188879f5687347ef329f490b487d9d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803608"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="8cbad-103">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8cbad-103">ICorDebugRegisterSet2 Interface</span></span>

<span data-ttu-id="8cbad-104">64を超えるレジスタを持つハードウェアプラットフォームに対し [て、の](icordebugregisterset-interface.md) 機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="8cbad-104">Extends the capabilities of the [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8cbad-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8cbad-105">Methods</span></span>  
  
|<span data-ttu-id="8cbad-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="8cbad-106">Method</span></span>|<span data-ttu-id="8cbad-107">説明</span><span class="sxs-lookup"><span data-stu-id="8cbad-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8cbad-108">GetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="8cbad-108">GetRegisters Method</span></span>](icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="8cbad-109">ビットマスクによって指定された、(現在コードを実行しているコンピューター上の) 各レジスタの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="8cbad-109">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="8cbad-110">GetRegistersAvailable メソッド</span><span class="sxs-lookup"><span data-stu-id="8cbad-110">GetRegistersAvailable Method</span></span>](icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="8cbad-111">使用できるレジスタのビットマップを提供するバイト配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="8cbad-111">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="8cbad-112">SetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="8cbad-112">SetRegisters Method</span></span>](icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="8cbad-113">.NET Framework バージョン2.0 では実装されていません。</span><span class="sxs-lookup"><span data-stu-id="8cbad-113">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cbad-114">解説</span><span class="sxs-lookup"><span data-stu-id="8cbad-114">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8cbad-115">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="8cbad-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cbad-116">要件</span><span class="sxs-lookup"><span data-stu-id="8cbad-116">Requirements</span></span>  

 <span data-ttu-id="8cbad-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8cbad-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cbad-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8cbad-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8cbad-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8cbad-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8cbad-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cbad-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cbad-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="8cbad-121">See also</span></span>

- [<span data-ttu-id="8cbad-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8cbad-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8cbad-123">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8cbad-123">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
