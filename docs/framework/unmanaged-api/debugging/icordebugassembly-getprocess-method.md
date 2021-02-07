---
description: '詳細については、次の情報を参照してください: のアセンブリ:: GetProcess メソッド'
title: ICorDebugAssembly::GetProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetProcess
helpviewer_keywords:
- ICorDebugAssembly::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: ea52be06-0a16-4f57-afca-4287d72e76c4
topic_type:
- apiref
ms.openlocfilehash: b121d7f892f6e2e2aa76290d4aee51767c72e9fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754148"
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="0efc9-103">ICorDebugAssembly::GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="0efc9-103">ICorDebugAssembly::GetProcess Method</span></span>

<span data-ttu-id="0efc9-104">このツールのアセンブリインスタンスが実行されているプロセスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="0efc9-104">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0efc9-105">構文</span><span class="sxs-lookup"><span data-stu-id="0efc9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0efc9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0efc9-106">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="0efc9-107">入出力プロセスを表す、オブジェクトインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0efc9-107">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0efc9-108">要件</span><span class="sxs-lookup"><span data-stu-id="0efc9-108">Requirements</span></span>  

 <span data-ttu-id="0efc9-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0efc9-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0efc9-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0efc9-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0efc9-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0efc9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0efc9-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0efc9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
