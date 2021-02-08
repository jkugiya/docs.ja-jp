---
description: '詳細については、次を参照してください: GetFrameType メソッド'
title: ICorDebugInternalFrame::GetFrameType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame.GetFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type:
- apiref
ms.openlocfilehash: ea96f032ebfa5914503287d124242b74a84ea11f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791180"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="f4f38-103">ICorDebugInternalFrame::GetFrameType メソッド</span><span class="sxs-lookup"><span data-stu-id="f4f38-103">ICorDebugInternalFrame::GetFrameType Method</span></span>

<span data-ttu-id="f4f38-104">この内部フレームの型を取得します。</span><span class="sxs-lookup"><span data-stu-id="f4f38-104">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4f38-105">構文</span><span class="sxs-lookup"><span data-stu-id="f4f38-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4f38-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f4f38-106">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="f4f38-107">入出力このオブジェクトによって表される内部フレームの種類を示す CorDebugInternalFrameType 列挙値へのポインター `ICorDebugInternalFrame` 。</span><span class="sxs-lookup"><span data-stu-id="f4f38-107">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4f38-108">解説</span><span class="sxs-lookup"><span data-stu-id="f4f38-108">Remarks</span></span>  

 <span data-ttu-id="f4f38-109">内部フレームの種類は STUBFRAME_NONE されません。</span><span class="sxs-lookup"><span data-stu-id="f4f38-109">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="f4f38-110">デバッガーは、認識されない内部フレーム型を正常に無視する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4f38-110">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4f38-111">要件</span><span class="sxs-lookup"><span data-stu-id="f4f38-111">Requirements</span></span>  

 <span data-ttu-id="f4f38-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4f38-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4f38-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4f38-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4f38-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4f38-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4f38-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4f38-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
