---
title: 制約された実行領域
description: 信頼性のあるマネージド コードを作成するための機構の一部である制約された実行領域 (CER) の使用を開始します。
ms.date: 03/30/2017
helpviewer_keywords:
- constrained execution regions
- CERs
ms.assetid: 99354547-39c1-4b0b-8553-938e8f8d1808
ms.openlocfilehash: 5014885e186b1fff16543c09d5652958f2463e3d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266858"
---
# <a name="constrained-execution-regions"></a><span data-ttu-id="ac931-103">制約された実行領域</span><span class="sxs-lookup"><span data-stu-id="ac931-103">Constrained Execution Regions</span></span>

<span data-ttu-id="ac931-104">制約された実行領域 (CER) は、信頼性のあるマネージド コードを作成するための機構の一部です。</span><span class="sxs-lookup"><span data-stu-id="ac931-104">A constrained execution region (CER) is part of a mechanism for authoring reliable managed code.</span></span> <span data-ttu-id="ac931-105">CER は、領域内のコードが領域全体で実行されるのを防ぐ帯域外の例外を、共通言語ランタイム (CLR) がスローすることが制約された領域を定義します。</span><span class="sxs-lookup"><span data-stu-id="ac931-105">A CER defines an area in which the common language runtime (CLR) is constrained from throwing out-of-band exceptions that would prevent the code in the area from executing in its entirety.</span></span> <span data-ttu-id="ac931-106">その領域内では、ユーザー コードは、帯域外の例外がスローされることになるコードの実行を制約されます。</span><span class="sxs-lookup"><span data-stu-id="ac931-106">Within that region, user code is constrained from executing code that would result in the throwing of out-of-band exceptions.</span></span> <span data-ttu-id="ac931-107"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> メソッドは `try` ブロックの直前にある必要があります。このメソッドによって、`catch`、`finally`、`fault` の各ブロックが制約された実行領域としてマークされます。</span><span class="sxs-lookup"><span data-stu-id="ac931-107">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method must immediately precede a `try` block and marks `catch`, `finally`, and `fault` blocks as constrained execution regions.</span></span> <span data-ttu-id="ac931-108">制約された領域としてマークされると、コードは信頼性の高いコントラクトでのみ他のコードを呼び出す必要があります。また、コードは、エラーを処理する準備ができている場合を除き、準備されていないメソッドや信頼性のないメソッドの割り当てや仮想呼び出しを行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="ac931-108">Once marked as a constrained region, code must only call other code with strong reliability contracts, and code should not allocate or make virtual calls to unprepared or unreliable methods unless the code is prepared to handle failures.</span></span> <span data-ttu-id="ac931-109">CLR は、CER で実行されるコードのスレッドの中止を遅らせます。</span><span class="sxs-lookup"><span data-stu-id="ac931-109">The CLR delays thread aborts for code that is executing in a CER.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="ac931-110">CER は .NET Framework でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ac931-110">CER is only supported in .NET Framework.</span></span> <span data-ttu-id="ac931-111">この記事は、.NET Core または .NET 5 以降には適用されません。</span><span class="sxs-lookup"><span data-stu-id="ac931-111">This article doesn't apply to .NET Core or .NET 5 and above.</span></span>

 <span data-ttu-id="ac931-112">制約された実行領域は、注釈付きの `try` ブロックだけでなく、特に <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> クラスから派生したクラス、および <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> メソッドを使用して実行されるコードで実行するクリティカル ファイナライザーなど、CLR のさまざまな形式で使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac931-112">Constrained execution regions are used in different forms in the CLR in addition to an annotated `try` block, notably critical finalizers executing in classes derived from the <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> class and code executed using the <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> method.</span></span>  
  
## <a name="cer-advance-preparation"></a><span data-ttu-id="ac931-113">CER の事前準備</span><span class="sxs-lookup"><span data-stu-id="ac931-113">CER Advance Preparation</span></span>  

 <span data-ttu-id="ac931-114">CLR は、メモリ不足の状態を回避するために、CER を事前に準備します。</span><span class="sxs-lookup"><span data-stu-id="ac931-114">The CLR prepares CERs in advance to avoid out-of-memory conditions.</span></span> <span data-ttu-id="ac931-115">JIT コンパイル時や型の読み込み時に、CLR がメモリ不足の状態を引き起こさないように、事前準備が必要となります。</span><span class="sxs-lookup"><span data-stu-id="ac931-115">Advance preparation is required so the CLR does not cause an out of memory condition during just-in-time compilation or type loading.</span></span>  
  
 <span data-ttu-id="ac931-116">次のように、開発者はコード領域が CER であることを示す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac931-116">The developer is required to indicate that a code region is a CER:</span></span>  
  
