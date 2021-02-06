---
description: '詳細について: ICorDebugProcess5:: EnableNGENPolicy メソッド'
title: ICorDebugProcess5::EnableNGENPolicy メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
ms.openlocfilehash: 0f3194893665bfe9fff802a293aaafed8254f2e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649924"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="8d71a-103">ICorDebugProcess5::EnableNGENPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="8d71a-103">ICorDebugProcess5::EnableNGENPolicy Method</span></span>

<span data-ttu-id="8d71a-104">マネージデバッガーで実行中にアプリケーションがネイティブイメージを読み込む方法を決定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="8d71a-104">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d71a-105">構文</span><span class="sxs-lookup"><span data-stu-id="8d71a-105">Syntax</span></span>  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d71a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d71a-106">Parameters</span></span>  

 `ePolicy`  
 <span data-ttu-id="8d71a-107">からマネージデバッガーで実行中にアプリケーションがネイティブイメージを読み込む方法を決定する [Cordebugngenpolicy](cordebugngenpolicy-enumeration.md) 定数。</span><span class="sxs-lookup"><span data-stu-id="8d71a-107">[in] A [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d71a-108">解説</span><span class="sxs-lookup"><span data-stu-id="8d71a-108">Remarks</span></span>  

 <span data-ttu-id="8d71a-109">ポリシーが正常に設定されている場合、メソッドはを返し `S_OK` ます。</span><span class="sxs-lookup"><span data-stu-id="8d71a-109">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="8d71a-110">`ePolicy`が[Cordebugngenpolicy](cordebugngenpolicy-enumeration.md)によって定義された列挙値の範囲外にある場合、メソッドはを返し、 `E_INVALIDARG` メソッドの呼び出しは無効です。</span><span class="sxs-lookup"><span data-stu-id="8d71a-110">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="8d71a-111">ネイティブイメージジェネレーター (Ngen.exe) のポリシーを更新できない場合、メソッドはを返し `E_FAIL` ます。</span><span class="sxs-lookup"><span data-stu-id="8d71a-111">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="8d71a-112">メソッドは、 `ICorDebugProcess5::EnableNGenPolicy` プロセスの有効期間中、いつでも呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8d71a-112">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="8d71a-113">ポリシーは、ポリシーが設定された後に読み込まれるすべてのモジュールに対して有効です。</span><span class="sxs-lookup"><span data-stu-id="8d71a-113">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d71a-114">要件</span><span class="sxs-lookup"><span data-stu-id="8d71a-114">Requirements</span></span>  

 <span data-ttu-id="8d71a-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d71a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d71a-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d71a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d71a-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d71a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d71a-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d71a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d71a-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d71a-119">See also</span></span>

- [<span data-ttu-id="8d71a-120">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d71a-120">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="8d71a-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d71a-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8d71a-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="8d71a-122">Debugging</span></span>](index.md)
