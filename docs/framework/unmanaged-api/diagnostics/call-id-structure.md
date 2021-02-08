---
description: '詳細情報: CALL_ID 構造'
title: CALL_ID 構造体
ms.date: 03/30/2017
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
ms.openlocfilehash: 4ef6023e382e8c5fead48494f428648a37f3bef4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800488"
---
# <a name="call_id-structure"></a><span data-ttu-id="6d387-103">CALL_ID 構造体</span><span class="sxs-lookup"><span data-stu-id="6d387-103">CALL_ID Structure</span></span>

<span data-ttu-id="6d387-104">呼び出されている関数についての情報をデバッガーに提供します。</span><span class="sxs-lookup"><span data-stu-id="6d387-104">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="6d387-105">詳細については、 [INotifySink2](inotifysink2-interface.md) インターフェイスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d387-105">See the [INotifySink2](inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d387-106">構文</span><span class="sxs-lookup"><span data-stu-id="6d387-106">Syntax</span></span>  
  
```cpp  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a><span data-ttu-id="6d387-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="6d387-107">Members</span></span>  
  
|<span data-ttu-id="6d387-108">メンバー</span><span class="sxs-lookup"><span data-stu-id="6d387-108">Member</span></span>|<span data-ttu-id="6d387-109">説明</span><span class="sxs-lookup"><span data-stu-id="6d387-109">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="6d387-110">呼び出しを行っているコンピューターを識別します。</span><span class="sxs-lookup"><span data-stu-id="6d387-110">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="6d387-111">マシンプロセッサを識別します。</span><span class="sxs-lookup"><span data-stu-id="6d387-111">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="6d387-112">呼び出しを実行しているスレッドを識別します。</span><span class="sxs-lookup"><span data-stu-id="6d387-112">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="6d387-113">呼び出し履歴のアドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="6d387-113">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="6d387-114">呼び出しのアドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="6d387-114">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="6d387-115">呼び出しを実行するコンピューターを識別します。</span><span class="sxs-lookup"><span data-stu-id="6d387-115">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6d387-116">要件</span><span class="sxs-lookup"><span data-stu-id="6d387-116">Requirements</span></span>  

 <span data-ttu-id="6d387-117">**ヘッダー:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="6d387-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d387-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d387-118">See also</span></span>

- [<span data-ttu-id="6d387-119">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6d387-119">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="6d387-120">シンボル ストア診断構造体</span><span class="sxs-lookup"><span data-stu-id="6d387-120">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