- <span data-ttu-id="ac931-117"><xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> 属性が適用されたすべての呼び出し先のトップレベルの CER 領域とメソッドは事前に準備されます。</span><span class="sxs-lookup"><span data-stu-id="ac931-117">The top level CER region and methods in the full call graph that have the <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> attribute applied are prepared in advance.</span></span> <span data-ttu-id="ac931-118"><xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> は、<xref:System.Runtime.ConstrainedExecution.Cer.Success> または <xref:System.Runtime.ConstrainedExecution.Cer.MayFail> の保証のみを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="ac931-118">The <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> can only state guarantees of <xref:System.Runtime.ConstrainedExecution.Cer.Success> or <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>.</span></span>  
  
- <span data-ttu-id="ac931-119">仮想ディスパッチなど、静的に決定できない呼び出しに対して事前準備を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="ac931-119">Advance preparation cannot be performed for calls that cannot be statically determined, such as virtual dispatch.</span></span> <span data-ttu-id="ac931-120">このような場合には、<xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="ac931-120">Use the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method in these cases.</span></span> <span data-ttu-id="ac931-121"><xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> メソッドを使用する場合は、<xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute> 属性をクリーンアップ コードに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac931-121">When using the <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> method, the <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute> attribute should be applied to the clean up code.</span></span>  
  
## <a name="constraints"></a><span data-ttu-id="ac931-122">制約</span><span class="sxs-lookup"><span data-stu-id="ac931-122">Constraints</span></span>  

 <span data-ttu-id="ac931-123">ユーザーは、CER で書き込むことのできるコードの種類で制約を受けます。</span><span class="sxs-lookup"><span data-stu-id="ac931-123">Users are constrained in the type of code they can write in a CER.</span></span> <span data-ttu-id="ac931-124">コードでは、次の操作によって生じる可能性のある帯域外の例外を発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="ac931-124">The code cannot cause an out-of-band exception, such as might result from the following operations:</span></span>  
  
- <span data-ttu-id="ac931-125">明示的な割り当て。</span><span class="sxs-lookup"><span data-stu-id="ac931-125">Explicit allocation.</span></span>  
  
- <span data-ttu-id="ac931-126">ボックス化。</span><span class="sxs-lookup"><span data-stu-id="ac931-126">Boxing.</span></span>  
  
- <span data-ttu-id="ac931-127">ロックの取得。</span><span class="sxs-lookup"><span data-stu-id="ac931-127">Acquiring a lock.</span></span>  
  
- <span data-ttu-id="ac931-128">準備されていないメソッドの仮想呼び出し。</span><span class="sxs-lookup"><span data-stu-id="ac931-128">Calling unprepared methods virtually.</span></span>  
  
- <span data-ttu-id="ac931-129">信頼性の低いコントラクトまたは信頼性のないコントラクトでのメソッド呼び出し。</span><span class="sxs-lookup"><span data-stu-id="ac931-129">Calling methods with a weak or nonexistent reliability contract.</span></span>  
  
 <span data-ttu-id="ac931-130">.NET Framework Version 2.0 では、これらの制約はガイドラインです。</span><span class="sxs-lookup"><span data-stu-id="ac931-130">In the .NET Framework version 2.0, these constraints are guidelines.</span></span> <span data-ttu-id="ac931-131">診断はコード分析ツールを通じて提供されます。</span><span class="sxs-lookup"><span data-stu-id="ac931-131">Diagnostics are provided through code analysis tools.</span></span>  
  
## <a name="reliability-contracts"></a><span data-ttu-id="ac931-132">信頼性のコントラクト</span><span class="sxs-lookup"><span data-stu-id="ac931-132">Reliability Contracts</span></span>  

 <span data-ttu-id="ac931-133"><xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> は、信頼性の保証と特定のメソッドの破損状態を文書化するカスタム属性です。</span><span class="sxs-lookup"><span data-stu-id="ac931-133">The <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> is a custom attribute that documents the reliability guarantees and the corruption state of a given method.</span></span>  
  
