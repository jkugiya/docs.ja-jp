---
title: dirtyCastAndCallOnInterface MDA
description: dirtyCastAndCallOnInterface マネージド デバッグ アシスタントについて確認します。これは、事前バインディングされた vtable の呼び出しが遅延バインディング専用のクラス インターフェイスで実行されたときに呼び出されます。
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), early bound calls AutoDispatch
- dispatch-only mode
- dirtyCastAndCallOnInterface
- early-bound managed classes
- early bound calls on AutoDispatch
- MDAs (managed debugging assistants), early bound calls AutoDispatch
- EarlyBoundCallOnAutorDispatchClassInteface MDA
ms.assetid: aa388ed3-7e3d-48ea-a0b5-c47ae19cec38
ms.openlocfilehash: 49a2930d91e76856436480512360e8b9f9fd3d7a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273582"
---
# <a name="dirtycastandcalloninterface-mda"></a><span data-ttu-id="5cd65-103">dirtyCastAndCallOnInterface MDA</span><span class="sxs-lookup"><span data-stu-id="5cd65-103">dirtyCastAndCallOnInterface MDA</span></span>

<span data-ttu-id="5cd65-104">`dirtyCastAndCallOnInterface` マネージド デバッグ アシスタント (MDA: Managed Debugging Assistant) は、vtable を使用して事前バインディングされた呼び出しが、遅延バインディング専用とマークされたクラス インターフェイスで試行されたときにアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="5cd65-104">The `dirtyCastAndCallOnInterface` managed debugging assistant (MDA) is activated when an early-bound call through a vtable is attempted on a class interface that has been marked late-bound only.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5cd65-105">現象</span><span class="sxs-lookup"><span data-stu-id="5cd65-105">Symptoms</span></span>  

 <span data-ttu-id="5cd65-106">COM 経由で CLR への事前バインディングされた呼び出しが実行されると、アプリケーションはアクセス違反をスローするか、予期しない動作に発生します。</span><span class="sxs-lookup"><span data-stu-id="5cd65-106">An application throws an access violation or has unexpected behavior when placing an early-bound call via COM into the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5cd65-107">原因</span><span class="sxs-lookup"><span data-stu-id="5cd65-107">Cause</span></span>  

 <span data-ttu-id="5cd65-108">コードは、遅延バインディング専用のクラス インターフェイス経由で、vtable を使用して事前バインディングされた呼び出しを試行しています。</span><span class="sxs-lookup"><span data-stu-id="5cd65-108">Code is attempting an early-bound call through a vtable via a class interface that is late-bound only.</span></span> <span data-ttu-id="5cd65-109">既定では、クラス インターフェイスは遅延バインディング専用として識別されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5cd65-109">Note that by default class interfaces are identified as being late-bound only.</span></span> <span data-ttu-id="5cd65-110">また、<xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 属性に <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> 値 (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`) が設定されている場合も、遅延バインディングとして識別されます。</span><span class="sxs-lookup"><span data-stu-id="5cd65-110">They can also be identified as late-bound with the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute with an <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> value (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5cd65-111">解決方法</span><span class="sxs-lookup"><span data-stu-id="5cd65-111">Resolution</span></span>  

 <span data-ttu-id="5cd65-112">推奨される解決策としては、COM で使用するための明示的なインターフェイスを定義し、自動生成されるクラス インターフェイスを通してではなく、このインターフェイスを通して、COM クライアント呼び出しを実行するようにする方法があります。</span><span class="sxs-lookup"><span data-stu-id="5cd65-112">The recommended resolution is to define an explicit interface for use by COM and have the COM clients call through this interface instead of through the automatically generated class interface.</span></span> <span data-ttu-id="5cd65-113">代わりに、`IDispatch` を介して、COM からの呼び出しを遅延バインディングされた呼び出しに変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="5cd65-113">Alternatively, the call from COM can be transformed into a late-bound call via `IDispatch`.</span></span>  
  
 <span data-ttu-id="5cd65-114">事前バインディングされた呼び出しを COM から実行できるように、クラスを <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) として識別することもできます。ただし、「<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>」に記載されているバージョン管理の制約から、<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> を使用しないことを強く推奨します。</span><span class="sxs-lookup"><span data-stu-id="5cd65-114">Finally, it is possible to identify the class as <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) to allow early bound calls to be placed from COM; however, using <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> is strongly discouraged because of the versioning limitations described in <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5cd65-115">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="5cd65-115">Effect on the Runtime</span></span>  

 <span data-ttu-id="5cd65-116">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="5cd65-116">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="5cd65-117">遅延バインディングされたインターフェイス上の事前バインディングされた呼び出しに関するデータを報告するだけです。</span><span class="sxs-lookup"><span data-stu-id="5cd65-117">It only reports data about early-bound calls on late-bound interfaces.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5cd65-118">出力</span><span class="sxs-lookup"><span data-stu-id="5cd65-118">Output</span></span>  

 <span data-ttu-id="5cd65-119">事前バインディングでアクセスされたメソッド名またはフィールド名です。</span><span class="sxs-lookup"><span data-stu-id="5cd65-119">The name of the method or name of the field being accessed early-bound.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5cd65-120">構成</span><span class="sxs-lookup"><span data-stu-id="5cd65-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5cd65-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="5cd65-121">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="5cd65-122">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="5cd65-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
