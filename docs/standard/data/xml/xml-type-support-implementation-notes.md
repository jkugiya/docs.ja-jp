---
description: '詳細情報: XML 型サポートの実装に関するメモ'
title: XML 型サポートの実装に関するメモ
ms.date: 03/30/2017
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
ms.openlocfilehash: 52a014f0056b1f78b297ec9289e9748ec7dd392e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782677"
---
# <a name="xml-type-support-implementation-notes"></a><span data-ttu-id="53226-103">XML 型サポートの実装に関するメモ</span><span class="sxs-lookup"><span data-stu-id="53226-103">XML Type Support Implementation Notes</span></span>

<span data-ttu-id="53226-104">このトピックでは、認識しておく必要があるいくつかの実装上の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="53226-104">This topic describes some implementation details that you want to be aware of.</span></span>  
  
## <a name="list-mappings"></a><span data-ttu-id="53226-105">リストのマッピング</span><span class="sxs-lookup"><span data-stu-id="53226-105">List Mappings</span></span>  

 <span data-ttu-id="53226-106"><xref:System.Collections.IList>、<xref:System.Collections.ICollection>、<xref:System.Collections.IEnumerable>、**Type[]** 、<xref:System.String> 型は、XML スキーマ定義言語 (XSD) のリスト型を表現するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="53226-106">The <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Type[]**, and <xref:System.String> types are used to represent XML Schema definition language (XSD) list types.</span></span>  
  
## <a name="union-mappings"></a><span data-ttu-id="53226-107">ユニオンのマッピング</span><span class="sxs-lookup"><span data-stu-id="53226-107">Union Mappings</span></span>  

 <span data-ttu-id="53226-108">ユニオン型は <xref:System.Xml.Schema.XmlAtomicValue> 型または <xref:System.String> 型を使用して表現されます。</span><span class="sxs-lookup"><span data-stu-id="53226-108">Union types are represented using the <xref:System.Xml.Schema.XmlAtomicValue> or <xref:System.String> type.</span></span> <span data-ttu-id="53226-109">したがって、変換前の型または変換後の型は常に <xref:System.String> または <xref:System.Xml.Schema.XmlAtomicValue> のどちらかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="53226-109">The source type or the destination type must therefore always be either <xref:System.String> or <xref:System.Xml.Schema.XmlAtomicValue>.</span></span>  
  
 <span data-ttu-id="53226-110"><xref:System.Xml.Schema.XmlSchemaDatatype> オブジェクトがリスト型を表す場合、このオブジェクトは入力文字列値をリストまたは複数のオブジェクトに変換します。</span><span class="sxs-lookup"><span data-stu-id="53226-110">If the <xref:System.Xml.Schema.XmlSchemaDatatype> object represents a list type the object converts the input string value to a list of one or more objects.</span></span> <span data-ttu-id="53226-111"><xref:System.Xml.Schema.XmlSchemaDatatype> が共用体型を表す場合は、共用体のメンバーの型として入力値が解析されます。</span><span class="sxs-lookup"><span data-stu-id="53226-111">If the <xref:System.Xml.Schema.XmlSchemaDatatype> represents a union type then an attempt is made to parse the input value as a member type of the union.</span></span> <span data-ttu-id="53226-112">解析が失敗した場合は、変換が成功するか他のメンバーの型がなくなるまで、ユニオンの次のメンバーを使用して変換が試行されます。変換を試行するメンバーの型がなくなると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="53226-112">If the parse attempt fails then the conversion is attempted with the next member of the union and so on until the conversion is successful, or there are no other member types to try, in which case an exception is thrown.</span></span>  
  
## <a name="differences-between-clr-and-xml-data-types"></a><span data-ttu-id="53226-113">CLR 型と XML データ型の違い</span><span class="sxs-lookup"><span data-stu-id="53226-113">Differences Between CLR and XML Data Types</span></span>  

 <span data-ttu-id="53226-114">CLR 型と XML データ型の間で発生する可能性のある不一致とその処理方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="53226-114">The following describes certain mismatches that can occur between CLR types and XML data types and how they are handled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53226-115">`xs` プレフィックスは、<https://www.w3.org/2001/XMLSchema> と名前空間の URI にマップされます。</span><span class="sxs-lookup"><span data-stu-id="53226-115">The `xs` prefix is mapped to the <https://www.w3.org/2001/XMLSchema> and namespace URI.</span></span>
  
