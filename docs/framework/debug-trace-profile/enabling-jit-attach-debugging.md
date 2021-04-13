---
title: JIT アタッチ デバッグの有効化
description: エラーが発生したときにデバッガーをプロセスにアタッチするには、Just-In-Time (JIT) アタッチ デバッグを有効にします。 これは、特定のメソッドまたは関数によってトリガーできます。
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
ms.openlocfilehash: dc1c8608b0d16e618b5ad6144d492db3302532dc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273504"
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="061d0-104">JIT アタッチ デバッグの有効化</span><span class="sxs-lookup"><span data-stu-id="061d0-104">Enabling JIT-Attach Debugging</span></span>

<span data-ttu-id="061d0-105">JIT アタッチ デバッグとは、エラーが発生したとき、または特定のメソッドまたは関数によってトリガーすることで、プロセスにデバッガーをアタッチすることを表すために使用される語句です。</span><span class="sxs-lookup"><span data-stu-id="061d0-105">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="061d0-106">JIT アタッチ デバッグは、次のエラー状態で使用されます。</span><span class="sxs-lookup"><span data-stu-id="061d0-106">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
- <span data-ttu-id="061d0-107">未処理の例外 (ネイティブ コードとマネージド コードの両方)。</span><span class="sxs-lookup"><span data-stu-id="061d0-107">Unhandled exceptions (in both native and managed code).</span></span>  
  
- <span data-ttu-id="061d0-108"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> メソッドまたは [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) 関数 (Windows 7 ファミリ)。</span><span class="sxs-lookup"><span data-stu-id="061d0-108"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) function (Windows 7 family).</span></span>  
  
- <span data-ttu-id="061d0-109">実行時の致命的なエラー。</span><span class="sxs-lookup"><span data-stu-id="061d0-109">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="061d0-110">JIT アタッチ デバッグは、次のメソッドや関数への呼び出しによってもトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="061d0-110">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
- <span data-ttu-id="061d0-111"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> メソッド</span><span class="sxs-lookup"><span data-stu-id="061d0-111"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="061d0-112"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> メソッド</span><span class="sxs-lookup"><span data-stu-id="061d0-112"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="061d0-113">[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) 関数 (Win32)。</span><span class="sxs-lookup"><span data-stu-id="061d0-113">[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) function (Win32).</span></span>  
  
 <span data-ttu-id="061d0-114">.NET Framework 4 より前のバージョンでは、.NET Framework がネイティブおよびマネージド デバッガーの動作を制御するために別々のレジストリ キーを提供していました。</span><span class="sxs-lookup"><span data-stu-id="061d0-114">Before the .NET Framework 4, the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="061d0-115">.NET Framework 4 以降では、制御が 1 つのレジストリ キー、HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug に統合されました。</span><span class="sxs-lookup"><span data-stu-id="061d0-115">Starting with the .NET Framework 4, control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="061d0-116">このキーに設定できる値により、デバッガーを呼び出すかどうか、呼び出す場合は、ユーザーの操作を必要とするダイアログ ボックスによって呼び出すかどうかが決まります。</span><span class="sxs-lookup"><span data-stu-id="061d0-116">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="061d0-117">このレジストリ キーを設定する方法について詳しくは、「[自動デバッグを構成する](/windows/win32/debug/configuring-automatic-debugging)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="061d0-117">For information about setting this registry key, see [Configuring Automatic Debugging](/windows/win32/debug/configuring-automatic-debugging).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="061d0-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="061d0-118">See also</span></span>

- [<span data-ttu-id="061d0-119">デバッグ、トレース、およびプロファイリング</span><span class="sxs-lookup"><span data-stu-id="061d0-119">Debugging, Tracing, and Profiling</span></span>](index.md)
- [<span data-ttu-id="061d0-120">イメージのデバッグの簡略化</span><span class="sxs-lookup"><span data-stu-id="061d0-120">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)
