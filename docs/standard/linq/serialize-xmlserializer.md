---
title: XmlSerializer を使用してシリアル化する方法 - LINQ to XML
description: XmlSerializer を使用してオブジェクトをシリアル化および逆シリアル化する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2e0a0bbc-c548-4fe2-8741-be5a9ccd0cbb
ms.openlocfilehash: 5da09a75adb2fb65980a6e55449b33c3234d5e49
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412039"
---
# <a name="how-to-serialize-using-xmlserializer-linq-to-xml"></a><span data-ttu-id="f2e28-103">XmlSerializer を使用してシリアル化する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f2e28-103">How to serialize using XmlSerializer (LINQ to XML)</span></span>

<span data-ttu-id="f2e28-104">この記事では、C# および Visual Basic で <xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化と逆シリアル化を行う例を示します。</span><span class="sxs-lookup"><span data-stu-id="f2e28-104">This article shows an example that serializes and deserializes using <xref:System.Xml.Serialization.XmlSerializer> in C# and Visual Basic.</span></span>

## <a name="example-create-objects-that-contain-xelement-objects-then-serialize-and-deserialize-them"></a><span data-ttu-id="f2e28-105">例: `XElement` オブジェクトを含むオブジェクトを作成し、それらをシリアル化および逆シリアル化する</span><span class="sxs-lookup"><span data-stu-id="f2e28-105">Example: Create objects that contain `XElement` objects, then serialize and deserialize them</span></span>

<span data-ttu-id="f2e28-106">次の例では、<xref:System.Xml.Linq.XElement> オブジェクトを含んでいる多数のオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f2e28-106">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="f2e28-107">次に、それらのオブジェクトをメモリ ストリームにシリアル化し、メモリ ストリームから逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="f2e28-107">It then serializes them to a memory stream, and then deserializes them from the memory stream.</span></span>

```csharp
using System;
using System.IO;
using System.Linq;
using System.Xml;
using System.Xml.Serialization;
using System.Xml.Linq;

public class XElementContainer
{
    public XElement member;

    public XElementContainer()
    {
        member = XLinqTest.CreateXElement();
    }

    public override string ToString()
    {
        return member.ToString();
    }
}

public class XElementNullContainer
{
    public XElement member;

    public XElementNullContainer()
    {
    }
}

class XLinqTest
{
    static void Main(string[] args)
    {
        Test<XElementNullContainer>(new XElementNullContainer());
        Test<XElement>(CreateXElement());
        Test<XElementContainer>(new XElementContainer());
    }

    public static XElement CreateXElement()
    {
        XNamespace ns = "http://www.adventure-works.com";
        return new XElement(ns + "aw");
    }

    static void Test<T>(T obj)
    {
        using (MemoryStream stream = new MemoryStream())
        {
            XmlSerializer s = new XmlSerializer(typeof(T));
            Console.WriteLine("Testing for type: {0}", typeof(T));
            s.Serialize(XmlWriter.Create(stream), obj);
            stream.Flush();
            stream.Seek(0, SeekOrigin.Begin);
            object o = s.Deserialize(XmlReader.Create(stream));
            Console.WriteLine("  Deserialized type: {0}", o.GetType());
        }
    }
}
```

```vb
Imports System
Imports System.Xml
Imports System.Xml.Linq
Imports System.IO
Imports System.Runtime.Serialization
Imports System.Xml.Serialization

Public Class XElementContainer
    Public member As XElement

    Public Sub XElementContainer()
        member = XLinqTest.CreateXElement()
    End Sub

    Overrides Function ToString() As String
        Return member.ToString()
    End Function
End Class

Public Class XElementNullContainer
    Public member As XElement

    Public Sub XElementNullContainer()
        member = Nothing
    End Sub
End Class

Public Class XLinqTest
    Shared Sub Main()
        Test(Of XElementNullContainer)(New XElementNullContainer())
        Test(Of XElement)(CreateXElement())
        Test(Of XElementContainer)(New XElementContainer())
    End Sub

    Public Shared Function CreateXElement() As XElement
        Dim ns As XNamespace = "http://www.adventure-works.com"
        Return New XElement(ns + "aw")
    End Function

    Public Shared Sub Test(Of T)(ByRef obj)
        Using stream As New MemoryStream()
            Dim s As XmlSerializer = New XmlSerializer(GetType(T))
            Console.WriteLine("Testing for type: {0}", GetType(T))
            s.Serialize(XmlWriter.Create(stream), obj)
            stream.Flush()
            stream.Seek(0, SeekOrigin.Begin)
            Dim o As Object = s.Deserialize(XmlReader.Create(stream))
            Console.WriteLine("  Deserialized type: {0}", o.GetType())
        End Using
    End Sub
End Class
```

<span data-ttu-id="f2e28-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f2e28-108">This example produces the following output:</span></span>

```output
Testing for type: XElementNullContainer
  Deserialized type: XElementNullContainer
Testing for type: System.Xml.Linq.XElement
  Deserialized type: System.Xml.Linq.XElement
Testing for type: XElementContainer
  Deserialized type: XElementContainer
```
