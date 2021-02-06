---
description: '詳細については、次を参照してください: を参照してください。テキスト:: GetBase メソッド'
title: ICorDebugType::GetBase メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type:
- apiref
ms.openlocfilehash: 78cd540974b540b704e946f6c723214d72e89ab4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658387"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="10f0d-103">ICorDebugType::GetBase メソッド</span><span class="sxs-lookup"><span data-stu-id="10f0d-103">ICorDebugType::GetBase Method</span></span>

<span data-ttu-id="10f0d-104">このによって表される型の基本型 (存在する場合) を表す、の型へのインターフェイスポインターを取得し `ICorDebugType` ます。</span><span class="sxs-lookup"><span data-stu-id="10f0d-104">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10f0d-105">構文</span><span class="sxs-lookup"><span data-stu-id="10f0d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10f0d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="10f0d-106">Parameters</span></span>  

 `pBase`  
 <span data-ttu-id="10f0d-107">入出力基本型を表すオブジェクトのアドレスへのポインター `ICorDebugType` 。</span><span class="sxs-lookup"><span data-stu-id="10f0d-107">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10f0d-108">解説</span><span class="sxs-lookup"><span data-stu-id="10f0d-108">Remarks</span></span>  

 <span data-ttu-id="10f0d-109">型の基本型を検索すると、オブジェクトまたはその親クラスのすべてのフィールドを出力するなど、一般的なデバッガー機能を実装するのに便利です。</span><span class="sxs-lookup"><span data-stu-id="10f0d-109">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10f0d-110">要件</span><span class="sxs-lookup"><span data-stu-id="10f0d-110">Requirements</span></span>  

 <span data-ttu-id="10f0d-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10f0d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10f0d-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10f0d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10f0d-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10f0d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10f0d-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10f0d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
