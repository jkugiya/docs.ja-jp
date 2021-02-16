---
description: '詳細情報: オブジェクトの有効期間:オブジェクトの作成と破棄 (Visual Basic)'
title: オブジェクトの有効期間:オブジェクトの作成と破棄
ms.date: 07/20/2015
f1_keywords:
- vb.Constructor
helpviewer_keywords:
- destructors, object lifetime
- Sub Finalize destructor
- objects [Visual Basic], destroying
- lifetime [Visual Basic], objects
- Sub New constructor, object lifetime
- Finalize method [Visual Basic], object lifetime
- objects [Visual Basic], creating
- Class_Terminate
- Dispose method [Visual Basic], object lifetime
- Class_Initialize
- object creation [Visual Basic], object lifetime
- parameterized constructors
- objects [Visual Basic], lifetime
- objects [Visual Basic], garbage collection
- constructors [Visual Basic], object lifetime
- Sub Dispose destructor
- garbage collection [Visual Basic], Visual Basic
ms.assetid: f1ee8458-b156-44e0-9a8a-5dd171648cd8
ms.openlocfilehash: 424a5619ea50d9da9bf069488ce7cac16527efbe
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100438828"
---
# <a name="object-lifetime-how-objects-are-created-and-destroyed-visual-basic"></a><span data-ttu-id="c4ce0-103">オブジェクトの有効期間:オブジェクトの作成と破棄 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4ce0-103">Object Lifetime: How Objects Are Created and Destroyed (Visual Basic)</span></span>

<span data-ttu-id="c4ce0-104">クラスのインスタンス (オブジェクト) を作成するには、`New` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-104">An instance of a class, an object, is created by using the `New` keyword.</span></span> <span data-ttu-id="c4ce0-105">新しいオブジェクトを使用する前に、多くの場合、そのオブジェクトに対して初期化タスクを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-105">Initialization tasks often must be performed on new objects before they are used.</span></span> <span data-ttu-id="c4ce0-106">一般的な初期化タスクとして、ファイルを開く、データベースに接続する、レジストリ キーの値を読み取る、などがあります。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-106">Common initialization tasks include opening files, connecting to databases, and reading values of registry keys.</span></span> <span data-ttu-id="c4ce0-107">Visual Basic では、*コンストラクター* (初期化を制御できる特殊なメソッド) と呼ばれるプロシージャを使用して、新しいオブジェクトの初期化を制御します。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-107">Visual Basic controls the initialization of new objects using procedures called *constructors* (special methods that allow control over initialization).</span></span>

<span data-ttu-id="c4ce0-108">スコープを離れたオブジェクトは、共通言語ランタイム (CLR) によって解放されます。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-108">After an object leaves scope, it is released by the common language runtime (CLR).</span></span> <span data-ttu-id="c4ce0-109">Visual Basic では、*デストラクター* と呼ばれるプロシージャを使用して、システム リソースの解放を制御します。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-109">Visual Basic controls the release of system resources using procedures called *destructors*.</span></span> <span data-ttu-id="c4ce0-110">コンストラクターとデストラクターは共に、堅牢で予測可能なクラス ライブラリの作成をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-110">Together, constructors and destructors support the creation of robust and predictable class libraries.</span></span>

## <a name="using-constructors-and-destructors"></a><span data-ttu-id="c4ce0-111">コンストラクターとデストラクターの使用</span><span class="sxs-lookup"><span data-stu-id="c4ce0-111">Using Constructors and Destructors</span></span>

<span data-ttu-id="c4ce0-112">コンストラクターとデストラクターは、オブジェクトの作成および破棄を制御します。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-112">Constructors and destructors control the creation and destruction of objects.</span></span> <span data-ttu-id="c4ce0-113">Visual Basic の `Sub New` と `Sub Finalize` の各プロシージャが、オブジェクトを初期化および破棄します。これらは、Visual Basic 6.0 とそれ以前のバージョンで使用される `Class_Initialize` と `Class_Terminate` の各メソッドに置き換わるものです。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-113">The `Sub New` and `Sub Finalize` procedures in Visual Basic initialize and destroy objects; they replace the `Class_Initialize` and `Class_Terminate` methods used in Visual Basic 6.0 and earlier versions.</span></span>

