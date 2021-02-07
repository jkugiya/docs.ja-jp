---
description: 詳細については、「ICoreClrDebugTarget インターフェイス」を参照してください。
title: ICoreClrDebugTarget インターフェイス
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
ms.openlocfilehash: f0ed4dd75cd1daca6e83617433b29bbaecb1dd36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728757"
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="3ab64-103">ICoreClrDebugTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3ab64-103">ICoreClrDebugTarget Interface</span></span>

<span data-ttu-id="3ab64-104">参照カウントを制御し、プロセスを列挙し、リモートの Macintosh Silverlight ターゲットにアタッチされているデバッガーに関連付けられているメモリを解放するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="3ab64-104">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ab64-105">構文</span><span class="sxs-lookup"><span data-stu-id="3ab64-105">Syntax</span></span>  
  
```cpp  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3ab64-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="3ab64-106">Methods</span></span>  
  
|<span data-ttu-id="3ab64-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="3ab64-107">Method</span></span>|<span data-ttu-id="3ab64-108">説明</span><span class="sxs-lookup"><span data-stu-id="3ab64-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3ab64-109">ICoreClrDebugTarget::EnumProcesses メソッド</span><span class="sxs-lookup"><span data-stu-id="3ab64-109">ICoreClrDebugTarget::EnumProcesses Method</span></span>](icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="3ab64-110">リモート コンピューターで実行されているプロセスを列挙します。</span><span class="sxs-lookup"><span data-stu-id="3ab64-110">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="3ab64-111">ICoreClrDebugTarget::EnumRuntimes メソッド</span><span class="sxs-lookup"><span data-stu-id="3ab64-111">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="3ab64-112">リモートコンピューター上の指定されたプロセスの共通言語ランタイム (CLRs) を列挙します。</span><span class="sxs-lookup"><span data-stu-id="3ab64-112">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="3ab64-113">ICoreClrDebugTarget::FreeMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="3ab64-113">ICoreClrDebugTarget::FreeMemory Method</span></span>](icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="3ab64-114">このクラスの列挙メソッドによって割り当てられたメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="3ab64-114">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ab64-115">解説</span><span class="sxs-lookup"><span data-stu-id="3ab64-115">Remarks</span></span>  

 <span data-ttu-id="3ab64-116">現在、この機能は、リモートの Macintosh コンピューターで実行されている Silverlight ベースのアプリケーションターゲットをデバッグする場合にのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="3ab64-116">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ab64-117">要件</span><span class="sxs-lookup"><span data-stu-id="3ab64-117">Requirements</span></span>  

 <span data-ttu-id="3ab64-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ab64-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ab64-119">**ヘッダー:** Coreclrremoteデバッグインターフェイス .h</span><span class="sxs-lookup"><span data-stu-id="3ab64-119">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="3ab64-120">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="3ab64-120">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="3ab64-121">**.NET Framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="3ab64-121">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ab64-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ab64-122">See also</span></span>

- [<span data-ttu-id="3ab64-123">ICorDebugRemoteTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3ab64-123">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="3ab64-124">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3ab64-124">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="3ab64-125">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3ab64-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
