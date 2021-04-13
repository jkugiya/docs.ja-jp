---
title: invalidApartmentStateChange MDA
description: .NET の invalidApartmentStateChange マネージド デバッグ アシスタント (MDA) について説明します。これは、COM アパートメント状態に問題がある場合にアクティブになります。
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid apartment state
- managed debugging assistants (MDAs), invalid apartment state
- InvalidApartmentStateChange MDA
- invalid apartment state changes
- threading [.NET Framework], apartment states
- apartment states
- threading [.NET Framework], managed debugging assistants
- COM apartment states
ms.assetid: e56fb9df-5286-4be7-b313-540c4d876cd7
ms.openlocfilehash: db55e3ac2d6862d008013abef0f09f67213d9faa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272749"
---
# <a name="invalidapartmentstatechange-mda"></a><span data-ttu-id="d0f10-103">invalidApartmentStateChange MDA</span><span class="sxs-lookup"><span data-stu-id="d0f10-103">invalidApartmentStateChange MDA</span></span>

<span data-ttu-id="d0f10-104">`invalidApartmentStateChange` マネージド デバッグ アシスタント (MDS) は、次の 2 つのどちらかの問題によってアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="d0f10-104">The `invalidApartmentStateChange` managed debugging assistant (MDS) is activated by either of two problems:</span></span>  
  
- <span data-ttu-id="d0f10-105">COM によって既に初期化されているスレッドの COM アパートメント状態を異なるアパートメント状態に変更しようとした。</span><span class="sxs-lookup"><span data-stu-id="d0f10-105">An attempt is made to change the COM apartment state of a thread that has already been initialized by COM to a different apartment state.</span></span>  
  
- <span data-ttu-id="d0f10-106">スレッドの COM アパートメント状態が予期せず変更された。</span><span class="sxs-lookup"><span data-stu-id="d0f10-106">The COM apartment state of a thread changes unexpectedly.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d0f10-107">現象</span><span class="sxs-lookup"><span data-stu-id="d0f10-107">Symptoms</span></span>  
  
- <span data-ttu-id="d0f10-108">スレッドの COM アパートメント状態が要求されたものと異なります。</span><span class="sxs-lookup"><span data-stu-id="d0f10-108">A thread's COM apartment state is not what was requested.</span></span> <span data-ttu-id="d0f10-109">これが原因で、現在のモデルと異なるスレッド処理モデルの COM コンポーネントがプロキシで使用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="d0f10-109">This may cause proxies to be used for COM components that have a threading model different from the current one.</span></span> <span data-ttu-id="d0f10-110">これにより、アパートメント間のマーシャリング用に設定されていないインターフェイスを介して COM オブジェクトが呼び出されるときに <xref:System.InvalidCastException> がスローされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d0f10-110">This in turn may cause an <xref:System.InvalidCastException> to be thrown when calling the COM object through interfaces that are not set up for cross-apartment marshaling.</span></span>  
  
- <span data-ttu-id="d0f10-111">スレッドの COM アパートメント状態が予想と異なります。</span><span class="sxs-lookup"><span data-stu-id="d0f10-111">The COM apartment state of the thread is different than expected.</span></span> <span data-ttu-id="d0f10-112">これが原因で、[ランタイム呼び出し可能ラッパー](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) で呼び出しを行うときに、HRESULT が RPC_E_WRONG_THREAD の <xref:System.Runtime.InteropServices.COMException>、および <xref:System.InvalidCastException> が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d0f10-112">This can cause a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD as well as a <xref:System.InvalidCastException> when making calls on a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="d0f10-113">これにより、一部のシングル スレッド COM が同時に複数のスレッドによってアクセスされ、そのために破損またはデータの損失につながることがあります。</span><span class="sxs-lookup"><span data-stu-id="d0f10-113">This can also cause some single-threaded COM components to be accessed by multiple threads at the same time, which can lead to corruption or data loss.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d0f10-114">原因</span><span class="sxs-lookup"><span data-stu-id="d0f10-114">Cause</span></span>  
  
