---
description: '詳細について: ICorDebugMergedAssemblyRecord:: GetCulture メソッド'
title: ICorDebugMergedAssemblyRecord::GetCulture メソッド
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: f530bb68a1e7e4c4bff53b8f3046f6ae9ca42aab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754005"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="dd1d9-103">ICorDebugMergedAssemblyRecord::GetCulture メソッド</span><span class="sxs-lookup"><span data-stu-id="dd1d9-103">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>

<span data-ttu-id="dd1d9-104">アセンブリのカルチャ名文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="dd1d9-104">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd1d9-105">構文</span><span class="sxs-lookup"><span data-stu-id="dd1d9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,
   [out] ULONG32 *pcchCulture,
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd1d9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dd1d9-106">Parameters</span></span>  

 `cchCulture`  
 <span data-ttu-id="dd1d9-107">[in] `szCulture` バッファー内の文字数。</span><span class="sxs-lookup"><span data-stu-id="dd1d9-107">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="dd1d9-108">[out] `szCulture` バッファーに実際に書き込まれた文字数。</span><span class="sxs-lookup"><span data-stu-id="dd1d9-108">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="dd1d9-109">[out] カルチャ名を格納する文字配列。</span><span class="sxs-lookup"><span data-stu-id="dd1d9-109">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd1d9-110">解説</span><span class="sxs-lookup"><span data-stu-id="dd1d9-110">Remarks</span></span>  

 <span data-ttu-id="dd1d9-111">カルチャ名は、"en-US" (英語 (米国) カルチャ)、"neutral" (ニュートラル カルチャ) など、カルチャを識別する一意の文字列です。</span><span class="sxs-lookup"><span data-stu-id="dd1d9-111">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd1d9-112">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="dd1d9-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd1d9-113">要件</span><span class="sxs-lookup"><span data-stu-id="dd1d9-113">Requirements</span></span>  

 <span data-ttu-id="dd1d9-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd1d9-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd1d9-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dd1d9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd1d9-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd1d9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd1d9-117">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd1d9-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd1d9-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd1d9-118">See also</span></span>

- [<span data-ttu-id="dd1d9-119">ICorDebugMergedAssemblyRecord インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd1d9-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="dd1d9-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd1d9-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
