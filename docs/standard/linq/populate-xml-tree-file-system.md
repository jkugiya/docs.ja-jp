---
title: ファイル システムから XML ツリーを設定する方法 - LINQ to XML
description: C# または Visual Basic でファイル システムから XML ツリーを設定する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2aa2ccac-4a22-47ae-9107-3bb8df232576
ms.openlocfilehash: 6b0307aca9c9075120021967c08efcad8b595653
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412087"
---
# <a name="how-to-populate-an-xml-tree-from-the-file-system-linq-to-xml"></a><span data-ttu-id="01278-103">ファイル システムから XML ツリーを設定する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="01278-103">How to populate an XML tree from the file system (LINQ to XML)</span></span>

<span data-ttu-id="01278-104">XML ツリーの一般的で便利な用途の 1 つに、名前と値の階層データ ストアとしての用途があります。</span><span class="sxs-lookup"><span data-stu-id="01278-104">A common and useful application of XML trees is as a hierarchical name-value data store.</span></span> <span data-ttu-id="01278-105">階層データを XML ツリーに設定し、そのツリーをクエリや変換の対象としたり、必要に応じてシリアル化したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="01278-105">You can populate an XML tree with hierarchical data, and then query it, transform it, and if necessary, serialize it.</span></span> <span data-ttu-id="01278-106">この用途には、名前空間や空白に関する動作など XML 固有のセマンティクスの多くは重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="01278-106">For this use, many of the XML-specific semantics, such as namespaces and white space behavior, aren't important.</span></span> <span data-ttu-id="01278-107">その代わりに、XML ツリーをメモリ内の小さなシングル ユーザー階層データベースとして使用します。</span><span class="sxs-lookup"><span data-stu-id="01278-107">Instead, you're using the XML tree as a small, in-memory, single-user hierarchical database.</span></span>

## <a name="example-populate-an-xml-tree-and-then-query-it"></a><span data-ttu-id="01278-108">例: XML ツリーを設定してクエリを実行する</span><span class="sxs-lookup"><span data-stu-id="01278-108">Example: Populate an XML tree and then query it</span></span>

<span data-ttu-id="01278-109">次の例では、再帰を使用して、ローカル ファイル システム内のファイルに関するデータを XML ツリーに設定します。</span><span class="sxs-lookup"><span data-stu-id="01278-109">The following example uses recursion to populate an XML tree with data about the files in the local file system.</span></span> <span data-ttu-id="01278-110">次に、ツリーに対してクエリを行い、すべてのファイル サイズを合計します。</span><span class="sxs-lookup"><span data-stu-id="01278-110">It then queries the tree, totalling all the file sizes.</span></span>

```csharp
class Program
{
    static XElement CreateFileSystemXmlTree(string source)
    {
        DirectoryInfo di = new DirectoryInfo(source);
        return new XElement("Dir",
            new XAttribute("Name", di.Name),
            from d in Directory.GetDirectories(source)
            select CreateFileSystemXmlTree(d),
            from fi in di.GetFiles()
            select new XElement("File",
                new XElement("Name", fi.Name),
                new XElement("Length", fi.Length)
            )
        );
    }

    static void Main(string[] args)
    {
        XElement fileSystemTree = CreateFileSystemXmlTree("C:/Tmp");
        Console.WriteLine(fileSystemTree);
        Console.WriteLine("------");
        long totalFileSize =
            (from f in fileSystemTree.Descendants("File")
             select (long)f.Element("Length")).Sum();
        Console.WriteLine("Total File Size:{0}", totalFileSize);
    }
}
```

```vb
Module Module1
    Function CreateFileSystemXmlTree(ByVal source As String) As XElement
        Dim di As DirectoryInfo = New DirectoryInfo(source)
        Return <Dir Name=<%= di.Name %>>
                   <%= From d In Directory.GetDirectories(source) _
                       Select CreateFileSystemXmlTree(d) %>
                   <%= From fi In di.GetFiles() _
                       Select <File>
                                  <Name><%= fi.Name %></Name>
                                  <Length><%= fi.Length %></Length>
                              </File> %>
               </Dir>
    End Function

    Sub Main()
        Dim fileSystemTree As XElement = CreateFileSystemXmlTree("C:/Tmp")
        Console.WriteLine(fileSystemTree)
        Console.WriteLine("------")
        Dim totalFileSize As Long = _
            ( _
                From f In fileSystemTree...<File> _
                Select CLng(f.<Length>(0)) _
            ).Sum()
        Console.WriteLine("Total File Size:{0}", totalFileSize)
    End Sub
End Module
```

<span data-ttu-id="01278-111">この例では次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="01278-111">The example produces output similar to the following:</span></span>

```xml
<Dir Name="Tmp">
  <Dir Name="ConsoleApplication1">
    <Dir Name="bin">
      <Dir Name="Debug">
        <File>
          <Name>ConsoleApplication1.exe</Name>
          <Length>4608</Length>
        </File>
        <File>
          <Name>ConsoleApplication1.pdb</Name>
          <Length>11776</Length>
        </File>
        <File>
          <Name>ConsoleApplication1.vshost.exe</Name>
          <Length>9568</Length>
        </File>
        <File>
          <Name>ConsoleApplication1.vshost.exe.manifest</Name>
          <Length>473</Length>
        </File>
      </Dir>
    </Dir>
    <Dir Name="obj">
      <Dir Name="Debug">
        <Dir Name="TempPE" />
        <File>
          <Name>ConsoleApplication1.csproj.FileListAbsolute.txt</Name>
          <Length>322</Length>
        </File>
        <File>
          <Name>ConsoleApplication1.exe</Name>
          <Length>4608</Length>
        </File>
        <File>
          <Name>ConsoleApplication1.pdb</Name>
          <Length>11776</Length>
        </File>
      </Dir>
    </Dir>
    <Dir Name="Properties">
      <File>
        <Name>AssemblyInfo.cs</Name>
        <Length>1454</Length>
      </File>
    </Dir>
    <File>
      <Name>ConsoleApplication1.csproj</Name>
      <Length>2546</Length>
    </File>
    <File>
      <Name>ConsoleApplication1.sln</Name>
      <Length>937</Length>
    </File>
    <File>
      <Name>ConsoleApplication1.suo</Name>
      <Length>10752</Length>
    </File>
    <File>
      <Name>Program.cs</Name>
      <Length>269</Length>
    </File>
  </Dir>
</Dir>
------
Total File Size:59089
```