- <span data-ttu-id="d0f10-115">スレッドは以前に異なる COM アパートメント状態に初期化されました。</span><span class="sxs-lookup"><span data-stu-id="d0f10-115">The thread was previously initialized to a different COM apartment state.</span></span> <span data-ttu-id="d0f10-116">スレッドのアパートメント状態を明示的または暗黙的に設定できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d0f10-116">Note that the apartment state of a thread can be set either explicitly or implicitly.</span></span> <span data-ttu-id="d0f10-117">明示的な操作には、<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> プロパティ、<xref:System.Threading.Thread.SetApartmentState%2A> メソッド、<xref:System.Threading.Thread.TrySetApartmentState%2A> メソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d0f10-117">The explicit operations include the <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> property and the <xref:System.Threading.Thread.SetApartmentState%2A> and <xref:System.Threading.Thread.TrySetApartmentState%2A> methods.</span></span> <span data-ttu-id="d0f10-118"><xref:System.Threading.Thread.Start%2A> メソッドを使用して作成されたスレッドは、スレッドが開始される前に <xref:System.Threading.Thread.SetApartmentState%2A> が呼び出されない限り、暗黙的に <xref:System.Threading.ApartmentState.MTA> に設定されます。</span><span class="sxs-lookup"><span data-stu-id="d0f10-118">A thread created using the <xref:System.Threading.Thread.Start%2A> method is implicitly set to <xref:System.Threading.ApartmentState.MTA> unless <xref:System.Threading.Thread.SetApartmentState%2A> is called before the thread is started.</span></span> <span data-ttu-id="d0f10-119">アプリケーションのメイン スレッドも、メイン メソッドで <xref:System.STAThreadAttribute> 属性が指定されない限り、暗黙的に <xref:System.Threading.ApartmentState.MTA> に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="d0f10-119">The main thread of the application is also implicitly initialized to <xref:System.Threading.ApartmentState.MTA> unless the <xref:System.STAThreadAttribute> attribute is specified on the main method.</span></span>  
  
- <span data-ttu-id="d0f10-120">異なるコンカレンシー モデルを持つ `CoUninitialize` メソッド (または `CoInitializeEx` メソッド) がスレッドで呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d0f10-120">The `CoUninitialize` method (or the `CoInitializeEx` method) with a different concurrency model is called on the thread.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d0f10-121">解決方法</span><span class="sxs-lookup"><span data-stu-id="d0f10-121">Resolution</span></span>  

 <span data-ttu-id="d0f10-122">スレッドの実行開始前に、スレッドのアパートメント状態を設定するか、<xref:System.STAThreadAttribute> 属性または <xref:System.MTAThreadAttribute> 属性をアプリケーションのメイン メソッドに適用します。</span><span class="sxs-lookup"><span data-stu-id="d0f10-122">Set the apartment state of the thread before it begins executing, or apply either the <xref:System.STAThreadAttribute> attribute or the <xref:System.MTAThreadAttribute> attribute to the main method of the application.</span></span>  
  
 <span data-ttu-id="d0f10-123">2 番目の原因の場合、理想的には、`CoUninitialize` メソッドを呼び出すコードを変更し、スレッドの終了間近になり、RCW がなく、基になる COM コンポーネントがまだスレッドによって使用されている状態まで、呼び出しを遅延する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0f10-123">For the second cause, ideally, the code that calls the `CoUninitialize` method should be modified to delay the call until the thread is about to terminate and there are no RCWs and their underlying COM components still in use by the thread.</span></span> <span data-ttu-id="d0f10-124">ただし、`CoUninitialize` を呼び出すコードを変更できない場合は、この方法で初期化解除されるスレッドから RCW を使用しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0f10-124">However, if it is not possible to modify the code that calls the `CoUninitialize` method, then no RCWs should be used from threads that are uninitialized in this way.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d0f10-125">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="d0f10-125">Effect on the Runtime</span></span>  

 <span data-ttu-id="d0f10-126">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="d0f10-126">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d0f10-127">出力</span><span class="sxs-lookup"><span data-stu-id="d0f10-127">Output</span></span>  

 <span data-ttu-id="d0f10-128">現在のスレッドの COM アパートメント状態、およびコードが適用しようとした状態。</span><span class="sxs-lookup"><span data-stu-id="d0f10-128">The COM apartment state of the current thread, and the state that the code was attempting to apply.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d0f10-129">構成</span><span class="sxs-lookup"><span data-stu-id="d0f10-129">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="d0f10-130">例</span><span class="sxs-lookup"><span data-stu-id="d0f10-130">Example</span></span>  

 <span data-ttu-id="d0f10-131">次のコードの例は、この MDA がアクティブ化されることのある状況を示しています。</span><span class="sxs-lookup"><span data-stu-id="d0f10-131">The following code example demonstrates a situation that can activate this MDA.</span></span>  
  
```csharp
using System.Threading;  
namespace ApartmentStateMDA  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Thread.CurrentThread.SetApartmentState(ApartmentState.STA);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0f10-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0f10-132">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="d0f10-133">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="d0f10-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="d0f10-134">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="d0f10-134">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
