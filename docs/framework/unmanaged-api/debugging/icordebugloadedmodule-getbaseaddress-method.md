---
description: '詳細について: ICorDebugLoadedModule:: GetBaseAddress メソッド'
title: ICorDebugLoadedModule::GetBaseAddress メソッド
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
ms.openlocfilehash: 2852131d543cfb9593cf4ff607d1f752226c2880
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801268"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="86221-103">ICorDebugLoadedModule::GetBaseAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="86221-103">ICorDebugLoadedModule::GetBaseAddress Method</span></span>

<span data-ttu-id="86221-104">読み込まれたモジュールのベース アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="86221-104">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86221-105">構文</span><span class="sxs-lookup"><span data-stu-id="86221-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86221-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="86221-106">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="86221-107">[out] 読み込まれたモジュールのベース アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="86221-107">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86221-108">解説</span><span class="sxs-lookup"><span data-stu-id="86221-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86221-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="86221-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86221-110">要件</span><span class="sxs-lookup"><span data-stu-id="86221-110">Requirements</span></span>  

 <span data-ttu-id="86221-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86221-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86221-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86221-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86221-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86221-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86221-114">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86221-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86221-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="86221-115">See also</span></span>

- [<span data-ttu-id="86221-116">ICorDebugLoadedModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="86221-116">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="86221-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="86221-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
