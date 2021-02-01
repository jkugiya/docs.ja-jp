---
title: ファイナライザー - C# プログラミング ガイド
description: ガベージ コレクターによってクラス インスタンスが収集されている場合は、C# のファイナライザー (デストラクターとも呼ばれます) によって、最終的に必要なすべてのクリーンアップが実行されます。
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: a2f4f5f9342d5df1f9fa741c86cfe6f8b1d88bd1
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899062"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="6c63c-103">ファイナライザー (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="6c63c-103">Finalizers (C# Programming Guide)</span></span>

<span data-ttu-id="6c63c-104">ガベージ コレクターによってクラス インスタンスが収集されている場合は、ファイナライザー (**デストラクター** とも呼ばれます) を使用して、最終的に必要なすべてのクリーンアップが実行されます。</span><span class="sxs-lookup"><span data-stu-id="6c63c-104">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c63c-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="6c63c-105">Remarks</span></span>  
  
- <span data-ttu-id="6c63c-106">ファイナライザーは、構造体には定義できません。</span><span class="sxs-lookup"><span data-stu-id="6c63c-106">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="6c63c-107">クラスでだけ使用します。</span><span class="sxs-lookup"><span data-stu-id="6c63c-107">They are only used with classes.</span></span>  
  
- <span data-ttu-id="6c63c-108">クラスで使用できるファイナライザーは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="6c63c-108">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="6c63c-109">ファイナライザーを継承またはオーバーロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="6c63c-109">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="6c63c-110">ファイナライザーを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="6c63c-110">Finalizers cannot be called.</span></span> <span data-ttu-id="6c63c-111">デストラクターは自動的に起動されます。</span><span class="sxs-lookup"><span data-stu-id="6c63c-111">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="6c63c-112">ファイナライザーは修飾子を取らず、パラメーターはありません。</span><span class="sxs-lookup"><span data-stu-id="6c63c-112">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="6c63c-113">たとえば、次はクラス `Car` に対するファイナライザーの宣言です。</span><span class="sxs-lookup"><span data-stu-id="6c63c-113">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](snippets/destructors/Program.cs#2)]

<span data-ttu-id="6c63c-114">ファイナライザーは、式本体の定義として実行することもできます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6c63c-114">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="6c63c-115">ファイナライザーは、オブジェクトの基底クラスで <xref:System.Object.Finalize%2A> を暗黙的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6c63c-115">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="6c63c-116">そのため、ファイナライザーの呼び出しは、暗黙的に次のコードに解釈されます。</span><span class="sxs-lookup"><span data-stu-id="6c63c-116">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
```csharp  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 <span data-ttu-id="6c63c-117">この設計が意味することは、派生が最も多いクラスから派生が最も少ないクラスまで、継承チェーンのすべてのインスタンスに対して、`Finalize` メソッドが再帰的に呼び出されるということです。</span><span class="sxs-lookup"><span data-stu-id="6c63c-117">This design means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6c63c-118">空のファイナライザーは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="6c63c-118">Empty finalizers should not be used.</span></span> <span data-ttu-id="6c63c-119">ファイナライザーがクラスに存在するときは、エントリが `Finalize` キューで作成されます。</span><span class="sxs-lookup"><span data-stu-id="6c63c-119">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="6c63c-120">ファイナライザーを呼び出すと、ガベージ コレクターが呼び出され、このキューを処理します。</span><span class="sxs-lookup"><span data-stu-id="6c63c-120">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="6c63c-121">ファイナライザーが空の場合、パフォーマンスを不必要に低下させるだけです。</span><span class="sxs-lookup"><span data-stu-id="6c63c-121">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="6c63c-122">ファイナライザーがいつ呼び出されるかは、プログラマは制御できません。それはガベージ コレクターによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="6c63c-122">The programmer has no control over when the finalizer is called; the garbage collector decides when to call it.</span></span> <span data-ttu-id="6c63c-123">ガベージ コレクターは、アプリケーションが使用していないオブジェクトをチェックします。</span><span class="sxs-lookup"><span data-stu-id="6c63c-123">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="6c63c-124">終了処理が可能なオブジェクトと考えられる場合、ファイナライザー (存在する場合) を呼び出し、オブジェクトの格納に使用されているメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="6c63c-124">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span>

 <span data-ttu-id="6c63c-125">(.NET Core アプリケーションではなく) .NET Framework アプリケーションでは、プログラムが存在する場合、ファイナライザーも呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6c63c-125">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span>
  
 <span data-ttu-id="6c63c-126"><xref:System.GC.Collect%2A> を呼び出すことによって、ガベージ コレクションを強制的に行うことができます。ただし、パフォーマンスに問題が発生する可能性があるため、通常はこの呼び出しを避けます。</span><span class="sxs-lookup"><span data-stu-id="6c63c-126">It's possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this call should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="6c63c-127">ファイナライザーを使ったリソースの解放</span><span class="sxs-lookup"><span data-stu-id="6c63c-127">Using finalizers to release resources</span></span>  

 <span data-ttu-id="6c63c-128">一般に C# の場合、ガベージ コレクションでランタイムをターゲットにしない言語のような大量のメモリ管理は開発者側で必要になりません。</span><span class="sxs-lookup"><span data-stu-id="6c63c-128">In general, C# does not require as much memory management on the part of the developer as languages that don't target a runtime with garbage collection.</span></span> <span data-ttu-id="6c63c-129">.NET のガベージ コレクターが、オブジェクトに対するメモリの割り当てと解放を暗黙的に管理するからです。</span><span class="sxs-lookup"><span data-stu-id="6c63c-129">This is because the .NET garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="6c63c-130">ただし、ウィンドウ、ファイル、ネットワーク接続などのアンマネージ リソースをアプリケーションでカプセル化する場合は、ファイナライザーを使ってこれらのリソースを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c63c-130">However, when your application encapsulates unmanaged resources, such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="6c63c-131">終了処理が可能なオブジェクトの場合、ガベージ コレクターはそのオブジェクトの `Finalize` メソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6c63c-131">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="6c63c-132">リソースの明示的な解放</span><span class="sxs-lookup"><span data-stu-id="6c63c-132">Explicit release of resources</span></span>  

 <span data-ttu-id="6c63c-133">アプリケーションで高額な外部リソースを使用している場合、ガベージ コレクターがオブジェクトを解放する前にリソースを明示的に解放する手段を用意することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="6c63c-133">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="6c63c-134">リソースを解放するには、オブジェクトに必要なクリーンアップを実行する <xref:System.IDisposable> インターフェイスから `Dispose` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="6c63c-134">To release the resource, implement a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="6c63c-135">これによって、アプリケーションのパフォーマンスを大幅に向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="6c63c-135">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="6c63c-136">このようにリソースを明示的に制御する場合でも、ファイナライザーは、`Dispose` メソッドの呼び出しが失敗したときにリソースをクリーンアップするための安全装置になります。</span><span class="sxs-lookup"><span data-stu-id="6c63c-136">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method fails.</span></span>  
  
 <span data-ttu-id="6c63c-137">リソースのクリーンアップの詳細については、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c63c-137">For more information about cleaning up resources, see the following articles:</span></span>  
  
- [<span data-ttu-id="6c63c-138">アンマネージ リソースのクリーンアップ</span><span class="sxs-lookup"><span data-stu-id="6c63c-138">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
- [<span data-ttu-id="6c63c-139">Dispose メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="6c63c-139">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="6c63c-140">using ステートメント</span><span class="sxs-lookup"><span data-stu-id="6c63c-140">using Statement</span></span>](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="6c63c-141">例</span><span class="sxs-lookup"><span data-stu-id="6c63c-141">Example</span></span>  

 <span data-ttu-id="6c63c-142">次の例では、継承チェーンを形成する 3 つのクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="6c63c-142">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="6c63c-143">`First` が基底クラスであり、`Second` は `First` から派生し、`Third` は `Second` から派生します。</span><span class="sxs-lookup"><span data-stu-id="6c63c-143">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="6c63c-144">3 つのクラスのいずれにもファイナライザーがあります。</span><span class="sxs-lookup"><span data-stu-id="6c63c-144">All three have finalizers.</span></span> <span data-ttu-id="6c63c-145">`Main` では、派生が最も多いクラスのインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6c63c-145">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="6c63c-146">プログラムを実行すると、3 つのクラスのファイナライザーが派生が最も多いクラスから派生が最も少ないクラスの順に自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6c63c-146">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[Destructors#1](snippets/destructors/Program.cs#1)]
  
## <a name="c-language-specification"></a><span data-ttu-id="6c63c-147">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="6c63c-147">C# language specification</span></span>  

<span data-ttu-id="6c63c-148">詳細については、「[C# 言語仕様](/dotnet/csharp/language-reference/language-specification/introduction)」の [デストラクタ―](~/_csharplang/spec/classes.md#destructors)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c63c-148">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6c63c-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c63c-149">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="6c63c-150">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="6c63c-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6c63c-151">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="6c63c-151">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="6c63c-152">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="6c63c-152">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
