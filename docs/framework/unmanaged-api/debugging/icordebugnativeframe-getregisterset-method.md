---
description: '詳細については、次のページを参照してください: テキストボックス'
title: ICorDebugNativeFrame::GetRegisterSet メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetRegisterSet
helpviewer_keywords:
- ICorDebugNativeFrame::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 6f309b5f-5556-4f1e-b1dd-4fe97fc81d01
topic_type:
- apiref
ms.openlocfilehash: 8878c438ad76b1a87429e09b8a4a8bbffb90d00d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722413"
---
# <a name="icordebugnativeframegetregisterset-method"></a><span data-ttu-id="ed229-103">ICorDebugNativeFrame::GetRegisterSet メソッド</span><span class="sxs-lookup"><span data-stu-id="ed229-103">ICorDebugNativeFrame::GetRegisterSet Method</span></span>

<span data-ttu-id="ed229-104">このスタックフレームのレジスタセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="ed229-104">Gets the register set for this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed229-105">構文</span><span class="sxs-lookup"><span data-stu-id="ed229-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed229-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ed229-106">Parameters</span></span>  

 `ppRegisters`  
 <span data-ttu-id="ed229-107">入出力このスタックフレームの [レジスタセットを表す、オブジェクトの](icordebugregisterset-interface.md) アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ed229-107">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) object that represents the register set for this stack frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed229-108">要件</span><span class="sxs-lookup"><span data-stu-id="ed229-108">Requirements</span></span>  

 <span data-ttu-id="ed229-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed229-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed229-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ed229-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed229-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed229-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed229-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed229-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed229-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ed229-113">See also</span></span>
