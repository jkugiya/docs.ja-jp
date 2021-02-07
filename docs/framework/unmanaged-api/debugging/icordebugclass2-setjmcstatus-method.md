---
description: '詳細について: ICorDebugClass2:: SetJMCStatus メソッド'
title: ICorDebugClass2::SetJMCStatus メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type:
- apiref
ms.openlocfilehash: 28859522052fd9587dc3890eb4137929dbdc6763
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711477"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="b17ee-103">ICorDebugClass2::SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="b17ee-103">ICorDebugClass2::SetJMCStatus Method</span></span>

<span data-ttu-id="b17ee-104">クラスの各メソッドについて、メソッドがユーザー定義のコードかどうかを示す値を設定します。</span><span class="sxs-lookup"><span data-stu-id="b17ee-104">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b17ee-105">構文</span><span class="sxs-lookup"><span data-stu-id="b17ee-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b17ee-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b17ee-106">Parameters</span></span>  

 `bIsJustMyCode`  
 <span data-ttu-id="b17ee-107">から `true` メソッドがユーザー定義コードであることを示す場合はに設定します。それ以外の場合はに設定 `false` します。</span><span class="sxs-lookup"><span data-stu-id="b17ee-107">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b17ee-108">解説</span><span class="sxs-lookup"><span data-stu-id="b17ee-108">Remarks</span></span>  

 <span data-ttu-id="b17ee-109">マイコードのみ (JMC) のステッパは、ユーザー定義ではないコードをスキップします。</span><span class="sxs-lookup"><span data-stu-id="b17ee-109">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="b17ee-110">ユーザー定義コードは、デバッグ可能なコードのサブセットである必要があります。</span><span class="sxs-lookup"><span data-stu-id="b17ee-110">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="b17ee-111">`SetJMCStatus` は、他のすべてのメソッドの値が正常に設定された場合でも、メソッドの値の設定に失敗した場合に S_FALSE の HRESULT 値を返します。</span><span class="sxs-lookup"><span data-stu-id="b17ee-111">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b17ee-112">要件</span><span class="sxs-lookup"><span data-stu-id="b17ee-112">Requirements</span></span>  

 <span data-ttu-id="b17ee-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b17ee-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b17ee-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b17ee-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b17ee-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b17ee-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b17ee-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b17ee-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
