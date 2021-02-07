---
description: '詳細について: ICorDebugEval2:: NewStringWithLength メソッド'
title: ICorDebugEval2::NewStringWithLength メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewStringWithLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type:
- apiref
ms.openlocfilehash: 23864dabefcb4fc12f73c66bc2d19a6cca1aacf0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693526"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="63cb2-103">ICorDebugEval2::NewStringWithLength メソッド</span><span class="sxs-lookup"><span data-stu-id="63cb2-103">ICorDebugEval2::NewStringWithLength Method</span></span>

<span data-ttu-id="63cb2-104">指定したコンテンツを使用して、指定した長さの文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="63cb2-104">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63cb2-105">構文</span><span class="sxs-lookup"><span data-stu-id="63cb2-105">Syntax</span></span>  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63cb2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="63cb2-106">Parameters</span></span>  

 `string`  
 <span data-ttu-id="63cb2-107">から文字列値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="63cb2-107">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="63cb2-108">から文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="63cb2-108">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63cb2-109">解説</span><span class="sxs-lookup"><span data-stu-id="63cb2-109">Remarks</span></span>  

 <span data-ttu-id="63cb2-110">文字列の末尾の null 文字がマネージ文字列に含まれると想定される場合、メソッドの呼び出し元は、 `NewStringWithLength` 文字列の長さに末尾の null 文字が含まれていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63cb2-110">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="63cb2-111">文字列は常に、スレッドが現在実行されているアプリケーションドメインで作成されます。</span><span class="sxs-lookup"><span data-stu-id="63cb2-111">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63cb2-112">要件</span><span class="sxs-lookup"><span data-stu-id="63cb2-112">Requirements</span></span>  

 <span data-ttu-id="63cb2-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63cb2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63cb2-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63cb2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63cb2-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63cb2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63cb2-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63cb2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
