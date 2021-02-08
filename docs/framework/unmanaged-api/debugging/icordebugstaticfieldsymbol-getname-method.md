---
description: 詳細については、次を参照してください
title: ICorDebugStaticFieldSymbol::GetName メソッド
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: c74de604f5880a69b77c89e56a82ae08517dd69c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794703"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="e73bb-103">ICorDebugStaticFieldSymbol::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="e73bb-103">ICorDebugStaticFieldSymbol::GetName Method</span></span>

<span data-ttu-id="e73bb-104">静的フィールドの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="e73bb-104">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e73bb-105">構文</span><span class="sxs-lookup"><span data-stu-id="e73bb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e73bb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e73bb-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="e73bb-107">[in] `szName` バッファー内の文字数。</span><span class="sxs-lookup"><span data-stu-id="e73bb-107">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e73bb-108">[out] `szName` バッファーに実際に書き込まれた文字数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e73bb-108">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="e73bb-109">[out] 返される名前を格納する文字配列。</span><span class="sxs-lookup"><span data-stu-id="e73bb-109">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e73bb-110">解説</span><span class="sxs-lookup"><span data-stu-id="e73bb-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e73bb-111">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e73bb-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e73bb-112">要件</span><span class="sxs-lookup"><span data-stu-id="e73bb-112">Requirements</span></span>  

 <span data-ttu-id="e73bb-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e73bb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e73bb-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e73bb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e73bb-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e73bb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e73bb-116">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e73bb-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e73bb-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="e73bb-117">See also</span></span>

- [<span data-ttu-id="e73bb-118">ICorDebugStaticFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e73bb-118">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="e73bb-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e73bb-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
