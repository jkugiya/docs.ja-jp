---
description: 詳細については、次をご覧ください。
title: ICorDebugInternalFrame インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame
helpviewer_keywords:
- ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type:
- apiref
ms.openlocfilehash: 7143f270b97e10fb9664aa7f7387749ddecbbcc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791141"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="52a52-103">ICorDebugInternalFrame インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52a52-103">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="52a52-104">スタック上のランタイム内部フレームを表します。</span><span class="sxs-lookup"><span data-stu-id="52a52-104">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="52a52-105">このインターフェイスは、テキストボックスのインターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="52a52-105">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="52a52-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="52a52-106">Methods</span></span>  
  
|<span data-ttu-id="52a52-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="52a52-107">Method</span></span>|<span data-ttu-id="52a52-108">説明</span><span class="sxs-lookup"><span data-stu-id="52a52-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="52a52-109">GetFrameType メソッド</span><span class="sxs-lookup"><span data-stu-id="52a52-109">GetFrameType Method</span></span>](icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="52a52-110">この内部フレームの型を取得します。</span><span class="sxs-lookup"><span data-stu-id="52a52-110">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52a52-111">解説</span><span class="sxs-lookup"><span data-stu-id="52a52-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52a52-112">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="52a52-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52a52-113">要件</span><span class="sxs-lookup"><span data-stu-id="52a52-113">Requirements</span></span>  

 <span data-ttu-id="52a52-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52a52-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52a52-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52a52-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52a52-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52a52-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52a52-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52a52-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52a52-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="52a52-118">See also</span></span>

- [<span data-ttu-id="52a52-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="52a52-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
