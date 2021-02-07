---
description: '詳細については、次を参照してください: EnumerateFrames メソッド'
title: ICorDebugChain::EnumerateFrames メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
ms.openlocfilehash: 45bf69760eeccebada743d81e859a19e209b611a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711597"
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="3c7e1-103">ICorDebugChain::EnumerateFrames メソッド</span><span class="sxs-lookup"><span data-stu-id="3c7e1-103">ICorDebugChain::EnumerateFrames Method</span></span>

<span data-ttu-id="3c7e1-104">チェーン内のすべてのマネージスタックフレームが格納された列挙子を取得します。これは、最新のフレームから始まります。</span><span class="sxs-lookup"><span data-stu-id="3c7e1-104">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c7e1-105">構文</span><span class="sxs-lookup"><span data-stu-id="3c7e1-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c7e1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3c7e1-106">Parameters</span></span>  

 `ppFrames`  
 <span data-ttu-id="3c7e1-107">入出力スタックフレームの列挙子である、テキストフレームの列挙型オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3c7e1-107">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c7e1-108">解説</span><span class="sxs-lookup"><span data-stu-id="3c7e1-108">Remarks</span></span>  

 <span data-ttu-id="3c7e1-109">チェーンは、スレッドの物理呼び出し履歴を表します。</span><span class="sxs-lookup"><span data-stu-id="3c7e1-109">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="3c7e1-110">メソッドは、 `EnumerateFrames` マネージドチェーンに対してのみ呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7e1-110">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="3c7e1-111">デバッグ API には、アンマネージチェーンに含まれるフレームを取得するためのメソッドが用意されていません。</span><span class="sxs-lookup"><span data-stu-id="3c7e1-111">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="3c7e1-112">デバッガーは、この情報を取得するために他の手段を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7e1-112">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c7e1-113">要件</span><span class="sxs-lookup"><span data-stu-id="3c7e1-113">Requirements</span></span>  

 <span data-ttu-id="3c7e1-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c7e1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c7e1-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c7e1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c7e1-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c7e1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c7e1-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c7e1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
