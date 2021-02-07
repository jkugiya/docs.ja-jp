---
description: '詳細については、次のページを参照してください: いいね!: GetNext メソッド'
title: ICorDebugChain::GetNext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetNext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetNext
helpviewer_keywords:
- GetNext method [.NET Framework debugging]
- ICorDebugChain::GetNext method [.NET Framework debugging]
ms.assetid: 8d9744a5-e08b-4ab2-9855-5c22711cc1e6
topic_type:
- apiref
ms.openlocfilehash: ced7032feffa4c14c07341242b854c08b8c897a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661325"
---
# <a name="icordebugchaingetnext-method"></a><span data-ttu-id="18795-103">ICorDebugChain::GetNext メソッド</span><span class="sxs-lookup"><span data-stu-id="18795-103">ICorDebugChain::GetNext Method</span></span>

<span data-ttu-id="18795-104">スレッドの次のフレームのチェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="18795-104">Gets the next chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18795-105">構文</span><span class="sxs-lookup"><span data-stu-id="18795-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNext (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18795-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="18795-106">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="18795-107">入出力スレッドの次のフレームのチェーンを表す、テキストチェーンオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="18795-107">[out] A pointer to the address of an ICorDebugChain object that represents the next chain of frames for the thread.</span></span> <span data-ttu-id="18795-108">このチェーンが最後のチェーンの場合、 `ppChain` は null です。</span><span class="sxs-lookup"><span data-stu-id="18795-108">If this chain is the last chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18795-109">要件</span><span class="sxs-lookup"><span data-stu-id="18795-109">Requirements</span></span>  

 <span data-ttu-id="18795-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18795-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18795-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18795-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18795-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18795-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18795-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18795-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