### <a name="reliability-guarantees"></a><span data-ttu-id="ac931-134">信頼性の保証</span><span class="sxs-lookup"><span data-stu-id="ac931-134">Reliability Guarantees</span></span>  

 <span data-ttu-id="ac931-135"><xref:System.Runtime.ConstrainedExecution.Cer> 列挙値によって表される信頼性の保証は、特定のメソッドの信頼度を次のように示します。</span><span class="sxs-lookup"><span data-stu-id="ac931-135">Reliability guarantees, represented by <xref:System.Runtime.ConstrainedExecution.Cer> enumeration values, indicate the degree of reliability of a given method:</span></span>  
  
- <span data-ttu-id="ac931-136"><xref:System.Runtime.ConstrainedExecution.Cer.MayFail>.</span><span class="sxs-lookup"><span data-stu-id="ac931-136"><xref:System.Runtime.ConstrainedExecution.Cer.MayFail>.</span></span> <span data-ttu-id="ac931-137">例外的な条件下で、メソッドは失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ac931-137">Under exceptional conditions, the method might fail.</span></span> <span data-ttu-id="ac931-138">この場合、メソッドは呼び出し元のメソッドに成功したか失敗したかを報告します。</span><span class="sxs-lookup"><span data-stu-id="ac931-138">In this case, the method reports back to the calling method whether it succeeded or failed.</span></span> <span data-ttu-id="ac931-139">メソッドが戻り値を確実に報告できるように、メソッドは CER に含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac931-139">The method must be contained in a CER to ensure that it can report the return value.</span></span>  
  
- <span data-ttu-id="ac931-140"><xref:System.Runtime.ConstrainedExecution.Cer.None>.</span><span class="sxs-lookup"><span data-stu-id="ac931-140"><xref:System.Runtime.ConstrainedExecution.Cer.None>.</span></span> <span data-ttu-id="ac931-141">メソッド、型、またはアセンブリには CER の概念がないため、状態の破損を大幅に軽減しなければ、CER 内での呼び出しが安全ではない可能性が最も高くなります。</span><span class="sxs-lookup"><span data-stu-id="ac931-141">The method, type, or assembly has no concept of a CER and is most likely not safe to call within a CER without substantial mitigation from state corruption.</span></span> <span data-ttu-id="ac931-142">この値では、CER の保証を利用しません。</span><span class="sxs-lookup"><span data-stu-id="ac931-142">It does not take advantage of CER guarantees.</span></span> <span data-ttu-id="ac931-143">これは以下を意味します。</span><span class="sxs-lookup"><span data-stu-id="ac931-143">This implies the following:</span></span>  
  
    1. <span data-ttu-id="ac931-144">例外的な条件下で、メソッドが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ac931-144">Under exceptional conditions the method might fail.</span></span>  
  
    2. <span data-ttu-id="ac931-145">メソッドは、失敗したことを報告する場合としない場合があります。</span><span class="sxs-lookup"><span data-stu-id="ac931-145">The method might or might not report that it failed.</span></span>  
  
    3. <span data-ttu-id="ac931-146">メソッドは、CER の最も可能性の高いシナリオを使用するように書かれていません。</span><span class="sxs-lookup"><span data-stu-id="ac931-146">The method is not written to use a CER, the most likely scenario.</span></span>  
  
    4. <span data-ttu-id="ac931-147">メソッド、型、またはアセンブリの成功が明示的に識別されていない場合、暗黙的に <xref:System.Runtime.ConstrainedExecution.Cer.None> として識別されます。</span><span class="sxs-lookup"><span data-stu-id="ac931-147">If a method, type, or assembly is not explicitly identified to succeed, it is implicitly identified as <xref:System.Runtime.ConstrainedExecution.Cer.None>.</span></span>  
  
