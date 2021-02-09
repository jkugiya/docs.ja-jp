---
description: '詳細情報: バイト配列に読み取るにはファイルが大きすぎます。'
title: バイト配列に読み取るにはファイルが大きすぎます。
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 8b2eb7bcbbea42c56d607147e55d6c02695c5670
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796289"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="b0fbb-103">バイト配列に読み取るにはファイルが大きすぎます。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-103">File is too large to read into a byte array</span></span>

<span data-ttu-id="b0fbb-104">バイト配列に読み取ろうとしているファイルのサイズが 4 GB を超えています。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-104">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="b0fbb-105">`My.Computer.FileSystem.ReadAllBytes` メソッドは、このサイズを超えるファイルを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-105">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b0fbb-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="b0fbb-106">To correct this error</span></span>  
  
- <span data-ttu-id="b0fbb-107"><xref:System.IO.StreamReader> を使用してファイルを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-107">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="b0fbb-108">詳細については、「[.NET Framework のファイル I/O とファイル システムの基礎 (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-108">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0fbb-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0fbb-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [<span data-ttu-id="b0fbb-110">Visual Basic におけるファイル アクセス</span><span class="sxs-lookup"><span data-stu-id="b0fbb-110">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
- [<span data-ttu-id="b0fbb-111">方法: StreamReader を使用してファイルからテキストを読み取る</span><span class="sxs-lookup"><span data-stu-id="b0fbb-111">How to: Read Text from Files with a StreamReader</span></span>](../../developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
