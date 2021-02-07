---
description: '詳細については、次を参照してください: いいね:: EnumerateAssemblies メソッド'
title: ICorDebugAppDomain::EnumerateAssemblies メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateAssemblies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateAssemblies
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateAssemblies method [.NET Framework debugging]
- EnumerateAssemblies method [.NET Framework debugging]
ms.assetid: 7add64f9-19a8-46a9-be62-905d5e7d1bd8
topic_type:
- apiref
ms.openlocfilehash: 3ffa3180b80eac46e2d61019e4e4aa992f7c0e72
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754265"
---
# <a name="icordebugappdomainenumerateassemblies-method"></a><span data-ttu-id="d6acc-103">ICorDebugAppDomain::EnumerateAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="d6acc-103">ICorDebugAppDomain::EnumerateAssemblies Method</span></span>

<span data-ttu-id="d6acc-104">アプリケーションドメイン内のアセンブリの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="d6acc-104">Gets an enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6acc-105">構文</span><span class="sxs-lookup"><span data-stu-id="d6acc-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateAssemblies (  
    [out] ICorDebugAssemblyEnum  **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6acc-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d6acc-106">Parameters</span></span>  

 `ppAssemblies`  
 <span data-ttu-id="d6acc-107">入出力アプリケーションドメイン内のアセンブリの列挙子である、の各オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d6acc-107">[out] A pointer to the address of an ICorDebugAssemblyEnum object that is the enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6acc-108">要件</span><span class="sxs-lookup"><span data-stu-id="d6acc-108">Requirements</span></span>  

 <span data-ttu-id="d6acc-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6acc-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6acc-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6acc-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6acc-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6acc-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6acc-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6acc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
