---
title: 規模が大きく、応答性の高い .NET Framework アプリの作成
description: 規模が大きく応答性の高い .NET アプリ、またはファイルやデータベースなど大量のデータを処理するアプリを作成します。
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 20b9f34595f8586eb5162715eb6b0df171f132a1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266845"
---
# <a name="writing-large-responsive-net-framework-apps"></a><span data-ttu-id="acf58-103">規模が大きく、応答性の高い .NET Framework アプリの作成</span><span class="sxs-lookup"><span data-stu-id="acf58-103">Writing Large, Responsive .NET Framework Apps</span></span>

<span data-ttu-id="acf58-104">この記事では、大規模な .NET Framework アプリや、ファイルやデータベースなど大量のデータを処理するアプリのパフォーマンス改善のヒントを説明します。</span><span class="sxs-lookup"><span data-stu-id="acf58-104">This article provides tips for improving the performance of large .NET Framework apps, or apps that process a large amount of data such as files or databases.</span></span> <span data-ttu-id="acf58-105">説明するヒントは C# および Visual Basic コンパイラを マネージド コードで作成し直した際に得られたものです。この記事では C# コンパイラでの実際の例をいくつか紹介します。</span><span class="sxs-lookup"><span data-stu-id="acf58-105">These tips come from rewriting the C# and Visual Basic compilers in managed code, and this article includes several real examples from the C# compiler.</span></span>
  
