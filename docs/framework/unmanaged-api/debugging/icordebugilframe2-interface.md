---
description: 詳細については、「ICorDebugILFrame2 インターフェイス」を参照してください。
title: ICorDebugILFrame2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2
helpviewer_keywords:
- ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type:
- apiref
ms.openlocfilehash: 8379fda39a210e1df902dab3ac85132f04aee5fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791310"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="d756f-103">ICorDebugILFrame2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d756f-103">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="d756f-104">モジュールの論理拡張機能インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="d756f-104">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d756f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d756f-105">Methods</span></span>  
  
|<span data-ttu-id="d756f-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="d756f-106">Method</span></span>|<span data-ttu-id="d756f-107">説明</span><span class="sxs-lookup"><span data-stu-id="d756f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d756f-108">EnumerateTypeParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="d756f-108">EnumerateTypeParameters Method</span></span>](icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="d756f-109">このフレームのパラメーターを格納している、テキスト型の型の列挙体オブジェクトを取得し <xref:System.Type> ます。</span><span class="sxs-lookup"><span data-stu-id="d756f-109">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="d756f-110">RemapFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="d756f-110">RemapFunction Method</span></span>](icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="d756f-111">新しい MSIL オフセットを指定して、編集された関数を再マップします。</span><span class="sxs-lookup"><span data-stu-id="d756f-111">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d756f-112">解説</span><span class="sxs-lookup"><span data-stu-id="d756f-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d756f-113">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d756f-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d756f-114">要件</span><span class="sxs-lookup"><span data-stu-id="d756f-114">Requirements</span></span>  

 <span data-ttu-id="d756f-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d756f-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d756f-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d756f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d756f-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d756f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d756f-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d756f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d756f-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="d756f-119">See also</span></span>

- [<span data-ttu-id="d756f-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d756f-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
