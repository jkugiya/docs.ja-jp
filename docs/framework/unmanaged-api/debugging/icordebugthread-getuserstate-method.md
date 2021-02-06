---
description: '詳細については、次のページを参照してください: いい Thread:: GetUserState メソッド'
title: ICorDebugThread::GetUserState メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetUserState
helpviewer_keywords:
- GetUserState method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetUserState method [.NET Framework debugging]
ms.assetid: ae0cfd73-8ead-4d36-9310-dccaac9db0bd
topic_type:
- apiref
ms.openlocfilehash: b63b474525534f9e934954ebe660691db90b8b67
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658868"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="771e4-103">ICorDebugThread::GetUserState メソッド</span><span class="sxs-lookup"><span data-stu-id="771e4-103">ICorDebugThread::GetUserState Method</span></span>

<span data-ttu-id="771e4-104">このスレッドの現在のユーザー状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="771e4-104">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="771e4-105">構文</span><span class="sxs-lookup"><span data-stu-id="771e4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="771e4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="771e4-106">Parameters</span></span>  

 `pState`  
 <span data-ttu-id="771e4-107">入出力このスレッドの現在のユーザー状態を示す CorDebugUserState 列挙値のビットごとの組み合わせへのポインター。</span><span class="sxs-lookup"><span data-stu-id="771e4-107">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="771e4-108">解説</span><span class="sxs-lookup"><span data-stu-id="771e4-108">Remarks</span></span>  

 <span data-ttu-id="771e4-109">スレッドのユーザー状態は、デバッグ中のプログラムによって検査されるときのスレッドの状態です。</span><span class="sxs-lookup"><span data-stu-id="771e4-109">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="771e4-110">スレッドに複数の状態ビットが設定されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="771e4-110">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="771e4-111">要件</span><span class="sxs-lookup"><span data-stu-id="771e4-111">Requirements</span></span>  

 <span data-ttu-id="771e4-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="771e4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="771e4-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="771e4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="771e4-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="771e4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="771e4-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="771e4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