### <a name="sub-new"></a><span data-ttu-id="c4ce0-114">Sub New</span><span class="sxs-lookup"><span data-stu-id="c4ce0-114">Sub New</span></span>

<span data-ttu-id="c4ce0-115">`Sub New` コンストラクターは、クラスの作成時に 1 回だけ実行できます。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-115">The `Sub New` constructor can run only once when a class is created.</span></span> <span data-ttu-id="c4ce0-116">同じクラスまたは派生クラスから別のコンストラクターの最初のコード行以外の任意の場所で、明示的に呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-116">It cannot be called explicitly anywhere other than in the first line of code of another constructor from either the same class or from a derived class.</span></span> <span data-ttu-id="c4ce0-117">また、`Sub New` メソッド内のコードは常に、クラス内の他のすべてのコードより先に実行されます。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-117">Furthermore, the code in the `Sub New` method always runs before any other code in a class.</span></span> <span data-ttu-id="c4ce0-118">Visual Basic では、クラスの `Sub New` プロシージャを明示的に定義していない場合、実行時に `Sub New` コンストラクターが暗黙的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-118">Visual Basic implicitly creates a `Sub New` constructor at run time if you do not explicitly define a `Sub New` procedure for a class.</span></span>

<span data-ttu-id="c4ce0-119">クラスのコンストラクターを作成するには、クラス定義の任意の場所に `Sub New` という名前のプロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-119">To create a constructor for a class, create a procedure named `Sub New` anywhere in the class definition.</span></span> <span data-ttu-id="c4ce0-120">パラメーター化されたコンストラクターを作成するには、次のコードに示すように、他のプロシージャの引数を指定する場合と同じく、`Sub New` に引数の名前とデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-120">To create a parameterized constructor, specify the names and data types of arguments to `Sub New` just as you would specify arguments for any other procedure, as in the following code:</span></span>