- <span data-ttu-id="ac931-148"><xref:System.Runtime.ConstrainedExecution.Cer.Success>.</span><span class="sxs-lookup"><span data-stu-id="ac931-148"><xref:System.Runtime.ConstrainedExecution.Cer.Success>.</span></span> <span data-ttu-id="ac931-149">例外的な条件下で、メソッドは成功することが保証されます。</span><span class="sxs-lookup"><span data-stu-id="ac931-149">Under exceptional conditions, the method is guaranteed to succeed.</span></span> <span data-ttu-id="ac931-150">このレベルの信頼性を実現するには、メソッドが CER 以外の領域内から呼び出される場合でも、呼び出されるメソッドの周辺に CER を常に構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac931-150">To achieve this level of reliability you should always construct a CER around the method that is called, even when it is called from within a non-CER region.</span></span> <span data-ttu-id="ac931-151">成功の判断は主観的なものですが、メソッドが意図したとおりに実行された場合、そのメソッドは成功ということになります。</span><span class="sxs-lookup"><span data-stu-id="ac931-151">A method is successful if it accomplishes what is intended, although success can be viewed subjectively.</span></span> <span data-ttu-id="ac931-152">たとえば、Count を `ReliabilityContractAttribute(Cer.Success)` でマークした場合、CER での実行時に、常に <xref:System.Collections.ArrayList> の要素数が返され、内部フィールドを不明な状態のままにすることはできないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="ac931-152">For example, marking Count with `ReliabilityContractAttribute(Cer.Success)` implies that when it is run under a CER, it always returns a count of the number of elements in the <xref:System.Collections.ArrayList> and it can never leave the internal fields in an undetermined state.</span></span>  <span data-ttu-id="ac931-153"><xref:System.Threading.Interlocked.CompareExchange%2A> メソッドも同様に成功としてマークされますが、その成功は競合状態によって値を新しい値に置き換えることができなかったことを意味する場合があります。</span><span class="sxs-lookup"><span data-stu-id="ac931-153">However, the <xref:System.Threading.Interlocked.CompareExchange%2A> method is marked as success as well, with the understanding that success may mean the value could not be replaced with a new value due to a race condition.</span></span>  <span data-ttu-id="ac931-154">重要な点は、メソッドが文書化されたとおりに動作することと、正しいにもかかわらず信頼性のないコードの外観以外の異常な動作を予測して CER コードを記述する必要はないということです。</span><span class="sxs-lookup"><span data-stu-id="ac931-154">The key point is that the method behaves in the way it is documented to behave, and CER code does not need to be written to expect any unusual behavior beyond what correct but unreliable code would look like.</span></span>  
  
### <a name="corruption-levels"></a><span data-ttu-id="ac931-155">破損レベル</span><span class="sxs-lookup"><span data-stu-id="ac931-155">Corruption levels</span></span>  

 <span data-ttu-id="ac931-156"><xref:System.Runtime.ConstrainedExecution.Consistency> 列挙値によって表される破損レベルは、特定の環境で状態がどの程度破損する可能性があるかを示します。</span><span class="sxs-lookup"><span data-stu-id="ac931-156">Corruption levels, represented by <xref:System.Runtime.ConstrainedExecution.Consistency> enumeration values, indicate how much state may be corrupted in a given environment:</span></span>  
  
- <span data-ttu-id="ac931-157"><xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>.</span><span class="sxs-lookup"><span data-stu-id="ac931-157"><xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>.</span></span> <span data-ttu-id="ac931-158">例外的な条件下で、共通言語ランタイム (CLR) は、現在のアプリケーション ドメインにおける状態の一貫性に関して一切保証しません。</span><span class="sxs-lookup"><span data-stu-id="ac931-158">Under exceptional conditions, the common language runtime (CLR) makes no guarantees regarding state consistency in the current application domain.</span></span>  
  
- <span data-ttu-id="ac931-159"><xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptInstance>.</span><span class="sxs-lookup"><span data-stu-id="ac931-159"><xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptInstance>.</span></span> <span data-ttu-id="ac931-160">例外的な条件下で、メソッドは状態の破損を現在のインスタンスに限定することが保証されます。</span><span class="sxs-lookup"><span data-stu-id="ac931-160">Under exceptional conditions, the method is guaranteed to limit state corruption to the current instance.</span></span>  
  
- <span data-ttu-id="ac931-161"><xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>。例外的な条件下で、CLR は状態の一貫性に関して一切保証しません。つまり、条件によってプロセスが破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ac931-161"><xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, Under exceptional conditions, the CLR makes no guarantees regarding state consistency; that is, the condition might corrupt the process.</span></span>  
  
