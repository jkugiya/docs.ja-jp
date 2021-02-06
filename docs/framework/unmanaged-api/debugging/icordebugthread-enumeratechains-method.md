---
description: 詳細については、次を参照してください
title: ICorDebugThread::EnumerateChains メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.EnumerateChains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type:
- apiref
ms.openlocfilehash: b9184a1b298e1d29970c5e56ceca76715b0ed096
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659297"
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="7b1d3-103">ICorDebugThread::EnumerateChains メソッド</span><span class="sxs-lookup"><span data-stu-id="7b1d3-103">ICorDebugThread::EnumerateChains Method</span></span>

<span data-ttu-id="7b1d3-104">この ICorDebugChainEnum Thread オブジェクト内のすべてのスタックチェーンを含む、列挙子へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="7b1d3-104">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b1d3-105">構文</span><span class="sxs-lookup"><span data-stu-id="7b1d3-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b1d3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7b1d3-106">Parameters</span></span>  

 `ppChains`  
 <span data-ttu-id="7b1d3-107">入出力 `ICorDebugChainEnum` アクティブな (つまり、最新の) チェーンを開始位置として、このスレッド内のすべてのスタックチェーンを列挙できるようにするオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7b1d3-107">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b1d3-108">解説</span><span class="sxs-lookup"><span data-stu-id="7b1d3-108">Remarks</span></span>  

 <span data-ttu-id="7b1d3-109">スタックチェーンは、スレッドの物理的な呼び出し履歴を表します。</span><span class="sxs-lookup"><span data-stu-id="7b1d3-109">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="7b1d3-110">次の状況では、スタックチェーン境界が作成されます。</span><span class="sxs-lookup"><span data-stu-id="7b1d3-110">The following circumstances create a stack chain boundary:</span></span>  
  
- <span data-ttu-id="7b1d3-111">マネージからアンマネージ、または管理対象外の遷移。</span><span class="sxs-lookup"><span data-stu-id="7b1d3-111">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
- <span data-ttu-id="7b1d3-112">コンテキストスイッチ。</span><span class="sxs-lookup"><span data-stu-id="7b1d3-112">A context switch.</span></span>  
  
- <span data-ttu-id="7b1d3-113">ユーザースレッドのデバッガーハイジャック。</span><span class="sxs-lookup"><span data-stu-id="7b1d3-113">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="7b1d3-114">単一のコンテキストで純粋なマネージコードを実行しているスレッドの単純なケースでは、スレッドとスタックチェーンの間に1対1の対応が存在します。</span><span class="sxs-lookup"><span data-stu-id="7b1d3-114">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="7b1d3-115">デバッガーは、すべてのスレッドの物理的な呼び出し履歴を論理呼び出し履歴に再配置することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7b1d3-115">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="7b1d3-116">これには、すべてのスレッドのチェーンを呼び出し元/呼び出し先の関係によって並べ替え、それらを再グループ化することが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7b1d3-116">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b1d3-117">要件</span><span class="sxs-lookup"><span data-stu-id="7b1d3-117">Requirements</span></span>  

 <span data-ttu-id="7b1d3-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b1d3-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b1d3-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b1d3-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b1d3-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b1d3-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b1d3-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b1d3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
