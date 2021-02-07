---
description: '詳細については、次のページを参照してください: いい Process:: GetThread メソッド'
title: ICorDebugProcess::GetThread メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThread
helpviewer_keywords:
- ICorDebugProcess::GetThread method [.NET Framework debugging]
- GetThread method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a48261ed-700b-41c9-8cb4-18c526546603
topic_type:
- apiref
ms.openlocfilehash: bd636df50afd3f12901c1b48559c44ac6ad0cb81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746900"
---
# <a name="icordebugprocessgetthread-method"></a><span data-ttu-id="d8eef-103">ICorDebugProcess::GetThread メソッド</span><span class="sxs-lookup"><span data-stu-id="d8eef-103">ICorDebugProcess::GetThread Method</span></span>

<span data-ttu-id="d8eef-104">指定されたオペレーティングシステム (OS) のスレッド ID を持つ、このプロセスのスレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="d8eef-104">Gets this process's thread that has the specified operating system (OS) thread ID.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8eef-105">構文</span><span class="sxs-lookup"><span data-stu-id="d8eef-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
    [in] DWORD dwThreadId,  
    [out] ICorDebugThread **ppThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8eef-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d8eef-106">Parameters</span></span>  

 `dwThreadId`  
 <span data-ttu-id="d8eef-107">から取得するスレッドの OS スレッド ID。</span><span class="sxs-lookup"><span data-stu-id="d8eef-107">[in] The OS thread ID of the thread to be retrieved.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="d8eef-108">入出力スレッドを表す、スレッドオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d8eef-108">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8eef-109">要件</span><span class="sxs-lookup"><span data-stu-id="d8eef-109">Requirements</span></span>  

 <span data-ttu-id="d8eef-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8eef-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8eef-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8eef-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8eef-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8eef-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8eef-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8eef-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
