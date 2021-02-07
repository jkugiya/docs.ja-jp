---
description: 詳細については、「ICLRDebugging インターフェイス」を参照してください。
title: ICLRDebugging インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
ms.openlocfilehash: 647b6f7634ef3b9f6ec6080aaff19476c027952a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723336"
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="fc857-103">ICLRDebugging インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc857-103">ICLRDebugging Interface</span></span>

<span data-ttu-id="fc857-104">デバッグ用にモジュールの読み込みとアンロードを処理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="fc857-104">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fc857-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="fc857-105">Methods</span></span>  
  
|<span data-ttu-id="fc857-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="fc857-106">Method</span></span>|<span data-ttu-id="fc857-107">説明</span><span class="sxs-lookup"><span data-stu-id="fc857-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fc857-108">OpenVirtualProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="fc857-108">OpenVirtualProcess Method</span></span>](iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="fc857-109">プロセスに読み込まれた共通言語ランタイム (CLR) モジュールに対応する "のプロセス" インターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="fc857-109">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="fc857-110">CanUnloadNow メソッド</span><span class="sxs-lookup"><span data-stu-id="fc857-110">CanUnloadNow Method</span></span>](iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="fc857-111">[ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)インターフェイスによって提供されたライブラリがまだ使用中であるか、またはアンロードできるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="fc857-111">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc857-112">解説</span><span class="sxs-lookup"><span data-stu-id="fc857-112">Remarks</span></span>  

 <span data-ttu-id="fc857-113">インターフェイスのインスタンスを取得する `ICLRDebugging` には、 [clrcreateinstance](../hosting/clrcreateinstance-function.md) 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="fc857-113">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc857-114">要件</span><span class="sxs-lookup"><span data-stu-id="fc857-114">Requirements</span></span>  

 <span data-ttu-id="fc857-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc857-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc857-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc857-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc857-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc857-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc857-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc857-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc857-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc857-119">See also</span></span>

- [<span data-ttu-id="fc857-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc857-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="fc857-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="fc857-121">Debugging</span></span>](index.md)
