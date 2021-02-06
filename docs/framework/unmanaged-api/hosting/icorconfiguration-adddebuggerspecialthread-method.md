---
description: '詳細については、次を参照してください: ICorConfiguration:: Addデバッガ特殊なスレッドメソッド'
title: ICorConfiguration::AddDebuggerSpecialThread メソッド
ms.date: 03/30/2017
api_name:
- ICorConfiguration.AddDebuggerSpecialThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type:
- apiref
ms.openlocfilehash: b6904c2e4d5c265244ac096e0d64c2fc7f5d1be5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636716"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="619f8-103">ICorConfiguration::AddDebuggerSpecialThread メソッド</span><span class="sxs-lookup"><span data-stu-id="619f8-103">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>

<span data-ttu-id="619f8-104">デバッグサービスに対して、マネージまたはアンマネージのデバッグシナリオでデバッガーがアプリケーションを停止している間に、特定のスレッドの実行を継続できるようにする必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="619f8-104">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="619f8-105">構文</span><span class="sxs-lookup"><span data-stu-id="619f8-105">Syntax</span></span>  
  
```cpp  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="619f8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="619f8-106">Parameters</span></span>  

 `dwSpecialThreadId`  
 <span data-ttu-id="619f8-107">から実行を継続することが許可されているスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="619f8-107">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="619f8-108">解説</span><span class="sxs-lookup"><span data-stu-id="619f8-108">Remarks</span></span>  

 <span data-ttu-id="619f8-109">指定されたスレッドはマネージコードの実行を許可されないか、または任意の方法でランタイムに入ることができません。</span><span class="sxs-lookup"><span data-stu-id="619f8-109">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="619f8-110">このようなスレッドの例として、レガシスクリプトデバッガーをサポートするインプロセススレッドがあります。</span><span class="sxs-lookup"><span data-stu-id="619f8-110">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="619f8-111">要件</span><span class="sxs-lookup"><span data-stu-id="619f8-111">Requirements</span></span>  

 <span data-ttu-id="619f8-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="619f8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="619f8-113">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="619f8-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="619f8-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="619f8-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="619f8-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="619f8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="619f8-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="619f8-116">See also</span></span>

- [<span data-ttu-id="619f8-117">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="619f8-117">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
