---
description: '詳細については、次のページを参照してください: EnumerateArguments メソッド'
title: ICorDebugILFrame::EnumerateArguments メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateArguments
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type:
- apiref
ms.openlocfilehash: 513f931e70a4e914b89f440545cf33ea1cce1fdf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791401"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="2b183-103">ICorDebugILFrame::EnumerateArguments メソッド</span><span class="sxs-lookup"><span data-stu-id="2b183-103">ICorDebugILFrame::EnumerateArguments Method</span></span>

<span data-ttu-id="2b183-104">このフレーム内の引数の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="2b183-104">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b183-105">構文</span><span class="sxs-lookup"><span data-stu-id="2b183-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b183-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2b183-106">Parameters</span></span>  

 `ppValueEnum`  
 <span data-ttu-id="2b183-107">入出力このフレーム内の引数の列挙子である、の各オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2b183-107">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b183-108">解説</span><span class="sxs-lookup"><span data-stu-id="2b183-108">Remarks</span></span>  

 <span data-ttu-id="2b183-109">`EnumerateArguments` このテキストボックスオブジェクトで表される呼び出しフレームで使用可能な引数を一覧表示できる列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="2b183-109">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="2b183-110">この一覧には、 [vararg](/cpp/windows/vararg) である引数 (可変個の引数) と、ではない引数が含まれ `vararg` ます。</span><span class="sxs-lookup"><span data-stu-id="2b183-110">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b183-111">要件</span><span class="sxs-lookup"><span data-stu-id="2b183-111">Requirements</span></span>  

 <span data-ttu-id="2b183-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b183-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b183-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b183-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b183-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b183-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b183-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b183-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
