---
description: '詳細については、次を参照してください: CoreClrDebugProcInfo 構造体'
title: CoreClrDebugProcInfo 構造体
ms.date: 03/30/2017
api_name:
- CoreClrDebugProcInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugProcInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreClrDebugProcInfo structure
- Silverlight, remote debugging
ms.assetid: 4ddc37da-5c94-4beb-b61c-b54071c0e749
topic_type:
- apiref
ms.openlocfilehash: 04befb057be689e68dd3571a13990da9af64551f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801489"
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="fa6c5-103">CoreClrDebugProcInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="fa6c5-103">CoreClrDebugProcInfo Structure</span></span>

<span data-ttu-id="fa6c5-104">リモート コンピューターで実行されているプロセスを表します。</span><span class="sxs-lookup"><span data-stu-id="fa6c5-104">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa6c5-105">構文</span><span class="sxs-lookup"><span data-stu-id="fa6c5-105">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="fa6c5-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="fa6c5-106">Members</span></span>  
  
|<span data-ttu-id="fa6c5-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="fa6c5-107">Member</span></span>|<span data-ttu-id="fa6c5-108">説明</span><span class="sxs-lookup"><span data-stu-id="fa6c5-108">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="fa6c5-109">OS によって割り当てられたプロセス識別子。</span><span class="sxs-lookup"><span data-stu-id="fa6c5-109">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="fa6c5-110">対象のコンピューターで実行されているリモート デバッグ プロキシによって割り当てられたプロセス識別子。</span><span class="sxs-lookup"><span data-stu-id="fa6c5-110">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="fa6c5-111">この識別子は OS 識別子よりも少ない頻度で再利用されます。</span><span class="sxs-lookup"><span data-stu-id="fa6c5-111">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="fa6c5-112">プロセスのコマンド ライン。</span><span class="sxs-lookup"><span data-stu-id="fa6c5-112">Command-line of the process.</span></span> <span data-ttu-id="fa6c5-113">このメンバーは切り詰められる場合があります。</span><span class="sxs-lookup"><span data-stu-id="fa6c5-113">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fa6c5-114">要件</span><span class="sxs-lookup"><span data-stu-id="fa6c5-114">Requirements</span></span>  

 <span data-ttu-id="fa6c5-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa6c5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa6c5-116">**ヘッダー:** Coreclrremoteデバッグインターフェイス .h</span><span class="sxs-lookup"><span data-stu-id="fa6c5-116">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="fa6c5-117">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="fa6c5-117">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="fa6c5-118">**.NET Framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="fa6c5-118">**.NET Framework Versions:** 3.5 SP1</span></span>
