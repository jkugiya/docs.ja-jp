---
description: '詳細情報: XmlSchemaCollection を使用した XDR 検証'
title: XmlSchemaCollection を使用した XDR 検証
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00833027-1428-4586-83c1-42f5de3323d1
ms.openlocfilehash: 270626a99fd87f859e8b32bbce522caeba44acdc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782794"
---
# <a name="xdr-validation-with-xmlschemacollection"></a><span data-ttu-id="f781d-103">XmlSchemaCollection を使用した XDR 検証</span><span class="sxs-lookup"><span data-stu-id="f781d-103">XDR Validation with XmlSchemaCollection</span></span>

<span data-ttu-id="f781d-104">検証の基準とする XDR (XML-Data Reduced) スキーマが **XmlSchemaCollection** に格納されている場合、そのスキーマは、XmlSchemaCollection に追加したときに指定された名前空間 URI に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="f781d-104">If the XML-Data Reduced (XDR) schema you are validating against is stored in the **XmlSchemaCollection**, it is associated with the namespace URI specified when the schema was added to the collection.</span></span> <span data-ttu-id="f781d-105">**XmlValidatingReader** は、XML ドキュメント内の名前空間 URI を、コレクション内のその URI に対応するスキーマに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="f781d-105">**XmlValidatingReader** maps the namespace URI in the XML document to the schema that corresponds to that URI in the collection.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f781d-106"><xref:System.Xml.Schema.XmlSchemaCollection> クラスは廃止されており、<xref:System.Xml.Schema.XmlSchemaSet> クラスに置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="f781d-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="f781d-107"><xref:System.Xml.Schema.XmlSchemaSet> クラスの詳細については、「[スキーマをコンパイルするための XmlSchemaSet](xmlschemaset-for-schema-compilation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f781d-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](xmlschemaset-for-schema-compilation.md).</span></span>

<span data-ttu-id="f781d-108">たとえば、XML ドキュメントのルート要素が `<bookstore xmlns="urn:newbooks-schema">` の場合、スキーマを **XmlSchemaCollection** に追加するときに、そのスキーマも、次に示すように同じ名前空間を参照します。</span><span class="sxs-lookup"><span data-stu-id="f781d-108">For example, if the root element of the XML document is `<bookstore xmlns="urn:newbooks-schema">`, when the schema is added to the **XmlSchemaCollection** it references the same namespace, as follows:</span></span>

```vb
xsc.Add("urn:newbooks-schema", "newbooks.xdr")
```

```csharp
xsc.Add("urn:newbooks-schema", "newbooks.xdr");
```

<span data-ttu-id="f781d-109">**XmlTextReader** を受け取り、XDR スキーマ HeadCount.xdr を **XmlSchemaCollection** に追加する **XmlValidatingReader** を作成するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="f781d-109">The following code example creates an **XmlValidatingReader** that takes an **XmlTextReader** and adds an XDR schema, HeadCount.xdr, to the **XmlSchemaCollection**:</span></span>

```vb
Imports System.IO
Imports System.Xml
Imports System.Xml.Schema

Namespace ValidationSample

    Class Sample

        Public Shared Sub Main()
            Dim tr As New XmlTextReader("HeadCount.xml")
            Dim vr As New XmlValidatingReader(tr)

            vr.Schemas.Add("xdrHeadCount", "HeadCount.xdr")
            vr.ValidationType = ValidationType.XDR
            AddHandler vr.ValidationEventHandler, AddressOf ValidationHandler

            While vr.Read()
                PrintTypeInfo(vr)
                If vr.NodeType = XmlNodeType.Element Then
                    While vr.MoveToNextAttribute()
                        PrintTypeInfo(vr)
                    End While
                End If
            End While
            Console.WriteLine("Validation finished")
        End Sub

        Public Shared Sub PrintTypeInfo(vr As XmlValidatingReader)
            If vr.SchemaType IsNot Nothing Then
                If TypeOf vr.SchemaType Is XmlSchemaDatatype Or TypeOf vr.SchemaType Is XmlSchemaSimpleType Then
                    Dim value As Object = vr.ReadTypedValue()
                    Console.WriteLine($"{vr.NodeType}({vr.Name},{value.GetType().Name}):{value}")
                End If
            End If
        End Sub

        Public Shared Sub ValidationHandler(sender As Object, args As ValidationEventArgs)
            Console.WriteLine("***Validation error")
            Console.WriteLine($"Severity:{args.Severity}")
            Console.WriteLine($"Message:{args.Message}")
        End Sub
    End Class
End Namespace
```

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Schema;

namespace ValidationSample
{
    class Sample
    {
        public static void Main()
        {
            var tr = new XmlTextReader("HeadCount.xml");
            var vr = new XmlValidatingReader(tr);

            vr.Schemas.Add("xdrHeadCount", "HeadCount.xdr");
            vr.ValidationType = ValidationType.XDR;
            vr.ValidationEventHandler += new ValidationEventHandler (ValidationHandler);

            while(vr.Read())
            {
                PrintTypeInfo(vr);
                if (vr.NodeType == XmlNodeType.Element)
                {
                   while(vr.MoveToNextAttribute())
                       PrintTypeInfo(vr);
                }
            }
            Console.WriteLine("Validation finished");
        }

        public static void PrintTypeInfo(XmlValidatingReader vr)
        {
            if (vr.SchemaType != null)
            {
                if(vr.SchemaType is XmlSchemaDatatype || vr.SchemaType is XmlSchemaSimpleType)
                {
                    object value = vr.ReadTypedValue();
                    Console.WriteLine($"{vr.NodeType}({vr.Name},{value.GetType().Name}):{value}");
                }
            }
        }

        public static void ValidationHandler(object sender, ValidationEventArgs args)
        {
            Console.WriteLine("***Validation error");
            Console.WriteLine($"\tSeverity:{args.Severity}");
            Console.WriteLine($"\tMessage:{args.Message}");
        }
    }
}
```

<span data-ttu-id="f781d-110">検証対象の入力ファイル *HeadCount.xml* の内容について、次に概略を示します。</span><span class="sxs-lookup"><span data-stu-id="f781d-110">The following outlines the contents of the input file, *HeadCount.xml*, to be validated:</span></span>

```xml
<!--Load HeadCount.xdr in SchemaCollection for Validation-->
<HeadCount xmlns='xdrHeadCount'>
   <Name>Waldo Pepper</Name>
   <Name>Red Pepper</Name>
</HeadCount>
```

<span data-ttu-id="f781d-111">検証の基準とする XDR スキーマ ファイル *HeadCount.xdr* の内容について、次に概略を示します。</span><span class="sxs-lookup"><span data-stu-id="f781d-111">The following outlines the contents of the XDR schema file, *HeadCount.xdr*, to be validated against:</span></span>

```xml
<Schema xmlns="urn:schemas-microsoft-com:xml-data" xmlns:dt="urn:schemas-microsoft-com:datatypes">
   <ElementType name="Name" content="textOnly"/>
   <AttributeType name="Bldg" default="2"/>
   <ElementType name="HeadCount" content="eltOnly">
      <element type="Name"/>
      <attribute type="Bldg"/>
   </ElementType>
</Schema>
```

## <a name="see-also"></a><span data-ttu-id="f781d-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="f781d-112">See also</span></span>

- <xref:System.Xml.XmlValidatingReader.ValidationType%2A>
- [<span data-ttu-id="f781d-113">XmlSchemaCollection スキーマのコンパイル</span><span class="sxs-lookup"><span data-stu-id="f781d-113">XmlSchemaCollection Schema Compilation</span></span>](xmlschemacollection-schema-compilation.md)
