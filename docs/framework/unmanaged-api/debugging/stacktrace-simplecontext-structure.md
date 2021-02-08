---
description: '詳細情報: StackTrace_SimpleContext 構造'
title: StackTrace_SimpleContext 構造体
ms.date: 03/30/2017
api_name:
- StackTrace_SimpleContext
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type:
- apiref
ms.openlocfilehash: 22a0acada5ef2d392dfdef5326953be137280d7f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800553"
---
# <a name="stacktrace_simplecontext-structure"></a><span data-ttu-id="846eb-103">StackTrace_SimpleContext 構造体</span><span class="sxs-lookup"><span data-stu-id="846eb-103">StackTrace_SimpleContext Structure</span></span>

<span data-ttu-id="846eb-104">完全な `CONTEXT` 構造の代わりに使用できる単純なコンテキストを提供します。</span><span class="sxs-lookup"><span data-stu-id="846eb-104">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="846eb-105">構文</span><span class="sxs-lookup"><span data-stu-id="846eb-105">Syntax</span></span>  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="846eb-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="846eb-106">Members</span></span>  
  
|<span data-ttu-id="846eb-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="846eb-107">Member</span></span>|<span data-ttu-id="846eb-108">説明</span><span class="sxs-lookup"><span data-stu-id="846eb-108">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="846eb-109">スタックポインター、または x86 プラットフォームの enter スタックポインター (ESP)。</span><span class="sxs-lookup"><span data-stu-id="846eb-109">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="846eb-110">フレームオフセット、または x86 プラットフォームでの EBP レジスタ。</span><span class="sxs-lookup"><span data-stu-id="846eb-110">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="846eb-111">命令ポインター、または x86 プラットフォームの enter 命令ポインター (EIP)。</span><span class="sxs-lookup"><span data-stu-id="846eb-111">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="846eb-112">解説</span><span class="sxs-lookup"><span data-stu-id="846eb-112">Remarks</span></span>  

 <span data-ttu-id="846eb-113">通常、スタックトレース関数はアドレス、フレームオフセット、およびスタックアドレスだけを返す必要があるため、必要に応じて、大きな構造体の代わりに構造体を使用することもでき `SimpleContext` `CONTEXT` ます。</span><span class="sxs-lookup"><span data-stu-id="846eb-113">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="846eb-114">要件</span><span class="sxs-lookup"><span data-stu-id="846eb-114">Requirements</span></span>  

 <span data-ttu-id="846eb-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="846eb-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="846eb-116">**ヘッダー:** SOS_Stacktrace</span><span class="sxs-lookup"><span data-stu-id="846eb-116">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="846eb-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="846eb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="846eb-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="846eb-118">See also</span></span>

- [<span data-ttu-id="846eb-119">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="846eb-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="846eb-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="846eb-120">Debugging</span></span>](index.md)
