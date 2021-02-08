---
description: '詳細について: ICorDebugObjectValue2:: GetVirtualMethodAndType メソッド'
title: ICorDebugObjectValue2::GetVirtualMethodAndType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue2.GetVirtualMethodAndType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue2::GetVirtualMethodAndType
helpviewer_keywords:
- GetVirtualMethodAndType method [.NET Framework debugging]
- ICorDebugObjectValue2::GetVirtualMethodAndType method
ms.assetid: 621b4543-a8f7-4117-98e4-930992cd688a
topic_type:
- apiref
ms.openlocfilehash: 73866cc902d60316e3f1f31a86473116c0bff129
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781923"
---
# <a name="icordebugobjectvalue2getvirtualmethodandtype-method"></a><span data-ttu-id="4ac3e-103">ICorDebugObjectValue2::GetVirtualMethodAndType メソッド</span><span class="sxs-lookup"><span data-stu-id="4ac3e-103">ICorDebugObjectValue2::GetVirtualMethodAndType Method</span></span>

<span data-ttu-id="4ac3e-104">このメソッドはまだ実装されていません。</span><span class="sxs-lookup"><span data-stu-id="4ac3e-104">This method is not yet implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ac3e-105">構文</span><span class="sxs-lookup"><span data-stu-id="4ac3e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVirtualMethodAndType (  
    [in] mdMemberRef          memberRef,  
    [out] ICorDebugFunction   **ppFunction,  
    [out] ICorDebugType       **ppType  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="4ac3e-106">解説</span><span class="sxs-lookup"><span data-stu-id="4ac3e-106">Remarks</span></span>  

 <span data-ttu-id="4ac3e-107">指定されたメンバー参照の最も派生したメソッドと型を表す "の型の関数" インスタンスおよび "参照型" インスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4ac3e-107">Gets interface pointers to the "ICorDebugFunction" and "ICorDebugType" instances that represent the most derived method and type for the specified member reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ac3e-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ac3e-108">See also</span></span>