[!code-vb[VbVbalrOOP#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#42)]

<span data-ttu-id="c4ce0-121">コンストラクターは、次のコードに示すように、頻繁にオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-121">Constructors are frequently overloaded, as in the following code:</span></span>

[!code-vb[VbVbalrOOP#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#116)]

<span data-ttu-id="c4ce0-122">別のクラスから派生したクラスを定義するときは、基本クラスにパラメーターを受け取らないアクセス可能なコンストラクターがある場合を除き、コンストラクターの 1 行目で基本クラスのコンストラクターを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-122">When you define a class derived from another class, the first line of a constructor must be a call to the constructor of the base class, unless the base class has an accessible constructor that takes no parameters.</span></span> <span data-ttu-id="c4ce0-123">たとえば、上記のコンストラクターを含む基本クラスの呼び出しは、`MyBase.New(s)` になります。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-123">A call to the base class that contains the above constructor, for example, would be `MyBase.New(s)`.</span></span> <span data-ttu-id="c4ce0-124">それ以外の場合、`MyBase.New` は省略可能であり、Visual Basic ランタイムによって暗黙的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-124">Otherwise, `MyBase.New` is optional, and the Visual Basic runtime calls it implicitly.</span></span>

<span data-ttu-id="c4ce0-125">親オブジェクトのコンストラクターを呼び出すコードを記述した後、追加の初期化コードを `Sub New` プロシージャに追加できます。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-125">After you write the code to call the parent object's constructor, you can add any additional initialization code to the `Sub New` procedure.</span></span> <span data-ttu-id="c4ce0-126">`Sub New`は、パラメーター化されたコンストラクターとして呼び出されたときには、引数を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-126">`Sub New` can accept arguments when called as a parameterized constructor.</span></span> <span data-ttu-id="c4ce0-127">このようなパラメーターは、コンストラクターを呼び出すプロシージャ (たとえば、`Dim AnObject As New ThisClass(X)`) から渡されます。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-127">These parameters are passed from the procedure calling the constructor, for example, `Dim AnObject As New ThisClass(X)`.</span></span>

### <a name="sub-finalize"></a><span data-ttu-id="c4ce0-128">Sub Finalize</span><span class="sxs-lookup"><span data-stu-id="c4ce0-128">Sub Finalize</span></span>

<span data-ttu-id="c4ce0-129">オブジェクトを解放する前に、CLR は `Finalize` プロシージャを定義するオブジェクトの `Sub Finalize` メソッドを自動的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-129">Before releasing objects, the CLR automatically calls the `Finalize` method for objects that define a `Sub Finalize` procedure.</span></span> <span data-ttu-id="c4ce0-130">`Finalize` メソッドには、ファイルを閉じて状態情報を保存するコードなど、オブジェクトを破棄する直前に実行する必要があるコードを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-130">The `Finalize` method can contain code that needs to execute just before an object is destroyed, such as code for closing files and saving state information.</span></span> <span data-ttu-id="c4ce0-131">`Sub Finalize` の実行には若干のパフォーマンス低下が伴うため、オブジェクトを明示的に解放する必要がある場合にのみ、`Sub Finalize` メソッドを定義してください。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-131">There is a slight performance penalty for executing `Sub Finalize`, so you should define a `Sub Finalize` method only when you need to release objects explicitly.</span></span>

> [!NOTE]
> <span data-ttu-id="c4ce0-132">CLR のガベージ コレクターは、*アンマネージ オブジェクト*、つまりオペレーティング システムが CLR 環境の外部で直接実行するオブジェクトは破棄しません (できません)。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-132">The garbage collector in the CLR does not (and cannot) dispose of *unmanaged objects*, objects that the operating system executes directly, outside the CLR environment.</span></span> <span data-ttu-id="c4ce0-133">これは、管理されていないオブジェクトごとに異なる方法で破棄する必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-133">This is because different unmanaged objects must be disposed of in different ways.</span></span> <span data-ttu-id="c4ce0-134">その情報は、管理されていないオブジェクトに直接には関連付けられません。オブジェクトのドキュメントに記載する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-134">That information is not directly associated with the unmanaged object; it must be found in the documentation for the object.</span></span> <span data-ttu-id="c4ce0-135">管理されていないオブジェクトを使用するクラスでは、`Finalize` メソッド内でそのオブジェクトを破棄する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-135">A class that uses unmanaged objects must dispose of them in its `Finalize` method.</span></span>

<span data-ttu-id="c4ce0-136">`Finalize` デストラクターは、所属先のクラスまたは派生クラスからのみ呼び出し可能な保護されたメソッドです。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-136">The `Finalize` destructor is a protected method that can be called only from the class it belongs to, or from derived classes.</span></span> <span data-ttu-id="c4ce0-137">`Finalize` はオブジェクトが破棄されるときに自動的に呼び出されるため、派生クラスの `Finalize` 実装の外部から `Finalize` を明示的に呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-137">The system calls `Finalize` automatically when an object is destroyed, so you should not explicitly call `Finalize` from outside of a derived class's `Finalize` implementation.</span></span>

<span data-ttu-id="c4ce0-138">オブジェクトが nothing に設定されるとすぐに実行される `Class_Terminate` と異なり、通常、オブジェクトがスコープを失ってから Visual Basic が `Finalize` デストラクターを呼び出すまでに遅延が発生します。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-138">Unlike `Class_Terminate`, which executes as soon as an object is set to nothing, there is usually a delay between when an object loses scope and when Visual Basic calls the `Finalize` destructor.</span></span> <span data-ttu-id="c4ce0-139">Visual Basic .NET では、2 つ目の種類のデストラクターとして <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> が使用可能であり、いつでも明示的に呼び出してすぐにリソースを解放できます。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-139">Visual Basic .NET allows for a second kind of destructor, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>, which can be explicitly called at any time to immediately release resources.</span></span>

> [!NOTE]
> <span data-ttu-id="c4ce0-140">`Finalize` デストラクターからは例外をスローしません。これは、その例外をアプリケーションで処理できないために、アプリケーションが異常終了する可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-140">A `Finalize` destructor should not throw exceptions, because they cannot be handled by the application and can cause the application to terminate.</span></span>

### <a name="how-new-and-finalize-methods-work-in-a-class-hierarchy"></a><span data-ttu-id="c4ce0-141">クラス階層での New メソッドおよび Finalize メソッドの動作</span><span class="sxs-lookup"><span data-stu-id="c4ce0-141">How New and Finalize Methods Work in a Class Hierarchy</span></span>

<span data-ttu-id="c4ce0-142">クラスのインスタンスが作成されると、そのオブジェクト内に `New` という名前のプロシージャが存在する場合、共通言語ランタイム (CLR) はそのプロシージャを実行しようとします。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-142">Whenever an instance of a class is created, the common language runtime (CLR) attempts to execute a procedure named `New`, if it exists in that object.</span></span> <span data-ttu-id="c4ce0-143">`New` は、オブジェクトの他のコードを実行する前に新しいオブジェクトを初期化するために使用される、`constructor`と呼ばれる種類のプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-143">`New` is a type of procedure called a `constructor` that is used to initialize new objects before any other code in an object executes.</span></span> <span data-ttu-id="c4ce0-144">`New` コンストラクターを使用すると、ファイルを開く、データベースに接続する、変数を初期化するなど、オブジェクトを使用する前に実行する必要があるタスクを管理できます。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-144">A `New` constructor can be used to open files, connect to databases, initialize variables, and take care of any other tasks that need to be done before an object can be used.</span></span>

<span data-ttu-id="c4ce0-145">派生クラスのインスタンスが作成されると、まず基本クラスの `Sub New` コンストラクターが実行され、続いて派生クラスのコンストラクターが実行されます。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-145">When an instance of a derived class is created, the `Sub New` constructor of the base class executes first, followed by constructors in derived classes.</span></span> <span data-ttu-id="c4ce0-146">このように動作するのは、`Sub New` コンストラクターの最初のコード行では、`MyBase.New()` 構文を使用して、クラス階層の自身のすぐ上位にあるクラスのコンストラクターを呼び出すためです。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-146">This happens because the first line of code in a `Sub New` constructor uses the syntax `MyBase.New()`to call the constructor of the class immediately above itself in the class hierarchy.</span></span> <span data-ttu-id="c4ce0-147">`Sub New` コンストラクターはその後、基本クラスのコンストラクターに到達するまで、クラス階層のクラスごとに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-147">The `Sub New` constructor is then called for each class in the class hierarchy until the constructor for the base class is reached.</span></span> <span data-ttu-id="c4ce0-148">その時点で、基本クラスのコンストラクター内のコードが実行され、続いてすべての派生クラスの各コンストラクター内のコードが実行され、最後にほとんどの派生クラス内のコードが実行されます。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-148">At that point, the code in the constructor for the base class executes, followed by the code in each constructor in all derived classes and the code in the most derived classes is executed last.</span></span>

![クラス階層のコンストラクターと継承を示すスクリーンショット。](./media/object-lifetime-how-objects-are-created-and-destroyed/subnew-constructor-inheritance.gif)

<span data-ttu-id="c4ce0-150">オブジェクトが不要になると、CLR はメモリを解放する前にそのオブジェクトに対して <xref:System.Object.Finalize%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-150">When an object is no longer needed, the CLR calls the <xref:System.Object.Finalize%2A> method for that object before freeing its memory.</span></span> <span data-ttu-id="c4ce0-151"><xref:System.Object.Finalize%2A> メソッドは、状態情報の保存やファイルおよびデータベース接続の終了などのクリーンアップ タスク、およびオブジェクトを解放する前に行う必要があるその他のタスクを実行するために、`destructor`を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-151">The <xref:System.Object.Finalize%2A> method is called a `destructor` because it performs cleanup tasks, such as saving state information, closing files and connections to databases, and other tasks that must be done before releasing the object.</span></span>

![Finalize メソッドのデストラクターを示すスクリーンショット。](./media/object-lifetime-how-objects-are-created-and-destroyed/finalize-method-destructor.gif)

## <a name="idisposable-interface"></a><span data-ttu-id="c4ce0-153">IDisposable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c4ce0-153">IDisposable Interface</span></span>

<span data-ttu-id="c4ce0-154">クラスのインスタンスは、多くの場合、Windows ハンドルやデータベース接続など、CLR では管理されないリソースを制御します。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-154">Class instances often control resources not managed by the CLR, such as Windows handles and database connections.</span></span> <span data-ttu-id="c4ce0-155">これらのリソースは、オブジェクトがガベージ コレクターによって破棄されるときに解放されるように、クラスの `Finalize` メソッドで破棄する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-155">These resources must be disposed of in the `Finalize` method of the class, so that they will be released when the object is destroyed by the garbage collector.</span></span> <span data-ttu-id="c4ce0-156">ただし、ガベージ コレクターは、CLR でより多くの空きメモリが必要な場合にのみ、オブジェクトを破棄します。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-156">However, the garbage collector destroys objects only when the CLR requires more free memory.</span></span> <span data-ttu-id="c4ce0-157">つまり、オブジェクトがスコープ外になるまで、リソースが解放されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-157">This means that the resources may not be released until long after the object goes out of scope.</span></span>

<span data-ttu-id="c4ce0-158">ガベージ コレクションを補足するために、クラスが <xref:System.IDisposable> インターフェイスを実装している場合には、システム リソースを積極的に管理するためのメカニズムをクラスに用意することができます。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-158">To supplement garbage collection, your classes can provide a mechanism to actively manage system resources if they implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="c4ce0-159"><xref:System.IDisposable> には <xref:System.IDisposable.Dispose%2A> という 1 つのメソッドがあり、クライアントはオブジェクトの使用を終了するときにこのメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-159"><xref:System.IDisposable> has one method, <xref:System.IDisposable.Dispose%2A>, which clients should call when they finish using an object.</span></span> <span data-ttu-id="c4ce0-160"><xref:System.IDisposable.Dispose%2A> メソッドを使用して、すぐにリソースを解放し、ファイルおよびデータベース接続の終了などのタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-160">You can use the <xref:System.IDisposable.Dispose%2A> method to immediately release resources and perform tasks such as closing files and database connections.</span></span> <span data-ttu-id="c4ce0-161">`Finalize` デストラクターとは異なり、<xref:System.IDisposable.Dispose%2A> メソッドは自動的には呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-161">Unlike the `Finalize` destructor, the <xref:System.IDisposable.Dispose%2A> method is not called automatically.</span></span> <span data-ttu-id="c4ce0-162">リソースをすぐに解放するときには、クラスのクライアントが <xref:System.IDisposable.Dispose%2A> を明示的に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-162">Clients of a class must explicitly call <xref:System.IDisposable.Dispose%2A> when you want to immediately release resources.</span></span>

### <a name="implementing-idisposable"></a><span data-ttu-id="c4ce0-163">IDisposable の実装</span><span class="sxs-lookup"><span data-stu-id="c4ce0-163">Implementing IDisposable</span></span>

<span data-ttu-id="c4ce0-164"><xref:System.IDisposable> インターフェイスを実装するクラスには、次のコード セクションを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-164">A class that implements the <xref:System.IDisposable> interface should include these sections of code:</span></span>

- <span data-ttu-id="c4ce0-165">オブジェクトが破棄されているかどうかを追跡するためのフィールド。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-165">A field for keeping track of whether the object has been disposed:</span></span>

  ```vb
  Protected disposed As Boolean = False
  ```

- <span data-ttu-id="c4ce0-166">クラスのリソースを解放する <xref:System.IDisposable.Dispose%2A> のオーバーロード。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-166">An overload of the <xref:System.IDisposable.Dispose%2A> that frees the class's resources.</span></span> <span data-ttu-id="c4ce0-167">このメソッドは、基本クラスの <xref:System.IDisposable.Dispose%2A> メソッドおよび `Finalize` メソッドによって呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-167">This method should be called by the <xref:System.IDisposable.Dispose%2A> and `Finalize` methods of the base class:</span></span>

  ```vb
  Protected Overridable Sub Dispose(ByVal disposing As Boolean)
      If Not Me.disposed Then
          If disposing Then
              ' Insert code to free managed resources.
          End If
          ' Insert code to free unmanaged resources.
      End If
      Me.disposed = True
  End Sub
  ```

- <span data-ttu-id="c4ce0-168">次のコードのみを含む <xref:System.IDisposable.Dispose%2A> の実装。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-168">An implementation of <xref:System.IDisposable.Dispose%2A> that contains only the following code:</span></span>

  ```vb
  Public Sub Dispose() Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)
  End Sub
  ```

- <span data-ttu-id="c4ce0-169">次のコードのみを含む `Finalize` メソッドのオーバーライド。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-169">An override of the `Finalize` method that contains only the following code:</span></span>

  ```vb
  Protected Overrides Sub Finalize()
      Dispose(False)
      MyBase.Finalize()
  End Sub
  ```

### <a name="deriving-from-a-class-that-implements-idisposable"></a><span data-ttu-id="c4ce0-170">IDisposable を実装するクラスからの派生</span><span class="sxs-lookup"><span data-stu-id="c4ce0-170">Deriving from a Class that Implements IDisposable</span></span>

<span data-ttu-id="c4ce0-171"><xref:System.IDisposable> インターフェイスを実装する基本クラスから派生したクラスでは、破棄する必要がある追加のリソースを使用しない限り、基本メソッドをオーバーライドする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-171">A class that derives from a base class that implements the <xref:System.IDisposable> interface does not need to override any of the base methods unless it uses additional resources that need to be disposed.</span></span> <span data-ttu-id="c4ce0-172">その場合、派生クラスでは、派生クラスのリソースを破棄するように基本クラスの `Dispose(disposing)` メソッドをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-172">In that situation, the derived class should override the base class's `Dispose(disposing)` method to dispose of the derived class's resources.</span></span> <span data-ttu-id="c4ce0-173">このオーバーライドでは、基本クラスの `Dispose(disposing)` メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-173">This override must call the base class's `Dispose(disposing)` method.</span></span>

```vb
Protected Overrides Sub Dispose(ByVal disposing As Boolean)
    If Not Me.disposed Then
        If disposing Then
            ' Insert code to free managed resources.
        End If
        ' Insert code to free unmanaged resources.
    End If
    MyBase.Dispose(disposing)
End Sub
```

<span data-ttu-id="c4ce0-174">派生クラスでは、基本クラスの <xref:System.IDisposable.Dispose%2A> メソッドおよび `Finalize` メソッドをオーバーライドする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-174">A derived class should not override the base class's <xref:System.IDisposable.Dispose%2A> and `Finalize` methods.</span></span> <span data-ttu-id="c4ce0-175">これらのメソッドが派生クラスのインスタンスから呼び出されると、基本クラスでのこれらのメソッドの実装によって、派生クラスでの `Dispose(disposing)` メソッドのオーバーライドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-175">When those methods are called from an instance of the derived class, the base class's implementation of those methods call the derived class's override of the `Dispose(disposing)` method.</span></span>

## <a name="garbage-collection-and-the-finalize-destructor"></a><span data-ttu-id="c4ce0-176">ガベージ コレクションと Finalize デストラクター</span><span class="sxs-lookup"><span data-stu-id="c4ce0-176">Garbage Collection and the Finalize Destructor</span></span>

<span data-ttu-id="c4ce0-177">.NET Framework は、*参照トレース ガベージ コレクション* システムを使用して、未使用のリソースを定期的に解放します。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-177">The .NET Framework uses the *reference-tracing garbage collection* system to periodically release unused resources.</span></span> <span data-ttu-id="c4ce0-178">Visual Basic 6.0 とそれ以前のバージョンでは、*参照カウント* と呼ばれる別のシステムを使用して、リソースを管理していました。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-178">Visual Basic 6.0 and earlier versions used a different system called *reference counting* to manage resources.</span></span> <span data-ttu-id="c4ce0-179">どちらのシステムも同じ機能を自動的に実行しますが、いくつかの重要な違いがあります。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-179">Although both systems perform the same function automatically, there are a few important differences.</span></span>

<span data-ttu-id="c4ce0-180">CLR は、不要と判断したオブジェクトを定期的に破棄します。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-180">The CLR periodically destroys objects when the system determines that such objects are no longer needed.</span></span> <span data-ttu-id="c4ce0-181">オブジェクトは、システム リソースが不足したときには迅速に解放され、それ以外の場合には解放の頻度が低くなります。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-181">Objects are released more quickly when system resources are in short supply, and less frequently otherwise.</span></span> <span data-ttu-id="c4ce0-182">オブジェクトがスコープを失ってから CLR が解放するまでに遅延が発生します。つまり、Visual Basic 6.0 とそれ以前のバージョンのオブジェクトとは異なり、オブジェクトがいつ破棄されるかを正確に特定することはできません。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-182">The delay between when an object loses scope and when the CLR releases it means that, unlike with objects in Visual Basic 6.0 and earlier versions, you cannot determine exactly when the object will be destroyed.</span></span> <span data-ttu-id="c4ce0-183">このような状況の場合、オブジェクトには *不明確な有効期間* があると言われます。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-183">In such a situation, objects are said to have *non-deterministic lifetime*.</span></span> <span data-ttu-id="c4ce0-184">ほとんどの場合、有効期間が不明確でもアプリケーションの作成方法は変わりません。ただし、オブジェクトがスコープを失ってもすぐには `Finalize` デストラクターが実行されない可能性があることに留意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-184">In most cases, non-deterministic lifetime does not change how you write applications, as long as you remember that the `Finalize` destructor may not immediately execute when an object loses scope.</span></span>

<span data-ttu-id="c4ce0-185">ガベージ コレクション システム間の相違点にはこの他、`Nothing` を使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-185">Another difference between the garbage-collection systems involves the use of `Nothing`.</span></span> <span data-ttu-id="c4ce0-186">Visual Basic 6.0 とそれ以前のバージョンの参照カウントを利用するために、プログラマはオブジェクト変数に `Nothing` を割り当てて、オブジェクト変数が保持する参照を解放することがありました。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-186">To take advantage of reference counting in Visual Basic 6.0 and earlier versions, programmers sometimes assigned `Nothing` to object variables to release the references those variables held.</span></span> <span data-ttu-id="c4ce0-187">変数がオブジェクトへの最後の参照を保持していた場合、オブジェクトのリソースは直ちに解放されました。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-187">If the variable held the last reference to the object, the object's resources were released immediately.</span></span> <span data-ttu-id="c4ce0-188">Visual Basic のそれ以降のバージョンでも、このプロシージャが有益な場合がありますが、実行しても、参照したオブジェクトによってリソースが直ちに解放されることはありません。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-188">In later versions of Visual Basic, while there may be cases in which this procedure is still valuable, performing it never causes the referenced object to release its resources immediately.</span></span> <span data-ttu-id="c4ce0-189">リソースを直ちに解放するには、オブジェクトの <xref:System.IDisposable.Dispose%2A> メソッドを使用してください (使用可能な場合)。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-189">To release resources immediately, use the object's <xref:System.IDisposable.Dispose%2A> method, if available.</span></span> <span data-ttu-id="c4ce0-190">変数を `Nothing` に設定する必要があるのは、ガベージ コレクターが孤立したオブジェクトを検出するのに要する時間よりも、変数の有効期間が長い場合のみです。</span><span class="sxs-lookup"><span data-stu-id="c4ce0-190">The only time you should set a variable to `Nothing` is when its lifetime is long relative to the time the garbage collector takes to detect orphaned objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4ce0-191">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4ce0-191">See also</span></span>

- <xref:System.IDisposable.Dispose%2A>
- <span data-ttu-id="c4ce0-192">[コンポーネントの初期化と終了](/previous-versions/visualstudio/visual-studio-2013/ws9dc6t6(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="c4ce0-192">[Initialization and Termination of Components](/previous-versions/visualstudio/visual-studio-2013/ws9dc6t6(v=vs.120))</span></span>
- [<span data-ttu-id="c4ce0-193">New 演算子</span><span class="sxs-lookup"><span data-stu-id="c4ce0-193">New Operator</span></span>](../../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="c4ce0-194">アンマネージ リソースのクリーンアップ</span><span class="sxs-lookup"><span data-stu-id="c4ce0-194">Cleaning Up Unmanaged Resources</span></span>](../../../../standard/garbage-collection/unmanaged.md)
- [<span data-ttu-id="c4ce0-195">Nothing</span><span class="sxs-lookup"><span data-stu-id="c4ce0-195">Nothing</span></span>](../../../language-reference/nothing.md)
