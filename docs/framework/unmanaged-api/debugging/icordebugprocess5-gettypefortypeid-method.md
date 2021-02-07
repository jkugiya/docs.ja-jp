---
description: '詳細について: ICorDebugProcess5:: GetTypeForTypeID メソッド'
title: ICorDebugProcess5::GetTypeForTypeID メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeForTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeForTypeID
helpviewer_keywords:
- GetTypeForTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeForTypeID method [.NET Framework debugging]
ms.assetid: e0eed5a8-fa6d-4818-bd00-7babcea30325
topic_type:
- apiref
ms.openlocfilehash: a18543b0afc867dc3796264ac1d08a775c73ca59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746374"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="1cdc8-103">ICorDebugProcess5::GetTypeForTypeID メソッド</span><span class="sxs-lookup"><span data-stu-id="1cdc8-103">ICorDebugProcess5::GetTypeForTypeID Method</span></span>

<span data-ttu-id="1cdc8-104">型識別子をの型の値に変換します。</span><span class="sxs-lookup"><span data-stu-id="1cdc8-104">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cdc8-105">構文</span><span class="sxs-lookup"><span data-stu-id="1cdc8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cdc8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1cdc8-106">Parameters</span></span>  

 `id`  
 <span data-ttu-id="1cdc8-107">から型識別子。</span><span class="sxs-lookup"><span data-stu-id="1cdc8-107">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="1cdc8-108">入出力テキストオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1cdc8-108">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cdc8-109">解説</span><span class="sxs-lookup"><span data-stu-id="1cdc8-109">Remarks</span></span>  

 <span data-ttu-id="1cdc8-110">場合によっては、型識別子を返すメソッドが null 値を返すことがあり `COR_TYPEID` ます。</span><span class="sxs-lookup"><span data-stu-id="1cdc8-110">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="1cdc8-111">この値が引数として渡された場合 `id` 、 `GetTypeForTypeID` メソッドは失敗し、を返し `E_FAIL` ます。</span><span class="sxs-lookup"><span data-stu-id="1cdc8-111">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cdc8-112">要件</span><span class="sxs-lookup"><span data-stu-id="1cdc8-112">Requirements</span></span>  

 <span data-ttu-id="1cdc8-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1cdc8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cdc8-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1cdc8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1cdc8-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1cdc8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cdc8-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cdc8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cdc8-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="1cdc8-117">See also</span></span>

- [<span data-ttu-id="1cdc8-118">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1cdc8-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="1cdc8-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1cdc8-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
