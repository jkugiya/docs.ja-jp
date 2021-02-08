---
description: '詳細情報: ICorDebugVariableSymbol:: GetName メソッド'
title: ICorDebugVariableSymbol::GetName メソッド
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: 4a3ba1dfebd256dcbb8374634a52f1feca5d9611
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790595"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="860dd-103">ICorDebugVariableSymbol::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="860dd-103">ICorDebugVariableSymbol::GetName Method</span></span>

<span data-ttu-id="860dd-104">変数の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="860dd-104">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="860dd-105">構文</span><span class="sxs-lookup"><span data-stu-id="860dd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="860dd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="860dd-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="860dd-107">[in] `szName` バッファー内の文字数。</span><span class="sxs-lookup"><span data-stu-id="860dd-107">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="860dd-108">[out] `szName` バッファーに実際に書き込まれた文字数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="860dd-108">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="860dd-109">変数名が格納されている文字配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="860dd-109">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="860dd-110">解説</span><span class="sxs-lookup"><span data-stu-id="860dd-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="860dd-111">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="860dd-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="860dd-112">要件</span><span class="sxs-lookup"><span data-stu-id="860dd-112">Requirements</span></span>  

 <span data-ttu-id="860dd-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="860dd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="860dd-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="860dd-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="860dd-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="860dd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="860dd-116">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="860dd-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="860dd-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="860dd-117">See also</span></span>

- [<span data-ttu-id="860dd-118">ICorDebugVariableSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="860dd-118">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="860dd-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="860dd-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
