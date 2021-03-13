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
# <a name="how-to-deserialize-an-object-using-xmlserializer"></a>XmlSerializer を使用してオブジェクトを逆シリアル化する方法

オブジェクトを逆シリアル化する場合、転送形式によって、ストリーム オブジェクトとファイル オブジェクトのどちらを作成するかが決定されます。 転送形式を決定したら、必要に応じて <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> メソッドまたは <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> メソッドを呼び出すことができます。

## <a name="to-deserialize-an-object"></a>オブジェクトを逆シリアル化するには

1. 逆シリアル化するオブジェクトの型を使用して、<xref:System.Xml.Serialization.XmlSerializer> を構築します。

1. <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> メソッドを呼び出して、オブジェクトのレプリカを生成します。 逆シリアル化を行う際には、次の例に示すように、返されたオブジェクトを元の型にキャストする必要があります。この例では、オブジェクトをファイルから逆シリアル化しています (ストリームから逆シリアル化することもできます)。

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

## <a name="see-also"></a>関連項目

- [XML シリアル化の概要](introducing-xml-serialization.md)
- [方法: オブジェクトをシリアル化する](how-to-serialize-an-object.md)
