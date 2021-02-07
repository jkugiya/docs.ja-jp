---
description: '詳細については、次を参照してください: テキスト枠:: GetStackRange メソッド'
title: ICorDebugFrame::GetStackRange メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
ms.openlocfilehash: 1f1278e0c00addc3c14f4e1c8d3ed5aad0381526
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692902"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="1a374-103">ICorDebugFrame::GetStackRange メソッド</span><span class="sxs-lookup"><span data-stu-id="1a374-103">ICorDebugFrame::GetStackRange Method</span></span>

<span data-ttu-id="1a374-104">このスタックフレームの絶対アドレス範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="1a374-104">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a374-105">構文</span><span class="sxs-lookup"><span data-stu-id="1a374-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a374-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1a374-106">Parameters</span></span>  

 `pStart`  
 <span data-ttu-id="1a374-107">入出力 `CORDB_ADDRESS` このオブジェクトによって表されるスタックフレームの開始アドレスを指定するへのポインター `ICorDebugFrame` 。</span><span class="sxs-lookup"><span data-stu-id="1a374-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="1a374-108">入出力 `CORDB_ADDRESS` このオブジェクトによって表されるスタックフレームの終了アドレスを指定するへのポインター `ICorDebugFrame` 。</span><span class="sxs-lookup"><span data-stu-id="1a374-108">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a374-109">解説</span><span class="sxs-lookup"><span data-stu-id="1a374-109">Remarks</span></span>  

 <span data-ttu-id="1a374-110">スタックのアドレス範囲は、複数のデバッグエンジンから収集されたインターリーブスタックトレースを piecing する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1a374-110">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="1a374-111">数値の範囲は、スタックフレームの内容に関する情報を提供しません。</span><span class="sxs-lookup"><span data-stu-id="1a374-111">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="1a374-112">スタックフレームの位置を比較する場合にのみ意味があります。</span><span class="sxs-lookup"><span data-stu-id="1a374-112">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a374-113">要件</span><span class="sxs-lookup"><span data-stu-id="1a374-113">Requirements</span></span>  

 <span data-ttu-id="1a374-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a374-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a374-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a374-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a374-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a374-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a374-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a374-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
