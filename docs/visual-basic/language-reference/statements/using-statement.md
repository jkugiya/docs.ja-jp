---
description: '詳細情報: Using ステートメント (Visual Basic)'
title: Using ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: fea77a441182b7c3ecac58d4fe7f1297a87f086c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740887"
---
# <a name="using-statement-visual-basic"></a><span data-ttu-id="2a0b4-103">Using ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a0b4-103">Using Statement (Visual Basic)</span></span>

<span data-ttu-id="2a0b4-104">`Using` ブロックの開始を宣言し、必要に応じて、ブロックで制御するシステム リソースを取得します。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-104">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span></span>

## <a name="syntax"></a><span data-ttu-id="2a0b4-105">構文</span><span class="sxs-lookup"><span data-stu-id="2a0b4-105">Syntax</span></span>

```vb
Using { resourcelist | resourceexpression }
    [ statements ]
End Using
```

## <a name="parts"></a><span data-ttu-id="2a0b4-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="2a0b4-106">Parts</span></span>

|<span data-ttu-id="2a0b4-107">用語</span><span class="sxs-lookup"><span data-stu-id="2a0b4-107">Term</span></span>|<span data-ttu-id="2a0b4-108">定義</span><span class="sxs-lookup"><span data-stu-id="2a0b4-108">Definition</span></span>|  
|---|---|  
|`resourcelist`|<span data-ttu-id="2a0b4-109">`resourceexpression` を指定しない場合は必須です。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-109">Required if you do not supply `resourceexpression`.</span></span> <span data-ttu-id="2a0b4-110">この `Using` ブロックで制御する、コンマで区切られた 1 つまたは複数のシステム リソースの一覧。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-110">List of one or more system resources that this `Using` block controls, separated by commas.</span></span>|  
|`resourceexpression`|<span data-ttu-id="2a0b4-111">`resourcelist` を指定しない場合は必須です。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-111">Required if you do not supply `resourcelist`.</span></span> <span data-ttu-id="2a0b4-112">この `Using` ブロックによって制御されるシステム リソースを参照する、参照変数または式。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-112">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span></span>|  
|`statements`|<span data-ttu-id="2a0b4-113">任意。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-113">Optional.</span></span> <span data-ttu-id="2a0b4-114">`Using` ブロックで実行されるステートメントのブロック。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-114">Block of statements that the `Using` block runs.</span></span>|  
|`End Using`|<span data-ttu-id="2a0b4-115">必須です。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-115">Required.</span></span> <span data-ttu-id="2a0b4-116">`Using` ブロックの定義を終了し、それによって制御されているすべてのリソースを破棄します。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-116">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span></span>|  

 <span data-ttu-id="2a0b4-117">`resourcelist` 部分の各リソースには、次の構文と指定項目があります。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-117">Each resource in the `resourcelist` part has the following syntax and parts:</span></span>

 `resourcename As New resourcetype [ ( [ arglist ] ) ]`

 <span data-ttu-id="2a0b4-118">\- または -</span><span class="sxs-lookup"><span data-stu-id="2a0b4-118">-or-</span></span>

 `resourcename As resourcetype = resourceexpression`

## <a name="resourcelist-parts"></a><span data-ttu-id="2a0b4-119">resourcelist の指定項目</span><span class="sxs-lookup"><span data-stu-id="2a0b4-119">resourcelist Parts</span></span>

