---
description: '詳細情報: 方法:StreamWriter を使用してファイルにテキストを書き込む (Visual Basic)'
title: '方法: StreamWriter を使用してファイルにテキストを書き込む'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: d5528d0b5e7de40062558d29c0d3bebc227583a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797355"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="1d8a1-103">方法: StreamWriter を使用してファイルにテキストを書き込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d8a1-103">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>

<span data-ttu-id="1d8a1-104">この例では、`My.Computer.FileSystem.OpenTextFileWriter` メソッドで <xref:System.IO.StreamWriter> オブジェクトを開き、そのオブジェクトを使用し、<xref:System.IO.StreamWriter> クラスの <xref:System.IO.TextWriter.WriteLine%2A> メソッドでテキスト ファイルに文字列を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="1d8a1-104">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d8a1-105">例</span><span class="sxs-lookup"><span data-stu-id="1d8a1-105">Example</span></span>  

 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a><span data-ttu-id="1d8a1-106">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="1d8a1-106">Robust Programming</span></span>  

 <span data-ttu-id="1d8a1-107">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1d8a1-107">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="1d8a1-108">ファイルが存在するものの、読み取り専用の場合 (<xref:System.IO.IOException>)</span><span class="sxs-lookup"><span data-stu-id="1d8a1-108">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="1d8a1-109">ディスクの空き領域がない場合 (<xref:System.IO.IOException>)</span><span class="sxs-lookup"><span data-stu-id="1d8a1-109">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="1d8a1-110">パス名が長すぎる場合 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="1d8a1-110">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1d8a1-111">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1d8a1-111">.NET Framework Security</span></span>  

 <span data-ttu-id="1d8a1-112">次のコード例では、ファイルが存在しない場合は新規にファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1d8a1-112">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="1d8a1-113">アプリケーションでファイルを作成する必要がある場合、そのアプリケーションにはフォルダーに対する `Create` アクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="1d8a1-113">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="1d8a1-114">ファイルが既に存在する場合、アプリケーションに必要なのは、より低い権限である `Write` アクセスだけです。</span><span class="sxs-lookup"><span data-stu-id="1d8a1-114">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="1d8a1-115">フォルダーに対して `Read` アクセスを許可するのではなく、可能な限りアプリケーションの配置時にファイルを作成しておき、1 つのファイルに対してのみ `Create` アクセスを許可する方が安全です。</span><span class="sxs-lookup"><span data-stu-id="1d8a1-115">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d8a1-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d8a1-116">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [<span data-ttu-id="1d8a1-117">方法: テキスト ファイルからデータを読み取る</span><span class="sxs-lookup"><span data-stu-id="1d8a1-117">How to: Read from Text Files</span></span>](how-to-read-from-text-files.md)
- [<span data-ttu-id="1d8a1-118">ファイルへの書き込み</span><span class="sxs-lookup"><span data-stu-id="1d8a1-118">Writing to Files</span></span>](writing-to-files.md)
