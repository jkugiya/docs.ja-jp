---
description: '詳細について: ICorDebugDataTarget3:: Getロードモジュールメソッド'
title: ICorDebugDataTarget3::GetLoadedModules メソッド
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: ea6350155fd79b52a37133cad95f624635433a3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764347"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="2ae7f-103">ICorDebugDataTarget3::GetLoadedModules メソッド</span><span class="sxs-lookup"><span data-stu-id="2ae7f-103">ICorDebugDataTarget3::GetLoadedModules Method</span></span>

<span data-ttu-id="2ae7f-104">これまでに読み込まれたモジュールの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="2ae7f-104">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ae7f-105">構文</span><span class="sxs-lookup"><span data-stu-id="2ae7f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ae7f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2ae7f-106">Parameters</span></span>  

 `cRequestedModules`  
 <span data-ttu-id="2ae7f-107">[in] 情報を要求する対象のモジュールの数。</span><span class="sxs-lookup"><span data-stu-id="2ae7f-107">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="2ae7f-108">[out] 情報が返された対象モジュールの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="2ae7f-108">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="2ae7f-109">入出力読み込まれたモジュールに関する情報を提供する [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) オブジェクトの配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="2ae7f-109">[out] A pointer to an array of [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ae7f-110">解説</span><span class="sxs-lookup"><span data-stu-id="2ae7f-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ae7f-111">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="2ae7f-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ae7f-112">要件</span><span class="sxs-lookup"><span data-stu-id="2ae7f-112">Requirements</span></span>  

 <span data-ttu-id="2ae7f-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ae7f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ae7f-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ae7f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ae7f-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ae7f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ae7f-116">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ae7f-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ae7f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ae7f-117">See also</span></span>

- [<span data-ttu-id="2ae7f-118">ICorDebugDataTarget3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2ae7f-118">ICorDebugDataTarget3 Interface</span></span>](icordebugdatatarget3-interface.md)
- [<span data-ttu-id="2ae7f-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2ae7f-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