- <span data-ttu-id="ac931-162"><xref:System.Runtime.ConstrainedExecution.Consistency.WillNotCorruptState>.</span><span class="sxs-lookup"><span data-stu-id="ac931-162"><xref:System.Runtime.ConstrainedExecution.Consistency.WillNotCorruptState>.</span></span> <span data-ttu-id="ac931-163">例外的な条件下で、メソッドは状態を破損しないことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="ac931-163">Under exceptional conditions, the method is guaranteed not to corrupt state.</span></span>  
  
## <a name="reliability-trycatchfinally"></a><span data-ttu-id="ac931-164">信頼性の try/catch/finally</span><span class="sxs-lookup"><span data-stu-id="ac931-164">Reliability try/catch/finally</span></span>  

 <span data-ttu-id="ac931-165">信頼性の `try/catch/finally` は、予測可能性の保証がアンマネージ バージョンと同じレベルである例外処理機構です。</span><span class="sxs-lookup"><span data-stu-id="ac931-165">The reliability `try/catch/finally` is an exception handling mechanism with the same level of predictability guarantees as the unmanaged version.</span></span> <span data-ttu-id="ac931-166">`catch/finally` ブロックは CER です。</span><span class="sxs-lookup"><span data-stu-id="ac931-166">The `catch/finally` block is the CER.</span></span> <span data-ttu-id="ac931-167">ブロック内のメソッドには事前準備が必要であり、中断不可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac931-167">Methods in the block require advance preparation and must be noninterruptible.</span></span>  
  
 <span data-ttu-id="ac931-168">.NET Framework バージョン 2.0 では、コードは、try ブロックの直前に <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> を呼び出すことにより、try が信頼できることをランタイムに通知します。</span><span class="sxs-lookup"><span data-stu-id="ac931-168">In the .NET Framework version 2.0, code informs the runtime that a try is reliable by calling <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> immediately preceding a try block.</span></span> <span data-ttu-id="ac931-169"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> は、コンパイラ サポート クラスである <xref:System.Runtime.CompilerServices.RuntimeHelpers> のメンバーです。</span><span class="sxs-lookup"><span data-stu-id="ac931-169"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> is a member of <xref:System.Runtime.CompilerServices.RuntimeHelpers>, a compiler support class.</span></span> <span data-ttu-id="ac931-170">コンパイラで使用できるようになるまで <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> を直接呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ac931-170">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> directly pending its availability through compilers.</span></span>  
  
## <a name="noninterruptible-regions"></a><span data-ttu-id="ac931-171">中断不可能な領域</span><span class="sxs-lookup"><span data-stu-id="ac931-171">Noninterruptible Regions</span></span>  

 <span data-ttu-id="ac931-172">中断不可能な領域は、一連の命令を CER にグループ化します。</span><span class="sxs-lookup"><span data-stu-id="ac931-172">A noninterruptible region groups a set of instructions into a CER.</span></span>  
  
 <span data-ttu-id="ac931-173">.NET Framework バージョン 2.0 では、コンパイラ サポートで使用できるようになるまで、ユーザー コードは、前に <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> メソッド呼び出しがある空の try/catch ブロックを含む信頼性のある try/catch/finally を使用して、中断不可能な領域を作成します。</span><span class="sxs-lookup"><span data-stu-id="ac931-173">In .NET Framework version 2.0, pending availability through compiler support, user code creates non-interruptible regions with a reliable try/catch/finally that contains an empty try/catch block preceded by a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call.</span></span>  
  