<span data-ttu-id="acf58-106">.NET Framework は、生産性の高いアプリ開発環境です。</span><span class="sxs-lookup"><span data-stu-id="acf58-106">The .NET Framework is highly productive for building apps.</span></span> <span data-ttu-id="acf58-107">強力で安全な言語と豊富なライブラリにより、アプリの開発生産性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="acf58-107">Powerful and safe languages and a rich collection of libraries make app building highly fruitful.</span></span> <span data-ttu-id="acf58-108">ただし、高い生産性には責任が伴います。</span><span class="sxs-lookup"><span data-stu-id="acf58-108">However, with great productivity comes responsibility.</span></span> <span data-ttu-id="acf58-109">.NET Framework のあらゆる機能を使用するするのであれば、必要に応じてコードのパフォーマンスを調整できるようにしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="acf58-109">You should use all the power of the .NET Framework, but be prepared to tune your code’s performance when needed.</span></span>
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a><span data-ttu-id="acf58-110">新しいコンパイラのパフォーマンスがアプリに適用される理由</span><span class="sxs-lookup"><span data-stu-id="acf58-110">Why the new compiler performance applies to your app</span></span>  

 <span data-ttu-id="acf58-111">.NET コンパイラ プラットフォーム ("Roslyn") チームは、コードのモデリングと分析、ツールの開発、そして Visual Studio でのより充実したコード対応エクスペリエンスの実現のための新たな API を提供するため、C# および Visual Basic コンパイラをマネージド コードで再作成しました。</span><span class="sxs-lookup"><span data-stu-id="acf58-111">The .NET Compiler Platform ("Roslyn") team rewrote the C# and Visual Basic compilers in managed code to provide new APIs for modeling and analyzing code, building tools, and enabling much richer, code-aware experiences in Visual Studio.</span></span> <span data-ttu-id="acf58-112">コンパイラの全体的な書き直しと、新しいコンパイラでの Visual Studio 機能の構築を通して、大規模 .NET Framework アプリや、大量データを処理するアプリに適用できる有用なパフォーマンス情報が明らかになりました。</span><span class="sxs-lookup"><span data-stu-id="acf58-112">Rewriting the compilers and building Visual Studio experiences on the new compilers revealed useful performance insights that are applicable to any large .NET Framework app or any app that processes a lot of data.</span></span> <span data-ttu-id="acf58-113">C# コンパイラについてのこのような情報や例を活用するために、コンパイラについて理解しておく必要はありません。</span><span class="sxs-lookup"><span data-stu-id="acf58-113">You don't need to know about compilers to take advantage of the insights and examples from the C# compiler.</span></span>
  
 <span data-ttu-id="acf58-114">Visual Studio ではコンパイラ API を使用して、ユーザーに人気のある IntelliSense 機能 (識別子とキーワードの色づけ、構文の入力候補一覧、エラーを示す波線、パラメーターのヒント、コードの問題、コードアクションなど) を作成します。</span><span class="sxs-lookup"><span data-stu-id="acf58-114">Visual Studio uses the compiler APIs to build all the IntelliSense features that users love, such as colorization of identifiers and keywords, syntax completion lists, squiggles for errors, parameter tips, code issues, and code actions.</span></span> <span data-ttu-id="acf58-115">Visual Studio では、開発者がコードを入力するときや変更するときにこのヘルプが表示されます。コンパイラがコード開発者による編集内容をモデル化している間も、Visual Studio は応答性を維持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acf58-115">Visual Studio provides this help while developers are typing and changing their code, and Visual Studio must remain responsive while the compiler continually models the code developers edit.</span></span>
  
 <span data-ttu-id="acf58-116">エンド ユーザはアプリを操作するときに、アプリが応答するものであると期待します。</span><span class="sxs-lookup"><span data-stu-id="acf58-116">When your end users interact with your app, they expect it to be responsive.</span></span> <span data-ttu-id="acf58-117">入力またはコマンドの処理がブロックされることがあってはなりません。</span><span class="sxs-lookup"><span data-stu-id="acf58-117">Typing or command handling should never be blocked.</span></span> <span data-ttu-id="acf58-118">ヘルプはすぐにポップアップ表示され、またユーザーが入力を続けるときには閉じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="acf58-118">Help should pop up quickly or give up if the user continues typing.</span></span> <span data-ttu-id="acf58-119">処理時間がかかっている UI スレッドがあり、これが原因でアプリの動作が遅くなっていると判断される場合でも、アプリがその UI スレッドをブロックしないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="acf58-119">Your app should avoid blocking the UI thread with long computations that make the app feel sluggish.</span></span>
  
 <span data-ttu-id="acf58-120">Roslyn コンパイラの詳細については、「[.NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="acf58-120">For more information about Roslyn compilers, see [The .NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md).</span></span>
  
## <a name="just-the-facts"></a><span data-ttu-id="acf58-121">.NET Framework についての事実</span><span class="sxs-lookup"><span data-stu-id="acf58-121">Just the Facts</span></span>  

 <span data-ttu-id="acf58-122">パフォーマンスを調整し、応答性のある .NET Framework アプリを作成する際には、次に説明する事実を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="acf58-122">Consider these facts when tuning performance and creating responsive .NET Framework apps.</span></span>
  
### <a name="fact-1-dont-prematurely-optimize"></a><span data-ttu-id="acf58-123">事実 1: 不完全な最適化は行わない</span><span class="sxs-lookup"><span data-stu-id="acf58-123">Fact 1: Don’t prematurely optimize</span></span>  

 <span data-ttu-id="acf58-124">必要以上に複雑なコードを記述すると、保守、デバッグ、細かな調整に伴うコストが発生します。</span><span class="sxs-lookup"><span data-stu-id="acf58-124">Writing code that is more complex than it needs to be incurs maintenance, debugging, and polishing costs.</span></span> <span data-ttu-id="acf58-125">経験豊富なプログラマは、コーディングの問題の解決方法を直観的に把握し、より効率的なコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="acf58-125">Experienced programmers have an intuitive grasp of how to solve coding problems and write more efficient code.</span></span> <span data-ttu-id="acf58-126">しかし、コードの最適化が不完全になることがあります。</span><span class="sxs-lookup"><span data-stu-id="acf58-126">However, they sometimes prematurely optimize their code.</span></span> <span data-ttu-id="acf58-127">たとえば、単純な配列で十分な場合にハッシュ テーブルを使用したり、単に値を再計算する代わりに、メモリ リークが発生する恐れのある複雑なキャッシュを使用したりします。</span><span class="sxs-lookup"><span data-stu-id="acf58-127">For example, they use a hash table when a simple array would suffice, or use complicated caching that may leak memory instead of simply recomputing values.</span></span> <span data-ttu-id="acf58-128">経験豊富なプログラマであっても、パフォーマンスを確認するテストを実施し、問題がある場合にはコードを分析してください。</span><span class="sxs-lookup"><span data-stu-id="acf58-128">Even if you’re an experience programmer, you should test for performance and analyze your code when you find issues.</span></span>
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a><span data-ttu-id="acf58-129">事実 2: 測定していないのであれば、それは推測である</span><span class="sxs-lookup"><span data-stu-id="acf58-129">Fact 2: If you’re not measuring, you’re guessing</span></span>  

 <span data-ttu-id="acf58-130">プロファイルと測定は嘘をつきません。</span><span class="sxs-lookup"><span data-stu-id="acf58-130">Profiles and measurements don’t lie.</span></span> <span data-ttu-id="acf58-131">プロファイルから、CPU の負荷が上限になっているかどうか、またはディスク I/O でブロックされているかどうかがわかります。</span><span class="sxs-lookup"><span data-stu-id="acf58-131">Profiles show you whether the CPU is fully loaded or whether you’re blocked on disk I/O.</span></span> <span data-ttu-id="acf58-132">プロファイルは、割り当てるメモリのサイズと種類、[ガベージ コレクション](../../standard/garbage-collection/index.md) (GC) の処理に CPU が長い時間を取られていないか示します。</span><span class="sxs-lookup"><span data-stu-id="acf58-132">Profiles tell you what kind and how much memory you’re allocating and whether your CPU is spending a lot of time in [garbage collection](../../standard/garbage-collection/index.md) (GC).</span></span>
  
 <span data-ttu-id="acf58-133">アプリでの主要な顧客エクスペリエンスやシナリオについてパフォーマンスの目標を設定し、パフォーマンスを測定するテストを作成してください。</span><span class="sxs-lookup"><span data-stu-id="acf58-133">You should set performance goals for key customer experiences or scenarios in your app and write tests to measure performance.</span></span> <span data-ttu-id="acf58-134">テスト失敗の調査には科学的な手法を使用します。ガイドとなるプロファイルを使用して、どのような問題が発生しているかを仮定し、実験やコード変更によってその仮定を検証します。</span><span class="sxs-lookup"><span data-stu-id="acf58-134">Investigate failing tests by applying the scientific method: use profiles to guide you, hypothesize what the issue might be, and test your hypothesis with an experiment or code change.</span></span> <span data-ttu-id="acf58-135">定期的にテストを実施して、時間の経過と共にベースライン パフォーマンス測定を確立します。これにより、パフォーマンス後退を引き起こしている変更を切り分けることができます。</span><span class="sxs-lookup"><span data-stu-id="acf58-135">Establish baseline performance measurements over time with regular testing, so you can isolate changes that cause regressions in performance.</span></span> <span data-ttu-id="acf58-136">パフォーマンス測定を厳密に実施することで、不要なコード更新に時間をかけることを回避できます。</span><span class="sxs-lookup"><span data-stu-id="acf58-136">By approaching performance work in a rigorous way, you’ll avoid wasting time with code updates you don’t need.</span></span>
  
### <a name="fact-3-good-tools-make-all-the-difference"></a><span data-ttu-id="acf58-137">事実 3: 優れたツールには大きな効果がある</span><span class="sxs-lookup"><span data-stu-id="acf58-137">Fact 3: Good tools make all the difference</span></span>  

 <span data-ttu-id="acf58-138">優れたツールを使用すれば、最も大きなパフォーマンスの問題 (CPU、メモリ、またはディスク) の詳細を迅速に確認し、このようなボトルネックを引き起こしているコードを特定できます。</span><span class="sxs-lookup"><span data-stu-id="acf58-138">Good tools let you drill quickly into the biggest performance issues (CPU, memory, or disk) and help you locate the code that causes those bottlenecks.</span></span> <span data-ttu-id="acf58-139">Microsoft では、[Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) や [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) など、さまざまなパフォーマンス ツールを提供しています。</span><span class="sxs-lookup"><span data-stu-id="acf58-139">Microsoft ships a variety of performance tools such as [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) and [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).</span></span>
  
 <span data-ttu-id="acf58-140">PerfView は、ディスク I/O、GC イベント、メモリなどの深刻な問題に取り組む際に役立つ極めて強力な無償のツールです。</span><span class="sxs-lookup"><span data-stu-id="acf58-140">PerfView is a free and amazingly powerful tool that helps you focus on deep issues such as disk I/O, GC events, and memory.</span></span> <span data-ttu-id="acf58-141">パフォーマンスに関連する [Windows イベント トレーシング](../wcf/samples/etw-tracing.md) (ETW) イベントをキャプチャし、アプリ別、プロセス別、スタック別、およびスレッド別に情報を容易に確認できます。</span><span class="sxs-lookup"><span data-stu-id="acf58-141">You can capture performance-related [Event Tracing for Windows](../wcf/samples/etw-tracing.md) (ETW) events and view easily per app, per process, per stack, and per thread information.</span></span> <span data-ttu-id="acf58-142">PerfView は、アプリによって割り当てられるメモリの種類と量、そしてメモリの割り当てにどの関数またはコール スタックがどの程度関与しているのかを示します。</span><span class="sxs-lookup"><span data-stu-id="acf58-142">PerfView shows you how much and what kind of memory your app allocates, and which functions or call stacks contribute how much to the memory allocations.</span></span> <span data-ttu-id="acf58-143">詳細については、ツールに付属している詳しいヘルプ トピック、デモ、ビデオ (Channel 9 の [PerfView チュートリアル](https://channel9.msdn.com/Series/PerfView-Tutorial) など) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="acf58-143">For details, see the rich help topics, demos, and videos included with the tool (such as the [PerfView tutorials](https://channel9.msdn.com/Series/PerfView-Tutorial) on Channel 9).</span></span>
  
### <a name="fact-4-its-all-about-allocations"></a><span data-ttu-id="acf58-144">事実 4: すべては割り当てで決まる</span><span class="sxs-lookup"><span data-stu-id="acf58-144">Fact 4: It’s all about allocations</span></span>  

 <span data-ttu-id="acf58-145">応答性の高い .NET Framework アプリ開発の要となるのはアルゴリズム (例: バブル ソートの代わりにクイック ソートを使用) であると思うかもしれませんが、それは正しくありません。</span><span class="sxs-lookup"><span data-stu-id="acf58-145">You might think that building a responsive .NET Framework app is all about algorithms, such as using quick sort instead of bubble sort, but that's not the case.</span></span> <span data-ttu-id="acf58-146">応答性の高いアプリを開発する上で最も重要なのは、メモリの割り当てです。これは特に、アプリが非常に大規模であり大量データを処理する場合に該当します。</span><span class="sxs-lookup"><span data-stu-id="acf58-146">The biggest factor in building a responsive app is allocating memory, especially when your app is very large or processes large amounts of data.</span></span>
  
 <span data-ttu-id="acf58-147">新しいコンパイラ API の応答性の高い IDE 機能のほとんどの開発作業には、割り当てを回避し、キャッシュ ストラテジを管理することが関連していました。</span><span class="sxs-lookup"><span data-stu-id="acf58-147">Almost all the work to build responsive IDE experiences with the new compiler APIs involved avoiding allocations and managing caching strategies.</span></span> <span data-ttu-id="acf58-148">PerfView トレースから、新しい C# および Visual Basic コンパイラのパフォーマンスはほとんど CPU とは関連していないことが判明しています。</span><span class="sxs-lookup"><span data-stu-id="acf58-148">PerfView traces show that the performance of the new C# and Visual Basic compilers is rarely CPU bound.</span></span> <span data-ttu-id="acf58-149">これらのコンパイラは、数十万行から数百万行のコード行の読み取り、メタデータの読み取り、または生成されたコードの出力の時点では I/O と関連しています。</span><span class="sxs-lookup"><span data-stu-id="acf58-149">The compilers can be I/O bound when reading hundreds of thousands or millions of lines of code, reading metadata, or emitting generated code.</span></span> <span data-ttu-id="acf58-150">UI スレッドの遅延の原因は、ほぼガベージ コレクションにあります。</span><span class="sxs-lookup"><span data-stu-id="acf58-150">The UI thread delays are nearly all due to garbage collection.</span></span> <span data-ttu-id="acf58-151">.NET Framework GC は、パフォーマンスのために高度に調整されており、その処理のほとんどはアプリ コードの実行中に同時に実行されます。</span><span class="sxs-lookup"><span data-stu-id="acf58-151">The .NET Framework GC is highly tuned for performance and does much of its work concurrently while app code executes.</span></span> <span data-ttu-id="acf58-152">ただし、1 回の割り当てによって負荷の高い [gen2](../../standard/garbage-collection/fundamentals.md) コレクションが実行され、これによってすべてのスレッドが停止されることがあります。</span><span class="sxs-lookup"><span data-stu-id="acf58-152">However, a single allocation can trigger an expensive [gen2](../../standard/garbage-collection/fundamentals.md) collection, stopping all threads.</span></span>
  
## <a name="common-allocations-and-examples"></a><span data-ttu-id="acf58-153">一般的な割り当てと例</span><span class="sxs-lookup"><span data-stu-id="acf58-153">Common allocations and examples</span></span>  

 <span data-ttu-id="acf58-154">このセクションの例の式では、小規模な割り当てについては特に問題になりません。</span><span class="sxs-lookup"><span data-stu-id="acf58-154">The example expressions in this section have hidden allocations that appear small.</span></span> <span data-ttu-id="acf58-155">ただし、大きなアプリが式をかなりの回数にわたって実行すると、数百メガバイトまたはギガバイトのメモリが割り当てられることがあります。</span><span class="sxs-lookup"><span data-stu-id="acf58-155">However, if a large app executes the expressions enough times, they can causes hundreds of megabytes, even gigabytes, of allocations.</span></span> <span data-ttu-id="acf58-156">たとえば、開発者によるエディターへの入力をシミュレーションする 1 分間のテストを実行したところ、ギガバイト単位のメモリが割り当てられたため、パフォーマンス チームは入力に関するシナリオに重点を置いて取り組みました。</span><span class="sxs-lookup"><span data-stu-id="acf58-156">For example, one-minute tests that simulated a developer’s typing in the editor allocated gigabytes of memory and led the performance team to focus on typing scenarios.</span></span>
  
### <a name="boxing"></a><span data-ttu-id="acf58-157">ボックス化</span><span class="sxs-lookup"><span data-stu-id="acf58-157">Boxing</span></span>  

 <span data-ttu-id="acf58-158">通常はスタックまたはデータ構造体内にある値型がオブジェクトでラップされると、[ボックス化](../../csharp/programming-guide/types/boxing-and-unboxing.md)が発生します。</span><span class="sxs-lookup"><span data-stu-id="acf58-158">[Boxing](../../csharp/programming-guide/types/boxing-and-unboxing.md) occurs when value types that normally live on the stack or in data structures are wrapped in an object.</span></span> <span data-ttu-id="acf58-159">つまり、データを保持するオブジェクトを割り当て、そのオブジェクトを指すポインタを返します。</span><span class="sxs-lookup"><span data-stu-id="acf58-159">That is, you allocate an object to hold the data, and then return a pointer to the object.</span></span> <span data-ttu-id="acf58-160">.NET Framework では、メソッドのシグネチャや格納場所の種類が原因で、値がボックス化されることがあります。</span><span class="sxs-lookup"><span data-stu-id="acf58-160">The .NET Framework sometimes boxes values due to the signature of a method or the type of a storage location.</span></span> <span data-ttu-id="acf58-161">オブジェクト内で値型がラップされると、メモリ割り当てが行われます。</span><span class="sxs-lookup"><span data-stu-id="acf58-161">Wrapping a value type in an object causes memory allocation.</span></span> <span data-ttu-id="acf58-162">多くのボックス化操作を実行すると、アプリへメガバイト単位またはギガバイト単位のメモリが割り当てられ、アプリがさらに多くの GC の原因になります。</span><span class="sxs-lookup"><span data-stu-id="acf58-162">Many boxing operations can contribute megabytes or gigabytes of allocations to your app, which means that your app will cause more GCs.</span></span> <span data-ttu-id="acf58-163">.NET Framework と言語コンパイラでは可能な限りボックス化を回避しますが、場合によっては、ほとんど予期していない状況でボックス化が行われることがあります。</span><span class="sxs-lookup"><span data-stu-id="acf58-163">The .NET Framework and the language compilers avoid boxing when possible, but sometimes it happens when you least expect it.</span></span>
  
 <span data-ttu-id="acf58-164">PerｆView でボックス化を確認するには、トレースを開き、アプリのプロセス名の下の [GC Heap Alloc Stacks (GC ヒープ割り当てスタック)] を参照します (PerfView はすべてのプロセスについて報告する点に注意してください)。</span><span class="sxs-lookup"><span data-stu-id="acf58-164">To see boxing in PerfView, open a trace and look at GC Heap Alloc Stacks under your app’s process name (remember, PerfView reports on all processes).</span></span> <span data-ttu-id="acf58-165"><xref:System.Int32?displayProperty=nameWithType> や <xref:System.Char?displayProperty=nameWithType> のような型が割り当ての下に表示される場合は、値型をボックス化しています。</span><span class="sxs-lookup"><span data-stu-id="acf58-165">If you see types like <xref:System.Int32?displayProperty=nameWithType> and <xref:System.Char?displayProperty=nameWithType> under allocations, you are boxing value types.</span></span> <span data-ttu-id="acf58-166">このような型のいずれか 1 つを選択すると、型がボックス化されているスタックと関数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="acf58-166">Choosing one of these types will show the stacks and functions in which they are boxed.</span></span>
  
 <span data-ttu-id="acf58-167">**例 1: string メソッドと値型引数**</span><span class="sxs-lookup"><span data-stu-id="acf58-167">**Example 1: string methods and value type arguments**</span></span>  
  
 <span data-ttu-id="acf58-168">このサンプル コードは、過剰であり不要である可能性のあるボックス化を示します。</span><span class="sxs-lookup"><span data-stu-id="acf58-168">This sample code illustrates potentially unnecessary and excessive boxing:</span></span>  
  
```csharp  
public class Logger  
{  
    public static void WriteLine(string s) { /*...*/ }  
}  
  
public class BoxingExample  
{  
    public void Log(int id, int size)  
    {  
        var s = string.Format("{0}:{1}", id, size);  
        Logger.WriteLine(s);  
    }  
}  
```  
  
 <span data-ttu-id="acf58-169">このコードはログ機能を提供するので、アプリは `Log` 関数を頻繁に (数百万回) 呼び出すことがあります。</span><span class="sxs-lookup"><span data-stu-id="acf58-169">This code provides logging functionality, so an app may call the `Log` function frequently, maybe millions of times.</span></span> <span data-ttu-id="acf58-170">ここで問題となるのは、`string.Format` の呼び出しが <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> オーバーロードに解決されることです。</span><span class="sxs-lookup"><span data-stu-id="acf58-170">The problem is that the call to `string.Format` resolves to the <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> overload.</span></span>
  
 <span data-ttu-id="acf58-171">このオーバーロードでは、.NET Framework が `int` 値をオブジェクトにボックス化し、このメソッド呼び出しに渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="acf58-171">This overload requires the .NET Framework to box the `int` values into objects to pass them to this method call.</span></span> <span data-ttu-id="acf58-172">部分的な修正として、`id.ToString()` と `size.ToString()` を呼び出し、すべての文字列 (オブジェクト) を `string.Format` 呼び出しに渡す方法があります。</span><span class="sxs-lookup"><span data-stu-id="acf58-172">A partial fix is to call `id.ToString()` and `size.ToString()` and pass all strings (which are objects) to the `string.Format` call.</span></span> <span data-ttu-id="acf58-173">`ToString()` を呼び出すと文字列が割り当てられますが、この割り当ては `string.Format` 内部で行われます。</span><span class="sxs-lookup"><span data-stu-id="acf58-173">Calling `ToString()` does allocate a string, but that allocation will happen anyway inside `string.Format`.</span></span>
  
 <span data-ttu-id="acf58-174">この基本的な `string.Format` 呼び出しは単なる文字列の連結であると考え、代わりに次のようなコードを記述することがあります。</span><span class="sxs-lookup"><span data-stu-id="acf58-174">You might consider that this basic call to `string.Format` is just string concatenation, so you might write this code instead:</span></span>  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 <span data-ttu-id="acf58-175">ただしこのコード行は <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29> にコンパイルされるため、ボックス化割り当てが行われます。</span><span class="sxs-lookup"><span data-stu-id="acf58-175">However, that line of code introduces a boxing allocation because it compiles to <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span></span> <span data-ttu-id="acf58-176">.NET Framework は `Concat` を呼び出すために文字リテラルをボックス化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acf58-176">The .NET Framework must box the character literal to invoke `Concat`</span></span>  
  
 <span data-ttu-id="acf58-177">**例 1 の修正**</span><span class="sxs-lookup"><span data-stu-id="acf58-177">**Fix for example 1**</span></span>  
  
 <span data-ttu-id="acf58-178">完全な修正策は単純です。</span><span class="sxs-lookup"><span data-stu-id="acf58-178">The complete fix is simple.</span></span> <span data-ttu-id="acf58-179">文字リテラルを文字列リテラルに置き換えるだけです。この場合、文字列は既にオブジェクトであるためボックス化は発生しません。</span><span class="sxs-lookup"><span data-stu-id="acf58-179">Just replace the character literal with a string literal, which incurs no boxing because strings are already objects:</span></span>  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 <span data-ttu-id="acf58-180">**例 2: 列挙型のボックス化**</span><span class="sxs-lookup"><span data-stu-id="acf58-180">**Example 2: enum boxing**</span></span>  
  
 <span data-ttu-id="acf58-181">この例では、特にディクショナリ検索操作で列挙型が頻繁に使用されることが原因で、新しい C# および Visual Basic コンパイラでメモリが大量に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="acf58-181">This example was responsible for a huge amount of allocation in the new C# and Visual Basic compilers due to frequent use of enumeration types, especially in dictionary lookup operations.</span></span>
  
```csharp  
public enum Color  
{  
    Red, Green, Blue  
}  
  
public class BoxingExample  
{  
    private string name;  
    private Color color;  
    public override int GetHashCode()  
    {  
        return name.GetHashCode() ^ color.GetHashCode();  
    }  
}  
```  
  
 <span data-ttu-id="acf58-182">これは、非常に微妙な問題です。</span><span class="sxs-lookup"><span data-stu-id="acf58-182">This problem is very subtle.</span></span> <span data-ttu-id="acf58-183">PerfView ではこれは <xref:System.Enum.GetHashCode> によるボックス化として報告されます。これは、実装上の理由からこのメソッドが列挙型の基になる表現をボックス化するためです。</span><span class="sxs-lookup"><span data-stu-id="acf58-183">PerfView would report this as <xref:System.Enum.GetHashCode> boxing because the method boxes the underlying representation of the enumeration type, for implementation reasons.</span></span> <span data-ttu-id="acf58-184">PerfView で詳しく調べると、<xref:System.Enum.GetHashCode> への呼び出しごとに、ボックス化割り当てが 2 つあることが分かります。</span><span class="sxs-lookup"><span data-stu-id="acf58-184">If you look closely in PerfView, you may see two boxing allocations for each call to <xref:System.Enum.GetHashCode>.</span></span> <span data-ttu-id="acf58-185">コンパイラと .NET Framework がそれぞれ 1 つずつ挿入します。</span><span class="sxs-lookup"><span data-stu-id="acf58-185">The compiler inserts one, and the .NET Framework inserts the other.</span></span>
  
 <span data-ttu-id="acf58-186">**例 2 の修正**</span><span class="sxs-lookup"><span data-stu-id="acf58-186">**Fix for example 2**</span></span>  
  
 <span data-ttu-id="acf58-187">両方の割り当てを容易に回避できます。このためには、<xref:System.Enum.GetHashCode> を呼び出す前に基となる表現にキャストします。</span><span class="sxs-lookup"><span data-stu-id="acf58-187">You can easily avoid both allocations by casting to the underlying representation before calling <xref:System.Enum.GetHashCode>:</span></span>  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 <span data-ttu-id="acf58-188">列挙型に対するボックス化のもう 1 つの一般的な原因は、<xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> メソッドです。</span><span class="sxs-lookup"><span data-stu-id="acf58-188">Another common source of boxing on enumeration types is the <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="acf58-189"><xref:System.Enum.HasFlag%28System.Enum%29> に渡す引数をボックス化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acf58-189">The argument passed to <xref:System.Enum.HasFlag%28System.Enum%29> has to be boxed.</span></span> <span data-ttu-id="acf58-190">ほとんどの場合、<xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> の呼び出しをビット演算テストに置き換える方法のほうが簡単であり、また割り当てが発生しません。</span><span class="sxs-lookup"><span data-stu-id="acf58-190">In most cases, replacing calls to <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> with a bitwise test is simpler and allocation-free.</span></span>
  
 <span data-ttu-id="acf58-191">パフォーマンスに関する 1 番目の事実 (不完全な最適化は行わない) に留意し、このような方法でコード全体を作成し直さないでください。</span><span class="sxs-lookup"><span data-stu-id="acf58-191">Keep the first performance fact in mind (that is, don’t prematurely optimize) and don’t start rewriting all your code in this way.</span></span> <span data-ttu-id="acf58-192">このようなボックス化にかかるコストに注意してください。また、コードの変更は、アプリのプロファイリングとホットスポットの検出の後に行ってください。</span><span class="sxs-lookup"><span data-stu-id="acf58-192">Be aware of these boxing costs, but change your code only after profiling your app and finding the hot spots.</span></span>
  
### <a name="strings"></a><span data-ttu-id="acf58-193">文字列</span><span class="sxs-lookup"><span data-stu-id="acf58-193">Strings</span></span>  

 <span data-ttu-id="acf58-194">文字列操作は、割り当てが発生する最も大きな原因の 1 つであり、PerfView で上位 5 件の割り当てに表示されることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="acf58-194">String manipulations are some of the biggest culprits for allocations, and they often show up in PerfView in the top five allocations.</span></span> <span data-ttu-id="acf58-195">プログラムはシリアル化、JSON、および REST API に文字列を使用します。</span><span class="sxs-lookup"><span data-stu-id="acf58-195">Programs use strings for serialization, JSON, and REST APIs.</span></span> <span data-ttu-id="acf58-196">列挙型を使用できない場合は、システムとの相互運用のためにプログラム定数として文字列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="acf58-196">You can use strings as programmatic constants for interoperating with systems when you can’t use enumeration types.</span></span> <span data-ttu-id="acf58-197">文字列がパフォーマンスに大きく影響していることがプロファイリングによって明らかになる場合は、<xref:System.String> メソッド (<xref:System.String.Format%2A>、<xref:System.String.Concat%2A>、<xref:System.String.Split%2A>、<xref:System.String.Join%2A>、<xref:System.String.Substring%2A> など) の呼び出しを探します。</span><span class="sxs-lookup"><span data-stu-id="acf58-197">When your profiling shows that strings are highly affecting performance, look for calls to <xref:System.String> methods such as <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, and so on.</span></span> <span data-ttu-id="acf58-198"><xref:System.Text.StringBuilder> を使用すると、複数の要素から 1 つの文字列を作成するコストを回避できます。ただし <xref:System.Text.StringBuilder> オブジェクトの割り当てでさえも、管理する必要があるボトルネックとなることがあります。</span><span class="sxs-lookup"><span data-stu-id="acf58-198">Using <xref:System.Text.StringBuilder> to avoid the cost of creating one string from many pieces helps, but even allocating the <xref:System.Text.StringBuilder> object might become a bottleneck that you need to manage.</span></span>
  
 <span data-ttu-id="acf58-199">**例 3: 文字列操作**</span><span class="sxs-lookup"><span data-stu-id="acf58-199">**Example 3: string operations**</span></span>  
  
 <span data-ttu-id="acf58-200">C# コンパイラには、書式設定された XML Doc コメントのテキストを書き込む次のコードがありました。</span><span class="sxs-lookup"><span data-stu-id="acf58-200">The C# compiler had this code that writes the text of a formatted XML doc comment:</span></span>  
  
```csharp  
public void WriteFormattedDocComment(string text)  
{  
    string[] lines = text.Split(new[] { "\r\n", "\r", "\n" },  
                                StringSplitOptions.None);  
    int numLines = lines.Length;  
    bool skipSpace = true;  
    if (lines[0].TrimStart().StartsWith("///"))  
    {  
        for (int i = 0; i < numLines; i++)  
        {  
            string trimmed = lines[i].TrimStart();  
            if (trimmed.Length < 4 || !char.IsWhiteSpace(trimmed[3]))  
            {  
                skipSpace = false;  
                break;  
            }  
        }  
        int substringStart = skipSpace ? 4 : 3;  
        for (int i = 0; i < numLines; i++)  
            WriteLine(lines[i].TrimStart().Substring(substringStart));  
    }  
    else { /* ... */ }  
```  
  
 <span data-ttu-id="acf58-201">このコードによって大量の文字列操作が実行されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="acf58-201">You can see that this code does a lot of string manipulation.</span></span> <span data-ttu-id="acf58-202">このコードはライブラリ メソッドを使用して、行を個々の文字列に分割し、空白をトリミングし、引数 `text` が XML ドキュメント コメントであるかどうかを確認し、行から部分文字列を抽出します。</span><span class="sxs-lookup"><span data-stu-id="acf58-202">The code uses library methods to split lines into separate strings, to trim white space, to check whether the argument `text` is an XML documentation comment, and to extract substrings from lines.</span></span>
  
 <span data-ttu-id="acf58-203">`WriteFormattedDocComment` 内部の最初の行では、`text.Split` が呼び出されるたびに、3 つの要素からなる新しい配列が引数として割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="acf58-203">On the first line inside `WriteFormattedDocComment`, the `text.Split` call allocates a new three-element array as the argument every time it’s called.</span></span> <span data-ttu-id="acf58-204">コンパイラは、この配列を割り当てるコードを毎回出力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acf58-204">The compiler has to emit code to allocate this array each time.</span></span> <span data-ttu-id="acf58-205">これは、<xref:System.String.Split%2A> による配列の格納先で、この配列が他のコードによって変更される可能性があるかどうかをコンパイラが認識できないためです。変更される場合は、後の `WriteFormattedDocComment` 呼び出しに影響があります。</span><span class="sxs-lookup"><span data-stu-id="acf58-205">That’s because the compiler doesn’t know if <xref:System.String.Split%2A> stores the array somewhere where the array might be modified by other code, which would affect later calls to `WriteFormattedDocComment`.</span></span> <span data-ttu-id="acf58-206"><xref:System.String.Split%2A> の呼び出しでは、`text` のすべての行に文字列が割り当てられ、操作を実行するために他のメモリが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="acf58-206">The call to <xref:System.String.Split%2A> also allocates a string for every line in `text` and allocates other memory to perform the operation.</span></span>
  
 <span data-ttu-id="acf58-207">`WriteFormattedDocComment` には <xref:System.String.TrimStart%2A> メソッド呼び出しが 3 つあります。</span><span class="sxs-lookup"><span data-stu-id="acf58-207">`WriteFormattedDocComment` has three calls to the <xref:System.String.TrimStart%2A> method.</span></span> <span data-ttu-id="acf58-208">このうちの 2 つは、処理と割り当てが重複する内側のループ内にあります。</span><span class="sxs-lookup"><span data-stu-id="acf58-208">Two are in inner loops that duplicate work and allocations.</span></span> <span data-ttu-id="acf58-209">さらに悪いことに、引数なしで <xref:System.String.TrimStart%2A> メソッドを呼び出すと、文字列結果の他に空の配列 (`params` パラメーター) が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="acf58-209">To make matters worse, calling the <xref:System.String.TrimStart%2A> method with no arguments allocates an empty array (for the `params` parameter) in addition to the string result.</span></span>
  
 <span data-ttu-id="acf58-210">最後に、<xref:System.String.Substring%2A> メソッドが呼び出されます。このメソッドは通常、新しい文字列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="acf58-210">Lastly, there is a call to the <xref:System.String.Substring%2A> method, which usually allocates a new string.</span></span>
  
 <span data-ttu-id="acf58-211">**例 3 の修正**</span><span class="sxs-lookup"><span data-stu-id="acf58-211">**Fix for example 3**</span></span>  
  
 <span data-ttu-id="acf58-212">前述の例と異なり、小規模な編集ではこれらの割り当てを修正できません。</span><span class="sxs-lookup"><span data-stu-id="acf58-212">Unlike the earlier examples, small edits cannot fix these allocations.</span></span> <span data-ttu-id="acf58-213">さかのぼって問題を調べ、異なる方法で対処する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acf58-213">You need to step back, look at the problem, and approach it differently.</span></span> <span data-ttu-id="acf58-214">たとえば、`WriteFormattedDocComment()` の引数が、このメソッドに必要な情報がすべて含まれている文字列の場合、コードでは複数の部分文字列を割り当てる代わりに、その分多くのインデックス作成処理を実行できます。</span><span class="sxs-lookup"><span data-stu-id="acf58-214">For example, you'll notice that the argument to `WriteFormattedDocComment()` is a string that has all the information that the method needs, so the code could do more indexing instead of allocating many partial strings.</span></span>
  
 <span data-ttu-id="acf58-215">コンパイラのパフォーマンス チームは、このような割り当てに対処するため次のようなコードを使用しました。</span><span class="sxs-lookup"><span data-stu-id="acf58-215">The compiler’s performance team tackled all these allocations with code like this:</span></span>  
  
```csharp  
private int IndexOfFirstNonWhiteSpaceChar(string text, int start) {  
    while (start < text.Length && char.IsWhiteSpace(text[start])) start++;  
    return start;  
}  
  
private bool TrimmedStringStartsWith(string text, int start, string prefix) {  
    start = IndexOfFirstNonWhiteSpaceChar(text, start);  
    int len = text.Length - start;  
    if (len < prefix.Length) return false;  
    for (int i = 0; i < len; i++)  
    {  
        if (prefix[i] != text[start + i]) return false;  
    }  
    return true;  
}  
  
// etc...
```  
  
 <span data-ttu-id="acf58-216">`WriteFormattedDocComment()` の最初のバージョンでは、配列、複数の部分文字列、トリミングされた部分文字列と空の `params` 配列が割り当てられました。</span><span class="sxs-lookup"><span data-stu-id="acf58-216">The first version of `WriteFormattedDocComment()` allocated an array, several substrings, and a trimmed substring along with an empty `params` array.</span></span> <span data-ttu-id="acf58-217">また、"///" の有無が確認されました。</span><span class="sxs-lookup"><span data-stu-id="acf58-217">It also checked for "///".</span></span> <span data-ttu-id="acf58-218">修正後のコードは、インデックス作成のみを使用し、割り当てを行いません。</span><span class="sxs-lookup"><span data-stu-id="acf58-218">The revised code uses only indexing and allocates nothing.</span></span> <span data-ttu-id="acf58-219">空白以外の最初の文字を検出し、文字を 1 つずつ調べて文字列が "///" で始まっているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="acf58-219">It finds the first character that is not white space, and then checks character by character to see if the string starts with "///".</span></span> <span data-ttu-id="acf58-220">この新しいコードでは <xref:System.String.TrimStart%2A> の代わりに `IndexOfFirstNonWhiteSpaceChar` が使用され、(指定された開始インデックスより後で) 空白以外の文字が含まれる最初のインデックスが返されます。</span><span class="sxs-lookup"><span data-stu-id="acf58-220">The new code uses `IndexOfFirstNonWhiteSpaceChar` instead of <xref:System.String.TrimStart%2A> to return the first index (after a specified start index) where a non-white-space character occurs.</span></span> <span data-ttu-id="acf58-221">この修正は完全ではありませんが、完全な解決策として類似の修正を適用する方法がわかります。</span><span class="sxs-lookup"><span data-stu-id="acf58-221">The fix is not complete, but you can see how to apply similar fixes for a complete solution.</span></span> <span data-ttu-id="acf58-222">コード全体でこの方法を適用することで、`WriteFormattedDocComment()` 内のすべての割り当てを削除できます。</span><span class="sxs-lookup"><span data-stu-id="acf58-222">By applying this approach throughout the code, you can remove all allocations in `WriteFormattedDocComment()`.</span></span>
  
 <span data-ttu-id="acf58-223">**例 4: StringBuilder**</span><span class="sxs-lookup"><span data-stu-id="acf58-223">**Example 4: StringBuilder**</span></span>  
  
 <span data-ttu-id="acf58-224">この例は <xref:System.Text.StringBuilder> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="acf58-224">This example uses a <xref:System.Text.StringBuilder> object.</span></span> <span data-ttu-id="acf58-225">次の関数は、ジェネリック型の完全な型名を生成します。</span><span class="sxs-lookup"><span data-stu-id="acf58-225">The following function generates a full type name for generic types:</span></span>  
  
```csharp  
public class Example  
{  
    // Constructs a name like "SomeType<T1, T2, T3>"  
    public string GenerateFullTypeName(string name, int arity)  
    {  
        StringBuilder sb = new StringBuilder();  
  
        sb.Append(name);  
        if (arity != 0)  
        {  
            sb.Append("<");  
            for (int i = 1; i < arity; i++)  
            {  
                sb.Append("T"); sb.Append(i.ToString()); sb.Append(", ");  
            }  
            sb.Append("T"); sb.Append(i.ToString()); sb.Append(">");  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
 <span data-ttu-id="acf58-226">新しい <xref:System.Text.StringBuilder> インスタンスを作成する行に注目します。</span><span class="sxs-lookup"><span data-stu-id="acf58-226">The focus is on the line that creates a new <xref:System.Text.StringBuilder> instance.</span></span> <span data-ttu-id="acf58-227">このコードが原因で、`sb.ToString()` の割り当てと <xref:System.Text.StringBuilder> 実装内での内部割り当てが発生しますが、文字列の結果が必要な場合はこれらの割り当てを制御できません。</span><span class="sxs-lookup"><span data-stu-id="acf58-227">The code causes an allocation for `sb.ToString()` and internal allocations within the <xref:System.Text.StringBuilder> implementation, but you cannot control those allocations if you want the string result.</span></span>
  
 <span data-ttu-id="acf58-228">**例 4 の修正**</span><span class="sxs-lookup"><span data-stu-id="acf58-228">**Fix for example 4**</span></span>  
  
 <span data-ttu-id="acf58-229">`StringBuilder` オブジェクトの割り当てを修正するには、このオブジェクトをキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="acf58-229">To fix the `StringBuilder` object allocation, cache the  object.</span></span> <span data-ttu-id="acf58-230">破棄される可能性がある 1 つのインスタンスをキャッシュするだけでも、パフォーマンスが大幅に改善されることがあります。</span><span class="sxs-lookup"><span data-stu-id="acf58-230">Even caching a single instance that might get thrown away can improve performance significantly.</span></span> <span data-ttu-id="acf58-231">これは関数の新しい実装であり、新しい最初の行と最後の行を除くすべてのコードを省略しています。</span><span class="sxs-lookup"><span data-stu-id="acf58-231">This is the function’s new implementation, omitting all the code except for the new first and last lines:</span></span>  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 <span data-ttu-id="acf58-232">重要なのは、新しい `AcquireBuilder()` および `GetStringAndReleaseBuilder()` 関数です。</span><span class="sxs-lookup"><span data-stu-id="acf58-232">The key parts are the new `AcquireBuilder()` and `GetStringAndReleaseBuilder()` functions:</span></span>  
  
```csharp  
[ThreadStatic]  
private static StringBuilder cachedStringBuilder;  
  
private static StringBuilder AcquireBuilder()  
{  
    StringBuilder result = cachedStringBuilder;  
    if (result == null)  
    {  
        return new StringBuilder();  
    }  
    result.Clear();  
    cachedStringBuilder = null;  
    return result;  
}  
  
private static string GetStringAndReleaseBuilder(StringBuilder sb)  
{  
    string result = sb.ToString();  
    cachedStringBuilder = sb;  
    return result;  
}  
```  
  
 <span data-ttu-id="acf58-233">新しいコンパイラはスレッド処理を使用するため、このような実装は thread-static フィールド (<xref:System.ThreadStaticAttribute> 属性) を使用して <xref:System.Text.StringBuilder> をキャッシュします。このため `ThreadStatic` 宣言を使用せずに済ませることができます。</span><span class="sxs-lookup"><span data-stu-id="acf58-233">Because the new compilers use threading, these implementations use a thread-static field (<xref:System.ThreadStaticAttribute> attribute) to cache the <xref:System.Text.StringBuilder>, and you likely can forgo the `ThreadStatic` declaration.</span></span> <span data-ttu-id="acf58-234">thread-static フィールドには、このコードを実行する各スレッドの一意の値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="acf58-234">The thread-static field holds a unique value for each thread that executes this code.</span></span>
  
 <span data-ttu-id="acf58-235">`AcquireBuilder()` は、キャッシュされた <xref:System.Text.StringBuilder> インスタンスがある場合はそのインスタンスを返します。その後、そのインスタンスをクリアしてフィールドまたはキャッシュを Null に設定します。</span><span class="sxs-lookup"><span data-stu-id="acf58-235">`AcquireBuilder()` returns the cached <xref:System.Text.StringBuilder> instance if there is one, after clearing it and setting the field or cache to null.</span></span> <span data-ttu-id="acf58-236">それ以外の場合は、`AcquireBuilder()` は新規インスタンスを作成して返し、フィールドまたはキャッシュは Null に設定したままにします。</span><span class="sxs-lookup"><span data-stu-id="acf58-236">Otherwise, `AcquireBuilder()` creates a new instance and returns it, leaving the field or cache set to null.</span></span>
  
 <span data-ttu-id="acf58-237"><xref:System.Text.StringBuilder> の処理が完了したら、`GetStringAndReleaseBuilder()` を呼び出して文字列結果を取得し、フィールドまたはキャッシュに <xref:System.Text.StringBuilder> インスタンスを保存し、結果を返します。</span><span class="sxs-lookup"><span data-stu-id="acf58-237">When you’re done with <xref:System.Text.StringBuilder> , you call `GetStringAndReleaseBuilder()` to get the string result, save the <xref:System.Text.StringBuilder> instance in the field or cache, and then return the result.</span></span> <span data-ttu-id="acf58-238">実行時にこのコードに再び入り、複数の <xref:System.Text.StringBuilder> オブジェクトが作成される可能性があります (ただし複数オブジェクトが作成されることはほとんどありません)。</span><span class="sxs-lookup"><span data-stu-id="acf58-238">It is possible for execution to re-enter this code and to create multiple <xref:System.Text.StringBuilder> objects (although that rarely happens).</span></span> <span data-ttu-id="acf58-239">このコードは最後に解放された <xref:System.Text.StringBuilder> インスタンスだけを、後で使用できるように保存します。</span><span class="sxs-lookup"><span data-stu-id="acf58-239">The code saves only the last released <xref:System.Text.StringBuilder> instance for later use.</span></span> <span data-ttu-id="acf58-240">この単純なキャッシュ対策によって、新しいコンパイラでの割り当てが大幅に減少しました。</span><span class="sxs-lookup"><span data-stu-id="acf58-240">This simple caching strategy significantly reduced allocations in the new compilers.</span></span> <span data-ttu-id="acf58-241">.NET Framework と MSBuild ("MSBuild") の一部では、パフォーマンス改善のために類似の手法が使用されています。</span><span class="sxs-lookup"><span data-stu-id="acf58-241">Parts of the .NET Framework and MSBuild ("MSBuild") use a similar technique to improve performance.</span></span>
  
 <span data-ttu-id="acf58-242">サイズ制限があるため、この単純なキャッシュ対策は適切なキャッシュ設計に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="acf58-242">This simple caching strategy adheres to good cache design because it has a size cap.</span></span> <span data-ttu-id="acf58-243">ただし、元のバージョンよりもコードが増えたため、保守コストも増加します。</span><span class="sxs-lookup"><span data-stu-id="acf58-243">However, there is more code now than in the original, which means more maintenance costs.</span></span> <span data-ttu-id="acf58-244">このキャッシュ対策を取り入れるのは、パフォーマンスの問題を検出し、PerfView で <xref:System.Text.StringBuilder> 割り当てがその問題の大きな原因であることが示されている場合だけにしてください。</span><span class="sxs-lookup"><span data-stu-id="acf58-244">You should adopt the caching strategy only if you’ve found a performance problem, and PerfView has shown that <xref:System.Text.StringBuilder> allocations are a significant contributor.</span></span>
  
### <a name="linq-and-lambdas"></a><span data-ttu-id="acf58-245">LINQ とラムダ</span><span class="sxs-lookup"><span data-stu-id="acf58-245">LINQ and lambdas</span></span>  

<span data-ttu-id="acf58-246">ラムダ式と組み合わせた統合言語クエリ (LINQ) は、生産性向上機能の一例です。</span><span class="sxs-lookup"><span data-stu-id="acf58-246">Language-Integrated Query (LINQ), in conjunction with lambda expressions, is an example of a productivity feature.</span></span> <span data-ttu-id="acf58-247">ただし、その使用は、時間の経過と共にパフォーマンスに大きな影響を与えるおそれがあり、コードの再作成が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="acf58-247">However, its use may have a significant impact on performance over time, and you might find you need to rewrite your code.</span></span>
  
 <span data-ttu-id="acf58-248">**例 5: ラムダ、List\<T>、および IEnumerable\<T>**</span><span class="sxs-lookup"><span data-stu-id="acf58-248">**Example 5: Lambdas, List\<T>, and IEnumerable\<T>**</span></span>  
  
 <span data-ttu-id="acf58-249">この例では、[LINQ と関数スタイルのコード](/archive/blogs/charlie/anders-hejlsberg-on-linq-and-functional-programming)を利用し、与えられた名前文字列で、コンパイラのモデルで記号を探します。</span><span class="sxs-lookup"><span data-stu-id="acf58-249">This example uses [LINQ and functional style code](/archive/blogs/charlie/anders-hejlsberg-on-linq-and-functional-programming) to find a symbol in the compiler’s model, given a name string:</span></span>  
  
```csharp  
class Symbol {  
    public string Name { get; private set; }  
    /*...*/  
}  
  
class Compiler {  
    private List<Symbol> symbols;  
    public Symbol FindMatchingSymbol(string name)  
    {  
        return symbols.FirstOrDefault(s => s.Name == name);  
    }  
}  
```  
  
 <span data-ttu-id="acf58-250">新しいコンパイラと、このコンパイラ上に構築された IDE 機能は `FindMatchingSymbol()` をかなり頻繁に呼び出します。この関数を記述する 1 行のコードには、割り当てがいくつか隠されています。</span><span class="sxs-lookup"><span data-stu-id="acf58-250">The new compiler and the IDE experiences built on it call `FindMatchingSymbol()` very frequently, and there are several hidden allocations in this function’s single line of code.</span></span> <span data-ttu-id="acf58-251">このような割り当てを調べるには、まず関数を記述する 1 行のコードを 2 行に分割します。</span><span class="sxs-lookup"><span data-stu-id="acf58-251">To examine those allocations, first split the function’s single line of code into two lines:</span></span>  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 <span data-ttu-id="acf58-252">最初の行で、[ラムダ式  がローカル変数 `name` を](../../csharp/language-reference/operators/lambda-expressions.md) `s => s.Name == name` [閉じ込めます](/archive/blogs/ericlippert/what-are-closures)。</span><span class="sxs-lookup"><span data-stu-id="acf58-252">In the first line, the [lambda expression](../../csharp/language-reference/operators/lambda-expressions.md) `s => s.Name == name` [closes over](/archive/blogs/ericlippert/what-are-closures) the local variable `name`.</span></span> <span data-ttu-id="acf58-253">つまり、このコードは `predicate` が保持している[デリゲート](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type)にオブジェクトを割り当てる以外に、`name` の値をキャプチャする環境を保持する静的クラスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="acf58-253">This means that in addition to allocating an object for the [delegate](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) that `predicate` holds, the code allocates a static class to hold the environment that captures the value of `name`.</span></span> <span data-ttu-id="acf58-254">コンパイラは次のようなコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="acf58-254">The compiler generates code like the following:</span></span>  
  
```csharp  
// Compiler-generated class to hold environment state for lambda  
private class Lambda1Environment  
{  
    public string capturedName;  
    public bool Evaluate(Symbol s)  
    {  
        return s.Name == this.capturedName;  
    }  
}  
  
// Expanded Func<Symbol, bool> predicate = s => s.Name == name;  
Lambda1Environment l = new Lambda1Environment() { capturedName = name };  
var predicate = new Func<Symbol, bool>(l.Evaluate);  
```  
  
 <span data-ttu-id="acf58-255">ここでは 2 つの `new` 割り当て (環境クラスに対する割り当てとデリゲートに対する割り当て) が明示的に行われます。</span><span class="sxs-lookup"><span data-stu-id="acf58-255">The two `new` allocations (one for the environment class and one for the delegate) are explicit now.</span></span>
  
 <span data-ttu-id="acf58-256">次に `FirstOrDefault`. の呼び出しを調べます。</span><span class="sxs-lookup"><span data-stu-id="acf58-256">Now look at the call to `FirstOrDefault`.</span></span> <span data-ttu-id="acf58-257"><xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 型に対するこの拡張メソッドでも割り当てが発生します。</span><span class="sxs-lookup"><span data-stu-id="acf58-257">This extension method on the <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> type incurs an allocation too.</span></span> <span data-ttu-id="acf58-258">`FirstOrDefault` が <xref:System.Collections.Generic.IEnumerable%601> オブジェクトを最初の引数として受け取るため、この呼び出しを拡張して次のコードのようにできます (このコードは説明のため単純化されています)。</span><span class="sxs-lookup"><span data-stu-id="acf58-258">Because `FirstOrDefault` takes an <xref:System.Collections.Generic.IEnumerable%601> object as its first argument, you can expand the call to the following code (simplified a bit for discussion):</span></span>  
  
```csharp  
// Expanded return symbols.FirstOrDefault(predicate) ...
     IEnumerable<Symbol> enumerable = symbols;  
     IEnumerator<Symbol> enumerator = enumerable.GetEnumerator();  
     while(enumerator.MoveNext())  
     {  
         if (predicate(enumerator.Current))  
             return enumerator.Current;  
     }  
     return default(Symbol);  
```  
  
 <span data-ttu-id="acf58-259">`symbols` 変数の型は <xref:System.Collections.Generic.List%601> です。</span><span class="sxs-lookup"><span data-stu-id="acf58-259">The `symbols` variable has type <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="acf58-260"><xref:System.Collections.Generic.List%601> コレクション型は <xref:System.Collections.Generic.IEnumerable%601> を実装し、<xref:System.Collections.Generic.IEnumerator%601> が <xref:System.Collections.Generic.List%601>を使用して実装する列挙子 (`struct` インターフェイス) を適切に定義します。</span><span class="sxs-lookup"><span data-stu-id="acf58-260">The <xref:System.Collections.Generic.List%601> collection type implements <xref:System.Collections.Generic.IEnumerable%601> and cleverly defines an enumerator (<xref:System.Collections.Generic.IEnumerator%601> interface) that <xref:System.Collections.Generic.List%601> implements with a `struct`.</span></span> <span data-ttu-id="acf58-261">クラスの代わりに構造体を使用すると、通常ヒープ割り当てが回避されます。ヒープ割り当ては、ガベージ コレクションのパフォーマンスに影響することがあります。</span><span class="sxs-lookup"><span data-stu-id="acf58-261">Using a structure instead of a class means that you usually avoid any heap allocations, which, in turn, can affect garbage collection performance.</span></span> <span data-ttu-id="acf58-262">通常、列挙子は言語の `foreach` ループで使用されます。このループは、コール スタックで返される列挙子構造を使用します。</span><span class="sxs-lookup"><span data-stu-id="acf58-262">Enumerators are typically used with the language’s `foreach` loop, which uses the enumerator structure as it is returned on the call stack.</span></span> <span data-ttu-id="acf58-263">オブジェクトのスペースを確保するためにコール スタック ポインターをインクリメントしても、GC はヒープ割り当てのような影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="acf58-263">Incrementing the call stack pointer to make room for an object does not affect GC the way a heap allocation does.</span></span>
  
 <span data-ttu-id="acf58-264">拡張 `FirstOrDefault` 呼び出しの場合、このコードは`GetEnumerator()` に対して <xref:System.Collections.Generic.IEnumerable%601> を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="acf58-264">In the case of the expanded `FirstOrDefault` call, the code needs to call `GetEnumerator()` on an <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="acf58-265">`symbols` を `enumerable` 型の `IEnumerable<Symbol>` 変数に割り当てると、実際のオブジェクトが <xref:System.Collections.Generic.List%601> であるという情報が失われます。.</span><span class="sxs-lookup"><span data-stu-id="acf58-265">Assigning `symbols` to the `enumerable` variable of type `IEnumerable<Symbol>` loses the information that the actual object is a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="acf58-266">つまり、コードが `enumerable.GetEnumerator()` で列挙子をフェッチするときには、.NET Framework は返される構造体をボックス化し、`enumerator` 変数に割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="acf58-266">This means that when the code fetches the enumerator with `enumerable.GetEnumerator()`, the .NET Framework has to box the returned structure to assign it to the `enumerator` variable.</span></span>
  
 <span data-ttu-id="acf58-267">**例 5 の修正**</span><span class="sxs-lookup"><span data-stu-id="acf58-267">**Fix for example 5**</span></span>  
  
 <span data-ttu-id="acf58-268">この修正では、`FindMatchingSymbol` を次のように書き直し、1 つのコード行を 6 行のコード行に置き換えます。この 6 行のコードは簡潔であり、読んで理解しやすく、また保守が容易です。</span><span class="sxs-lookup"><span data-stu-id="acf58-268">The fix is to rewrite `FindMatchingSymbol` as follows, replacing its single line of code with six lines of code that are still concise, easy to read and understand, and easy to maintain:</span></span>  
  
```csharp  
public Symbol FindMatchingSymbol(string name)  
    {  
        foreach (Symbol s in symbols)  
        {  
            if (s.Name == name)  
                return s;  
        }  
        return null;  
    }  
```  
  
 <span data-ttu-id="acf58-269">このコードは LINQ 拡張メソッド、ラムダ、列挙子を使用しないため、割り当ての問題は発生しません。</span><span class="sxs-lookup"><span data-stu-id="acf58-269">This code doesn’t use LINQ extension methods, lambdas, or enumerators, and it incurs no allocations.</span></span> <span data-ttu-id="acf58-270">`symbols` コレクションが <xref:System.Collections.Generic.List%601> であることをコンパイラが認識でき、結果列挙子 (構造体) を適切な型のローカル変数にバインドしてボックス化を回避できるため、割り当てが発生しません。</span><span class="sxs-lookup"><span data-stu-id="acf58-270">There are no allocations because the compiler can see that the `symbols` collection is a <xref:System.Collections.Generic.List%601> and can bind the resulting enumerator (a structure) to a local variable with the right type to avoid boxing.</span></span> <span data-ttu-id="acf58-271">この関数の元のバージョンは、C# の高い性能と .NET Framework の生産性を示す最適な例でした。</span><span class="sxs-lookup"><span data-stu-id="acf58-271">The original version of this function was a great example of the expressive power of C# and the productivity of the .NET Framework.</span></span> <span data-ttu-id="acf58-272">この新しく効率性が高いバージョンは、保守のために複雑なコードを追加することなく、このような品質を保持します。</span><span class="sxs-lookup"><span data-stu-id="acf58-272">This new and more efficient version preserves those qualities without adding any complex code to maintain.</span></span>
  
### <a name="async-method-caching"></a><span data-ttu-id="acf58-273">非同期のメソッド キャッシュ</span><span class="sxs-lookup"><span data-stu-id="acf58-273">Async method caching</span></span>  

<span data-ttu-id="acf58-274">次の例は、キャッシュされた結果を[非同期](../../csharp/programming-guide/concepts/async/index.md)メソッドで使用しようとすると発生する一般的な問題を示します。</span><span class="sxs-lookup"><span data-stu-id="acf58-274">The next example shows a common problem when you try to use cached results in an [async](../../csharp/programming-guide/concepts/async/index.md) method.</span></span>
  
 <span data-ttu-id="acf58-275">**例 6: 非同期メソッドでのキャッシュ**</span><span class="sxs-lookup"><span data-stu-id="acf58-275">**Example 6: caching in async methods**</span></span>  
  
 <span data-ttu-id="acf58-276">新しい C# および Visual Basic コンパイラ上に構築された Visual Studio IDE 機能は、構文ツリーを頻繁にフェッチします。コンパイラは、Visual Studio の応答性を維持するために非同期を使用します。</span><span class="sxs-lookup"><span data-stu-id="acf58-276">The Visual Studio IDE features built on the new C# and Visual Basic compilers frequently fetch syntax trees, and the compilers use async when doing so to keep Visual Studio responsive.</span></span> <span data-ttu-id="acf58-277">構文ツリーを取得する目的で作成するコードの最初のバージョンを次に示します。</span><span class="sxs-lookup"><span data-stu-id="acf58-277">Here’s the first version of the code you might write to get a syntax tree:</span></span>  
  
```csharp  
class SyntaxTree { /*...*/ }  
  
class Parser { /*...*/  
    public SyntaxTree Syntax { get; }  
    public Task ParseSourceCode() { /*...*/ }  
}  
  
class Compilation { /*...*/  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 <span data-ttu-id="acf58-278">`GetSyntaxTreeAsync()` を呼び出すと `Parser` がインスタンス化され、コードが解析され、<xref:System.Threading.Tasks.Task> オブジェクトが返されることがわかります。`Task<SyntaxTree>`.</span><span class="sxs-lookup"><span data-stu-id="acf58-278">You can see that calling `GetSyntaxTreeAsync()` instantiates a `Parser`, parses the code, and then returns a <xref:System.Threading.Tasks.Task> object, `Task<SyntaxTree>`.</span></span> <span data-ttu-id="acf58-279">コストがかかる部分は、`Parser` インスタンスの割り当てとコードの解析です。</span><span class="sxs-lookup"><span data-stu-id="acf58-279">The expensive part is allocating the `Parser` instance and parsing the code.</span></span> <span data-ttu-id="acf58-280">この関数は <xref:System.Threading.Tasks.Task> を返すので、呼び出し元はユーザー入力に応答するために解析作業を待ち、UI スレッドを解放できます。</span><span class="sxs-lookup"><span data-stu-id="acf58-280">The function returns a <xref:System.Threading.Tasks.Task> so that callers can await the parsing work and free the UI thread to be responsive to user input.</span></span>
  
 <span data-ttu-id="acf58-281">Visual Studio の複数の機能が同じ構文ツリーを取得しようとすることがあるため、解析結果をキャッシュする次のコードを記述すると、時間と割り当てを節約できます。</span><span class="sxs-lookup"><span data-stu-id="acf58-281">Several Visual Studio features might try to get the same syntax tree, so you might write the following code to cache the parsing result to save time and allocations.</span></span> <span data-ttu-id="acf58-282">ただしこのコードでは割り当てが発生します。</span><span class="sxs-lookup"><span data-stu-id="acf58-282">However, this code incurs an allocation:</span></span>  
  
```csharp  
class Compilation { /*...*/  
  
    private SyntaxTree cachedResult;  
  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        if (this.cachedResult == null)  
        {  
            var parser = new Parser(); // allocation  
            await parser.ParseSourceCode(); // expensive  
            this.cachedResult = parser.Syntax;  
        }  
        return this.cachedResult;  
    }  
}  
```  
  
 <span data-ttu-id="acf58-283">キャッシュに関する新しいコードには `SyntaxTree` という名前の `cachedResult` フィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="acf58-283">You see that the new code with caching has a `SyntaxTree` field named `cachedResult`.</span></span> <span data-ttu-id="acf58-284">このフィールドが Null の場合、`GetSyntaxTreeAsync()` が処理を行い、キャッシュに結果が保存されます。</span><span class="sxs-lookup"><span data-stu-id="acf58-284">When this field is null, `GetSyntaxTreeAsync()` does the work and saves the result in the cache.</span></span> <span data-ttu-id="acf58-285">`GetSyntaxTreeAsync()` は `SyntaxTree` オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="acf58-285">`GetSyntaxTreeAsync()` returns the `SyntaxTree` object.</span></span> <span data-ttu-id="acf58-286">ここで問題となるのは、`async` 型の `Task<SyntaxTree>` 関数があり、`SyntaxTree` 型の値を返す場合、コンパイラが、(`Task<SyntaxTree>.FromResult()` を使用して) 結果を保持するために Task を割り当てるコードを出力することです。</span><span class="sxs-lookup"><span data-stu-id="acf58-286">The problem is that when you have an `async` function of type `Task<SyntaxTree>`, and you return a value of type `SyntaxTree`, the compiler emits code to allocate a Task to hold the result (by using `Task<SyntaxTree>.FromResult()`).</span></span> <span data-ttu-id="acf58-287">Task は完了済みとしてマークされ、結果が即時に利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="acf58-287">The Task is marked as completed, and the result is immediately available.</span></span> <span data-ttu-id="acf58-288">新しいコンパイラのコードでは、既に完了している <xref:System.Threading.Tasks.Task> オブジェクトが頻繁に発生するため、このような割り当てを修正すると応答性が著しく向上することがよくありました。</span><span class="sxs-lookup"><span data-stu-id="acf58-288">In the code for the new compilers, <xref:System.Threading.Tasks.Task> objects that were already completed occurred so often that fixing these allocations improved responsiveness noticeably.</span></span>
  
 <span data-ttu-id="acf58-289">**例 6 の修正**</span><span class="sxs-lookup"><span data-stu-id="acf58-289">**Fix for example 6**</span></span>  
  
 <span data-ttu-id="acf58-290">完了した <xref:System.Threading.Tasks.Task> 割り当てを削除するには、完了した結果と共に Task オブジェクトをキャッシュできます。</span><span class="sxs-lookup"><span data-stu-id="acf58-290">To remove the completed <xref:System.Threading.Tasks.Task> allocation, you can cache the Task object with the completed result:</span></span>  
  
```csharp  
class Compilation { /*...*/  
  
    private Task<SyntaxTree> cachedResult;  
  
    public Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        return this.cachedResult ??
               (this.cachedResult = GetSyntaxTreeUncachedAsync());  
    }  
  
    private async Task<SyntaxTree> GetSyntaxTreeUncachedAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 <span data-ttu-id="acf58-291">このコードは `cachedResult` の型を `Task<SyntaxTree>` に変更し、`async` からの元のコードを保持する `GetSyntaxTreeAsync()` ヘルパー関数を採用しています。</span><span class="sxs-lookup"><span data-stu-id="acf58-291">This code changes the type of `cachedResult` to `Task<SyntaxTree>` and employs an `async` helper function that holds the original code from `GetSyntaxTreeAsync()`.</span></span> <span data-ttu-id="acf58-292">`GetSyntaxTreeAsync()` は [null 合体演算子](../../csharp/language-reference/operators/null-coalescing-operator.md)を使用して、`cachedResult` が null でない場合にそれを返します。</span><span class="sxs-lookup"><span data-stu-id="acf58-292">`GetSyntaxTreeAsync()` now uses the [null coalescing operator](../../csharp/language-reference/operators/null-coalescing-operator.md) to return `cachedResult` if it isn't null.</span></span> <span data-ttu-id="acf58-293">`cachedResult` が null の場合、`GetSyntaxTreeAsync()` は `GetSyntaxTreeUncachedAsync()` を呼び出し、結果をキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="acf58-293">If `cachedResult` is null, then `GetSyntaxTreeAsync()` calls `GetSyntaxTreeUncachedAsync()` and caches the result.</span></span> <span data-ttu-id="acf58-294">`GetSyntaxTreeAsync()` は、通常のコードのようには、`GetSyntaxTreeUncachedAsync()` 呼び出しを待たないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="acf58-294">Notice that `GetSyntaxTreeAsync()` doesn’t await the call to `GetSyntaxTreeUncachedAsync()` as the code would normally.</span></span> <span data-ttu-id="acf58-295">待機しないということは、`GetSyntaxTreeUncachedAsync()` がその <xref:System.Threading.Tasks.Task> オブジェクトを返す場合、`GetSyntaxTreeAsync()` が即時に<xref:System.Threading.Tasks.Task> を返すことになります。</span><span class="sxs-lookup"><span data-stu-id="acf58-295">Not using await means that when `GetSyntaxTreeUncachedAsync()` returns its <xref:System.Threading.Tasks.Task> object, `GetSyntaxTreeAsync()` immediately returns the <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="acf58-296">この時点で、キャッシュされた結果は <xref:System.Threading.Tasks.Task> であるため、キャシュされた結果を返すための割り当ては行われません。</span><span class="sxs-lookup"><span data-stu-id="acf58-296">Now, the cached result is a <xref:System.Threading.Tasks.Task>, so there are no allocations to return the cached result.</span></span>
  
### <a name="additional-considerations"></a><span data-ttu-id="acf58-297">その他の注意点</span><span class="sxs-lookup"><span data-stu-id="acf58-297">Additional considerations</span></span>  

 <span data-ttu-id="acf58-298">大きなアプリまたは大量データを処理するアプリで発生する可能性がある問題に関するその他の点を次に説明します。</span><span class="sxs-lookup"><span data-stu-id="acf58-298">Here are a few more points about potential problems in large apps or apps that process a lot of data.</span></span>
  
 <span data-ttu-id="acf58-299">**辞書**</span><span class="sxs-lookup"><span data-stu-id="acf58-299">**Dictionaries**</span></span>  
  
 <span data-ttu-id="acf58-300">ディクショナリは多くのプログラムで随所に使用されており、非常に便利で本質的に効率的です。</span><span class="sxs-lookup"><span data-stu-id="acf58-300">Dictionaries are used ubiquitously in many programs, and though dictionaries are very convenient and inherently efficient.</span></span> <span data-ttu-id="acf58-301">ただし、使い方が不適切なことがよくあります。</span><span class="sxs-lookup"><span data-stu-id="acf58-301">However, they’re often used inappropriately.</span></span> <span data-ttu-id="acf58-302">Visual Studio と新しいコンパイラでは、分析から、多くのディクショナリでは含まれている要素が 1つだけであるか、何も含まれていないことが判明しました。</span><span class="sxs-lookup"><span data-stu-id="acf58-302">In Visual Studio and the new compilers, analysis shows that many of the dictionaries contained a single element or were empty.</span></span> <span data-ttu-id="acf58-303">x86 マシンでは、空の <xref:System.Collections.Generic.Dictionary%602> には 10 個のフィールドがあり、ヒープで 48 バイトを占有しています。</span><span class="sxs-lookup"><span data-stu-id="acf58-303">An empty <xref:System.Collections.Generic.Dictionary%602> has ten fields and occupies 48 bytes on the heap on an x86 machine.</span></span> <span data-ttu-id="acf58-304">ディクショナリが役立つのは、一定時間内の検索のマッピングまたは関連データ構造体が必要な場合です。</span><span class="sxs-lookup"><span data-stu-id="acf58-304">Dictionaries are great when you need a mapping or associative data structure with constant-time lookup.</span></span> <span data-ttu-id="acf58-305">ただし要素の数が少ない場合は、ディクショナリを使用するとスペースを無駄に使用することになります。</span><span class="sxs-lookup"><span data-stu-id="acf58-305">However, when you have only a few elements, you waste a lot of space by using a dictionary.</span></span> <span data-ttu-id="acf58-306">代わりに、たとえば `List<KeyValuePair\<K,V>>` の繰り返し検索も、同じ速度で行えます。</span><span class="sxs-lookup"><span data-stu-id="acf58-306">Instead, for example, you could iteratively look through a `List<KeyValuePair\<K,V>>`, just as fast.</span></span> <span data-ttu-id="acf58-307">ディクショナリにデータを読み込み、ディクショナリから読み取るだけのためにディクショナリを使用する場合 (非常に一般的なパターン)、N(log(N)) ルックアップで並べ替えた配列を使用すると、使用している要素の数に応じて、ほぼ同程度の速度を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="acf58-307">If you use a dictionary only to load it with data and then read from it (a very common pattern), using a sorted array with an N(log(N)) lookup might be nearly as fast, depending on the number of elements you're using.</span></span>
  
 <span data-ttu-id="acf58-308">**クラスと構造体**</span><span class="sxs-lookup"><span data-stu-id="acf58-308">**Classes vs. structures**</span></span>  
  
 <span data-ttu-id="acf58-309">クラスと構造体は、アプリを調整する上で従来型のスペース/時間のトレードオフを生じさせます。</span><span class="sxs-lookup"><span data-stu-id="acf58-309">In a way, classes and structures provide a classic space/time tradeoff for tuning your apps.</span></span> <span data-ttu-id="acf58-310">フィールドが含まれていないクラスでは、x86 マシンで 12 バイトのオーバーヘッドが生じますが、クラス インスタンスを指すポインタをだけを受け取るので、クラスの受け渡しにかかるコストは低くなります。</span><span class="sxs-lookup"><span data-stu-id="acf58-310">Classes incur 12 bytes of overhead on an x86 machine even if they have no fields, but they are inexpensive to pass around because it only takes a pointer to refer to a class instance.</span></span> <span data-ttu-id="acf58-311">ボックス化されていない構造体の場合、ヒープ割り当ては行われませんが、大きな構造体を関数の引数または戻り値として渡すと、構造体のすべてのデータ メンバーをアトミックにコピーするために、CPU 時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="acf58-311">Structures incur no heap allocations if they aren’t boxed, but when you pass large structures as function arguments or return values, it takes CPU time to atomically copy all the data members of the structures.</span></span> <span data-ttu-id="acf58-312">構造体を返すプロパティ呼び出しの繰り返しに注意し、過剰なデータ コピーを行わないようにするため、プロパティの値をローカル変数にキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="acf58-312">Watch out for repeated calls to properties that return structures, and cache the property’s value in a local variable to avoid excessive data copying.</span></span>
  
 <span data-ttu-id="acf58-313">**キャッシュ**</span><span class="sxs-lookup"><span data-stu-id="acf58-313">**Caches**</span></span>  
  
 <span data-ttu-id="acf58-314">一般的なパフォーマンス向上のためのテクニックは、結果をキャッシュすることです。</span><span class="sxs-lookup"><span data-stu-id="acf58-314">A common performance trick is to cache results.</span></span> <span data-ttu-id="acf58-315">ただし、サイズ制限や破棄ポリシーが設定されていないキャッシュはメモリ リークとなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="acf58-315">However, a cache without a size cap or disposal policy can be a memory leak.</span></span> <span data-ttu-id="acf58-316">大量のデータを処理するときに、キャッシュに大量のメモリを維持すると、ガベージ コレクションによって、キャッシュしたルックアップによるメリットがオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="acf58-316">When processing large amounts of data, if you hold on to a lot of memory in caches, you can cause garbage collection to override the benefits of your cached lookups.</span></span>
  
 <span data-ttu-id="acf58-317">この記事では、特に大規模システムや大量のデータを処理するシステムにおいて、アプリの応答性に影響する可能性があるパフォーマンスのボトルネックの症状にどのように注意したらよいかを説明しました。</span><span class="sxs-lookup"><span data-stu-id="acf58-317">In this article, we discussed how you should be aware of performance bottleneck symptoms that can affect your app's responsiveness, especially for large systems or systems that process a large amount of data.</span></span> <span data-ttu-id="acf58-318">一般的な問題には、ボックス化、文字列操作、LINQ およびラムダ、非同期方式でのキャッシュ、サイズ制限または破棄ポリシーのないキャッシュ、不適切なディクショナリの使用、構造体の受け渡しなどがあります。</span><span class="sxs-lookup"><span data-stu-id="acf58-318">Common culprits include boxing, string manipulations, LINQ and lambda, caching in async methods, caching without a size limit or disposal policy, inappropriate use of dictionaries, and passing around structures.</span></span> <span data-ttu-id="acf58-319">アプリの調整に関する 4 つの事実に注意してください。</span><span class="sxs-lookup"><span data-stu-id="acf58-319">Keep in mind the four facts for tuning your apps:</span></span>  
  
- <span data-ttu-id="acf58-320">不完全な最適化は行わない - 生産的に作業し、問題を見つけたらアプリを調整します。</span><span class="sxs-lookup"><span data-stu-id="acf58-320">Don’t prematurely optimize – be productive and tune your app when you spot problems.</span></span>
  
- <span data-ttu-id="acf58-321">プロファイルは嘘をつかない - 測定していないのであれば、推測にすぎません。</span><span class="sxs-lookup"><span data-stu-id="acf58-321">Profiles don’t lie – you’re guessing if you’re not measuring.</span></span>
  
- <span data-ttu-id="acf58-322">優れたツールには大きな効果がある - PerfView をダウンロードして試してみてください。</span><span class="sxs-lookup"><span data-stu-id="acf58-322">Good tools make all the difference – download PerfView and try it out.</span></span>
  
- <span data-ttu-id="acf58-323">すべては割り当てで決まる - コンパイラ プラットフォーム チームは、新しいコンパイラのパフォーマンスの向上のため、この分野に最も多くの時間をかけました。</span><span class="sxs-lookup"><span data-stu-id="acf58-323">It's all about allocations – that is where the compiler platform team spent most of their time improving the performance of the new compilers.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="acf58-324">関連項目</span><span class="sxs-lookup"><span data-stu-id="acf58-324">See also</span></span>

- [<span data-ttu-id="acf58-325">このトピックのプレゼンテーション動画</span><span class="sxs-lookup"><span data-stu-id="acf58-325">Video of presentation of this topic</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)
- [<span data-ttu-id="acf58-326">パフォーマンス プロファイリングのビギナーズ ガイド</span><span class="sxs-lookup"><span data-stu-id="acf58-326">Beginners Guide to Performance Profiling</span></span>](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [<span data-ttu-id="acf58-327">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="acf58-327">Performance</span></span>](index.md)
- <span data-ttu-id="acf58-328">[.NET のパフォーマンスに関するヒント](/previous-versions/dotnet/articles/ms973839(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="acf58-328">[.NET Performance Tips](/previous-versions/dotnet/articles/ms973839(v=msdn.10))</span></span>
- [<span data-ttu-id="acf58-329">Channel 9 PerfView チュートリアル</span><span class="sxs-lookup"><span data-stu-id="acf58-329">Channel 9 PerfView tutorials</span></span>](https://channel9.msdn.com/Series/PerfView-Tutorial)
- [<span data-ttu-id="acf58-330">.NET Compiler Platform SDK</span><span class="sxs-lookup"><span data-stu-id="acf58-330">The .NET Compiler Platform SDK</span></span>](../../csharp/roslyn-sdk/index.md)
- [<span data-ttu-id="acf58-331">GitHub の dotnet/roslyn リポジトリ</span><span class="sxs-lookup"><span data-stu-id="acf58-331">dotnet/roslyn repo on GitHub</span></span>](https://github.com/dotnet/roslyn)
