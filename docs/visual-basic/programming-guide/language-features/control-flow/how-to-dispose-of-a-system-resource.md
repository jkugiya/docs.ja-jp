---
description: '詳細情報: 方法:システム リソースを破棄する (Visual Basic)'
title: '方法: システム リソースを破棄する'
ms.date: 07/20/2015
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
ms.openlocfilehash: 6594c9e2eedf756cc7a46c2c17deab58fcba3a8c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480662"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="f13bb-103">方法: システム リソースを破棄する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f13bb-103">How to: Dispose of a System Resource (Visual Basic)</span></span>

<span data-ttu-id="f13bb-104">`Using` ブロックを使用すると、コードがこのブロックを終了するときに、リソースが必ず破棄されることを保証できます。</span><span class="sxs-lookup"><span data-stu-id="f13bb-104">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="f13bb-105">これは、大量のメモリを消費するシステム リソースを使用している場合、または、他のコンポーネントでもそのシステム リソースを使いたい場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f13bb-105">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="f13bb-106">コードでの使用が済んだ時点でデータベース接続を破棄するには</span><span class="sxs-lookup"><span data-stu-id="f13bb-106">To dispose of a database connection when your code is finished with it</span></span>  
  
1. <span data-ttu-id="f13bb-107">データベース接続用の適切な [Imports ステートメント (.NET名前空間と型)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) を、ソース ファイル (この場合は <xref:System.Data.SqlClient>) の先頭に必ず追加します。</span><span class="sxs-lookup"><span data-stu-id="f13bb-107">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2. <span data-ttu-id="f13bb-108">`Using` ステートメントと `End Using` ステートメントを使用して、`Using` ブロックを作成します。</span><span class="sxs-lookup"><span data-stu-id="f13bb-108">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="f13bb-109">ブロック内に、データベース接続を処理するコードを配置します。</span><span class="sxs-lookup"><span data-stu-id="f13bb-109">Inside the block, put the code that deals with the database connection.</span></span>  
  
3. <span data-ttu-id="f13bb-110">接続を宣言し、そのインスタンスを `Using` ステートメントの一部として作成します。</span><span class="sxs-lookup"><span data-stu-id="f13bb-110">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```vb  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="f13bb-111">ハンドルされていない例外のケースを含め、ブロックを終了する方法に関係なくリソースが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="f13bb-111">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="f13bb-112">スコープがブロックに限定されているため、`Using` ブロック外から `sqc` にアクセスできないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f13bb-112">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="f13bb-113">同じ手法を、ファイル ハンドルや COM ラッパーなどのシステム リソースでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="f13bb-113">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="f13bb-114">`Using` ブロックは、`Using` ブロックを終了した後に、リソースを確実に他のコンポーネントで使用できるようにしたいときに使用します。</span><span class="sxs-lookup"><span data-stu-id="f13bb-114">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f13bb-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f13bb-115">See also</span></span>

- <xref:System.Data.SqlClient.SqlConnection>
- [<span data-ttu-id="f13bb-116">制御フロー</span><span class="sxs-lookup"><span data-stu-id="f13bb-116">Control Flow</span></span>](index.md)
- [<span data-ttu-id="f13bb-117">条件判断構造</span><span class="sxs-lookup"><span data-stu-id="f13bb-117">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="f13bb-118">ループ構造</span><span class="sxs-lookup"><span data-stu-id="f13bb-118">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="f13bb-119">その他の制御構造</span><span class="sxs-lookup"><span data-stu-id="f13bb-119">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="f13bb-120">入れ子になった制御構造</span><span class="sxs-lookup"><span data-stu-id="f13bb-120">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="f13bb-121">Using ステートメント</span><span class="sxs-lookup"><span data-stu-id="f13bb-121">Using Statement</span></span>](../../../language-reference/statements/using-statement.md)
