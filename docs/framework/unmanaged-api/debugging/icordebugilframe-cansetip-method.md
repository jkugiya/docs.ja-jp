---
description: '詳細については、次の情報を参照してください:: テキストの表示方法'
title: ICorDebugILFrame::CanSetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
ms.openlocfilehash: d6ba0d073e8807ac6173f7f3e3982fe1d3eb4e01
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791440"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="7889e-103">ICorDebugILFrame::CanSetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="7889e-103">ICorDebugILFrame::CanSetIP Method</span></span>

<span data-ttu-id="7889e-104">命令ポインターを Microsoft 中間言語 (MSIL) コード内の指定したオフセット位置に安全に設定できるかどうかを示す HRESULT を取得します。</span><span class="sxs-lookup"><span data-stu-id="7889e-104">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7889e-105">構文</span><span class="sxs-lookup"><span data-stu-id="7889e-105">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7889e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7889e-106">Parameters</span></span>  

 `nOffset`  
 <span data-ttu-id="7889e-107">から命令ポインターに必要な設定。</span><span class="sxs-lookup"><span data-stu-id="7889e-107">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7889e-108">解説</span><span class="sxs-lookup"><span data-stu-id="7889e-108">Remarks</span></span>  

 <span data-ttu-id="7889e-109">次のように、メソッドを使用します。 `CanSetIP` [](icordebugilframe-setip-method.md)</span><span class="sxs-lookup"><span data-stu-id="7889e-109">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="7889e-110">が `CanSetIP` S_OK 以外の HRESULT を返した場合でもを呼び出すことはでき `ICorDebugILFrame::SetIP` ますが、デバッガーがデバッグ中のコードの安全かつ適切な実行を継続する保証はありません。</span><span class="sxs-lookup"><span data-stu-id="7889e-110">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7889e-111">要件</span><span class="sxs-lookup"><span data-stu-id="7889e-111">Requirements</span></span>  

 <span data-ttu-id="7889e-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7889e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7889e-113">**ヘッダー:** CorDebug .idl、CorDebug、h</span><span class="sxs-lookup"><span data-stu-id="7889e-113">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="7889e-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7889e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7889e-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7889e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
