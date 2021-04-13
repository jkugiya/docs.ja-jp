---
title: invalidCERCall MDA
description: invalidCERCall マネージド デバッグ アシスタント (MDA) について確認します。これは、制約された実行領域 (CER) グラフ内に無効な呼び出しがある場合にアクティブになります。
ms.date: 03/30/2017
helpviewer_keywords:
- invalid CER calls
- InvalidCERCall MDA
- MDAs (managed debugging assistants), CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: c4577410-602e-44e5-9dab-fea7c55bcdfe
ms.openlocfilehash: 6f0d9d8e3059729098975080224999d0c0fac46e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272658"
---
# <a name="invalidcercall-mda"></a><span data-ttu-id="87fc8-103">invalidCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="87fc8-103">invalidCERCall MDA</span></span>

<span data-ttu-id="87fc8-104">`invalidCERCall` マネージド デバッグ アシスタント (MDA) は、制約された実行領域 (CER) グラフ内で信頼契約がないかまたは過度に脆弱な契約を持つメソッドの呼び出しがある場合に、アクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="87fc8-104">The `invalidCERCall` managed debugging assistant (MDA) is activated when there is a call within the constrained execution region (CER) graph to a method that has no reliability contract or an excessively weak contract.</span></span> <span data-ttu-id="87fc8-105">脆弱な契約とは、最悪のケースの状態の破損が、呼び出しに渡されるインスタンスよりも大きい範囲であることを宣言する契約です。つまり、<xref:System.AppDomain> またはプロセスの状態が破損するか、または CER 内で呼び出されたときにその結果を常に確定的に計算できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="87fc8-105">A weak contract is a contract that declares that the worst case state corruption is of greater scope than the instance passed to the call, that is, the <xref:System.AppDomain> or process state may become corrupted or that its result is not always deterministically computable when called within a CER.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="87fc8-106">現象</span><span class="sxs-lookup"><span data-stu-id="87fc8-106">Symptoms</span></span>  

 <span data-ttu-id="87fc8-107">CER でコードを実行するときの予期しない結果。</span><span class="sxs-lookup"><span data-stu-id="87fc8-107">Unexpected results when executing code in a CER.</span></span> <span data-ttu-id="87fc8-108">この現象は固有ではありません。</span><span class="sxs-lookup"><span data-stu-id="87fc8-108">The symptoms are not specific.</span></span> <span data-ttu-id="87fc8-109">ランタイムがメソッドを事前に準備しないか、実行時に <xref:System.Threading.ThreadAbortException> 例外から保護しないため、信頼できないメソッドの呼び出し時に予期しない <xref:System.OutOfMemoryException>、<xref:System.Threading.ThreadAbortException>、または他の例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="87fc8-109">They could be an unexpected <xref:System.OutOfMemoryException>, a <xref:System.Threading.ThreadAbortException>, or other exceptions at the call into the unreliable method because the runtime did not prepare it ahead of time or protect it from <xref:System.Threading.ThreadAbortException> exceptions at run time.</span></span> <span data-ttu-id="87fc8-110">より大きな脅威は、実行時にメソッドから結果として発生する例外が <xref:System.AppDomain> またはプロセスを CER の目的とは反対の不安定な状態にする可能性があることです。</span><span class="sxs-lookup"><span data-stu-id="87fc8-110">A greater threat is that any exception resulting from the method at run time could leave the <xref:System.AppDomain> or process in an unstable state, which is contrary to the objective of a CER.</span></span> <span data-ttu-id="87fc8-111">CER が作成される理由は、このような状態の破損を避けるためです。</span><span class="sxs-lookup"><span data-stu-id="87fc8-111">The reason a CER is created is to avoid state corruptions such as this.</span></span> <span data-ttu-id="87fc8-112">一貫性のある状態の定義がアプリケーション間で異なるために、破損状態の現象はアプリケーションに固有です。</span><span class="sxs-lookup"><span data-stu-id="87fc8-112">The symptoms of corrupt state are application specific because the definition of consistent state is different between applications.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="87fc8-113">原因</span><span class="sxs-lookup"><span data-stu-id="87fc8-113">Cause</span></span>  

 <span data-ttu-id="87fc8-114">CER 内のコードが、<xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> を持たない関数、または CER での実行と互換性のない脆弱な <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> を持つ関数を呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="87fc8-114">Code within a CER is calling a function with no <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> or with a weak <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> that is not compatible with running in a CER.</span></span>  
  
 <span data-ttu-id="87fc8-115">信頼契約の構文の観点から、脆弱な契約とは、<xref:System.Runtime.ConstrainedExecution.Consistency> 列挙値を指定しない契約、または <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>、<xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>、<xref:System.Runtime.ConstrainedExecution.Cer.None> の <xref:System.Runtime.ConstrainedExecution.Consistency> 値を指定する契約です。</span><span class="sxs-lookup"><span data-stu-id="87fc8-115">In terms of reliability contract syntax, a weak contract is a contract that does not specify a <xref:System.Runtime.ConstrainedExecution.Consistency> enumeration value or specifies a <xref:System.Runtime.ConstrainedExecution.Consistency> value of <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>, or <xref:System.Runtime.ConstrainedExecution.Cer.None>.</span></span> <span data-ttu-id="87fc8-116">これらのどの状態も、呼び出されるコードが一貫性のある状態を維持するための CER の他のコードの処理を妨げる可能性があることを示します。</span><span class="sxs-lookup"><span data-stu-id="87fc8-116">Any of these conditions indicates that the code called may impede the efforts of the other code in the CER to maintain consistent state.</span></span>  <span data-ttu-id="87fc8-117">CER では、エラーを非常に明確な方法で処理し、アプリケーションにとって重要な内部の不変性を維持し、メモリ不足の例外などの一時的なエラーが発生したときにアプリケーションの実行を継続することができます。</span><span class="sxs-lookup"><span data-stu-id="87fc8-117">CERs allow code to treat errors in a very deterministic manner, maintaining internal invariants that are important to the application and allowing it to continue running in the face of transient errors such as out-of-memory exceptions.</span></span>  
  
 <span data-ttu-id="87fc8-118">この MDA がアクティブ化は、CER で呼び出されるメソッドが、呼び出し元が予期しない方法で失敗する可能性があるか、<xref:System.AppDomain> またはプロセスの状態が破損または回復不能な状態になることを示します。</span><span class="sxs-lookup"><span data-stu-id="87fc8-118">The activation of this MDA indicates a possibility the method being called in the CER can fail in a way that the caller did not expect or that leaves the <xref:System.AppDomain> or process state corrupted or unrecoverable.</span></span> <span data-ttu-id="87fc8-119">当然ながら、呼び出されたコードが正しく実行され、問題が単純な契約の不足である場合があります。</span><span class="sxs-lookup"><span data-stu-id="87fc8-119">Of course, the called code might execute correctly and the problem is simply a missing contract.</span></span> <span data-ttu-id="87fc8-120">ただし、信頼できるコードの記述に関連する問題は微妙であり、契約がない状況は、コードが正しく実行できないことを示す有効な指標です。</span><span class="sxs-lookup"><span data-stu-id="87fc8-120">However, the issues involved in writing reliable code are subtle and the absence of a contract is a good indicator the code might not execute correctly.</span></span> <span data-ttu-id="87fc8-121">契約は、プログラマが確実にコードを記述したことを示すインジケーターであり、コードの将来のリビジョンで保証が変更されないことを約束します。</span><span class="sxs-lookup"><span data-stu-id="87fc8-121">The contracts are indicators that the programmer has coded reliably and also promises that these guarantees will not change in future revisions of the code.</span></span>  <span data-ttu-id="87fc8-122">つまり、契約は、単なる実装の詳細ではなく、意図の宣言です。</span><span class="sxs-lookup"><span data-stu-id="87fc8-122">That is, the contracts are declarations of intent and not just implementation details.</span></span>  
  
 <span data-ttu-id="87fc8-123">弱い契約または存在しない契約を持つメソッドは、予期しない方法で失敗する可能性があるため、ランタイムは、レイジーな JIT コンパイル、ジェネリック ディクショナリの読み込み、スレッドの中断などによって発生する、メソッドからの独自の予期しないエラーを削除しようとしません。</span><span class="sxs-lookup"><span data-stu-id="87fc8-123">Because any method with a weak or nonexistent contract can potentially fail in many unpredictable ways, the runtime does not attempt to remove any of its own unpredictable failures from the method  that are introduced by lazy JIT-compiling, generics dictionary population, or thread aborts, for example.</span></span> <span data-ttu-id="87fc8-124">つまり、この MDA がアクティブになっているときは、ランタイムが、定義されている CER に呼び出されたメソッドを含めなかったことを意味します。引き続きこのサブツリーを準備すると潜在的なエラーが隠される可能性があるので、呼び出し先はこのノードで終了しました。</span><span class="sxs-lookup"><span data-stu-id="87fc8-124">That is, when this MDA is activated, it indicates that the runtime did not include the called method in the CER being defined; the call graph was terminated at this node because continuing to prepare this subtree would help mask the potential error.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="87fc8-125">解決方法</span><span class="sxs-lookup"><span data-stu-id="87fc8-125">Resolution</span></span>  

 <span data-ttu-id="87fc8-126">有効な信頼契約を関数に追加するか、その関数呼び出しを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="87fc8-126">Add a valid reliability contract to the function or avoid using that function call.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="87fc8-127">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="87fc8-127">Effect on the Runtime</span></span>  

 <span data-ttu-id="87fc8-128">CER から脆弱な契約を呼び出そうとする、CER でその操作を完了できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="87fc8-128">The effect of calling a weak contract from a CER could be the CER failure to complete its operations.</span></span> <span data-ttu-id="87fc8-129">これにより、<xref:System.AppDomain> プロセス ツリーが破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="87fc8-129">This could lead to corruption of the <xref:System.AppDomain> process state.</span></span>  
  
## <a name="output"></a><span data-ttu-id="87fc8-130">出力</span><span class="sxs-lookup"><span data-stu-id="87fc8-130">Output</span></span>  

 <span data-ttu-id="87fc8-131">この MDA の出力サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="87fc8-131">The following is sample output from this MDA.</span></span>  
  
 `Method 'MethodWithCer', while executing within a constrained execution region, makes a call at IL offset 0x000C to 'MethodWithWeakContract', which does not have a sufficiently strong reliability contract and might cause non-deterministic results.`  
  
## <a name="configuration"></a><span data-ttu-id="87fc8-132">構成</span><span class="sxs-lookup"><span data-stu-id="87fc8-132">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="87fc8-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="87fc8-133">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [<span data-ttu-id="87fc8-134">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="87fc8-134">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
