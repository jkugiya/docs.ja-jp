---
description: 詳細については、「ISymUnmanagedAsyncMethod インターフェイス」を参照してください。
title: ISymUnmanagedAsyncMethod インターフェイス
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: cb3120464224137dfdcff4f13ca4aee82ef4d89e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790270"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="0ab2a-103">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0ab2a-103">ISymUnmanagedAsyncMethod Interface</span></span>

<span data-ttu-id="0ab2a-104">このインターフェイスは、 [ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス](isymunmanagedasyncmethodpropertieswriter-interface.md)への読み取り補数です。</span><span class="sxs-lookup"><span data-stu-id="0ab2a-104">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ab2a-105">構文</span><span class="sxs-lookup"><span data-stu-id="0ab2a-105">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="0ab2a-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="0ab2a-106">Methods</span></span>  

 <span data-ttu-id="0ab2a-107">このインターフェイスには、次のメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0ab2a-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="0ab2a-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="0ab2a-108">Method</span></span>|<span data-ttu-id="0ab2a-109">説明</span><span class="sxs-lookup"><span data-stu-id="0ab2a-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ab2a-110">GetAsyncStepInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="0ab2a-110">GetAsyncStepInfo Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="0ab2a-111">「 [DefineAsyncStepInfo メソッド](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ab2a-111">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="0ab2a-112">GetAsyncStepInfoCount メソッド</span><span class="sxs-lookup"><span data-stu-id="0ab2a-112">GetAsyncStepInfoCount Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="0ab2a-113">「 [DefineAsyncStepInfo メソッド](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ab2a-113">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="0ab2a-114">GetCatchHandlerILOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="0ab2a-114">GetCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="0ab2a-115">「 [DefineCatchHandlerILOffset メソッド](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ab2a-115">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="0ab2a-116">GetKickoffMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="0ab2a-116">GetKickoffMethod Method</span></span>](isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="0ab2a-117">「 [DefineKickoffMethod メソッド](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ab2a-117">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="0ab2a-118">HasCatchHandlerILOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="0ab2a-118">HasCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="0ab2a-119">「 [DefineCatchHandlerILOffset メソッド](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ab2a-119">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="0ab2a-120">IsAsyncMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="0ab2a-120">IsAsyncMethod Method</span></span>](isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="0ab2a-121">メソッドに非同期情報があるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="0ab2a-121">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="0ab2a-122">このメソッドがを返す場合 `FALSE` 、このインターフェイス内の他のメソッドを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="0ab2a-122">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="0ab2a-123">これらはすべて、 `E_UNEXPECTED` この場合はを返します。</span><span class="sxs-lookup"><span data-stu-id="0ab2a-123">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0ab2a-124">要件</span><span class="sxs-lookup"><span data-stu-id="0ab2a-124">Requirements</span></span>  

 <span data-ttu-id="0ab2a-125">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="0ab2a-125">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ab2a-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ab2a-126">See also</span></span>

- [<span data-ttu-id="0ab2a-127">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0ab2a-127">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
