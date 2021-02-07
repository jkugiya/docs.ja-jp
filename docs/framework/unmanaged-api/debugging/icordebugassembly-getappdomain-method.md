---
description: '詳細については、次の情報を参照してください: のアセンブリ:: GetAppDomain メソッド'
title: ICorDebugAssembly::GetAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type:
- apiref
ms.openlocfilehash: f67b2a211b080843e2bd7b8820a5bf54dae638e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712104"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="d1eba-103">ICorDebugAssembly::GetAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="d1eba-103">ICorDebugAssembly::GetAppDomain Method</span></span>

<span data-ttu-id="d1eba-104">このインスタンスを含むアプリケーションドメインへのインターフェイスポインターを取得し `ICorDebugAssembly` ます。</span><span class="sxs-lookup"><span data-stu-id="d1eba-104">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1eba-105">構文</span><span class="sxs-lookup"><span data-stu-id="d1eba-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1eba-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d1eba-106">Parameters</span></span>  

 `ppAppDomain`  
 <span data-ttu-id="d1eba-107">入出力アプリケーションドメインを表す、のアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d1eba-107">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1eba-108">解説</span><span class="sxs-lookup"><span data-stu-id="d1eba-108">Remarks</span></span>  

 <span data-ttu-id="d1eba-109">このアセンブリがシステムアセンブリの場合、は `GetAppDomain` null を返します。</span><span class="sxs-lookup"><span data-stu-id="d1eba-109">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1eba-110">要件</span><span class="sxs-lookup"><span data-stu-id="d1eba-110">Requirements</span></span>  

 <span data-ttu-id="d1eba-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1eba-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1eba-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1eba-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1eba-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1eba-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1eba-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1eba-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