|<span data-ttu-id="2a0b4-120">用語</span><span class="sxs-lookup"><span data-stu-id="2a0b4-120">Term</span></span>|<span data-ttu-id="2a0b4-121">定義</span><span class="sxs-lookup"><span data-stu-id="2a0b4-121">Definition</span></span>|  
|---|---|  
|`resourcename`|<span data-ttu-id="2a0b4-122">必須です。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-122">Required.</span></span> <span data-ttu-id="2a0b4-123">`Using` ブロックで制御されるシステム リソースを参照する参照変数。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-123">Reference variable that refers to a system resource that the `Using` block controls.</span></span>|  
|`New`|<span data-ttu-id="2a0b4-124">`Using` ステートメントでリソースを取得する場合は必須です。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-124">Required if the `Using` statement acquires the resource.</span></span> <span data-ttu-id="2a0b4-125">リソースを既に取得している場合は、2 番目の代替構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-125">If you have already acquired the resource, use the second syntax alternative.</span></span>|  
|`resourcetype`|<span data-ttu-id="2a0b4-126">必須です。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-126">Required.</span></span> <span data-ttu-id="2a0b4-127">リソースのクラス。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-127">The class of the resource.</span></span> <span data-ttu-id="2a0b4-128">クラスでは、<xref:System.IDisposable> インターフェイスを実装している必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-128">The class must implement the <xref:System.IDisposable> interface.</span></span>|  
|`arglist`|<span data-ttu-id="2a0b4-129">任意。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-129">Optional.</span></span> <span data-ttu-id="2a0b4-130">`resourcetype` のインスタンスを作成するためにコンストラクターに渡す引数の一覧。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-130">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span></span> <span data-ttu-id="2a0b4-131">「[パラメーター リスト](parameter-list.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-131">See [Parameter List](parameter-list.md).</span></span>|  
|`resourceexpression`|<span data-ttu-id="2a0b4-132">必須です。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-132">Required.</span></span> <span data-ttu-id="2a0b4-133">`resourcetype` の要件を満たすシステム リソースを参照する変数または式。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-133">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span></span> <span data-ttu-id="2a0b4-134">2 番目の代替構文を使用する場合は、`Using` ステートメントに制御を渡す前にリソースを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-134">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a0b4-135">Remarks</span><span class="sxs-lookup"><span data-stu-id="2a0b4-135">Remarks</span></span>

 <span data-ttu-id="2a0b4-136">コードに、ファイル ハンドル、COM ラッパー、SQL 接続などのアンマネージド リソースが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-136">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span></span> <span data-ttu-id="2a0b4-137">`Using` ブロックによって、コードでそのようなリソースを使い終わったときに、それらの 1 つまたは複数が確実に破棄されます。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-137">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span></span> <span data-ttu-id="2a0b4-138">これにより、それらを他のコードで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-138">This makes them available for other code to use.</span></span>

 <span data-ttu-id="2a0b4-139">管理対象リソースは、.NET Framework ガベージ コレクター (GC) によって、ユーザー側の追加のコーディングなしで破棄されます。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-139">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span></span> <span data-ttu-id="2a0b4-140">管理対象リソースには `Using` ブロックは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-140">You do not need a `Using` block for managed resources.</span></span> <span data-ttu-id="2a0b4-141">ただし、`Using` ブロックを使用して、ガベージ コレクターを待つことなく、管理対象リソースを強制的に破棄することもできます。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-141">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>

 <span data-ttu-id="2a0b4-142">`Using` ブロックには、取得、使用、破棄という 3 つの部分があります。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-142">A `Using` block has three parts: acquisition, usage, and disposal.</span></span>

- <span data-ttu-id="2a0b4-143">*取得* とは、変数を作成して、システム リソースを参照するようにそれを初期化することを意味します。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-143">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span></span> <span data-ttu-id="2a0b4-144">`Using` ステートメントでは 1 つ以上のリソースを取得できます。または、ブロックに入る前にリソースを 1 つだけ取得し、それを `Using` ステートメントに指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-144">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span></span> <span data-ttu-id="2a0b4-145">`resourceexpression` を指定する場合は、`Using` ステートメントに制御を渡す前にリソースを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-145">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span></span>

- <span data-ttu-id="2a0b4-146">*使用* とは、リソースにアクセスし、それらによってアクションを実行することを意味します。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-146">*Usage* means accessing the resources and performing actions with them.</span></span> <span data-ttu-id="2a0b4-147">`Using` と `End Using` の間のステートメントは、リソースの使用を表します。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-147">The statements between `Using` and `End Using` represent the usage of the resources.</span></span>

- <span data-ttu-id="2a0b4-148">*破棄* は、`resourcename` 内のオブジェクトに対して <xref:System.IDisposable.Dispose%2A> メソッドを呼び出すことを意味します。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-148">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span></span> <span data-ttu-id="2a0b4-149">これにより、オブジェクトでそのリソースを完全に終了させることができます。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-149">This allows the object to cleanly terminate its resources.</span></span> <span data-ttu-id="2a0b4-150">`End Using` ステートメントでは、`Using` ブロックの制御下にあるリソースが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-150">The `End Using` statement disposes of the resources under the `Using` block's control.</span></span>

## <a name="behavior"></a><span data-ttu-id="2a0b4-151">動作</span><span class="sxs-lookup"><span data-stu-id="2a0b4-151">Behavior</span></span>

 <span data-ttu-id="2a0b4-152">`Using` ブロックは、`Try`...`Finally` コンストラクションのように動作します。そのコンストラクションでは、`Try` ブロックでリソースを使用し、`Finally` ブロックでそれらを破棄します。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-152">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span></span> <span data-ttu-id="2a0b4-153">このため、`Using` ブロックでは、ブロックを終了する方法に関係なく、確実にリソースが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-153">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span></span> <span data-ttu-id="2a0b4-154">これは、<xref:System.StackOverflowException> を除いて、ハンドルされない例外が発生した場合でも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-154">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span></span>

 <span data-ttu-id="2a0b4-155">`Using` ステートメントによって取得されるすべてのリソース変数のスコープは、`Using` ブロックに制限されます。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-155">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span></span>

 <span data-ttu-id="2a0b4-156">`Using` ステートメントで複数のシステム リソースを指定した場合、その効果は、`Using` ブロックを別のブロック内に入れ子にした場合と同じになります。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-156">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span></span>

 <span data-ttu-id="2a0b4-157">`resourcename` が `Nothing` の場合、<xref:System.IDisposable.Dispose%2A> の呼び出しは行われず、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-157">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span></span>

## <a name="structured-exception-handling-within-a-using-block"></a><span data-ttu-id="2a0b4-158">Using ブロック内の構造化例外処理</span><span class="sxs-lookup"><span data-stu-id="2a0b4-158">Structured Exception Handling Within a Using Block</span></span>

 <span data-ttu-id="2a0b4-159">`Using` ブロック内で発生する可能性のある例外を処理する必要がある場合は、完全な `Try`...`Finally` コンストラクションをこれに追加できます。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-159">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span></span> <span data-ttu-id="2a0b4-160">`Using` ステートメントでリソースの取得に失敗した状況に対処する必要がある場合は、`resourcename` が `Nothing` であるかどうかをテストして確認できます。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-160">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span></span>

## <a name="structured-exception-handling-instead-of-a-using-block"></a><span data-ttu-id="2a0b4-161">Using ブロックの代わりの構造化例外処理</span><span class="sxs-lookup"><span data-stu-id="2a0b4-161">Structured Exception Handling Instead of a Using Block</span></span>

 <span data-ttu-id="2a0b4-162">リソースの取得をより詳細に制御する必要がある場合、または `Finally` ブロックに追加のコードが必要な場合は、`Using` ブロックを `Try`...`Finally` コンストラクションとして書き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-162">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span></span> <span data-ttu-id="2a0b4-163">次の例では、`resource` の取得と破棄において同等であるスケルトン `Try` と `Using` のコントラクションを示しています。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-163">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span></span>

```vb
Using resource As New resourceType
    ' Insert code to work with resource.
End Using

' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.
Dim resource As New resourceType
Try
    ' Insert code to work with resource.
Finally
    If resource IsNot Nothing Then
        resource.Dispose()
    End If
End Try
```

> [!NOTE]
> <span data-ttu-id="2a0b4-164">`Using` ブロック内のコードでは、`resourcename` 内のオブジェクトを別の変数に割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-164">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span></span> <span data-ttu-id="2a0b4-165">`Using` ブロックを終了すると、リソースが破棄され、他の変数はそれが指すリソースにアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-165">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span></span>

## <a name="example"></a><span data-ttu-id="2a0b4-166">例</span><span class="sxs-lookup"><span data-stu-id="2a0b4-166">Example</span></span>

 <span data-ttu-id="2a0b4-167">次の例では、log.txt という名前のファイルを作成し、ファイルに 2 行のテキストを書き込んでいます。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-167">The following example creates a file that is named log.txt and writes two lines of text to the file.</span></span> <span data-ttu-id="2a0b4-168">さらに、この例では、同じファイルを読み取って、テキスト行を表示しています。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-168">The example also reads that same file and displays the lines of text:</span></span>

 <span data-ttu-id="2a0b4-169"><xref:System.IO.TextWriter> クラスと <xref:System.IO.TextReader> クラスでは <xref:System.IDisposable> インターフェイスを実装するため、コードでは `Using` ステートメントを使用して、書き込み操作と読み取り操作の後でファイルが正しく閉じられるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="2a0b4-169">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span></span>

 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]

## <a name="see-also"></a><span data-ttu-id="2a0b4-170">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a0b4-170">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="2a0b4-171">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="2a0b4-171">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="2a0b4-172">方法: システム リソースを破棄する</span><span class="sxs-lookup"><span data-stu-id="2a0b4-172">How to: Dispose of a System Resource</span></span>](../../programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
