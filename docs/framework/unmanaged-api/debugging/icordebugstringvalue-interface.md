---
description: '詳細については、次を参照してください: いいねインターフェイス'
title: ICorDebugStringValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue
helpviewer_keywords:
- ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: bf84d0af-53e1-4c04-bc5b-7e5f81ba2cc2
topic_type:
- apiref
ms.openlocfilehash: b4e762d8c0a62c1b76b59364e9d29c4b8d2386fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717330"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="d7641-103">ICorDebugStringValue インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7641-103">ICorDebugStringValue Interface</span></span>

<span data-ttu-id="d7641-104">文字列値に適用される、値のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="d7641-104">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d7641-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d7641-105">Methods</span></span>  
  
|<span data-ttu-id="d7641-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="d7641-106">Method</span></span>|<span data-ttu-id="d7641-107">説明</span><span class="sxs-lookup"><span data-stu-id="d7641-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d7641-108">GetLength メソッド</span><span class="sxs-lookup"><span data-stu-id="d7641-108">GetLength Method</span></span>](icordebugstringvalue-getlength-method.md)|<span data-ttu-id="d7641-109">このによって参照される文字列の文字数を取得し `ICorDebugStringValue` ます。</span><span class="sxs-lookup"><span data-stu-id="d7641-109">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="d7641-110">GetString メソッド</span><span class="sxs-lookup"><span data-stu-id="d7641-110">GetString Method</span></span>](icordebugstringvalue-getstring-method.md)|<span data-ttu-id="d7641-111">このによって参照される文字列を取得し `ICorDebugStringValue` ます。</span><span class="sxs-lookup"><span data-stu-id="d7641-111">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7641-112">解説</span><span class="sxs-lookup"><span data-stu-id="d7641-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7641-113">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d7641-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7641-114">要件</span><span class="sxs-lookup"><span data-stu-id="d7641-114">Requirements</span></span>  

 <span data-ttu-id="d7641-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7641-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7641-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7641-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7641-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7641-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7641-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7641-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7641-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7641-119">See also</span></span>

- [<span data-ttu-id="d7641-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7641-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
