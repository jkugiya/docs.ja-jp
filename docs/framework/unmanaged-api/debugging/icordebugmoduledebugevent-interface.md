---
description: '詳細情報: モジュールの詳細'
title: ICorDebugModuleDebugEvent インターフェイス
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: 0c2d43d7b04caeea0407ede23f0df6e278d60c92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801034"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="4826b-103">ICorDebugModuleDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4826b-103">ICorDebugModuleDebugEvent Interface</span></span>

<span data-ttu-id="4826b-104">モジュールレベルのイベントをサポートするように、のモジュールレベル [のイベントを](icordebugdebugevent-interface.md) 拡張します。</span><span class="sxs-lookup"><span data-stu-id="4826b-104">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4826b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="4826b-105">Methods</span></span>  
  
|<span data-ttu-id="4826b-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="4826b-106">Method</span></span>|<span data-ttu-id="4826b-107">説明</span><span class="sxs-lookup"><span data-stu-id="4826b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4826b-108">GetModule メソッド</span><span class="sxs-lookup"><span data-stu-id="4826b-108">GetModule Method</span></span>](icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="4826b-109">ロードまたはアンロードされたばかりのマージ モジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="4826b-109">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4826b-110">解説</span><span class="sxs-lookup"><span data-stu-id="4826b-110">Remarks</span></span>  

 <span data-ttu-id="4826b-111">[MODULE_LOADED](cordebugdebugeventkind-enumeration.md)イベントと[MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md)イベントの種類は、このインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="4826b-111">The [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4826b-112">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="4826b-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="4826b-113">インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。</span><span class="sxs-lookup"><span data-stu-id="4826b-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4826b-114">要件</span><span class="sxs-lookup"><span data-stu-id="4826b-114">Requirements</span></span>  

 <span data-ttu-id="4826b-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4826b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4826b-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4826b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4826b-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4826b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4826b-118">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4826b-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4826b-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="4826b-119">See also</span></span>

- [<span data-ttu-id="4826b-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="4826b-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4826b-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="4826b-121">Debugging</span></span>](index.md)
