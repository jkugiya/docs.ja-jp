---
description: 詳細については、「のリモートインターフェイス」を参照してください。
title: ICorDebugRemote インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugRemote
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemote
helpviewer_keywords:
- ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: 53d073c6-fa02-40d2-82e1-b9452bb6abaa
topic_type:
- apiref
ms.openlocfilehash: 4c9d92800c68155216a077180ea0b613c67423dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790673"
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="04bc8-103">ICorDebugRemote インターフェイス</span><span class="sxs-lookup"><span data-stu-id="04bc8-103">ICorDebugRemote Interface</span></span>

<span data-ttu-id="04bc8-104">リモート ターゲット プロセスに対してマネージド デバッガーを起動または接続する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="04bc8-104">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04bc8-105">構文</span><span class="sxs-lookup"><span data-stu-id="04bc8-105">Syntax</span></span>  
  
```cpp  
interface ICorDebugRemote : IUnknown  
{  
    HRESULT CreateProcessEx  
      (  
      [in] ICorDebugRemoteTarget *     pRemoteTarget,  
      [in] LPCWSTR                     lpApplicationName,  
      [in] LPWSTR                      lpCommandLine,  
      [in] LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
      [in] LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
      [in] BOOL                        bInheritHandles,  
      [in] DWORD                       dwCreationFlags,  
      [in] PVOID                       lpEnvironment,  
      [in] LPCWSTR                     lpCurrentDirectory,  
      [in] LPSTARTUPINFOW              lpStartupInfo,  
      [in] LPPROCESS_INFORMATION       lpProcessInformation,  
      [in] CorDebugCreateProcessFlags  debuggingFlags,  
      [out] ICorDebugProcess **        ppProcess  
      );  
  
    HRESULT DebugActiveProcessEx  
      (  
      [in] ICorDebugRemoteTarget *   pRemoteTarget,  
      [in] DWORD                     dwProcessId,  
      [in] BOOL                      fWin32Attach,  
      [out] ICorDebugProcess **      ppProcess  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="04bc8-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="04bc8-106">Methods</span></span>  
  
|<span data-ttu-id="04bc8-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="04bc8-107">Method</span></span>|<span data-ttu-id="04bc8-108">説明</span><span class="sxs-lookup"><span data-stu-id="04bc8-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="04bc8-109">ICorDebugRemote::CreateProcessEx メソッド</span><span class="sxs-lookup"><span data-stu-id="04bc8-109">ICorDebugRemote::CreateProcessEx Method</span></span>](icordebugremote-createprocessex-method.md)|<span data-ttu-id="04bc8-110">マネージデバッグ用にリモートコンピューター上にプロセスを作成します。</span><span class="sxs-lookup"><span data-stu-id="04bc8-110">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="04bc8-111">ICorDebugRemote::DebugActiveProcessEx メソッド</span><span class="sxs-lookup"><span data-stu-id="04bc8-111">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="04bc8-112">デバッガーでリモートコンピューター上のプロセスを起動します。</span><span class="sxs-lookup"><span data-stu-id="04bc8-112">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04bc8-113">解説</span><span class="sxs-lookup"><span data-stu-id="04bc8-113">Remarks</span></span>  

 <span data-ttu-id="04bc8-114">現在、この機能は、リモートの Macintosh コンピューターで実行されている Silverlight ベースのアプリケーションターゲットをデバッグする場合にのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="04bc8-114">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04bc8-115">要件</span><span class="sxs-lookup"><span data-stu-id="04bc8-115">Requirements</span></span>  

 <span data-ttu-id="04bc8-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04bc8-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04bc8-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04bc8-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04bc8-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04bc8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04bc8-119">**.NET Framework のバージョン:** 4.5、4、3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="04bc8-119">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04bc8-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="04bc8-120">See also</span></span>

- [<span data-ttu-id="04bc8-121">ICorDebugRemoteTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="04bc8-121">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="04bc8-122">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="04bc8-122">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="04bc8-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="04bc8-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
