---
description: '詳細については、次の情報を参照してください: の関数:: GetNativeCode メソッド'
title: ICorDebugFunction::GetNativeCode メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type:
- apiref
ms.openlocfilehash: 8938e11a5fdc3aa693faf04eec639941475d95ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692447"
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="1f321-103">ICorDebugFunction::GetNativeCode メソッド</span><span class="sxs-lookup"><span data-stu-id="1f321-103">ICorDebugFunction::GetNativeCode Method</span></span>

<span data-ttu-id="1f321-104">このコード例で表される関数のネイティブコードを取得します。</span><span class="sxs-lookup"><span data-stu-id="1f321-104">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f321-105">構文</span><span class="sxs-lookup"><span data-stu-id="1f321-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f321-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1f321-106">Parameters</span></span>  

 `ppCode`  
 <span data-ttu-id="1f321-107">入出力この関数のネイティブコードを表す、のコードインスタンスへのポインター。この関数が just-in-time (JIT) コンパイルされていない Microsoft 中間言語 (MSIL) コードの場合は null。</span><span class="sxs-lookup"><span data-stu-id="1f321-107">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f321-108">解説</span><span class="sxs-lookup"><span data-stu-id="1f321-108">Remarks</span></span>  

 <span data-ttu-id="1f321-109">このインスタンスで表される関数が、 `ICorDebugFunction` ジェネリック型の場合と同じように JIT コンパイルされた場合、は、 `GetNativeCode` ランダムなネイティブコードオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="1f321-109">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f321-110">要件</span><span class="sxs-lookup"><span data-stu-id="1f321-110">Requirements</span></span>  

 <span data-ttu-id="1f321-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f321-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f321-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f321-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f321-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f321-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f321-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f321-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
