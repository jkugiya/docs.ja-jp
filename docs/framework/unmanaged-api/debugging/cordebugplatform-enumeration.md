---
description: 詳細については、「CorDebugPlatform 列挙型」を参照してください。
title: CorDebugPlatform 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugPlatformEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugPlatformEnum
helpviewer_keywords:
- CorDebugPlatformEnum enumeration [.NET Framework debugging]
ms.assetid: c5444816-7378-4521-afd3-bf5e4b5303d5
topic_type:
- apiref
ms.openlocfilehash: d6a78ec00f99ff34158f784e039372c8937e6d16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661858"
---
# <a name="cordebugplatform-enumeration"></a><span data-ttu-id="26182-103">CorDebugPlatform 列挙型</span><span class="sxs-lookup"><span data-stu-id="26182-103">CorDebugPlatform Enumeration</span></span>

<span data-ttu-id="26182-104">は [、のターゲットプラットフォームの値](icordebugdatatarget-getplatform-method.md) を提供しています。</span><span class="sxs-lookup"><span data-stu-id="26182-104">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26182-105">構文</span><span class="sxs-lookup"><span data-stu-id="26182-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugPlatform  
{  
    CORDB_PLATFORM_WINDOWS_X86,    // Windows on Intel x86  
    CORDB_PLATFORM_WINDOWS_AMD64,  // Windows x64 (AMD64, Intel EM64T)  
    CORDB_PLATFORM_WINDOWS_IA64,   // Windows on Intel IA-64  
    CORDB_PLATFORM_MAC_PPC,        // Macintosh OS on PowerPC  
    CORDB_PLATFORM_MAC_X86,        // Macintosh OS on Intel x86  
    CORDB_PLATFORM_WINDOWS_ARM,    // Windows on ARM  
    CORDB_PLATFORM_MAC_AMD64       // MacOS on Intel x64  
} CorDebugPlatform;  
```  
  
## <a name="members"></a><span data-ttu-id="26182-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="26182-106">Members</span></span>  
  
|<span data-ttu-id="26182-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="26182-107">Member</span></span>|<span data-ttu-id="26182-108">説明</span><span class="sxs-lookup"><span data-stu-id="26182-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="26182-109">CORDB_PLATFORM_WINDOWS_X86</span><span class="sxs-lookup"><span data-stu-id="26182-109">CORDB_PLATFORM_WINDOWS_X86</span></span>|<span data-ttu-id="26182-110">ターゲット プラットフォームは、Intel x86 ハードウェア上で稼動する Windows です。</span><span class="sxs-lookup"><span data-stu-id="26182-110">The target platform is Windows running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="26182-111">CORDB_PLATFORM_WINDOWS_AMD64</span><span class="sxs-lookup"><span data-stu-id="26182-111">CORDB_PLATFORM_WINDOWS_AMD64</span></span>|<span data-ttu-id="26182-112">ターゲット プラットフォームは、AMD64 または Intel EM64T ハードウェア上で稼動する 64 ビット Windows です。</span><span class="sxs-lookup"><span data-stu-id="26182-112">The target platform is 64 bit Windows running on AMD64 or Intel EM64T hardware.</span></span>|  
|<span data-ttu-id="26182-113">CORDB_PLATFORM_WINDOWS_IA64</span><span class="sxs-lookup"><span data-stu-id="26182-113">CORDB_PLATFORM_WINDOWS_IA64</span></span>|<span data-ttu-id="26182-114">ターゲット プラットフォームは、Intel IA-64 ハードウェア上で稼動する 32 ビット Windows です。</span><span class="sxs-lookup"><span data-stu-id="26182-114">The target platform is 32 bit Windows running on Intel IA-64 hardware.</span></span>|  
|<span data-ttu-id="26182-115">CORDB_PLATFORM_MAC_PPC</span><span class="sxs-lookup"><span data-stu-id="26182-115">CORDB_PLATFORM_MAC_PPC</span></span>|<span data-ttu-id="26182-116">ターゲットプラットフォームは、PowerPC ハードウェアで実行されている Macintosh オペレーティングシステムです。</span><span class="sxs-lookup"><span data-stu-id="26182-116">The target platform is the Macintosh operating system running on PowerPC hardware.</span></span>|  
|<span data-ttu-id="26182-117">CORDB_PLATFORM_MAC_X86</span><span class="sxs-lookup"><span data-stu-id="26182-117">CORDB_PLATFORM_MAC_X86</span></span>|<span data-ttu-id="26182-118">ターゲットプラットフォームは、Intel x86 ハードウェア上で実行されている Macintosh オペレーティングシステムです。</span><span class="sxs-lookup"><span data-stu-id="26182-118">The target platform is the Macintosh operating system running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="26182-119">CORDB_PLATFORM_WINDOWS_ARM</span><span class="sxs-lookup"><span data-stu-id="26182-119">CORDB_PLATFORM_WINDOWS_ARM</span></span>|<span data-ttu-id="26182-120">ターゲットプラットフォームは、Windows ARM ハードウェアで実行されている Macintosh オペレーティングシステムです。</span><span class="sxs-lookup"><span data-stu-id="26182-120">The target platform is the Macintosh operating system running on Windows ARM hardware.</span></span>|  
|<span data-ttu-id="26182-121">CORDB_PLATFORM_MAC_AMD64</span><span class="sxs-lookup"><span data-stu-id="26182-121">CORDB_PLATFORM_MAC_AMD64</span></span>|<span data-ttu-id="26182-122">ターゲットプラットフォームは、AMD64 ハードウェアで実行されている Macintosh オペレーティングシステムです。</span><span class="sxs-lookup"><span data-stu-id="26182-122">The target platform is the Macintosh operating system running on AMD64 hardware.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="26182-123">要件</span><span class="sxs-lookup"><span data-stu-id="26182-123">Requirements</span></span>  

 <span data-ttu-id="26182-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26182-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26182-125">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26182-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26182-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26182-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26182-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26182-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
 <span data-ttu-id="26182-128">`CORDB_PLATFORM_WINDOWS_ARM` および `CORDB_PLATFORM_MAC_AMD64` メンバーは、.NET Framework 4.5.2 以降のバージョンでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="26182-128">The `CORDB_PLATFORM_WINDOWS_ARM` and `CORDB_PLATFORM_MAC_AMD64` members are available in the .NET Framework 4.5.2 and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26182-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="26182-129">See also</span></span>

- [<span data-ttu-id="26182-130">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="26182-130">Debugging Enumerations</span></span>](debugging-enumerations.md)
