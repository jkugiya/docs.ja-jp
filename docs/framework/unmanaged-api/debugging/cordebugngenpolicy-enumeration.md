---
description: '詳細については、次を参照してください: CorDebugNGenPolicy 列挙型'
title: CorDebugNGenPolicy 列挙型
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugNGenPolicy
helpviewer_keywords:
- CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type:
- apiref
ms.openlocfilehash: 529a5979bacef32ce78262c122004a66b54156ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801580"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="67893-103">CorDebugNGenPolicy 列挙型</span><span class="sxs-lookup"><span data-stu-id="67893-103">CorDebugNGenPolicy Enumeration</span></span>

<span data-ttu-id="67893-104">デバッガーがネイティブ イメージ キャッシュからネイティブ (NGen) イメージを読み込むかどうかを指定する値を提供します。</span><span class="sxs-lookup"><span data-stu-id="67893-104">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67893-105">構文</span><span class="sxs-lookup"><span data-stu-id="67893-105">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="67893-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="67893-106">Members</span></span>  
  
|<span data-ttu-id="67893-107">メンバー名</span><span class="sxs-lookup"><span data-stu-id="67893-107">Member name</span></span>|<span data-ttu-id="67893-108">説明</span><span class="sxs-lookup"><span data-stu-id="67893-108">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="67893-109">Windows 8.x ストアアプリでは、ローカルのネイティブイメージキャッシュからのイメージの使用は無効になっています。</span><span class="sxs-lookup"><span data-stu-id="67893-109">In a Windows 8.x Store app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="67893-110">デスクトップアプリでは、この設定による影響はありません。</span><span class="sxs-lookup"><span data-stu-id="67893-110">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67893-111">解説</span><span class="sxs-lookup"><span data-stu-id="67893-111">Remarks</span></span>  

 <span data-ttu-id="67893-112">`CorDebugNGENPolicy`列挙体は、 [ICorDebugProcess5:: EnableNGENPolicy](icordebugprocess5-enablengenpolicy-method.md)メソッドによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="67893-112">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="67893-113">ローカルのネイティブイメージキャッシュからのイメージの使用を無効にすると、最適化されたネイティブイメージの代わりにデバッグ可能な JIT コンパイルイメージをデバッガーが読み込むことができるため、一貫したデバッグエクスペリエンスを実現できます。</span><span class="sxs-lookup"><span data-stu-id="67893-113">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67893-114">要件</span><span class="sxs-lookup"><span data-stu-id="67893-114">Requirements</span></span>  

 <span data-ttu-id="67893-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67893-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67893-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67893-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67893-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67893-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67893-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67893-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67893-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="67893-119">See also</span></span>

- [<span data-ttu-id="67893-120">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="67893-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
