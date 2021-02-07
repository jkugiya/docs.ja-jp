---
description: '詳細情報: の説明'
title: ICorDebugAppDomain インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
ms.openlocfilehash: 5f1ac20a7376a741da2e34de74c810c0f45e8293
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754200"
---
# <a name="icordebugappdomain-interface"></a><span data-ttu-id="18013-103">ICorDebugAppDomain インターフェイス</span><span class="sxs-lookup"><span data-stu-id="18013-103">ICorDebugAppDomain Interface</span></span>

<span data-ttu-id="18013-104">アプリケーション ドメインをデバッグするためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="18013-104">Provides methods for debugging application domains.</span></span> <span data-ttu-id="18013-105">このインターフェイスは、というコントロールのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="18013-105">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="18013-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="18013-106">Methods</span></span>  
  
|<span data-ttu-id="18013-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="18013-107">Method</span></span>|<span data-ttu-id="18013-108">説明</span><span class="sxs-lookup"><span data-stu-id="18013-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="18013-109">Attach メソッド</span><span class="sxs-lookup"><span data-stu-id="18013-109">Attach Method</span></span>](icordebugappdomain-attach-method.md)|<span data-ttu-id="18013-110">デバッガーをアプリケーションドメインにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="18013-110">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="18013-111">EnumerateAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="18013-111">EnumerateAssemblies Method</span></span>](icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="18013-112">アプリケーションドメイン内のアセンブリの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="18013-112">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="18013-113">EnumerateBreakpoints メソッド</span><span class="sxs-lookup"><span data-stu-id="18013-113">EnumerateBreakpoints Method</span></span>](icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="18013-114">アプリケーションドメイン内のすべてのアクティブなブレークポイントの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="18013-114">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="18013-115">EnumerateSteppers メソッド</span><span class="sxs-lookup"><span data-stu-id="18013-115">EnumerateSteppers Method</span></span>](icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="18013-116">アプリケーションドメイン内のすべてのアクティブな steppers の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="18013-116">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="18013-117">GetId メソッド</span><span class="sxs-lookup"><span data-stu-id="18013-117">GetId Method</span></span>](icordebugappdomain-getid-method.md)|<span data-ttu-id="18013-118">アプリケーションドメインの一意の ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="18013-118">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="18013-119">GetModuleFromMetaDataInterface メソッド</span><span class="sxs-lookup"><span data-stu-id="18013-119">GetModuleFromMetaDataInterface Method</span></span>](icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="18013-120">指定されたメタデータインターフェイスを持つ、のモジュールオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="18013-120">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="18013-121">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="18013-121">GetName Method</span></span>](icordebugappdomain-getname-method.md)|<span data-ttu-id="18013-122">アプリケーションドメインの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="18013-122">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="18013-123">GetObject メソッド</span><span class="sxs-lookup"><span data-stu-id="18013-123">GetObject Method</span></span>](icordebugappdomain-getobject-method.md)|<span data-ttu-id="18013-124">共通言語ランタイム (CLR) アプリケーションドメインへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="18013-124">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="18013-125">GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="18013-125">GetProcess Method</span></span>](icordebugappdomain-getprocess-method.md)|<span data-ttu-id="18013-126">アプリケーションドメインを格納しているプロセスを取得します。</span><span class="sxs-lookup"><span data-stu-id="18013-126">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="18013-127">IsAttached メソッド</span><span class="sxs-lookup"><span data-stu-id="18013-127">IsAttached Method</span></span>](icordebugappdomain-isattached-method.md)|<span data-ttu-id="18013-128">デバッガーがアプリケーションドメインにアタッチされているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="18013-128">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18013-129">解説</span><span class="sxs-lookup"><span data-stu-id="18013-129">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18013-130">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="18013-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18013-131">要件</span><span class="sxs-lookup"><span data-stu-id="18013-131">Requirements</span></span>  

 <span data-ttu-id="18013-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18013-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18013-133">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18013-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18013-134">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18013-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18013-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18013-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18013-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="18013-136">See also</span></span>

- [<span data-ttu-id="18013-137">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="18013-137">Debugging Interfaces</span></span>](debugging-interfaces.md)
