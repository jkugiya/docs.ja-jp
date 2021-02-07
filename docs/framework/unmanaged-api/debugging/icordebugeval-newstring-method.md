---
description: '詳細については、次のページを参照してください: いい評価:: NewString メソッド'
title: ICorDebugEval::NewString メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
ms.openlocfilehash: 21eb49900d84cb1ad1f68a701998a4a778c3ef17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693838"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="c670e-103">ICorDebugEval::NewString メソッド</span><span class="sxs-lookup"><span data-stu-id="c670e-103">ICorDebugEval::NewString Method</span></span>

<span data-ttu-id="c670e-104">指定された内容を持つ新しい文字列インスタンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="c670e-104">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c670e-105">構文</span><span class="sxs-lookup"><span data-stu-id="c670e-105">Syntax</span></span>  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c670e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c670e-106">Parameters</span></span>  

 `string`  
 <span data-ttu-id="c670e-107">から文字列のコンテンツへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c670e-107">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c670e-108">解説</span><span class="sxs-lookup"><span data-stu-id="c670e-108">Remarks</span></span>  

 <span data-ttu-id="c670e-109">文字列は常に、スレッドが現在実行されているアプリケーションドメインで作成されます。</span><span class="sxs-lookup"><span data-stu-id="c670e-109">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c670e-110">要件</span><span class="sxs-lookup"><span data-stu-id="c670e-110">Requirements</span></span>  

 <span data-ttu-id="c670e-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c670e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c670e-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c670e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c670e-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c670e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c670e-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c670e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
