---
description: '詳細について: ICorDebugThread2:: GetConnectionID メソッド'
title: ICorDebugThread2::GetConnectionID メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetConnectionID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type:
- apiref
ms.openlocfilehash: 0f8035e703d3638b11f4206d9c47e39fe487d71d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658738"
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="7d888-103">ICorDebugThread2::GetConnectionID メソッド</span><span class="sxs-lookup"><span data-stu-id="7d888-103">ICorDebugThread2::GetConnectionID Method</span></span>

<span data-ttu-id="7d888-104">この ICorDebugThread2 オブジェクトの接続識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="7d888-104">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d888-105">構文</span><span class="sxs-lookup"><span data-stu-id="7d888-105">Syntax</span></span>  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d888-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7d888-106">Parameters</span></span>  

 `pdwConnectionId`  
 <span data-ttu-id="7d888-107">入出力 `CONNID` 接続識別子を表す。</span><span class="sxs-lookup"><span data-stu-id="7d888-107">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d888-108">解説</span><span class="sxs-lookup"><span data-stu-id="7d888-108">Remarks</span></span>  

 <span data-ttu-id="7d888-109">`GetConnectionID` `pdwConnectionId` このスレッドが接続の一部でない場合、このメソッドはパラメーターで0を返します。</span><span class="sxs-lookup"><span data-stu-id="7d888-109">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="7d888-110">このスレッドが Microsoft SQL Server 2005 Analysis Services (SSAS) のインスタンスに接続されている場合、は `CONNID` サーバープロセス識別子 (SPID) にマップされます。</span><span class="sxs-lookup"><span data-stu-id="7d888-110">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d888-111">要件</span><span class="sxs-lookup"><span data-stu-id="7d888-111">Requirements</span></span>  

 <span data-ttu-id="7d888-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d888-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d888-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d888-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d888-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d888-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d888-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d888-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
