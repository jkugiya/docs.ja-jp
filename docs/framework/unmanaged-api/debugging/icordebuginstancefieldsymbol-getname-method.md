---
description: 詳細については、次を参照
title: ICorDebugInstanceFieldSymbol::GetName メソッド
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
ms.openlocfilehash: 9cc2106d1527aa0b4d9e5c52115b703ffe55037f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791193"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="1d770-103">ICorDebugInstanceFieldSymbol::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="1d770-103">ICorDebugInstanceFieldSymbol::GetName Method</span></span>

<span data-ttu-id="1d770-104">インスタンス フィールドの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="1d770-104">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d770-105">構文</span><span class="sxs-lookup"><span data-stu-id="1d770-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d770-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1d770-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="1d770-107">[in] `szName` バッファー内の文字数。</span><span class="sxs-lookup"><span data-stu-id="1d770-107">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="1d770-108">[out] `szName` バッファーに実際に書き込まれた文字数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1d770-108">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="1d770-109">[out] 返される名前を格納する文字配列。</span><span class="sxs-lookup"><span data-stu-id="1d770-109">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d770-110">解説</span><span class="sxs-lookup"><span data-stu-id="1d770-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d770-111">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="1d770-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d770-112">要件</span><span class="sxs-lookup"><span data-stu-id="1d770-112">Requirements</span></span>  

 <span data-ttu-id="1d770-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d770-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d770-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d770-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d770-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d770-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d770-116">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d770-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d770-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d770-117">See also</span></span>

- [<span data-ttu-id="1d770-118">ICorDebugInstanceFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1d770-118">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="1d770-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1d770-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
