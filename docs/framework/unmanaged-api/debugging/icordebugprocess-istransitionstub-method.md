---
description: '詳細については、次を参照してください: IsTransitionStub Method:: メソッド'
title: ICorDebugProcess::IsTransitionStub メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
ms.openlocfilehash: 0da8527538c2573b1ec0d26f8711644fe8fcca2a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782001"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="05196-103">ICorDebugProcess::IsTransitionStub メソッド</span><span class="sxs-lookup"><span data-stu-id="05196-103">ICorDebugProcess::IsTransitionStub Method</span></span>

<span data-ttu-id="05196-104">アドレスが、マネージコードへの遷移を発生させるスタブ内にあるかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="05196-104">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05196-105">構文</span><span class="sxs-lookup"><span data-stu-id="05196-105">Syntax</span></span>  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05196-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="05196-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="05196-107">から `CORDB_ADDRESS` 対象のアドレスを示す値です。</span><span class="sxs-lookup"><span data-stu-id="05196-107">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="05196-108">入出力`true`指定されたアドレスが、マネージコードへの遷移を発生させるスタブ内にある場合は、それ以外の場合 `pbTransitionStub` はとなるブール値へのポインター。 `false`</span><span class="sxs-lookup"><span data-stu-id="05196-108">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05196-109">解説</span><span class="sxs-lookup"><span data-stu-id="05196-109">Remarks</span></span>  

 <span data-ttu-id="05196-110">`IsTransitionStub`アンマネージステッピングコードでは、メソッドを使用して、管理対象のステッパにステップ実行コントロールをいつ返すかを決定できます。</span><span class="sxs-lookup"><span data-stu-id="05196-110">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="05196-111">ポータブル実行可能 (PE) ファイルの情報を参照して、遷移スタブを識別することもできます。</span><span class="sxs-lookup"><span data-stu-id="05196-111">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05196-112">要件</span><span class="sxs-lookup"><span data-stu-id="05196-112">Requirements</span></span>  

 <span data-ttu-id="05196-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05196-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05196-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05196-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05196-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05196-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05196-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05196-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
