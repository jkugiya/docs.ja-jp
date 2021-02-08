---
description: '詳細については、次のページを参照してください:: テキストの追加方法'
title: ICorDebugILFrame::GetLocalVariable メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetLocalVariable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetLocalVariable
helpviewer_keywords:
- ICorDebugILFrame::GetLocalVariable method [.NET Framework debugging]
- GetLocalVariable method [.NET Framework debugging]
ms.assetid: c8706356-d50b-4f87-a40c-39c3b7f4fd38
topic_type:
- apiref
ms.openlocfilehash: c4bb3e5a5d970539607efbaf55f3f7f08f7e72af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791375"
---
# <a name="icordebugilframegetlocalvariable-method"></a><span data-ttu-id="98a46-103">ICorDebugILFrame::GetLocalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="98a46-103">ICorDebugILFrame::GetLocalVariable Method</span></span>

<span data-ttu-id="98a46-104">この MSIL (Microsoft 中間言語) スタックフレーム内の指定されたローカル変数の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="98a46-104">Gets the value of the specified local variable in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98a46-105">構文</span><span class="sxs-lookup"><span data-stu-id="98a46-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98a46-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="98a46-106">Parameters</span></span>  

 `dwIndex`  
 <span data-ttu-id="98a46-107">からこの MSIL スタックフレーム内のローカル変数のインデックス。</span><span class="sxs-lookup"><span data-stu-id="98a46-107">[in] The index of the local variable in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="98a46-108">[out] 取得した値を表す ICorDebugValue オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="98a46-108">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98a46-109">解説</span><span class="sxs-lookup"><span data-stu-id="98a46-109">Remarks</span></span>  

 <span data-ttu-id="98a46-110">メソッドは、 `GetLocalVariable` MSIL スタックフレーム内または just-in-time (JIT) コンパイルフレームで使用できます。</span><span class="sxs-lookup"><span data-stu-id="98a46-110">The `GetLocalVariable` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98a46-111">要件</span><span class="sxs-lookup"><span data-stu-id="98a46-111">Requirements</span></span>  

 <span data-ttu-id="98a46-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98a46-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98a46-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98a46-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98a46-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98a46-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98a46-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98a46-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
