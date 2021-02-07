---
description: '詳細については、次のページを参照してください: テキスト枠:: GetCode メソッド'
title: ICorDebugFrame::GetCode メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCode
helpviewer_keywords:
- GetCode method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCode method [.NET Framework debugging]
ms.assetid: fbaa0794-a031-4015-8beb-2749e47ac340
topic_type:
- apiref
ms.openlocfilehash: f45e0a29530a8b4ddbeaa92db4489a030ac1ae79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693020"
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="96ac8-103">ICorDebugFrame::GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="96ac8-103">ICorDebugFrame::GetCode Method</span></span>

<span data-ttu-id="96ac8-104">このスタックフレームに関連付けられているコードへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="96ac8-104">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96ac8-105">構文</span><span class="sxs-lookup"><span data-stu-id="96ac8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96ac8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="96ac8-106">Parameters</span></span>  

 `ppCode`  
 <span data-ttu-id="96ac8-107">入出力このフレームに関連付けられているコードを表す、コードオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="96ac8-107">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96ac8-108">要件</span><span class="sxs-lookup"><span data-stu-id="96ac8-108">Requirements</span></span>  

 <span data-ttu-id="96ac8-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96ac8-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96ac8-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96ac8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96ac8-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96ac8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96ac8-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96ac8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
