---
description: '詳細については、次のページを参照してください: いいね:: の GetObject メソッド'
title: ICorDebugAppDomain::GetObject メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetObject
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type:
- apiref
ms.openlocfilehash: 59389e2a4ca72f8dcdd7117213e968440d30aaa6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754213"
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="9f258-103">ICorDebugAppDomain::GetObject メソッド</span><span class="sxs-lookup"><span data-stu-id="9f258-103">ICorDebugAppDomain::GetObject Method</span></span>

<span data-ttu-id="9f258-104">共通言語ランタイム (CLR) アプリケーションドメインへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="9f258-104">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f258-105">構文</span><span class="sxs-lookup"><span data-stu-id="9f258-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f258-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f258-106">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="9f258-107">入出力CLR アプリケーションドメインを表す ICorDebugValue インターフェイスオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9f258-107">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f258-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="9f258-108">Return Value</span></span>  

 <span data-ttu-id="9f258-109"><xref:System.AppDomain?displayProperty=nameWithType>このアプリケーションドメインに対してマネージオブジェクトが構築されていない場合、メソッドはを返し、を `S_FALSE` に配置し `NULL` `*ppObject` ます。</span><span class="sxs-lookup"><span data-stu-id="9f258-109">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f258-110">解説</span><span class="sxs-lookup"><span data-stu-id="9f258-110">Remarks</span></span>  

 <span data-ttu-id="9f258-111">プロセス内の各アプリケーションドメインは、 <xref:System.AppDomain?displayProperty=nameWithType> それを表すランタイムにマネージオブジェクトを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="9f258-111">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="9f258-112">この関数は、このマネージオブジェクトに対応する ICorDebugValue インターフェイスオブジェクトを取得し <xref:System.AppDomain?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="9f258-112">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f258-113">要件</span><span class="sxs-lookup"><span data-stu-id="9f258-113">Requirements</span></span>  

 <span data-ttu-id="9f258-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f258-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f258-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f258-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f258-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f258-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f258-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f258-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
