---
title: XmlSerializer を使用してオブジェクトを逆シリアル化する方法
description: オブジェクトを逆シリアル化する方法を説明します。 転送形式によって、ストリーム オブジェクトとファイル オブジェクトのどちらを作成するかが決まります。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
ms.openlocfilehash: c0fb5b2206251d880618a68e5cdb2db2b19c57da
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259513"
---
# <a name="how-to-deserialize-an-object-using-xmlserializer"></a><span data-ttu-id="e0b05-104">XmlSerializer を使用してオブジェクトを逆シリアル化する方法</span><span class="sxs-lookup"><span data-stu-id="e0b05-104">How to deserialize an object using XmlSerializer</span></span>

<span data-ttu-id="e0b05-105">オブジェクトを逆シリアル化する場合、転送形式によって、ストリーム オブジェクトとファイル オブジェクトのどちらを作成するかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="e0b05-105">When you deserialize an object, the transport format determines whether you will create a stream or file object.</span></span> <span data-ttu-id="e0b05-106">転送形式を決定したら、必要に応じて <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> メソッドまたは <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="e0b05-106">After the transport format is determined, you can call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> or <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> methods, as required.</span></span>

## <a name="to-deserialize-an-object"></a><span data-ttu-id="e0b05-107">オブジェクトを逆シリアル化するには</span><span class="sxs-lookup"><span data-stu-id="e0b05-107">To deserialize an object</span></span>

1. <span data-ttu-id="e0b05-108">逆シリアル化するオブジェクトの型を使用して、<xref:System.Xml.Serialization.XmlSerializer> を構築します。</span><span class="sxs-lookup"><span data-stu-id="e0b05-108">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object to deserialize.</span></span>

1. <span data-ttu-id="e0b05-109"><xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> メソッドを呼び出して、オブジェクトのレプリカを生成します。</span><span class="sxs-lookup"><span data-stu-id="e0b05-109">Call the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> method to produce a replica of the object.</span></span> <span data-ttu-id="e0b05-110">逆シリアル化を行う際には、次の例に示すように、返されたオブジェクトを元の型にキャストする必要があります。この例では、オブジェクトをファイルから逆シリアル化しています (ストリームから逆シリアル化することもできます)。</span><span class="sxs-lookup"><span data-stu-id="e0b05-110">When deserializing, you must cast the returned object to the type of the original, as shown in the following example, which deserializes the object from a file (although it could also be deserialized from a stream).</span></span>

    ```vb
    ' Construct an instance of the XmlSerializer with the type
    ' of object that is being deserialized.
    Dim mySerializer As New XmlSerializer(GetType(MySerializableClass))
    ' To read the file, create a FileStream.
    Using myFileStream As New FileStream("myFileName.xml", FileMode.Open)
        ' Call the Deserialize method and cast to the object type.
        Dim myObject = CType( _
             mySerializer.Deserialize(myFileStream), MySerializableClass)
     End Using
    ```

    ```csharp
    // Construct an instance of the XmlSerializer with the type
    // of object that is being deserialized.
    var mySerializer = new XmlSerializer(typeof(MySerializableClass));
    // To read the file, create a FileStream.
    using var myFileStream = new FileStream("myFileName.xml", FileMode.Open);
    // Call the Deserialize method and cast to the object type.
    var myObject = (MySerializableClass)mySerializer.Deserialize(myFileStream);
    ```

## <a name="see-also"></a><span data-ttu-id="e0b05-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0b05-111">See also</span></span>

- [<span data-ttu-id="e0b05-112">XML シリアル化の概要</span><span class="sxs-lookup"><span data-stu-id="e0b05-112">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="e0b05-113">方法: オブジェクトをシリアル化する</span><span class="sxs-lookup"><span data-stu-id="e0b05-113">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