## <a name="critical-finalizer-object"></a><span data-ttu-id="ac931-174">クリティカル ファイナライザー オブジェクト</span><span class="sxs-lookup"><span data-stu-id="ac931-174">Critical Finalizer Object</span></span>  

 <span data-ttu-id="ac931-175"><xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> は、ガベージ コレクションでファイナライザーが実行されることを保証します。</span><span class="sxs-lookup"><span data-stu-id="ac931-175">A <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> guarantees that garbage collection will execute the finalizer.</span></span> <span data-ttu-id="ac931-176">割り当て時に、ファイナライザーとその呼び出し先は事前に準備されます。</span><span class="sxs-lookup"><span data-stu-id="ac931-176">Upon allocation, the finalizer and its call graph are prepared in advance.</span></span> <span data-ttu-id="ac931-177">ファイナライザー メソッドは CER で実行されるため、CER とファイナライザーのすべての制約に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac931-177">The finalizer method executes in a CER, and must obey all the constraints on CERs and finalizers.</span></span>  
  
 <span data-ttu-id="ac931-178"><xref:System.Runtime.InteropServices.SafeHandle> および <xref:System.Runtime.InteropServices.CriticalHandle> から継承するすべての型は、CER 内でファイナライザーが実行されることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="ac931-178">Any types inheriting from <xref:System.Runtime.InteropServices.SafeHandle> and <xref:System.Runtime.InteropServices.CriticalHandle> are guaranteed to have their finalizer execute within a CER.</span></span> <span data-ttu-id="ac931-179"><xref:System.Runtime.InteropServices.SafeHandle> の派生クラスで <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> を実装して、ハンドルを解放する必要のあるコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="ac931-179">Implement <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> in <xref:System.Runtime.InteropServices.SafeHandle> derived classes to execute any code that is required to free the handle.</span></span>  
  
## <a name="code-not-permitted-in-cers"></a><span data-ttu-id="ac931-180">CER で許可されないコード</span><span class="sxs-lookup"><span data-stu-id="ac931-180">Code Not Permitted in CERs</span></span>  

 <span data-ttu-id="ac931-181">CER では、次の操作は許可されません。</span><span class="sxs-lookup"><span data-stu-id="ac931-181">The following operations are not permitted in CERs:</span></span>  
  
- <span data-ttu-id="ac931-182">明示的な割り当て。</span><span class="sxs-lookup"><span data-stu-id="ac931-182">Explicit allocations.</span></span>  
  
- <span data-ttu-id="ac931-183">ロックの取得。</span><span class="sxs-lookup"><span data-stu-id="ac931-183">Acquiring a lock.</span></span>  
  
- <span data-ttu-id="ac931-184">ボックス化。</span><span class="sxs-lookup"><span data-stu-id="ac931-184">Boxing.</span></span>  
  
- <span data-ttu-id="ac931-185">多次元配列アクセス。</span><span class="sxs-lookup"><span data-stu-id="ac931-185">Multidimensional array access.</span></span>  
  
- <span data-ttu-id="ac931-186">リフレクションを通じたメソッド呼び出し。</span><span class="sxs-lookup"><span data-stu-id="ac931-186">Method calls through reflection.</span></span>  
  
- <span data-ttu-id="ac931-187"><xref:System.Threading.Monitor.Enter%2A> または <xref:System.IO.FileStream.Lock%2A>。</span><span class="sxs-lookup"><span data-stu-id="ac931-187"><xref:System.Threading.Monitor.Enter%2A> or <xref:System.IO.FileStream.Lock%2A>.</span></span>  
  
- <span data-ttu-id="ac931-188">セキュリティのチェック。</span><span class="sxs-lookup"><span data-stu-id="ac931-188">Security checks.</span></span> <span data-ttu-id="ac931-189">要求は実行しないでください (リンク確認要求のみ)。</span><span class="sxs-lookup"><span data-stu-id="ac931-189">Do not perform demands, only link demands.</span></span>  
  
- <span data-ttu-id="ac931-190">COM オブジェクトおよびプロキシの <xref:System.Reflection.Emit.OpCodes.Isinst> と <xref:System.Reflection.Emit.OpCodes.Castclass>。</span><span class="sxs-lookup"><span data-stu-id="ac931-190"><xref:System.Reflection.Emit.OpCodes.Isinst> and <xref:System.Reflection.Emit.OpCodes.Castclass> for COM objects and proxies</span></span>  
  
- <span data-ttu-id="ac931-191">透過プロキシのフィールドの取得または設定。</span><span class="sxs-lookup"><span data-stu-id="ac931-191">Getting or setting fields on a transparent proxy.</span></span>  
  
- <span data-ttu-id="ac931-192">シリアル化。</span><span class="sxs-lookup"><span data-stu-id="ac931-192">Serialization.</span></span>  
  
- <span data-ttu-id="ac931-193">関数ポインターとデリゲート。</span><span class="sxs-lookup"><span data-stu-id="ac931-193">Function pointers and delegates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac931-194">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac931-194">See also</span></span>

- [<span data-ttu-id="ac931-195">信頼性に関するベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="ac931-195">Reliability Best Practices</span></span>](reliability-best-practices.md)
