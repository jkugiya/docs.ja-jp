---
description: '詳細情報: USER_THREAD 構造'
title: USER_THREAD 構造体
ms.date: 03/30/2017
api_name:
- USER_THREAD
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- USER_THREAD
helpviewer_keywords:
- USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type:
- apiref
ms.openlocfilehash: a4bd22073b7610307e67107781bdb68a15ef795f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761269"
---
# <a name="user_thread-structure"></a><span data-ttu-id="8ad20-103">USER_THREAD 構造体</span><span class="sxs-lookup"><span data-stu-id="8ad20-103">USER_THREAD Structure</span></span>

<span data-ttu-id="8ad20-104">スレッドに関する情報をデバッガーに提供します。</span><span class="sxs-lookup"><span data-stu-id="8ad20-104">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="8ad20-105">詳細については、 [INotifySource2:: SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) メソッドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ad20-105">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ad20-106">構文</span><span class="sxs-lookup"><span data-stu-id="8ad20-106">Syntax</span></span>  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="8ad20-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="8ad20-107">Members</span></span>  
  
|<span data-ttu-id="8ad20-108">メンバー</span><span class="sxs-lookup"><span data-stu-id="8ad20-108">Member</span></span>|<span data-ttu-id="8ad20-109">説明</span><span class="sxs-lookup"><span data-stu-id="8ad20-109">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="8ad20-110">スレッドバッファーのアドレス。</span><span class="sxs-lookup"><span data-stu-id="8ad20-110">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="8ad20-111">スレッドバッファーの長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="8ad20-111">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="8ad20-112">スレッド ID。</span><span class="sxs-lookup"><span data-stu-id="8ad20-112">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8ad20-113">要件</span><span class="sxs-lookup"><span data-stu-id="8ad20-113">Requirements</span></span>  

 <span data-ttu-id="8ad20-114">**ヘッダー:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="8ad20-114">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ad20-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ad20-115">See also</span></span>

- [<span data-ttu-id="8ad20-116">SetNotifyFilter メソッド</span><span class="sxs-lookup"><span data-stu-id="8ad20-116">SetNotifyFilter Method</span></span>](inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="8ad20-117">シンボル ストア診断構造体</span><span class="sxs-lookup"><span data-stu-id="8ad20-117">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
