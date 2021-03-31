---
description: '詳細情報: System.Xml クラスでの型のサポート'
title: System.Xml クラスでの型のサポート
ms.date: 03/30/2017
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
ms.openlocfilehash: 0cc30a0f3da3aba4533f81ec3360a1f660f1f127
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782898"
---
# <a name="type-support-in-the-systemxml-classes"></a><span data-ttu-id="d8b8a-103">System.Xml クラスでの型のサポート</span><span class="sxs-lookup"><span data-stu-id="d8b8a-103">Type Support in the System.Xml Classes</span></span>

<span data-ttu-id="d8b8a-104">.NET Framework Version 2.0 では、コアの XML クラスが強化され、型サポート機能が追加されています。</span><span class="sxs-lookup"><span data-stu-id="d8b8a-104">In the .NET Framework version 2.0, the core XML classes have been enhanced to include type support features.</span></span> <span data-ttu-id="d8b8a-105"><xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter>、および <xref:System.Xml.XPath.XPathNavigator> クラスには、XML スキーマ型と共通言語ランタイム (CLR) 型の間の変換機能を含む型サポート機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d8b8a-105">The <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes include type support features including the ability to convert between XML Schema types and common language runtime (CLR) types.</span></span>  
  
 <span data-ttu-id="d8b8a-106">.NET Framework Version 2.0 では、<xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter>、および <xref:System.Xml.XPath.XPathNavigator> クラスが強化され、型サポート機能が追加されています。</span><span class="sxs-lookup"><span data-stu-id="d8b8a-106">In the .NET Framework version 2.0, the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes have been enhanced to include type support features.</span></span>  
  
- <span data-ttu-id="d8b8a-107"><xref:System.Xml.XmlReader> および <xref:System.Xml.XPath.XPathNavigator> クラスにはそれぞれ、ノードのスキーマ情報を返す **SchemaInfo** プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d8b8a-107">The <xref:System.Xml.XmlReader> and <xref:System.Xml.XPath.XPathNavigator> classes each include a **SchemaInfo** property that returns the schema information on a node.</span></span>  
  
- <span data-ttu-id="d8b8a-108"><xref:System.Xml.XmlReader> クラスの **ReadContentAs** と **ReadElementContentAs** メソッドは、1 回のメソッド呼び出しでテキスト値を読み取り、それを CLR 値に変換します。</span><span class="sxs-lookup"><span data-stu-id="d8b8a-108">The **ReadContentAs** and **ReadElementContentAs** and methods on the <xref:System.Xml.XmlReader> class read a text value and convert it to a CLR value in a single method call.</span></span>  
  
- <span data-ttu-id="d8b8a-109"><xref:System.Xml.XmlWriter.WriteValue%2A> クラスの <xref:System.Xml.XmlWriter> メソッドは、XML の書き出し時に、CLR 型を XML スキーマ型に変換します。</span><span class="sxs-lookup"><span data-stu-id="d8b8a-109">The <xref:System.Xml.XmlWriter.WriteValue%2A> method on the <xref:System.Xml.XmlWriter> class converts a CLR type to an XML Schema type when writing out XML.</span></span>  
  
- <span data-ttu-id="d8b8a-110"><xref:System.Xml.XPath.XPathNavigator> クラスの **ValueAs** および <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> プロパティは、1 回のメソッド呼び出しでノード値を返し、それを CLR 値に変換します。</span><span class="sxs-lookup"><span data-stu-id="d8b8a-110">The **ValueAs** and <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> properties on the <xref:System.Xml.XPath.XPathNavigator> class return a node value and convert it to a CLR value in a single method call.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8b8a-111">.NET Framework Version 1.0 では、XML スキーマ型と CLR 型の間の変換に <xref:System.Xml.XmlConvert> クラスが必要でした。</span><span class="sxs-lookup"><span data-stu-id="d8b8a-111">In the .NET Framework version 1.0 the <xref:System.Xml.XmlConvert> class was needed to convert between XML Schema and CLR types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d8b8a-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d8b8a-112">In This Section</span></span>  

 [<span data-ttu-id="d8b8a-113">XML データ型から CLR 型へのマッピング</span><span class="sxs-lookup"><span data-stu-id="d8b8a-113">Mapping XML Data Types to CLR Types</span></span>](mapping-xml-data-types-to-clr-types.md)  
 <span data-ttu-id="d8b8a-114">XML データ型から CLR 型への既定のマッピングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d8b8a-114">Describes the default mappings of XML data types to CLR types.</span></span>  
  
 [<span data-ttu-id="d8b8a-115">XML 型サポートの実装に関するメモ</span><span class="sxs-lookup"><span data-stu-id="d8b8a-115">XML Type Support Implementation Notes</span></span>](xml-type-support-implementation-notes.md)  
 <span data-ttu-id="d8b8a-116">型サポート実装の詳細のいくつかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d8b8a-116">Discusses some of the type support implementation details.</span></span>  
  
 [<span data-ttu-id="d8b8a-117">XML データ型の変換</span><span class="sxs-lookup"><span data-stu-id="d8b8a-117">Conversion of XML Data Types</span></span>](conversion-of-xml-data-types.md)  
 <span data-ttu-id="d8b8a-118">XML スキーマ型と CLR 型の間の変換に <xref:System.Xml.XmlConvert> クラスを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d8b8a-118">Describes how to use the <xref:System.Xml.XmlConvert> class to convert between XML Schema and CLR types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d8b8a-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8b8a-119">Related Sections</span></span>  

 [<span data-ttu-id="d8b8a-120">厳密に型指定された XML データへの XPathNavigator を使用したアクセス</span><span class="sxs-lookup"><span data-stu-id="d8b8a-120">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](accessing-strongly-typed-xml-data-using-xpathnavigator.md)
