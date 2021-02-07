---
description: '詳細については、次の情報を参照してください: いい Assembly:: 列挙'
title: ICorDebugAssembly::EnumerateModules メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.EnumerateModules
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::EnumerateModules
helpviewer_keywords:
- ICorDebugAssembly::EnumerateModules method [.NET Framework debugging]
- EnumerateModules method [.NET Framework debugging]
ms.assetid: c7ba51a1-0dd5-4452-b471-232febe0f897
topic_type:
- apiref
ms.openlocfilehash: 5d34fb1762e8f953007d6fcb59ab1147028f06a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722868"
---
# <a name="icordebugassemblyenumeratemodules-method"></a><span data-ttu-id="fa22a-103">ICorDebugAssembly::EnumerateModules メソッド</span><span class="sxs-lookup"><span data-stu-id="fa22a-103">ICorDebugAssembly::EnumerateModules Method</span></span>

<span data-ttu-id="fa22a-104">に格納されているモジュールの列挙子を取得し `ICorDebugAssembly` ます。</span><span class="sxs-lookup"><span data-stu-id="fa22a-104">Gets an enumerator for the modules contained in the `ICorDebugAssembly`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa22a-105">構文</span><span class="sxs-lookup"><span data-stu-id="fa22a-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateModules (  
    [out] ICorDebugModuleEnum **ppModules  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa22a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fa22a-106">Parameters</span></span>  

 `ppModules`  
 <span data-ttu-id="fa22a-107">入出力列挙子である、モジュールの列挙型インターフェイスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fa22a-107">[out] A pointer to the address of the ICorDebugModuleEnum interface that is the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa22a-108">要件</span><span class="sxs-lookup"><span data-stu-id="fa22a-108">Requirements</span></span>  

 <span data-ttu-id="fa22a-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa22a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa22a-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa22a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa22a-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa22a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa22a-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa22a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
