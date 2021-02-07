---
description: '詳細については、次を参照してください: CorDebugInternalFrameType 列挙型'
title: CorDebugInternalFrameType 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugInternalFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInternalFrameType
helpviewer_keywords:
- CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type:
- apiref
ms.openlocfilehash: 0479ae7602224e03086b9dacf91d360253b61818
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662001"
---
# <a name="cordebuginternalframetype-enumeration"></a><span data-ttu-id="48765-103">CorDebugInternalFrameType 列挙型</span><span class="sxs-lookup"><span data-stu-id="48765-103">CorDebugInternalFrameType Enumeration</span></span>

<span data-ttu-id="48765-104">スタック フレームの型を示します。</span><span class="sxs-lookup"><span data-stu-id="48765-104">Identifies the type of stack frame.</span></span> <span data-ttu-id="48765-105">この列挙体は、 [GetFrameType](icordebuginternalframe-getframetype-method.md) メソッドによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="48765-105">This enumeration is used by the [ICorDebugInternalFrame::GetFrameType](icordebuginternalframe-getframetype-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48765-106">構文</span><span class="sxs-lookup"><span data-stu-id="48765-106">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugInternalFrameType {  
  
    STUBFRAME_NONE                 = 0x00000000,  
    STUBFRAME_M2U                  = 0x00000001,  
    STUBFRAME_U2M                  = 0x00000002,  
    STUBFRAME_APPDOMAIN_TRANSITION = 0x00000003,  
    STUBFRAME_LIGHTWEIGHT_FUNCTION = 0x00000004,  
    STUBFRAME_FUNC_EVAL            = 0x00000005,  
    STUBFRAME_INTERNALCALL         = 0x00000006,  
    STUBFRAME_CLASS_INIT           = 0x00000007,  
    STUBFRAME_EXCEPTION            = 0x00000008,  
    STUBFRAME_SECURITY             = 0x00000009,  
    STUBFRAME_JIT_COMPILATION     = 0x0000000a,  
} CorDebugInternalFrameType;  
```  
  
## <a name="members"></a><span data-ttu-id="48765-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="48765-107">Members</span></span>  
  
|<span data-ttu-id="48765-108">メンバー</span><span class="sxs-lookup"><span data-stu-id="48765-108">Member</span></span>|<span data-ttu-id="48765-109">説明</span><span class="sxs-lookup"><span data-stu-id="48765-109">Description</span></span>|  
|------------|-----------------|  
|`STUBFRAME_NONE`|<span data-ttu-id="48765-110">null 値。</span><span class="sxs-lookup"><span data-stu-id="48765-110">A null value.</span></span> <span data-ttu-id="48765-111">メソッドは、 `ICorDebugInternalFrame::GetFrameType` この値を返しません。</span><span class="sxs-lookup"><span data-stu-id="48765-111">The `ICorDebugInternalFrame::GetFrameType` method never returns this value.</span></span>|  
|`STUBFRAME_M2U`|<span data-ttu-id="48765-112">アンマネージスタブフレーム。</span><span class="sxs-lookup"><span data-stu-id="48765-112">A managed-to-unmanaged stub frame.</span></span>|  
|`STUBFRAME_U2M`|<span data-ttu-id="48765-113">アンマネージスタブフレーム。</span><span class="sxs-lookup"><span data-stu-id="48765-113">An unmanaged-to-managed stub frame.</span></span>|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|<span data-ttu-id="48765-114">アプリケーションドメイン間の移行。</span><span class="sxs-lookup"><span data-stu-id="48765-114">A transition between application domains.</span></span>|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|<span data-ttu-id="48765-115">ライトウェイトメソッド呼び出し。</span><span class="sxs-lookup"><span data-stu-id="48765-115">A lightweight method call.</span></span>|  
|`STUBFRAME_FUNC_EVAL`|<span data-ttu-id="48765-116">関数の評価の開始。</span><span class="sxs-lookup"><span data-stu-id="48765-116">The start of function evaluation.</span></span>|  
|`STUBFRAME_INTERNALCALL`|<span data-ttu-id="48765-117">共通言語ランタイムへの内部呼び出し。</span><span class="sxs-lookup"><span data-stu-id="48765-117">An internal call into the common language runtime.</span></span>|  
|`STUBFRAME_CLASS_INIT`|<span data-ttu-id="48765-118">クラスの初期化の開始。</span><span class="sxs-lookup"><span data-stu-id="48765-118">The start of a class initialization.</span></span>|  
|`STUBFRAME_EXCEPTION`|<span data-ttu-id="48765-119">スローされる例外。</span><span class="sxs-lookup"><span data-stu-id="48765-119">An exception that is thrown.</span></span>|  
|`STUBFRAME_SECURITY`|<span data-ttu-id="48765-120">コードアクセスセキュリティに使用されるフレーム。</span><span class="sxs-lookup"><span data-stu-id="48765-120">A frame used for code access security.</span></span>|  
|`STUBFRAME_JIT_COMPILATION`|<span data-ttu-id="48765-121">ランタイムは、メソッドを JIT コンパイルしています。</span><span class="sxs-lookup"><span data-stu-id="48765-121">The runtime is JIT-compiling a method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="48765-122">要件</span><span class="sxs-lookup"><span data-stu-id="48765-122">Requirements</span></span>  

 <span data-ttu-id="48765-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48765-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48765-124">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48765-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48765-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48765-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48765-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48765-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48765-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="48765-127">See also</span></span>

- [<span data-ttu-id="48765-128">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="48765-128">Debugging Enumerations</span></span>](debugging-enumerations.md)
