---
description: '詳細情報: チュートリアル: Visual Basic での IEnumerable(Of T) の実装'
title: IEnumerable の実装
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: 87905e4f110d3a9d95b1cad642296ea8105f32f4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428143"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a><span data-ttu-id="2f002-103">チュートリアル: Visual Basic での IEnumerable(Of T) の実装</span><span class="sxs-lookup"><span data-stu-id="2f002-103">Walkthrough: Implementing IEnumerable(Of T) in Visual Basic</span></span>

<span data-ttu-id="2f002-104"><xref:System.Collections.Generic.IEnumerable%601> インターフェイスは、値のシーケンスを、一度に 1 項目ずつ返すことができるクラスによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="2f002-104">The <xref:System.Collections.Generic.IEnumerable%601> interface is implemented by classes that can return a sequence of values one item at a time.</span></span> <span data-ttu-id="2f002-105">一度に 1 項目ずつデータを返す利点は、データ セット全体をメモリに読み込んで操作する必要がないことです。</span><span class="sxs-lookup"><span data-stu-id="2f002-105">The advantage of returning data one item at a time is that you do not have to load the complete set of data into memory to work with it.</span></span> <span data-ttu-id="2f002-106">データから 1 つの項目を読み込むのに必要なメモリを使用するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="2f002-106">You only have to use sufficient memory to load a single item from the data.</span></span> <span data-ttu-id="2f002-107">`IEnumerable(T)` インターフェイスを実装するクラスを、`For Each` ループまたは LINQ クエリで使用できます。</span><span class="sxs-lookup"><span data-stu-id="2f002-107">Classes that implement the `IEnumerable(T)` interface can be used with `For Each` loops or LINQ queries.</span></span>  
  
 <span data-ttu-id="2f002-108">たとえば、大きなテキスト ファイルを読み取り、そのファイルから、特定の検索条件に一致する各行を返す必要があるアプリケーションがあるとします。</span><span class="sxs-lookup"><span data-stu-id="2f002-108">For example, consider an application that must read a large text file and return each line from the file that matches particular search criteria.</span></span> <span data-ttu-id="2f002-109">アプリケーションは LINQ クエリを使用して、指定された条件に一致する行をファイルから返します。</span><span class="sxs-lookup"><span data-stu-id="2f002-109">The application uses a LINQ query to return lines from the file that match the specified criteria.</span></span> <span data-ttu-id="2f002-110">LINQ クエリを使用してファイルのコンテンツにクエリを実行するために、アプリケーションでは、ファイルのコンテンツを配列またはコレクションに読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="2f002-110">To query the contents of the file by using a LINQ query, the application could load the contents of the file into an array or a collection.</span></span> <span data-ttu-id="2f002-111">ただし、ファイル全体を配列またはコレクションに読み込むと、必要以上にメモリが消費されます。</span><span class="sxs-lookup"><span data-stu-id="2f002-111">However, loading the whole file into an array or collection would consume far more memory than is required.</span></span> <span data-ttu-id="2f002-112">LINQ クエリは、列挙可能なクラスを使用してファイルのコンテンツにクエリを実行し、検索条件に一致する値のみを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="2f002-112">The LINQ query could instead query the file contents by using an enumerable class, returning only values that match the search criteria.</span></span> <span data-ttu-id="2f002-113">一致する値だけをいくつか返すクエリの場合、消費メモリは格段に少なくなります。</span><span class="sxs-lookup"><span data-stu-id="2f002-113">Queries that return only a few matching values would consume far less memory.</span></span>  
  
 <span data-ttu-id="2f002-114"><xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装するクラスを作成して、ソース データを、列挙可能なデータとして公開できます。</span><span class="sxs-lookup"><span data-stu-id="2f002-114">You can create a class that implements the <xref:System.Collections.Generic.IEnumerable%601> interface to expose source data as enumerable data.</span></span> <span data-ttu-id="2f002-115">`IEnumerable(T)` インターフェイスを実装するクラスには、ソース データを反復処理するために <xref:System.Collections.Generic.IEnumerator%601> インターフェイスを実装する別のクラスが必要です。</span><span class="sxs-lookup"><span data-stu-id="2f002-115">Your class that implements the `IEnumerable(T)` interface will require another class that implements the <xref:System.Collections.Generic.IEnumerator%601> interface to iterate through the source data.</span></span> <span data-ttu-id="2f002-116">この 2 つのクラスを使用すると、データの項目を特定の型として順番に返すことができます。</span><span class="sxs-lookup"><span data-stu-id="2f002-116">These two classes enable you to return items of data sequentially as a specific type.</span></span>  
  
 <span data-ttu-id="2f002-117">このチュートリアルでは、`IEnumerable(Of String)` インターフェイスを実装するクラスと `IEnumerator(Of String)` インターフェイスを実装するクラスを作成して、テキスト ファイルを 1 行ずつ読み取ります。</span><span class="sxs-lookup"><span data-stu-id="2f002-117">In this walkthrough, you will create a class that implements the `IEnumerable(Of String)` interface and a class that implements the `IEnumerator(Of String)` interface to read a text file one line at a time.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a><span data-ttu-id="2f002-118">列挙可能なクラスの作成</span><span class="sxs-lookup"><span data-stu-id="2f002-118">Creating the Enumerable Class</span></span>  
  
