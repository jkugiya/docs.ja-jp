---
description: '詳細情報: ICorDebugLoadedModule:: GetName メソッド'
title: ICorDebugLoadedModule::GetName メソッド
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
ms.openlocfilehash: 40a0715b513115177cabac01727ce9166a40d50b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801255"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="5376d-103">ICorDebugLoadedModule::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="5376d-103">ICorDebugLoadedModule::GetName Method</span></span>

<span data-ttu-id="5376d-104">読み込まれたモジュールの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="5376d-104">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5376d-105">構文</span><span class="sxs-lookup"><span data-stu-id="5376d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5376d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5376d-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="5376d-107">[in] `szName` バッファー内の文字数。</span><span class="sxs-lookup"><span data-stu-id="5376d-107">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5376d-108">[out] `szName` バッファーに実際に書き込まれた文字数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5376d-108">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="5376d-109">[out] 読み込まれたモジュールの名前が含まれている文字配列。</span><span class="sxs-lookup"><span data-stu-id="5376d-109">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5376d-110">解説</span><span class="sxs-lookup"><span data-stu-id="5376d-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5376d-111">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="5376d-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5376d-112">要件</span><span class="sxs-lookup"><span data-stu-id="5376d-112">Requirements</span></span>  

 <span data-ttu-id="5376d-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5376d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5376d-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5376d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5376d-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5376d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5376d-116">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5376d-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5376d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="5376d-117">See also</span></span>

- [<span data-ttu-id="5376d-118">ICorDebugLoadedModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5376d-118">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="5376d-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5376d-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
