---
description: '詳細については、次のページを参照してください: GetCode メソッド'
title: 'いい変数 Home:: GetCode メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetCode
helpviewer_keywords:
- ICorDebugVariableHome::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: ef002890-4a7b-4a5d-abbf-16c60083f794
topic_type:
- apiref
ms.openlocfilehash: e3ff96816e580fe3cd1cee782dc5bd4166f08a14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794638"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="0f5e3-103">いい変数 Home:: GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="0f5e3-103">ICorDebugVariableHome::GetCode Method</span></span>

<span data-ttu-id="0f5e3-104">このこのコード例の [ホーム](icordebugvariablehome-interface.md) オブジェクトを含む "コード" インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="0f5e3-104">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f5e3-105">構文</span><span class="sxs-lookup"><span data-stu-id="0f5e3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f5e3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0f5e3-106">Parameters</span></span>  

 `ppCode`  
 <span data-ttu-id="0f5e3-107">入出力この表示 [変数ホーム](icordebugvariablehome-interface.md) オブジェクトを含む "コード" インスタンスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0f5e3-107">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f5e3-108">要件</span><span class="sxs-lookup"><span data-stu-id="0f5e3-108">Requirements</span></span>  

 <span data-ttu-id="0f5e3-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f5e3-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f5e3-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f5e3-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f5e3-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f5e3-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f5e3-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f5e3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f5e3-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f5e3-113">See also</span></span>

- [<span data-ttu-id="0f5e3-114">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0f5e3-114">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
