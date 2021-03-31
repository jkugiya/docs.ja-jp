---
description: '詳細情報: XML ドキュメントの作成'
title: XML ドキュメントの作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
ms.openlocfilehash: 825c616fc6c0f7216248ae71e7d7630383d9cfea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782781"
---
# <a name="xml-document-creation"></a>XML ドキュメントの作成

XML ドキュメントは、2 とおりの方法で作成できます。 1 つは、パラメーターを使用せずに **XmlDocument** を作成する方法です。 もう 1 つは、**XmlDocument** の作成時に XmlNameTable をパラメーターとして渡す方法です。 パラメーターを使用せず、新しい空の **XmlDocument** を作成する方法を次の例に示します。  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 ドキュメントを作成すると、**Load** メソッドを使用することにより、文字列、ストリーム、URL、テキスト リーダー、または **XmlReader** から派生したクラスのデータを読み込むことができます。 文字列から XML を読み込む **LoadXML** メソッドという読み込みメソッドもあります。 各種の **Load** メソッドの詳細については、「[XML ドキュメントの DOM への読み込み](reading-an-xml-document-into-the-dom.md)」を参照してください。  
  
 **XmlNameTable** というクラスがあります。 このクラスは、分解された文字列オブジェクトのテーブルです。 このテーブルを使用すると、パーサーは XML ドキュメント内で繰り返されているすべての要素名と属性名に同じ文字列オブジェクトを使用でき、効率が向上します。 **XmlNameTable** は、前述のようにドキュメントの作成時に自動的に作成され、ドキュメントの読み込み時に属性名および要素名と共に読み込まれます。 名前テーブルのあるドキュメントが既に存在し、それらの名前が別のドキュメントで役に立つ場合は、**XmlNameTable** をパラメーターとしてとる **Load** メソッドを使用して新しいドキュメントを作成できます。 このメソッドによるドキュメントの作成時には、別のドキュメントからの既存の **XmlNameTable** と、既に読み込まれているすべての属性および要素が使われます。 XmlNameTable を使用すると、要素名と属性名を効率的に比較できます。 **XmlNameTable** の詳細については、「[XmlNameTable によるオブジェクトの比較](object-comparison-using-xmlnametable.md)」を参照してください。 <xref:System.Xml.XmlNameTable>を参照してください。  
  
## <a name="see-also"></a>関連項目

- [XML ドキュメント オブジェクト モデル (DOM)](xml-document-object-model-dom.md)
