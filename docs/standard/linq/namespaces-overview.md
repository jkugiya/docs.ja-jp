---
title: 名前空間の概要 - LINQ to XML
description: XML 名、XML 名前空間、XML 名前空間のプレフィックス、XName と XNamespace クラスについて学習します。
ms.date: 07/20/2015
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
ms.openlocfilehash: 81fe678a8d6be32461c675cc527595033e826165
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412189"
---
# <a name="namespaces-overview-linq-to-xml"></a>名前空間の概要 (LINQ to XML)

この記事では、*XML 名*、*XML 名前空間*、*XML 名前空間プレフィックス*、<xref:System.Xml.Linq.XName> および <xref:System.Xml.Linq.XNamespace> クラスについて紹介します。

XML 名は、多くの場合、XML プログラミングを複雑にしている原因です。 XML 名は、XML 名前空間 (XML 名前空間 URI) とローカル名で構成されます。 XML 名前空間は、.NET プログラムの名前空間と似ています。 これにより、XML ドキュメントのさまざまな部分の間で名前が競合しないように、要素と属性の名前を一意に修飾できます。 XML 名前空間を宣言した場合、ローカル名を選択できます。これは、その名前空間内でのみ一意である必要があります。

XML 名のもう 1 つの側面は、XML 名前空間プレフィックスであり、これが XML 名を複雑にしている原因の大部分です。 このプレフィックスを使用すると、XML 名前空間に対するショートカットを作成できるため、XML ドキュメントがより簡潔でわかりやすくなります。 しかし、XML プレフィックスの意味はコンテキストによって異なり、複雑さが増します。 たとえば、XML プレフィックス `aw` は、XML ツリーの部分の XML 名前空間や、別の部分の別の名前空間に関連付けられている可能性があります。

C# で LINQ to XML を使用する利点の 1 つは、XML プレフィックスを使用する必要がないという点です。 LINQ to XML で XML ドキュメントを読み込んで解析するときに、各 XML プレフィックスは、対応する XML 名前空間に解決されます。 以後、名前空間を使用するドキュメントの操作時には、ほとんどの場合、名前空間プレフィックスではなく名前空間 URI を通して名前空間にアクセスします。 開発者が LINQ to XML で XML 名を操作するときは、常に完全修飾 XML 名 (つまり XML 名前空間とローカル名) を操作します。 しかし、LINQ to XML では、必要に応じて名前空間プレフィックスを操作したり制御したりすることができます。

Visual Basic および XML リテラルで LINQ to XML を使用する場合は、名前空間内のドキュメントの操作時に名前空間プレフィックスを使用する必要があります。

LINQ to XML で XML 名を表すクラスは <xref:System.Xml.Linq.XName> です。 LINQ to XML API では XML 名が頻繁に出現し、XML 名が必要な場合には必ず <xref:System.Xml.Linq.XName> パラメーターがあります。 しかし、<xref:System.Xml.Linq.XName> を直接操作することはほとんどありません。 <xref:System.Xml.Linq.XName> には、文字列からの暗黙の変換が含まれています。

詳細については、次のトピックを参照してください。 <xref:System.Xml.Linq.XNamespace> および <xref:System.Xml.Linq.XName>
