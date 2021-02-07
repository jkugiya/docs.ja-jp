---
description: 詳細については、「ICorDebugNativeFrame2 インターフェイス」を参照してください。
title: ICorDebugNativeFrame2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2
helpviewer_keywords:
- ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type:
- apiref
ms.openlocfilehash: 9ed0e20bb29bef3b210258956ebecb1ee7a96df8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722348"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="ddc14-103">ICorDebugNativeFrame2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ddc14-103">ICorDebugNativeFrame2 Interface</span></span>

<span data-ttu-id="ddc14-104">子と親のフレームの関係をテストするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="ddc14-104">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ddc14-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ddc14-105">Methods</span></span>  
  
|<span data-ttu-id="ddc14-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="ddc14-106">Method</span></span>|<span data-ttu-id="ddc14-107">説明</span><span class="sxs-lookup"><span data-stu-id="ddc14-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ddc14-108">IsChild メソッド</span><span class="sxs-lookup"><span data-stu-id="ddc14-108">IsChild Method</span></span>](icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="ddc14-109">現在のフレームが子フレームであるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="ddc14-109">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="ddc14-110">IsMatchingParentFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="ddc14-110">IsMatchingParentFrame Method</span></span>](icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="ddc14-111">指定したフレームが現在のフレームの親であるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="ddc14-111">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="ddc14-112">GetStackParameterSize メソッド</span><span class="sxs-lookup"><span data-stu-id="ddc14-112">GetStackParameterSize Method</span></span>](icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="ddc14-113">X86 オペレーティングシステムのスタックのパラメーターの累積サイズを返します。</span><span class="sxs-lookup"><span data-stu-id="ddc14-113">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddc14-114">解説</span><span class="sxs-lookup"><span data-stu-id="ddc14-114">Remarks</span></span>  

 <span data-ttu-id="ddc14-115">このインターフェイスは、"" の "テキスト" インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="ddc14-115">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ddc14-116">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="ddc14-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddc14-117">要件</span><span class="sxs-lookup"><span data-stu-id="ddc14-117">Requirements</span></span>  

 <span data-ttu-id="ddc14-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddc14-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddc14-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ddc14-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ddc14-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ddc14-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ddc14-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddc14-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddc14-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="ddc14-122">See also</span></span>

- [<span data-ttu-id="ddc14-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ddc14-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ddc14-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="ddc14-124">Debugging</span></span>](index.md)
