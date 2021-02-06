---
description: '詳細については、次を参照してください:、テキスト:: テキストメソッド'
title: ICorDebugType::GetFirstTypeParameter メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetFirstTypeParameter
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type:
- apiref
ms.openlocfilehash: 4c37217f34f80c916d618d88e4917eab794a1d90
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658283"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a><span data-ttu-id="7b339-103">ICorDebugType::GetFirstTypeParameter メソッド</span><span class="sxs-lookup"><span data-stu-id="7b339-103">ICorDebugType::GetFirstTypeParameter Method</span></span>

<span data-ttu-id="7b339-104"><xref:System.Type>このによって表される型の最初のパラメーターを表す、の型へのインターフェイスポインターを取得し `ICorDebugType` ます。</span><span class="sxs-lookup"><span data-stu-id="7b339-104">Gets an interface pointer to an ICorDebugType that represents the first <xref:System.Type> parameter of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b339-105">構文</span><span class="sxs-lookup"><span data-stu-id="7b339-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b339-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7b339-106">Parameters</span></span>  

 `value`  
 <span data-ttu-id="7b339-107">入出力最初のパラメーターを表すオブジェクトのアドレスへのポインター `ICorDebugType` 。</span><span class="sxs-lookup"><span data-stu-id="7b339-107">[out] A pointer to the address of an `ICorDebugType` object that represents the first parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b339-108">解説</span><span class="sxs-lookup"><span data-stu-id="7b339-108">Remarks</span></span>  

 <span data-ttu-id="7b339-109">`GetFirstTypeParameter` 型に関する追加情報には、最大で1つの型パラメーターが含まれる場合に、を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="7b339-109">`GetFirstTypeParameter` can be called in cases where the additional information about the type involves, at most, one type parameter.</span></span> <span data-ttu-id="7b339-110">具体的には、型が ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF、または ELEMENT_TYPE_PTR である場合に使用できます。これは、のように、の型 [:: GetType](icordebugtype-gettype-method.md) メソッドによって示されます。</span><span class="sxs-lookup"><span data-stu-id="7b339-110">In particular, it can be used if the type is an ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR, as indicated by the [ICorDebugType::GetType](icordebugtype-gettype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b339-111">要件</span><span class="sxs-lookup"><span data-stu-id="7b339-111">Requirements</span></span>  

 <span data-ttu-id="7b339-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b339-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b339-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b339-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b339-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b339-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b339-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b339-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