### <a name="systemtimespan-and-xsduration"></a><span data-ttu-id="53226-116">System.TimeSpan と xs:duration</span><span class="sxs-lookup"><span data-stu-id="53226-116">System.TimeSpan and xs:duration</span></span>  

 <span data-ttu-id="53226-117">`xs:duration` 型は、値は異なるが同等の継続時間値として、部分的な順序付けが行われます。</span><span class="sxs-lookup"><span data-stu-id="53226-117">The `xs:duration` type is partially ordered in that there are certain duration values that are different but equivalent.</span></span> <span data-ttu-id="53226-118">これは、たとえば 1 か月 (P1M) という `xs:duration` 型の値が、32 日 (P32D) より小さく、27 日 (P27D) より大きく、28 日、29 日または 30 日と同等であることを意味します。</span><span class="sxs-lookup"><span data-stu-id="53226-118">This means that for the `xs:duration` type value such as 1 month (P1M) is less than 32 days (P32D), larger than 27 days (P27D) and equivalent to 28, 29 or 30 days.</span></span>  
  
 <span data-ttu-id="53226-119"><xref:System.TimeSpan> クラスは、この部分的な順序付けをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="53226-119">The <xref:System.TimeSpan> class does not support this partial ordering.</span></span> <span data-ttu-id="53226-120">その代わりに、1 年および 1 か月に特定の日数 (それぞれ 365 日と 30 日) を使用します。</span><span class="sxs-lookup"><span data-stu-id="53226-120">Instead, it picks a specific number of days for 1 year and 1 month; 365 days and 30 days respectively.</span></span>  
  
 <span data-ttu-id="53226-121">`xs:duration` 型の詳細については、W3C の「[XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/)」 (XML スキーマ第 2 部: データ型の推奨事項) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53226-121">For more information on the `xs:duration` type, see the W3C [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a><span data-ttu-id="53226-122">xs:time、グレオリオ暦の日付、および System.DateTime</span><span class="sxs-lookup"><span data-stu-id="53226-122">xs:time, Gregorian Date Types, and System.DateTime</span></span>  

 <span data-ttu-id="53226-123">`xs:time` 値が <xref:System.DateTime> オブジェクトにマップされている場合、<xref:System.DateTime.MinValue> フィールドは <xref:System.DateTime> オブジェクトの日付プロパティ (<xref:System.DateTime.Year%2A>、<xref:System.DateTime.Month%2A>、<xref:System.DateTime.Day%2A> など) を可能な最小の <xref:System.DateTime> 値に初期化するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="53226-123">When an `xs:time` value is mapped to a <xref:System.DateTime> object, the <xref:System.DateTime.MinValue> field is used to initialize the date properties of the <xref:System.DateTime> object (such as <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, and <xref:System.DateTime.Day%2A>) to the smallest possible <xref:System.DateTime> value.</span></span>  
  
 <span data-ttu-id="53226-124">同様に、`xs:gMonth`、`xs:gDay`、`xs:gYear`、`xs:gYearMonth`、および `xs:gMonthDay` のインスタンスは、<xref:System.DateTime> オブジェクトにマップされます。</span><span class="sxs-lookup"><span data-stu-id="53226-124">Similarly, instances of `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` and `xs:gMonthDay` are also mapped to a <xref:System.DateTime> object.</span></span> <span data-ttu-id="53226-125"><xref:System.DateTime> オブジェクトの未使用のプロパティは、<xref:System.DateTime.MinValue> の値で初期化されます。</span><span class="sxs-lookup"><span data-stu-id="53226-125">Unused properties on the <xref:System.DateTime> object are initialized to those from <xref:System.DateTime.MinValue>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53226-126">内容が <xref:System.DateTime.Year%2A?displayProperty=nameWithType> として型指定されている場合は、`xs:gMonthDay` 値は信頼できません。</span><span class="sxs-lookup"><span data-stu-id="53226-126">You cannot rely on the <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value when the content is typed as `xs:gMonthDay`.</span></span> <span data-ttu-id="53226-127">この場合、<xref:System.DateTime.Year%2A?displayProperty=nameWithType> 値は常に 1,904 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="53226-127">The <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value is always set to 1904 in this case.</span></span>  
  
### <a name="xsanyuri-and-systemuri"></a><span data-ttu-id="53226-128">xs:anyURI および System.Uri</span><span class="sxs-lookup"><span data-stu-id="53226-128">xs:anyURI and System.Uri</span></span>  

 <span data-ttu-id="53226-129">相対 URI を表す `xs:anyURI` のインスタンスが <xref:System.Uri> にマップされている場合、<xref:System.Uri> オブジェクトには基本 URI がありません。</span><span class="sxs-lookup"><span data-stu-id="53226-129">When an instance of `xs:anyURI` that represents a relative URI is mapped to a <xref:System.Uri>, the <xref:System.Uri> object does not have a base URI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53226-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="53226-130">See also</span></span>

- [<span data-ttu-id="53226-131">System.Xml クラスでの型のサポート</span><span class="sxs-lookup"><span data-stu-id="53226-131">Type Support in the System.Xml Classes</span></span>](type-support-in-the-system-xml-classes.md)
