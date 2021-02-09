---
description: '詳細情報: 方法:My Documents ディレクトリの内容を取得する (Visual Basic)'
title: '方法: My Documents ディレクトリの内容を取得する'
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: e9e6ffc202332bd8d1849ef886fd4e7d6cc46a54
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797394"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="8b669-103">方法: My Documents ディレクトリの内容を取得する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b669-103">How to: Retrieve the Contents of the My Documents Directory in Visual Basic</span></span>

<span data-ttu-id="8b669-104"><xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> オブジェクトを使用すると、**My Documents** や **Desktop** など、多くの **All Users** ディレクトリを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="8b669-104">The <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> object can be used to read from many of the **All Users** directories, such as **My Documents** or **Desktop**.</span></span>  
  
### <a name="to-read-from-the-my-documents-folder"></a><span data-ttu-id="8b669-105">My Documents フォルダーを読み取るには</span><span class="sxs-lookup"><span data-stu-id="8b669-105">To read from the My Documents folder</span></span>  
  
- <span data-ttu-id="8b669-106">`ReadAllText` メソッドを使用して、指定したディレクトリの各ファイルからテキストを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="8b669-106">Use the `ReadAllText` method to read the text from each file in a specific directory.</span></span> <span data-ttu-id="8b669-107">次のコードでは、ディレクトリとファイルを指定し、`ReadAllText` を使用して、`patients` という名前の文字列に読み取ります。</span><span class="sxs-lookup"><span data-stu-id="8b669-107">The following code specifies a directory and file and then uses `ReadAllText` to read them into the string named `patients`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="8b669-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b669-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
