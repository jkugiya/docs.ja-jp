---
title: callbackOnCollectedDelegate MDA
description: .NET の callbackOnCollectedDelegate マネージド デバッグ アシスタント (MDA) について確認します。これは、デリゲートがガベージ コレクトされた後にコールバックが発生した場合に呼び出されます。
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- managed debugging assistants (MDAs), callback on collected delegates
- MDAs (managed debugging assistants), callback on collected delegates
- callback on delegate after garbage collection
- callbackOnCollectedDelegate MDA
- managed debugging assistants (MDAs), garbage collection
- call back collected delegates
- garbage collection, run-time errors
- delegates [.NET Framework], garbage collection
ms.assetid: 398b0ce0-5cc9-4518-978d-b8263aa21e5b
ms.openlocfilehash: 1d95d01fb1e5a49ca055717ef4701b6f46394df3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265233"
---
# <a name="callbackoncollecteddelegate-mda"></a><span data-ttu-id="ad7b1-103">callbackOnCollectedDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="ad7b1-103">callbackOnCollectedDelegate MDA</span></span>

<span data-ttu-id="ad7b1-104">`callbackOnCollectedDelegate` マネージド デバッグ アシスタント (MDA) は、デリゲートがマネージド コードからアンマネージド コードに関数ポインターとしてマーシャリングされ、デリゲートがガベージ コレクトされた後にその関数ポインター上にコールバックが配置された場合にアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-104">The `callbackOnCollectedDelegate` managed debugging assistant (MDA) is activated if a delegate is marshaled from managed to unmanaged code as a function pointer and a callback is placed on that function pointer after the delegate has been garbage collected.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ad7b1-105">現象</span><span class="sxs-lookup"><span data-stu-id="ad7b1-105">Symptoms</span></span>  

 <span data-ttu-id="ad7b1-106">マネージド デリゲートから取得した関数ポインターを通じてマネージド コードへの呼び出しをしようとすると、アクセス違反が発生します。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-106">Access violations occur when attempting to call into managed code through function pointers that were obtained from managed delegates.</span></span> <span data-ttu-id="ad7b1-107">このエラーは、共通言語ランタイム (CLR) コード内でアクセス違反が発生するため、CLR のバグのように見えますが、実際には違います。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-107">These failures, while not common language runtime (CLR) bugs, may appear to be so because the access violation occurs in the CLR code.</span></span>  
  
 <span data-ttu-id="ad7b1-108">このエラーには一貫性がなく、関数ポインターでの呼び出しが成功することもあれば、失敗することもあります。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-108">The failure is not consistent; sometimes the call on the function pointer succeeds and sometimes it fails.</span></span> <span data-ttu-id="ad7b1-109">高負荷のときのみエラーが発生することがあり、ランダムな試行回数ごとに発生することもあります。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-109">The failure might occur only under heavy load or on a random number of attempts.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ad7b1-110">原因</span><span class="sxs-lookup"><span data-stu-id="ad7b1-110">Cause</span></span>  

 <span data-ttu-id="ad7b1-111">関数ポインターが作成されてアンマネージ コードに公開されたデリゲートが、ガベージ コレクトされました。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-111">The delegate from which the function pointer was created and exposed to unmanaged code was garbage collected.</span></span> <span data-ttu-id="ad7b1-112">アンマネージ コンポーネントからその関数ポインターで呼び出しを行おうとすると、アクセス違反が発生します。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-112">When the unmanaged component tries to call on the function pointer, it generates an access violation.</span></span>  
  
 <span data-ttu-id="ad7b1-113">このエラーの発生するタイミングはガベージ コレクションが行われるタイミングに依存するため、ランダムに発生するように見えます。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-113">The failure appears random because it depends on when garbage collection occurs.</span></span> <span data-ttu-id="ad7b1-114">デリゲートがガベージ コレクションの対象になった場合でも、コールバックが行われて成功した後にガベージ コレクションが行われることがあります。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-114">If a delegate is eligible for collection, the garbage collection can occur after the callback and the call succeeds.</span></span> <span data-ttu-id="ad7b1-115">別の時には、コールバックの前にガベージ コレクションが実行されたため、コールバックがアクセス違反を生成し、プログラムが停止します。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-115">At other times, the garbage collection occurs before the callback, the callback generates an access violation, and the program stops.</span></span>  
  
 <span data-ttu-id="ad7b1-116">エラーの発生確率は、デリゲートのマーシャリングから関数ポインターの呼び出しまでの時間と、ガベージ コレクションの頻度に応じて変わります。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-116">The probability of the failure depends on the time between marshaling the delegate and the callback on the function pointer as well as the frequency of garbage collections.</span></span> <span data-ttu-id="ad7b1-117">デリゲートのマーシャリングから次のコールバックまでの時間が短い場合、エラーは散発的です。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-117">The failure is sporadic if the time between marshaling the delegate and the ensuing callback is short.</span></span> <span data-ttu-id="ad7b1-118">これは、関数ポインターを受け取るアンマネージ メソッドが後で使用するために関数ポインターを保存することはせず、代わりに関数ポインターをすぐにコールバックし、返る前に操作が完了する場合に当てはまります。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-118">This is usually the case if the unmanaged method receiving the function pointer does not save the function pointer for later use but instead calls back on the function pointer immediately to complete its operation before returning.</span></span> <span data-ttu-id="ad7b1-119">同様に、システムの負荷が高いと頻繁にガベージ コレクションが発生するため、コールバックの前にガベージ コレクションが発生する可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-119">Similarly, more garbage collections occur when a system is under heavy load, which makes it more likely that a garbage collection will occur before the callback.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ad7b1-120">解決方法</span><span class="sxs-lookup"><span data-stu-id="ad7b1-120">Resolution</span></span>  

 <span data-ttu-id="ad7b1-121">デリゲートがアンマネージ関数ポインターとしてマーシャリングされた後、ガベージ コレクターはその有効期間を追跡できません。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-121">Once a delegate has been marshaled out as an unmanaged function pointer, the garbage collector cannot track its lifetime.</span></span> <span data-ttu-id="ad7b1-122">代わりに、アンマネージ関数ポインターの有効期間にわたってデリゲートへの参照をコードで保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-122">Instead, your code must keep a reference to the delegate for the lifetime of the unmanaged function pointer.</span></span> <span data-ttu-id="ad7b1-123">しかし、それを行うには、まずどのデリゲートがガベージ コレクトされたかを識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-123">But before you can do that, you first must identify which delegate was collected.</span></span> <span data-ttu-id="ad7b1-124">MDA がアクティブになると、デリゲートの型名が提供されます。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-124">When the MDA is activated, it provides the type name of the delegate.</span></span> <span data-ttu-id="ad7b1-125">この名前を使用してコードを検索し、アンマネージ コードにデリゲートを渡すプラットフォーム呼び出しまたは COM シグネチャを見つけます。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-125">Use this name to search your code for platform invoke or COM signatures that pass that delegate out to unmanaged code.</span></span> <span data-ttu-id="ad7b1-126">問題が発生したデリゲートは、これらの呼び出しサイトのいずれかを通じて渡されます。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-126">The offending delegate is passed out through one of these call sites.</span></span> <span data-ttu-id="ad7b1-127">また、`gcUnmanagedToManaged` MDA を有効にして、ランタイムへのコールバックの前にガベージ コレクションを強制することもできます。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-127">You can also enable the `gcUnmanagedToManaged` MDA to force a garbage collection before every callback into the runtime.</span></span> <span data-ttu-id="ad7b1-128">これにより、コールバックが行われる前に必ずガベージ コレクションが行われるため、ガベージ コレクションによって持ち込まれる不確実性が排除されます。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-128">This will remove the uncertainty introduced by the garbage collection by ensuring that a garbage collection always occurs before the callback.</span></span> <span data-ttu-id="ad7b1-129">ガベージ コレクトされたデリゲートがわかったら、マーシャリングしたアンマネージド 関数ポインターの有効期間にわたってデリゲートへの参照をマネージド側に保持するようにコードを変更します。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-129">Once you know what delegate was collected, change your code to keep a reference to that delegate on the managed side for the lifetime of the marshaled unmanaged function pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ad7b1-130">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="ad7b1-130">Effect on the Runtime</span></span>  

 <span data-ttu-id="ad7b1-131">デリゲートを関数ポインターとしてマーシャリングすると、ランタイムはアンマネージドからマネージドへの遷移を行うサンクを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-131">When delegates are marshaled as function pointers, the runtime allocates a thunk that does the transition from unmanaged to managed.</span></span> <span data-ttu-id="ad7b1-132">このサンクが、マネージド デリゲートが最終的に呼び出される前に、アンマネージド コードによって実際に呼び出されるものです。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-132">This thunk is what the unmanaged code actually calls before the managed delegate is finally invoked.</span></span> <span data-ttu-id="ad7b1-133">`callbackOnCollectedDelegate` MDA を有効にしない場合、アンマネージのマーシャリング コードはデリゲートがガベージ コレクトされたときに削除されます。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-133">Without the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is deleted when the delegate is collected.</span></span> <span data-ttu-id="ad7b1-134">`callbackOnCollectedDelegate` MDA を有効にした場合、アンマネージのマーシャリング コードはデリゲートがガベージ コレクトされたとき、すぐには削除されません。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-134">With the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is not immediately deleted when the delegate is collected.</span></span> <span data-ttu-id="ad7b1-135">代わりに、既定では最新の 1,000 個のインスタンスが有効のまま保持され、呼び出されたときに MDA をアクティブ化するように変更されます。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-135">Instead, the last 1,000 instances are kept alive by default and changed to activate the MDA when called.</span></span> <span data-ttu-id="ad7b1-136">サンクはやがて、さらに 1,001 個のマーシャリングされたデリゲートがガベージ コレクトされた後に削除されます。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-136">The thunk is eventually deleted after 1,001 more marshaled delegates are collected.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ad7b1-137">出力</span><span class="sxs-lookup"><span data-stu-id="ad7b1-137">Output</span></span>  

 <span data-ttu-id="ad7b1-138">MDA は、デリゲートのアンマネージ関数ポインターへのコールバックが試みられる前に、ガベージ コレクトされたデリゲートの型名を報告します。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-138">The MDA reports the type name of the delegate that was collected before a callback was attempted on its unmanaged function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ad7b1-139">構成</span><span class="sxs-lookup"><span data-stu-id="ad7b1-139">Configuration</span></span>  

 <span data-ttu-id="ad7b1-140">次の例は、アプリケーションの構成オプションを示します。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-140">The following example shows the application configuration options.</span></span> <span data-ttu-id="ad7b1-141">MDA が有効に保持するサンクの数を 1,500 に設定しています。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-141">It sets the number of thunks the MDA keeps alive to 1,500.</span></span> <span data-ttu-id="ad7b1-142">`listSize` の既定値は 1,000、最小値は 50、最大値は 2,000 です。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-142">The default `listSize` value is 1,000, the minimum is 50, and the maximum is 2,000.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="ad7b1-143">例</span><span class="sxs-lookup"><span data-stu-id="ad7b1-143">Example</span></span>  

 <span data-ttu-id="ad7b1-144">次の例は、この MDA がアクティブ化されることのある状況を示しています。</span><span class="sxs-lookup"><span data-stu-id="ad7b1-144">The following example demonstrates a situation that can activate this MDA:</span></span>  
  
```cpp
// Library.cpp : Defines the unmanaged entry point for the DLL application.  
#include "windows.h"  
#include "stdio.h"  
  
void (__stdcall *g_pfTarget)();  
  
void __stdcall Initialize(void __stdcall pfTarget())  
{  
    g_pfTarget = pfTarget;  
}  
  
void __stdcall Callback()  
{  
    g_pfTarget();  
}
```

```csharp
// C# Client  
using System;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public delegate void DCallback();  
  
    public static void Main()  
    {  
        new Entry();  
        Initialize(Target);  
        GC.Collect();  
        GC.WaitForPendingFinalizers();  
        Callback();  
    }  
  
    public static void Target()  
    {
    }  
  
    [DllImport("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Initialize(DCallback pfDelegate);  
  
    [DllImport ("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Callback();  
  
    ~Entry() { Console.Error.WriteLine("Entry Collected"); }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ad7b1-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad7b1-145">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="ad7b1-146">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="ad7b1-146">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="ad7b1-147">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="ad7b1-147">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
- [<span data-ttu-id="ad7b1-148">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="ad7b1-148">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)
