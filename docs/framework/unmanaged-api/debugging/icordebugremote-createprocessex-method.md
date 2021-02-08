---
description: '詳細については、次を参照してください: Okremote:: CreateProcessEx メソッド'
title: ICorDebugRemote::CreateProcessEx メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.CreateProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type:
- apiref
ms.openlocfilehash: cd27400f5c9f348621fb66b3b7730cf15d397151
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794729"
---
# <a name="icordebugremotecreateprocessex-method"></a><span data-ttu-id="17d1e-103">ICorDebugRemote::CreateProcessEx メソッド</span><span class="sxs-lookup"><span data-stu-id="17d1e-103">ICorDebugRemote::CreateProcessEx Method</span></span>

<span data-ttu-id="17d1e-104">デバッガーでリモートコンピューター上のプロセスを起動します。</span><span class="sxs-lookup"><span data-stu-id="17d1e-104">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17d1e-105">構文</span><span class="sxs-lookup"><span data-stu-id="17d1e-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcessEx (  
    [in]  ICorDebugRemoteTarget*      pRemoteTarget,  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess**          ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17d1e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="17d1e-106">Parameters</span></span>  

 `pRemoteTarget`  
 <span data-ttu-id="17d1e-107">からツールの [ターゲットインターフェイス](icordebugremotetarget-interface.md)を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="17d1e-107">[in] Pointer to an [ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="17d1e-108">プロセスを起動するリモートコンピューターを決定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="17d1e-108">Used to determine the remote machine on which the process will be launched.</span></span>  
  
 `lpApplicationName`  
 <span data-ttu-id="17d1e-109">から起動されたプロセスによって実行されるモジュールを指定する、null で終わる文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="17d1e-109">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="17d1e-110">モジュールは、呼び出し元プロセスのセキュリティコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="17d1e-110">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="17d1e-111">から起動されたプロセスによって実行されるコマンドラインを指定する、null で終わる文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="17d1e-111">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="17d1e-112">からリモートデバッグには使用されません。</span><span class="sxs-lookup"><span data-stu-id="17d1e-112">[in] Unused for remote debugging.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="17d1e-113">からリモートデバッグには使用されません。</span><span class="sxs-lookup"><span data-stu-id="17d1e-113">[in] Unused for remote debugging.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="17d1e-114">からリモートデバッグには使用されません。</span><span class="sxs-lookup"><span data-stu-id="17d1e-114">[in] Unused for remote debugging.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="17d1e-115">からリモートデバッグには使用されません。</span><span class="sxs-lookup"><span data-stu-id="17d1e-115">[in] Unused for remote debugging.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="17d1e-116">から新しいプロセスの環境ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="17d1e-116">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="17d1e-117">からプロセスの現在のディレクトリへの完全パスを指定する、null で終わる文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="17d1e-117">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="17d1e-118">このパラメーターが null の場合、新しいプロセスは呼び出しプロセスと同じ現在のドライブとディレクトリを持ちます。</span><span class="sxs-lookup"><span data-stu-id="17d1e-118">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="17d1e-119">からリモートデバッグには使用されません。</span><span class="sxs-lookup"><span data-stu-id="17d1e-119">[in] Unused for remote debugging.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="17d1e-120">からリモートデバッグには使用されません。</span><span class="sxs-lookup"><span data-stu-id="17d1e-120">[in] Unused for remote debugging.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="17d1e-121">からリモートデバッグには使用されません。</span><span class="sxs-lookup"><span data-stu-id="17d1e-121">[in] Unused for remote debugging.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="17d1e-122">入出力プロセスを表す "いいプロセスインターフェイス" オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="17d1e-122">[out] A pointer to the address of a"ICorDebugProcess Interface" object that represents the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17d1e-123">戻り値</span><span class="sxs-lookup"><span data-stu-id="17d1e-123">Return Value</span></span>  

 <span data-ttu-id="17d1e-124">S_OK</span><span class="sxs-lookup"><span data-stu-id="17d1e-124">S_OK</span></span>  
 <span data-ttu-id="17d1e-125">リモートコンピューターでプロセスが正常に起動され、デバッグのために "のプロセスインターフェイス" が返されました。</span><span class="sxs-lookup"><span data-stu-id="17d1e-125">Successfully launched the process on the remote machine and returned an "ICorDebugProcess Interface" for debugging.</span></span>  
  
 <span data-ttu-id="17d1e-126">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="17d1e-126">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="17d1e-127">リモートコンピューターでプロセスを起動できず、デバッグのために "のプロセスインターフェイス" を返します。</span><span class="sxs-lookup"><span data-stu-id="17d1e-127">Unable to launch the process on the remote machine and return an "ICorDebugProcess Interface" for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17d1e-128">解説</span><span class="sxs-lookup"><span data-stu-id="17d1e-128">Remarks</span></span>  

 <span data-ttu-id="17d1e-129">混合モードのデバッグは、Silverlight ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="17d1e-129">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17d1e-130">要件</span><span class="sxs-lookup"><span data-stu-id="17d1e-130">Requirements</span></span>  

 <span data-ttu-id="17d1e-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17d1e-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17d1e-132">**ヘッダー:** CorDebug .idl</span><span class="sxs-lookup"><span data-stu-id="17d1e-132">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="17d1e-133">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17d1e-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17d1e-134">**.NET Framework のバージョン:** 4.5、4、3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="17d1e-134">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d1e-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="17d1e-135">See also</span></span>

- [<span data-ttu-id="17d1e-136">ICorDebugRemote インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17d1e-136">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="17d1e-137">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17d1e-137">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="17d1e-138">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="17d1e-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
