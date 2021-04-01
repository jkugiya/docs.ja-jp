---
title: ソースとなる Office Open XML ドキュメントの作成 - LINQ to XML
description: このチュートリアルの他の例で使用する Office Open XML WordprocessingML ドキュメントを作成する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: b3401d7309879661dcfc7062418ee75430dccf35
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411946"
---
# <a name="create-the-source-office-open-xml-document-linq-to-xml"></a><span data-ttu-id="400eb-103">ソースとなる Office Open XML ドキュメントの作成 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="400eb-103">Create the source Office Open XML document (LINQ to XML)</span></span>

<span data-ttu-id="400eb-104">この記事では、このチュートリアルの他の例で使用する Office Open XML WordprocessingML ドキュメントを作成する方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="400eb-104">This article shows how to create the Office Open XML WordprocessingML document used by the other examples in this tutorial.</span></span> <span data-ttu-id="400eb-105">この手順に従うと、それぞれの例に記載されているとおりの出力が得られます。</span><span class="sxs-lookup"><span data-stu-id="400eb-105">If you follow these instructions, your output will match the output provided in each example.</span></span>

<span data-ttu-id="400eb-106">ただし、このチュートリアルの例では、任意の有効な WordprocessingML ドキュメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="400eb-106">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>

<span data-ttu-id="400eb-107">このチュートリアルで使用するドキュメントを作成するには、Microsoft Office 2007 以降がインストールされているか、Microsoft Office 2003 と Word/Excel/PowerPoint 2007 ファイル形式用 Microsoft Office 互換機能パックを所有している必要があります。</span><span class="sxs-lookup"><span data-stu-id="400eb-107">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="create-the-wordprocessingml-document"></a><span data-ttu-id="400eb-108">WordprocessingML ドキュメントを作成する</span><span class="sxs-lookup"><span data-stu-id="400eb-108">Create the WordprocessingML document</span></span>

<span data-ttu-id="400eb-109">WordprocessingML ドキュメントは次の手順で作成します。</span><span class="sxs-lookup"><span data-stu-id="400eb-109">Use the following steps to create the WordprocessingML document:</span></span>

1. <span data-ttu-id="400eb-110">新しい Microsoft Word 文書を作成します。</span><span class="sxs-lookup"><span data-stu-id="400eb-110">Create a new Microsoft Word document.</span></span>
1. <span data-ttu-id="400eb-111">新しい文書に次のテキストを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="400eb-111">Paste the following text into the new document.</span></span>
   1. <span data-ttu-id="400eb-112">C# の場合、次のテキストを使用します。</span><span class="sxs-lookup"><span data-stu-id="400eb-112">For C#, use this text:</span></span>

         ```text
         Parsing WordprocessingML with LINQ to XML

         The following example prints to the console.

         using System;

            class Program {
               public static void Main(string[] args) {
               Console.WriteLine("Hello World");
            }
         }

         This example produces the following output:

         Hello World
         ```

   1. <span data-ttu-id="400eb-113">Visual Basic の場合、次のテキストを使用します。</span><span class="sxs-lookup"><span data-stu-id="400eb-113">For Visual Basic, use this text:</span></span>

      ```text
      Parsing WordprocessingML with LINQ to XML

      The following example prints to the console.

      Imports System

      Class Program
         Public Shared  Sub Main(ByVal args() As String)
            Console.WriteLine("Hello World")
         End Sub
      End Class

      This example produces the following output:

      Hello World
      ```

1. <span data-ttu-id="400eb-114">"見出し 1" スタイルを使用して最初の行を書式設定します。</span><span class="sxs-lookup"><span data-stu-id="400eb-114">Format the first line with the style "Heading 1".</span></span>
1. <span data-ttu-id="400eb-115">C# の場合、C# コードを含む行を選択します。</span><span class="sxs-lookup"><span data-stu-id="400eb-115">For C#, select the lines that contain the C# code.</span></span> <span data-ttu-id="400eb-116">最初の行は `using` キーワードで始まります。</span><span class="sxs-lookup"><span data-stu-id="400eb-116">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="400eb-117">最後の行は、最後の右中かっこ (}) です。</span><span class="sxs-lookup"><span data-stu-id="400eb-117">The last line is the last closing brace.</span></span> <span data-ttu-id="400eb-118">クーリエ フォントを使用してこれらの行を書式設定します。</span><span class="sxs-lookup"><span data-stu-id="400eb-118">Format the lines with the courier font.</span></span> <span data-ttu-id="400eb-119">これらの行を新しいスタイルで書式設定し、このスタイルに "Code" という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="400eb-119">Format them with a new style, and name the new style "Code".</span></span>
1. <span data-ttu-id="400eb-120">Visual Basic の場合、Visual Basic コードを含む行を選択します。</span><span class="sxs-lookup"><span data-stu-id="400eb-120">For Visual Basic, select the lines that contain the Visual Basic code.</span></span> <span data-ttu-id="400eb-121">最初の行は `Imports` キーワードで始まります。</span><span class="sxs-lookup"><span data-stu-id="400eb-121">The first line starts with the `Imports` keyword.</span></span> <span data-ttu-id="400eb-122">最後の行は "End Class" です。</span><span class="sxs-lookup"><span data-stu-id="400eb-122">The last line is "End Class".</span></span> <span data-ttu-id="400eb-123">クーリエ フォントを使用してこれらの行を書式設定します。</span><span class="sxs-lookup"><span data-stu-id="400eb-123">Format the lines with the courier font.</span></span> <span data-ttu-id="400eb-124">これらの行を新しいスタイルで書式設定し、このスタイルに "Code" という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="400eb-124">Format them with a new style, and name the new style "Code".</span></span>
1. <span data-ttu-id="400eb-125">最後に、出力が含まれる行全体を選択し、`Code` スタイルを使用して書式設定します。</span><span class="sxs-lookup"><span data-stu-id="400eb-125">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>
1. <span data-ttu-id="400eb-126">ドキュメントを保存し、SampleDoc.docx という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="400eb-126">Save the document, and name it SampleDoc.docx.</span></span>

> [!NOTE]
> <span data-ttu-id="400eb-127">Microsoft Word 2003 を使用している場合、 **[ファイルの種類]** ドロップダウン リストの一覧の **[Word 2007 文書]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="400eb-127">If you're using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>

## <a name="see-also"></a><span data-ttu-id="400eb-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="400eb-128">See also</span></span>

- [<span data-ttu-id="400eb-129">チュートリアル: WordprocessingML ドキュメント内のコンテンツを操作する</span><span class="sxs-lookup"><span data-stu-id="400eb-129">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
