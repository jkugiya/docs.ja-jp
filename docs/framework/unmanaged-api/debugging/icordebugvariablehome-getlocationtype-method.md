---
description: '詳細については、次のページを参照してください: GetLocationType メソッド'
title: 'いい変数 Home:: GetLocationType メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type:
- apiref
ms.openlocfilehash: 6efe9c045641d162be820961ca75c21a2b8fc14b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728796"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="a3629-103">いい変数 Home:: GetLocationType メソッド</span><span class="sxs-lookup"><span data-stu-id="a3629-103">ICorDebugVariableHome::GetLocationType Method</span></span>

<span data-ttu-id="a3629-104">変数のネイティブな場所の型を取得します。</span><span class="sxs-lookup"><span data-stu-id="a3629-104">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3629-105">構文</span><span class="sxs-lookup"><span data-stu-id="a3629-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3629-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a3629-106">Parameters</span></span>  

 `pLocationType`  
 <span data-ttu-id="a3629-107">入出力変数のネイティブな場所の型へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a3629-107">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="a3629-108">詳細については、 [VariableLocationType](variablelocationtype-enumeration.md) 列挙体を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3629-108">See the [VariableLocationType](variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3629-109">要件</span><span class="sxs-lookup"><span data-stu-id="a3629-109">Requirements</span></span>  

 <span data-ttu-id="a3629-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3629-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3629-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3629-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3629-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3629-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3629-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3629-113">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3629-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3629-114">See also</span></span>

- [<span data-ttu-id="a3629-115">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a3629-115">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="a3629-116">VariableLocationType 列挙型</span><span class="sxs-lookup"><span data-stu-id="a3629-116">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
