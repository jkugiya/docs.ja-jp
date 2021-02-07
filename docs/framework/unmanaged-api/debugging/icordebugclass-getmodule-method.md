---
description: '詳細について: モジュールのクラス:: GetModule メソッド'
title: ICorDebugClass::GetModule メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetModule
helpviewer_keywords:
- GetModule method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetModule method [.NET Framework debugging]
ms.assetid: 87029cc4-e5e1-42d5-8b98-655bb7ece520
topic_type:
- apiref
ms.openlocfilehash: 338ea5aeede4a209f7a3e3ed685ae9bd84105890
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711543"
---
# <a name="icordebugclassgetmodule-method"></a><span data-ttu-id="7495a-103">ICorDebugClass::GetModule メソッド</span><span class="sxs-lookup"><span data-stu-id="7495a-103">ICorDebugClass::GetModule Method</span></span>

<span data-ttu-id="7495a-104">このクラスを定義するモジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="7495a-104">Gets the module that defines this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7495a-105">構文</span><span class="sxs-lookup"><span data-stu-id="7495a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule    **pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7495a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7495a-106">Parameters</span></span>  

 `pModule`  
 <span data-ttu-id="7495a-107">入出力このクラスが定義されているモジュールを表す、モジュールオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7495a-107">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this class is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7495a-108">要件</span><span class="sxs-lookup"><span data-stu-id="7495a-108">Requirements</span></span>  

 <span data-ttu-id="7495a-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7495a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7495a-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7495a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7495a-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7495a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7495a-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7495a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
