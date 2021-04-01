---
title: DataContractSerializer を使用してシリアル化する方法 - LINQ to XML
description: DataContractSerializer を使用してオブジェクトをシリアル化および逆シリアル化する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3320ecbf-cdbe-480e-979c-2c14bbef9988
ms.openlocfilehash: 6fcc8f725855386fe987589fe4dde74b06ed60a6
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412009"
---
# <a name="how-to-serialize-using-datacontractserializer-linq-to-xml"></a><span data-ttu-id="abbe7-103">DataContractSerializer を使用してシリアル化する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="abbe7-103">How to serialize using DataContractSerializer (LINQ to XML)</span></span>

<span data-ttu-id="abbe7-104">この記事では、C# および Visual Basic で <xref:System.Runtime.Serialization.DataContractSerializer> を使用してシリアル化と逆シリアル化を行う例を示します。</span><span class="sxs-lookup"><span data-stu-id="abbe7-104">This article shows an example that serializes and deserializes using <xref:System.Runtime.Serialization.DataContractSerializer> in C# and Visual Basic.</span></span>

## <a name="example-create-objects-that-contain-xelement-objects-then-serialize-and-deserialize-them"></a><span data-ttu-id="abbe7-105">例: `XElement` オブジェクトを含むオブジェクトを作成し、それらをシリアル化および逆シリアル化する</span><span class="sxs-lookup"><span data-stu-id="abbe7-105">Example: Create objects that contain `XElement` objects, then serialize and deserialize them</span></span>

<span data-ttu-id="abbe7-106">次の例では、<xref:System.Xml.Linq.XElement> オブジェクトを含んでいる多数のオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="abbe7-106">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="abbe7-107">次に、それらのオブジェクトをテキスト ファイルにシリアル化し、テキスト ファイルから逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="abbe7-107">It then serializes them to text files, and then deserializes them from the text files.</span></span>

```csharp
using System;
using System.Xml;
using System.Xml.Linq;
using System.IO;
using System.Runtime.Serialization;

public class XLinqTest
{
    public static void Main()
    {
        Test<XElement>(CreateXElement());
        Test<XElementContainer>(new XElementContainer());
        Test<XElementNullContainer>(new XElementNullContainer());
    }

    public static void Test<T>(T obj)
    {
        DataContractSerializer s = new DataContractSerializer(typeof(T));
        using (FileStream fs = File.Open("test" + typeof(T).Name + ".xml", FileMode.Create))
        {
            Console.WriteLine("Testing for type: {0}", typeof(T));
            s.WriteObject(fs, obj);
        }
        using (FileStream fs = File.Open("test" + typeof(T).Name + ".xml", FileMode.Open))
        {
            object s2 = s.ReadObject(fs);
            if (s2 == null)
                Console.WriteLine("  Deserialized object is null (Nothing in VB)");
            else
                Console.WriteLine("  Deserialized type: {0}", s2.GetType());
        }
    }

    public static XElement CreateXElement()
    {
        return new XElement(XName.Get("NameInNamespace", "http://www.adventure-works.org"));
    }
}

[DataContract]
public class XElementContainer
{
    [DataMember]
    public XElement member;

    public XElementContainer()
    {
        member = XLinqTest.CreateXElement();
    }
}

[DataContract]
public class XElementNullContainer
{
    [DataMember]
    public XElement member;

    public XElementNullContainer()
    {
        member = null;
    }
}
```

```vb
Imports System
Imports System.Xml
Imports System.Xml.Linq
Imports System.IO
Imports System.Runtime.Serialization

Public Class XLinqTest
    Shared Sub Main()
        Test(Of XElement)(CreateXElement())
        Test(Of XElementContainer)(New XElementContainer())
        Test(Of XElementNullContainer)(New XElementNullContainer())
    End Sub

    Public Shared Sub Test(Of T)(ByRef obj)
        Dim s As DataContractSerializer = New DataContractSerializer(GetType(T))
        Using fs As FileStream = File.Open("test" & GetType(T).Name & ".xml", FileMode.Create)
            Console.WriteLine("Testing for type: {0}", GetType(T))
            s.WriteObject(fs, obj)
        End Using

        Using fs As FileStream = File.Open("test" & GetType(T).Name & ".xml", FileMode.Open)
            Dim s2 As Object = s.ReadObject(fs)
            If s2 Is Nothing Then
                Console.WriteLine("  Deserialized object is null (Nothing in VB)")
            Else
                Console.WriteLine("  Deserialized type: {0}", s2.GetType())
            End If
        End Using
    End Sub

    Public Shared Function CreateXElement() As XElement
        Return New XElement(XName.Get("NameInNamespace", "http://www.adventure-works.org"))
    End Function
End Class

<DataContract()> _
Public Class XElementContainer
    <DataMember()> _
    Public member As XElement

    Public Sub XElementContainer()
        member = XLinqTest.CreateXElement()
    End Sub
End Class

<DataContract()> _
Public Class XElementNullContainer
    <DataMember()> _
    Public member As XElement

    Public Sub XElementNullContainer()
        member = Nothing
    End Sub
End Class
```

 <span data-ttu-id="abbe7-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="abbe7-108">This example produces the following output:</span></span>

```output
Testing for type: System.Xml.Linq.XElement
  Deserialized type: System.Xml.Linq.XElement
Testing for type: XElementContainer
  Deserialized type: XElementContainer
Testing for type: XElementNullContainer
  Deserialized type: XElementNullContainer
```
