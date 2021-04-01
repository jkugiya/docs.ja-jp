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
# <a name="create-the-source-office-open-xml-document-linq-to-xml"></a>ソースとなる Office Open XML ドキュメントの作成 (LINQ to XML)

この記事では、このチュートリアルの他の例で使用する Office Open XML WordprocessingML ドキュメントを作成する方法を紹介します。 この手順に従うと、それぞれの例に記載されているとおりの出力が得られます。

ただし、このチュートリアルの例では、任意の有効な WordprocessingML ドキュメントを使用できます。

このチュートリアルで使用するドキュメントを作成するには、Microsoft Office 2007 以降がインストールされているか、Microsoft Office 2003 と Word/Excel/PowerPoint 2007 ファイル形式用 Microsoft Office 互換機能パックを所有している必要があります。

## <a name="create-the-wordprocessingml-document"></a>WordprocessingML ドキュメントを作成する

WordprocessingML ドキュメントは次の手順で作成します。

1. 新しい Microsoft Word 文書を作成します。
1. 新しい文書に次のテキストを貼り付けます。
   1. C# の場合、次のテキストを使用します。

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

   1. Visual Basic の場合、次のテキストを使用します。

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

1. "見出し 1" スタイルを使用して最初の行を書式設定します。
1. C# の場合、C# コードを含む行を選択します。 最初の行は `using` キーワードで始まります。 最後の行は、最後の右中かっこ (}) です。 クーリエ フォントを使用してこれらの行を書式設定します。 これらの行を新しいスタイルで書式設定し、このスタイルに "Code" という名前を付けます。
1. Visual Basic の場合、Visual Basic コードを含む行を選択します。 最初の行は `Imports` キーワードで始まります。 最後の行は "End Class" です。 クーリエ フォントを使用してこれらの行を書式設定します。 これらの行を新しいスタイルで書式設定し、このスタイルに "Code" という名前を付けます。
1. 最後に、出力が含まれる行全体を選択し、`Code` スタイルを使用して書式設定します。
1. ドキュメントを保存し、SampleDoc.docx という名前を付けます。

> [!NOTE]
> Microsoft Word 2003 を使用している場合、 **[ファイルの種類]** ドロップダウン リストの一覧の **[Word 2007 文書]** をクリックします。

## <a name="see-also"></a>関連項目

- [チュートリアル: WordprocessingML ドキュメント内のコンテンツを操作する](xml-shape-wordprocessingml-documents.md)
