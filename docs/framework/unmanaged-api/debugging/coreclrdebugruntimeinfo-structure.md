---
description: '詳細については、次を参照してください: CoreClrDebugRuntimeInfo 構造体'
title: CoreClrDebugRuntimeInfo 構造体
ms.date: 03/30/2017
api_name:
- CoreClrDebugRuntimeInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugRuntimeInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreDebugRuntimeInfo structure
- Silverlight, remote debugging
ms.assetid: bd01c30f-b7a8-4179-9497-622b6599b1a6
topic_type:
- apiref
ms.openlocfilehash: 588e8bd1598996d1676e2df5517bd9a52eb59df4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661715"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="eedcf-103">CoreClrDebugRuntimeInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="eedcf-103">CoreClrDebugRuntimeInfo Structure</span></span>

<span data-ttu-id="eedcf-104">リモート コンピューター上のプロセスに読み込まれる共通言語ランタイム (CLR) インスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="eedcf-104">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eedcf-105">構文</span><span class="sxs-lookup"><span data-stu-id="eedcf-105">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="eedcf-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="eedcf-106">Members</span></span>  
  
|<span data-ttu-id="eedcf-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="eedcf-107">Member</span></span>|<span data-ttu-id="eedcf-108">説明</span><span class="sxs-lookup"><span data-stu-id="eedcf-108">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="eedcf-109">対象のコンピューターで実行されているリモート デバッグ プロキシによって割り当てられたランタイム識別子。</span><span class="sxs-lookup"><span data-stu-id="eedcf-109">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eedcf-110">要件</span><span class="sxs-lookup"><span data-stu-id="eedcf-110">Requirements</span></span>  

 <span data-ttu-id="eedcf-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eedcf-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eedcf-112">**ヘッダー:** Coreclrremoteデバッグインターフェイス .h</span><span class="sxs-lookup"><span data-stu-id="eedcf-112">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="eedcf-113">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="eedcf-113">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="eedcf-114">**.NET Framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="eedcf-114">**.NET Framework Versions:** 3.5 SP1</span></span>
