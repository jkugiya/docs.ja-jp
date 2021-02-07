---
description: '詳細について: ISymUnmanagedAsyncMethod:: GetAsyncStepInfo メソッド'
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfo メソッド
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
ms.openlocfilehash: dc255323f103b3422b927b0489402b24767dcd92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737845"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="064a7-103">ISymUnmanagedAsyncMethod::GetAsyncStepInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="064a7-103">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>

<span data-ttu-id="064a7-104">「 [DefineAsyncStepInfo メソッド](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="064a7-104">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="064a7-105">構文</span><span class="sxs-lookup"><span data-stu-id="064a7-105">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="064a7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="064a7-106">Parameters</span></span>  
  
|<span data-ttu-id="064a7-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="064a7-107">Parameter</span></span>|<span data-ttu-id="064a7-108">説明</span><span class="sxs-lookup"><span data-stu-id="064a7-108">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="064a7-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="064a7-109">Return Value</span></span>  

 <span data-ttu-id="064a7-110">`HRESULT` が返されます。</span><span class="sxs-lookup"><span data-stu-id="064a7-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="064a7-111">要件</span><span class="sxs-lookup"><span data-stu-id="064a7-111">Requirements</span></span>  

 <span data-ttu-id="064a7-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="064a7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="064a7-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="064a7-113">See also</span></span>

- [<span data-ttu-id="064a7-114">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="064a7-114">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
