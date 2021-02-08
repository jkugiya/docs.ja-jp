---
description: '詳細について: ICorDebugLoadedModule:: GetSize メソッド'
title: ICorDebugLoadedModule::GetSize メソッド
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: 6701d2578559a039f352df19bf9e859658c6687f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801242"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="ca44d-103">ICorDebugLoadedModule::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="ca44d-103">ICorDebugLoadedModule::GetSize Method</span></span>

<span data-ttu-id="ca44d-104">読み込まれたモジュールのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="ca44d-104">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca44d-105">構文</span><span class="sxs-lookup"><span data-stu-id="ca44d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca44d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ca44d-106">Parameters</span></span>  

 `pcBytes`  
 <span data-ttu-id="ca44d-107">[out] 読み込まれたモジュールのバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ca44d-107">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca44d-108">解説</span><span class="sxs-lookup"><span data-stu-id="ca44d-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca44d-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ca44d-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca44d-110">要件</span><span class="sxs-lookup"><span data-stu-id="ca44d-110">Requirements</span></span>  

 <span data-ttu-id="ca44d-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca44d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca44d-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca44d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca44d-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca44d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca44d-114">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca44d-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca44d-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca44d-115">See also</span></span>

- [<span data-ttu-id="ca44d-116">ICorDebugLoadedModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca44d-116">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="ca44d-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca44d-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
