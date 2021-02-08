---
description: '詳細について: ISymUnmanagedAsyncMethod:: GetKickoffMethod メソッド'
title: ISymUnmanagedAsyncMethod::GetKickoffMethod メソッド
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
ms.openlocfilehash: c763109ac8556fd7941675f98879c6a1792e8bc4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790296"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="ef973-103">ISymUnmanagedAsyncMethod::GetKickoffMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="ef973-103">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>

<span data-ttu-id="ef973-104">「 [DefineKickoffMethod メソッド](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef973-104">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef973-105">構文</span><span class="sxs-lookup"><span data-stu-id="ef973-105">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef973-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ef973-106">Parameters</span></span>  
  
|<span data-ttu-id="ef973-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ef973-107">Parameter</span></span>|<span data-ttu-id="ef973-108">説明</span><span class="sxs-lookup"><span data-stu-id="ef973-108">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="ef973-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="ef973-109">Return Value</span></span>  

 <span data-ttu-id="ef973-110">`HRESULT` が返されます。</span><span class="sxs-lookup"><span data-stu-id="ef973-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef973-111">要件</span><span class="sxs-lookup"><span data-stu-id="ef973-111">Requirements</span></span>  

 <span data-ttu-id="ef973-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="ef973-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef973-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef973-113">See also</span></span>

- [<span data-ttu-id="ef973-114">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ef973-114">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
