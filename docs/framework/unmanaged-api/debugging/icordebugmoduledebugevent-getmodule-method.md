---
description: '詳細については、次のページを参照してください: いいね。イベント:: GetModule メソッド'
title: ICorDebugModuleDebugEvent::GetModule メソッド
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: c6d7171da231576ff90f54aaefe4b473af0afd40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790738"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="aca9d-103">ICorDebugModuleDebugEvent::GetModule メソッド</span><span class="sxs-lookup"><span data-stu-id="aca9d-103">ICorDebugModuleDebugEvent::GetModule Method</span></span>

<span data-ttu-id="aca9d-104">ロードまたはアンロードされたばかりのマージ モジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="aca9d-104">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aca9d-105">構文</span><span class="sxs-lookup"><span data-stu-id="aca9d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aca9d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aca9d-106">Parameters</span></span>  

 `ppModule`  
 <span data-ttu-id="aca9d-107">[out] ロードまたはアンロードされたばかりのマージ モジュールを表す ICorDebugModule オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aca9d-107">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aca9d-108">解説</span><span class="sxs-lookup"><span data-stu-id="aca9d-108">Remarks</span></span>  

 <span data-ttu-id="aca9d-109">[Geteventkind](icordebugdebugevent-geteventkind-method.md)メソッドを呼び出して、モジュールが読み込まれたかアンロードされたかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="aca9d-109">You can call the [GetEventKind](icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aca9d-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="aca9d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aca9d-111">要件</span><span class="sxs-lookup"><span data-stu-id="aca9d-111">Requirements</span></span>  

 <span data-ttu-id="aca9d-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aca9d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aca9d-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aca9d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aca9d-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aca9d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aca9d-115">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aca9d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aca9d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="aca9d-116">See also</span></span>

- [<span data-ttu-id="aca9d-117">ICorDebugModuleDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aca9d-117">ICorDebugModuleDebugEvent Interface</span></span>](icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="aca9d-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="aca9d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
