---
description: '詳細情報: 方法:Visual Basic でファイルを作成する'
title: '方法: ファイルを作成する'
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: b46786035c14021ceb27cce5b34eff5c8397fc9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797589"
---
# <a name="how-to-create-a-file-in-visual-basic"></a><span data-ttu-id="fec84-103">方法 : Visual Basic でファイルを作成する</span><span class="sxs-lookup"><span data-stu-id="fec84-103">How to: Create a File in Visual Basic</span></span>

<span data-ttu-id="fec84-104">この例では、<xref:System.IO.File> クラスで <xref:System.IO.File.Create%2A> メソッドを使用して、指定したパスに空のテキスト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="fec84-104">This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fec84-105">例</span><span class="sxs-lookup"><span data-stu-id="fec84-105">Example</span></span>  

 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fec84-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="fec84-106">Compiling the Code</span></span>  

 <span data-ttu-id="fec84-107">ファイルに書き込むには、`file` 変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="fec84-107">Use the `file` variable to write to the file.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fec84-108">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="fec84-108">Robust Programming</span></span>  

 <span data-ttu-id="fec84-109">ファイルが既に存在する場合、それは置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="fec84-109">If the file already exists, it is replaced.</span></span>  
  
 <span data-ttu-id="fec84-110">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fec84-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="fec84-111">パス名が不適切である場合。</span><span class="sxs-lookup"><span data-stu-id="fec84-111">The path name is malformed.</span></span> <span data-ttu-id="fec84-112">たとえば、不正な文字が含まれている場合や、空白だけの場合などです (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="fec84-112">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="fec84-113">パスが読み取り専用の場合 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="fec84-113">The path is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="fec84-114">パス名が `Nothing` の場合 (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="fec84-114">The path name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="fec84-115">パス名が長すぎる場合 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="fec84-115">The path name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="fec84-116">パスが無効な場合 (<xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="fec84-116">The path is invalid (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="fec84-117">パスがコロン ":" のみである場合 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="fec84-117">The path is only a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="fec84-118">.NET Framework のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="fec84-118">.NET Framework Security</span></span>  

 <span data-ttu-id="fec84-119">部分信頼環境では、<xref:System.Security.SecurityException> がスローされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="fec84-119">A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.</span></span>  
  
 <span data-ttu-id="fec84-120"><xref:System.IO.File.Create%2A> メソッドへの呼び出しでは、<xref:System.Security.Permissions.FileIOPermission> が必要です。</span><span class="sxs-lookup"><span data-stu-id="fec84-120">The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.</span></span>  
  
 <span data-ttu-id="fec84-121">ユーザーがファイルを作成するアクセス許可を持っていない場合、<xref:System.UnauthorizedAccessException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="fec84-121">An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fec84-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="fec84-122">See also</span></span>

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [<span data-ttu-id="fec84-123">部分信頼コードからのライブラリの使用</span><span class="sxs-lookup"><span data-stu-id="fec84-123">Using Libraries from Partially Trusted Code</span></span>](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [<span data-ttu-id="fec84-124">コード アクセス セキュリティの基礎</span><span class="sxs-lookup"><span data-stu-id="fec84-124">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
