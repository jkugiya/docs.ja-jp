---
description: '詳細について: ICorDebug:: CreateProcess メソッド'
title: ICorDebug::CreateProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CreateProcess
helpviewer_keywords:
- ICorDebug::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: b6128694-11ed-46e7-bd4e-49ea1914c46a
topic_type:
- apiref
ms.openlocfilehash: b504b5f7a60fd0fd4a8f8f1c5d8e3c3b8dcfd858
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712117"
---
# <a name="icordebugcreateprocess-method"></a><span data-ttu-id="1922d-103">ICorDebug::CreateProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="1922d-103">ICorDebug::CreateProcess Method</span></span>

<span data-ttu-id="1922d-104">デバッガーの制御下でプロセスとそのプライマリスレッドを起動します。</span><span class="sxs-lookup"><span data-stu-id="1922d-104">Launches a process and its primary thread under the control of the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1922d-105">構文</span><span class="sxs-lookup"><span data-stu-id="1922d-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
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
    [out] ICorDebugProcess            **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1922d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1922d-106">Parameters</span></span>  

 `lpApplicationName`  
 <span data-ttu-id="1922d-107">から起動されたプロセスによって実行されるモジュールを指定する、null で終わる文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1922d-107">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="1922d-108">モジュールは、呼び出し元プロセスのセキュリティコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="1922d-108">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="1922d-109">から起動されたプロセスによって実行されるコマンドラインを指定する、null で終わる文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1922d-109">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span> <span data-ttu-id="1922d-110">アプリケーション名 (たとえば、"SomeApp.exe") は最初の引数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1922d-110">The application name (for example, "SomeApp.exe") must be the first argument.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="1922d-111">から `SECURITY_ATTRIBUTES` プロセスのセキュリティ記述子を指定する Win32 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1922d-111">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the process.</span></span> <span data-ttu-id="1922d-112">`lpProcessAttributes`が null の場合、プロセスは既定のセキュリティ記述子を取得します。</span><span class="sxs-lookup"><span data-stu-id="1922d-112">If `lpProcessAttributes` is null, the process gets a default security descriptor.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="1922d-113">から `SECURITY_ATTRIBUTES` プロセスのプライマリスレッドのセキュリティ記述子を指定する Win32 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1922d-113">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the primary thread of the process.</span></span> <span data-ttu-id="1922d-114">`lpThreadAttributes`が null の場合、スレッドは既定のセキュリティ記述子を取得します。</span><span class="sxs-lookup"><span data-stu-id="1922d-114">If `lpThreadAttributes` is null, the thread gets a default security descriptor.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="1922d-115">から `true` 呼び出しプロセスの各継承可能なハンドルが、起動されるプロセスによって継承されることを示す場合はに設定し、ハンドルが継承されないことを示す場合はに設定し `false` ます。</span><span class="sxs-lookup"><span data-stu-id="1922d-115">[in] Set to `true` to indicate that each inheritable handle in the calling process is inherited by the launched process, or `false` to indicate that the handles are not inherited.</span></span> <span data-ttu-id="1922d-116">継承されたハンドルは、元のハンドルと同じ値とアクセス権を持ちます。</span><span class="sxs-lookup"><span data-stu-id="1922d-116">The inherited handles have the same value and access rights as the original handles.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="1922d-117">から優先順位クラスと起動されたプロセスの動作を制御する [Win32 プロセス作成フラグ](/windows/win32/procthread/process-creation-flags) のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="1922d-117">[in] A bitwise combination of the [Win32 Process Creation Flags](/windows/win32/procthread/process-creation-flags) that control the priority class and the behavior of the launched process.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="1922d-118">から新しいプロセスの環境ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1922d-118">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="1922d-119">からプロセスの現在のディレクトリへの完全パスを指定する、null で終わる文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1922d-119">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="1922d-120">このパラメーターが null の場合、新しいプロセスは呼び出しプロセスと同じ現在のドライブとディレクトリを持ちます。</span><span class="sxs-lookup"><span data-stu-id="1922d-120">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="1922d-121">から起動された `STARTUPINFOW` プロセスのメインウィンドウのウィンドウステーション、デスクトップ、標準ハンドル、および外観を指定する Win32 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1922d-121">[in] Pointer to a Win32 `STARTUPINFOW` structure that specifies the window station, desktop, standard handles, and appearance of the main window for the launched process.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="1922d-122">から `PROCESS_INFORMATION` 起動するプロセスに関する識別情報を指定する Win32 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1922d-122">[in] Pointer to a Win32 `PROCESS_INFORMATION` structure that specifies the identification information about the process to be launched.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="1922d-123">からデバッグオプションを指定する CorDebugCreateProcessFlags 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="1922d-123">[in] A value of the CorDebugCreateProcessFlags enumeration that specifies the debugging options.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="1922d-124">入出力プロセスを表す、オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1922d-124">[out] A pointer to the address of a ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1922d-125">解説</span><span class="sxs-lookup"><span data-stu-id="1922d-125">Remarks</span></span>  

 <span data-ttu-id="1922d-126">このメソッドのパラメーターは、Win32 メソッドのパラメーターと同じ `CreateProcess` です。</span><span class="sxs-lookup"><span data-stu-id="1922d-126">The parameters of this method are the same as those of the Win32 `CreateProcess` method.</span></span>  
  
 <span data-ttu-id="1922d-127">アンマネージ混合モードのデバッグを有効にするには、 `dwCreationFlags` を DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS に設定します。</span><span class="sxs-lookup"><span data-stu-id="1922d-127">To enable unmanaged mixed-mode debugging, set `dwCreationFlags` to DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span></span> <span data-ttu-id="1922d-128">マネージデバッグのみを使用する場合は、これらのフラグを設定しないでください。</span><span class="sxs-lookup"><span data-stu-id="1922d-128">If you want to use only managed debugging, do not set these flags.</span></span>  
  
 <span data-ttu-id="1922d-129">デバッガーとデバッグするプロセス (アタッチされたプロセス) が1つのコンソールを共有し、相互運用デバッグが使用されている場合、アタッチされたプロセスがコンソールロックを保持し、デバッグイベントで停止する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1922d-129">If the debugger and the process to be debugged (the attached process) share a single console, and if interop debugging is used, it is possible for the attached process to hold console locks and stop at a debug event.</span></span> <span data-ttu-id="1922d-130">デバッガーは、コンソールの使用をブロックします。</span><span class="sxs-lookup"><span data-stu-id="1922d-130">The debugger will then block any attempt to use the console.</span></span> <span data-ttu-id="1922d-131">この問題を回避するには、パラメーターに CREATE_NEW_CONSOLE フラグを設定し `dwCreationFlags` ます。</span><span class="sxs-lookup"><span data-stu-id="1922d-131">To avoid this problem, set the CREATE_NEW_CONSOLE flag in the `dwCreationFlags` parameter.</span></span>  
  
 <span data-ttu-id="1922d-132">相互運用デバッグは、IA-64 ベースおよび AMD64 ベースのプラットフォームなど、Win9x および x86 以外のプラットフォームではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1922d-132">Interop debugging is not supported on Win9x and non-x86 platforms such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1922d-133">要件</span><span class="sxs-lookup"><span data-stu-id="1922d-133">Requirements</span></span>  

 <span data-ttu-id="1922d-134">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1922d-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1922d-135">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1922d-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1922d-136">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1922d-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1922d-137">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1922d-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1922d-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="1922d-138">See also</span></span>

- [<span data-ttu-id="1922d-139">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1922d-139">ICorDebug Interface</span></span>](icordebug-interface.md)