<span data-ttu-id="2f002-119">**列挙可能なクラス プロジェクトを作成する**</span><span class="sxs-lookup"><span data-stu-id="2f002-119">**Create the enumerable class project**</span></span>

1. <span data-ttu-id="2f002-120">Visual Basic で、 **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f002-120">In Visual Basic, on the **File** menu, point to **New** and then click **Project**.</span></span>

1. <span data-ttu-id="2f002-121">**[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、 **[Windows]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2f002-121">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="2f002-122">**[テンプレート]** ペインで **[クラス ライブラリ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2f002-122">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="2f002-123">**[名前]** ボックスに `StreamReaderEnumerable` と入力して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f002-123">In the **Name** box, type `StreamReaderEnumerable`, and then click **OK**.</span></span> <span data-ttu-id="2f002-124">新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f002-124">The new project is displayed.</span></span>

1. <span data-ttu-id="2f002-125">**ソリューション エクスプローラー** で、Class1.vb ファイルを右クリックし、 **[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f002-125">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="2f002-126">ファイルの名前を `StreamReaderEnumerable.vb` に変更し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2f002-126">Rename the file to `StreamReaderEnumerable.vb` and press ENTER.</span></span> <span data-ttu-id="2f002-127">ファイルの名前を変更すると、クラスの名前も `StreamReaderEnumerable` に変更されます。</span><span class="sxs-lookup"><span data-stu-id="2f002-127">Renaming the file will also rename the class to `StreamReaderEnumerable`.</span></span> <span data-ttu-id="2f002-128">このクラスが `IEnumerable(Of String)` インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="2f002-128">This class will implement the `IEnumerable(Of String)` interface.</span></span>

1. <span data-ttu-id="2f002-129">StreamReaderEnumerable プロジェクトを右クリックして **[追加]** をポイントし、 **[新しい項目]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f002-129">Right-click the StreamReaderEnumerable project, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="2f002-130">**[クラス]** テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="2f002-130">Select the **Class** template.</span></span> <span data-ttu-id="2f002-131">**[名前]** ボックスに「`StreamReaderEnumerator.vb`」と入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f002-131">In the **Name** box, type `StreamReaderEnumerator.vb` and click **OK**.</span></span>

 <span data-ttu-id="2f002-132">このプロジェクトの最初のクラスは列挙可能なクラスであり、`IEnumerable(Of String)` インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="2f002-132">The first class in this project is the enumerable class and will implement the `IEnumerable(Of String)` interface.</span></span> <span data-ttu-id="2f002-133">このジェネリック インターフェイスは <xref:System.Collections.IEnumerable> インターフェイスを実装し、このクラスのコンシューマーが、`String` として型指定された値にアクセスできることを保証します。</span><span class="sxs-lookup"><span data-stu-id="2f002-133">This generic interface implements the <xref:System.Collections.IEnumerable> interface and guarantees that consumers of this class can access values typed as `String`.</span></span>  
  
<span data-ttu-id="2f002-134">**IEnumerable を実装するコードを追加する**</span><span class="sxs-lookup"><span data-stu-id="2f002-134">**Add the code to implement IEnumerable**</span></span>

1. <span data-ttu-id="2f002-135">StreamReaderEnumerable.vb ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="2f002-135">Open the StreamReaderEnumerable.vb file.</span></span>

2. <span data-ttu-id="2f002-136">`Public Class StreamReaderEnumerable` の後の行に以下を入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2f002-136">On the line after `Public Class StreamReaderEnumerable`, type the following and press ENTER.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   <span data-ttu-id="2f002-137">`IEnumerable(Of String)` インターフェイスに必要なメンバーが、クラスに自動入力されます。</span><span class="sxs-lookup"><span data-stu-id="2f002-137">Visual Basic automatically populates the class with the members that are required by the `IEnumerable(Of String)` interface.</span></span>
  
3. <span data-ttu-id="2f002-138">この列挙可能なクラスは、テキスト ファイルから 1 行ずつ行を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="2f002-138">This enumerable class will read lines from a text file one line at a time.</span></span> <span data-ttu-id="2f002-139">次のコードをクラスに追加して、ファイル パスを入力パラメーターとして取るパブリック コンストラクターを公開します。</span><span class="sxs-lookup"><span data-stu-id="2f002-139">Add the following code to the class to expose a public constructor that takes a file path as an input parameter.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. <span data-ttu-id="2f002-140">`IEnumerable(Of String)` インターフェイスの <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> メソッドの実装は、`StreamReaderEnumerator` クラスの新しいインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="2f002-140">Your implementation of the <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method of the `IEnumerable(Of String)` interface will return a new instance of the `StreamReaderEnumerator` class.</span></span> <span data-ttu-id="2f002-141">`IEnumerable(Of String)` インターフェイスのメンバーのみを公開する必要があるため、`IEnumerable` インターフェイスの `GetEnumerator` メソッドの実装は `Private` にできます。</span><span class="sxs-lookup"><span data-stu-id="2f002-141">The implementation of the `GetEnumerator` method of the `IEnumerable` interface can be made `Private`, because you have to expose only members of the `IEnumerable(Of String)` interface.</span></span> <span data-ttu-id="2f002-142">`GetEnumerator` メソッド用に生成されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2f002-142">Replace the code that Visual Basic generated for the `GetEnumerator` methods with the following code.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
<span data-ttu-id="2f002-143">**IEnumerator を実装するコードを追加する**</span><span class="sxs-lookup"><span data-stu-id="2f002-143">**Add the code to implement IEnumerator**</span></span>

1. <span data-ttu-id="2f002-144">StreamReaderEnumerator.vb ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="2f002-144">Open the StreamReaderEnumerator.vb file.</span></span>

2. <span data-ttu-id="2f002-145">`Public Class StreamReaderEnumerator` の後の行に以下を入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2f002-145">On the line after `Public Class StreamReaderEnumerator`, type the following and press ENTER.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   <span data-ttu-id="2f002-146">`IEnumerator(Of String)` インターフェイスに必要なメンバーが、クラスに自動入力されます。</span><span class="sxs-lookup"><span data-stu-id="2f002-146">Visual Basic automatically populates the class with the members that are required by the `IEnumerator(Of String)` interface.</span></span>

3. <span data-ttu-id="2f002-147">列挙子クラスはテキスト ファイルを開き、ファイルから行を読み取るためにファイル I/O を実行します。</span><span class="sxs-lookup"><span data-stu-id="2f002-147">The enumerator class opens the text file and performs the file I/O to read the lines from the file.</span></span> <span data-ttu-id="2f002-148">次のコードをクラスに追加して、ファイル パスを入力パラメーターとして取るパブリック コンストラクターを公開し、読み取るテキスト ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="2f002-148">Add the following code to the class to expose a public constructor that takes a file path as an input parameter and open the text file for reading.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. <span data-ttu-id="2f002-149">`IEnumerator(Of String)` インターフェイスと `IEnumerator` インターフェイスの両方の `Current` プロパティが、テキスト ファイルから現在の項目を `String` として返します。</span><span class="sxs-lookup"><span data-stu-id="2f002-149">The `Current` properties for both the `IEnumerator(Of String)` and `IEnumerator` interfaces return the current item from the text file as a `String`.</span></span> <span data-ttu-id="2f002-150">`IEnumerator(Of String)` インターフェイスのメンバーのみを公開する必要があるため、`IEnumerator` インターフェイスの `Current` プロパティの実装は `Private` にできます。</span><span class="sxs-lookup"><span data-stu-id="2f002-150">The implementation of the `Current` property of the `IEnumerator` interface can be made `Private`, because you have to expose only members of the `IEnumerator(Of String)` interface.</span></span> <span data-ttu-id="2f002-151">`Current` プロパティ用に生成されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2f002-151">Replace the code that Visual Basic generated for the `Current` properties with the following code.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. <span data-ttu-id="2f002-152">`IEnumerator` インターフェイスの `MoveNext` メソッドは、テキスト ファイル内の次の項目に移動し、`Current` プロパティによって返される値を更新します。</span><span class="sxs-lookup"><span data-stu-id="2f002-152">The `MoveNext` method of the `IEnumerator` interface navigates to the next item in the text file and updates the value that is returned by the `Current` property.</span></span> <span data-ttu-id="2f002-153">読み取る項目がない場合、`MoveNext` メソッドは `False` を返します。それ以外の場合、`MoveNext` メソッドは `True` を返します。</span><span class="sxs-lookup"><span data-stu-id="2f002-153">If there are no more items to read, the `MoveNext` method returns `False`; otherwise the `MoveNext` method returns `True`.</span></span> <span data-ttu-id="2f002-154">`MoveNext` メソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="2f002-154">Add the following code to the `MoveNext` method.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. <span data-ttu-id="2f002-155">`IEnumerator` インターフェイスの `Reset` メソッドは、テキスト ファイルの先頭を指すよう反復子に指示し、現在の項目の値をクリアします。</span><span class="sxs-lookup"><span data-stu-id="2f002-155">The `Reset` method of the `IEnumerator` interface directs the iterator to point to the start of the text file and clears the current item value.</span></span> <span data-ttu-id="2f002-156">`Reset` メソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="2f002-156">Add the following code to the `Reset` method.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. <span data-ttu-id="2f002-157">`IEnumerator` インターフェイスの `Dispose` メソッドは、反復子が破棄される前にすべてのアンマネージ リソースが解放されることを保証します。</span><span class="sxs-lookup"><span data-stu-id="2f002-157">The `Dispose` method of the `IEnumerator` interface guarantees that all unmanaged resources are released before the iterator is destroyed.</span></span> <span data-ttu-id="2f002-158">`StreamReader` オブジェクトによって使用されるファイル ハンドルはアンマネージ リソースです。このハンドルは、反復子インスタンスが破棄される前に閉じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f002-158">The file handle that is used by the `StreamReader` object is an unmanaged resource and must be closed before the iterator instance is destroyed.</span></span> <span data-ttu-id="2f002-159">`Dispose` メソッド用に生成されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2f002-159">Replace the code that Visual Basic generated for the `Dispose` method with the following code.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)]
  
## <a name="using-the-sample-iterator"></a><span data-ttu-id="2f002-160">サンプル反復子の使用</span><span class="sxs-lookup"><span data-stu-id="2f002-160">Using the Sample Iterator</span></span>

 <span data-ttu-id="2f002-161">コードでは、`For Next` ループや LINQ クエリなどの `IEnumerable` を実装するオブジェクトを必要とする制御構造と一緒に、列挙可能なクラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2f002-161">You can use an enumerable class in your code together with control structures that require an object that implements `IEnumerable`, such as a `For Next` loop or a LINQ query.</span></span> <span data-ttu-id="2f002-162">次の例は、LINQ クエリの `StreamReaderEnumerable` を示しています。</span><span class="sxs-lookup"><span data-stu-id="2f002-162">The following example shows the `StreamReaderEnumerable` in a LINQ query.</span></span>  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="2f002-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f002-163">See also</span></span>

- [<span data-ttu-id="2f002-164">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="2f002-164">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
- [<span data-ttu-id="2f002-165">制御フロー</span><span class="sxs-lookup"><span data-stu-id="2f002-165">Control Flow</span></span>](index.md)
- [<span data-ttu-id="2f002-166">ループ構造</span><span class="sxs-lookup"><span data-stu-id="2f002-166">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="2f002-167">For Each...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="2f002-167">For Each...Next Statement</span></span>](../../../language-reference/statements/for-each-next-statement.md)
