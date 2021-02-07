---
description: '詳細情報: Iデバッガ Info:: Isデバッガ添付メソッド'
title: IDebuggerInfo::IsDebuggerAttached メソッド
ms.date: 03/30/2017
api_name:
- IDebuggerInfo.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IsDebuggerAttached
helpviewer_keywords:
- IDebuggerInfo::IsDebuggerAttached method [.NET Framework hosting]
- IsDebuggerAttached method, IDebuggerInfo interface [.NET Framework hosting]
ms.assetid: 6e21872f-602f-411a-a423-bff5cdf27000
topic_type:
- apiref
ms.openlocfilehash: a17a7f5f1cef1d0c7025f4051e59767ce09ec421
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709808"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="d5c83-103">IDebuggerInfo::IsDebuggerAttached メソッド</span><span class="sxs-lookup"><span data-stu-id="d5c83-103">IDebuggerInfo::IsDebuggerAttached Method</span></span>

<span data-ttu-id="d5c83-104">マネージデバッガーがこのプロセスにアタッチされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="d5c83-104">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5c83-105">構文</span><span class="sxs-lookup"><span data-stu-id="d5c83-105">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5c83-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d5c83-106">Parameters</span></span>  

 `pbAttached`  
 <span data-ttu-id="d5c83-107">入出力 `true` マネージデバッガーがプロセスにアタッチされている場合は値を指すポインター。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="d5c83-107">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5c83-108">要件</span><span class="sxs-lookup"><span data-stu-id="d5c83-108">Requirements</span></span>  

 <span data-ttu-id="d5c83-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5c83-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5c83-110">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d5c83-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5c83-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d5c83-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5c83-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5c83-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5c83-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5c83-113">See also</span></span>

- [<span data-ttu-id="d5c83-114">IDebuggerInfo Iインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5c83-114">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)
