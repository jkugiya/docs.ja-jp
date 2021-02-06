---
description: '詳細については、次を参照してください: を参照してください::、GetClass メソッド'
title: ICorDebugType::GetClass メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
ms.openlocfilehash: 2e8d68fbc8909599ca649ba0e226cc84af820939
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658323"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="b7fd3-103">ICorDebugType::GetClass メソッド</span><span class="sxs-lookup"><span data-stu-id="b7fd3-103">ICorDebugType::GetClass Method</span></span>

<span data-ttu-id="b7fd3-104">インスタンスジェネリック型を表す、のクラスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="b7fd3-104">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7fd3-105">構文</span><span class="sxs-lookup"><span data-stu-id="b7fd3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7fd3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b7fd3-106">Parameters</span></span>  

 `ppClass`  
 <span data-ttu-id="b7fd3-107">入出力 `ICorDebugClass` インスタンスジェネリック型を表すインターフェイスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b7fd3-107">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7fd3-108">解説</span><span class="sxs-lookup"><span data-stu-id="b7fd3-108">Remarks</span></span>  

 <span data-ttu-id="b7fd3-109">`GetClass` は、特定の条件下でのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="b7fd3-109">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="b7fd3-110">を [呼び出す前に](icordebugtype-gettype-method.md) 、を呼び出して `GetClass` ください。</span><span class="sxs-lookup"><span data-stu-id="b7fd3-110">Call [ICorDebugType::GetType](icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="b7fd3-111">`ICorDebugType::GetType`が ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE の CorElementType 値を返す場合は、を呼び出して、 `GetClass` ジェネリック型のインスタンス型を取得できます。</span><span class="sxs-lookup"><span data-stu-id="b7fd3-111">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7fd3-112">要件</span><span class="sxs-lookup"><span data-stu-id="b7fd3-112">Requirements</span></span>  

 <span data-ttu-id="b7fd3-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7fd3-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7fd3-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7fd3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7fd3-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7fd3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7fd3-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7fd3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
