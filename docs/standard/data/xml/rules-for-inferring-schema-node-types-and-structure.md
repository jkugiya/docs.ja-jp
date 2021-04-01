---
description: '詳細情報: スキーマのノード型および構造を推論するときの規則'
title: スキーマのノード型および構造を推論するときの規則
ms.date: 03/30/2017
ms.assetid: d74ce896-717d-4871-8fd9-b070e2f53cb0
ms.openlocfilehash: cbcc60a4c2510fb75aa5194164881f573f1a688f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783028"
---
# <a name="rules-for-inferring-schema-node-types-and-structure"></a><span data-ttu-id="47b50-103">スキーマのノード型および構造を推論するときの規則</span><span class="sxs-lookup"><span data-stu-id="47b50-103">Rules for Inferring Schema Node Types and Structure</span></span>

<span data-ttu-id="47b50-104">このトピックでは、スキーマ推論プロセスで、XML ドキュメント内のノード型を XML スキーマ定義言語 (XSD) 構造に変換する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="47b50-104">This topic describes how the schema inference process translates the node types in an XML document to an XML Schema definition language (XSD) structure.</span></span>  
  
## <a name="element-inference-rules"></a><span data-ttu-id="47b50-105">要素を推論するときの規則</span><span class="sxs-lookup"><span data-stu-id="47b50-105">Element Inference Rules</span></span>  

 <span data-ttu-id="47b50-106">このセクションでは、要素宣言を推論するときの規則を説明します。</span><span class="sxs-lookup"><span data-stu-id="47b50-106">This section describes the inference rules for element declarations.</span></span> <span data-ttu-id="47b50-107">推論される要素宣言には 8 つの構造があります。</span><span class="sxs-lookup"><span data-stu-id="47b50-107">There are eight structures of element declarations that will be inferred:</span></span>  
  
1. <span data-ttu-id="47b50-108">単純型の要素</span><span class="sxs-lookup"><span data-stu-id="47b50-108">Element of simple type</span></span>  
  
2. <span data-ttu-id="47b50-109">空要素</span><span class="sxs-lookup"><span data-stu-id="47b50-109">Empty element</span></span>  
  
3. <span data-ttu-id="47b50-110">属性を持つ空要素</span><span class="sxs-lookup"><span data-stu-id="47b50-110">Empty element with attributes</span></span>  
  
4. <span data-ttu-id="47b50-111">属性と単純内容を持つ要素</span><span class="sxs-lookup"><span data-stu-id="47b50-111">Element with attributes and simple content</span></span>  
  
5. <span data-ttu-id="47b50-112">子要素のシーケンスを持つ要素</span><span class="sxs-lookup"><span data-stu-id="47b50-112">Element with a sequence of child elements</span></span>  
  
6. <span data-ttu-id="47b50-113">子要素のシーケンスと属性を持つ要素</span><span class="sxs-lookup"><span data-stu-id="47b50-113">Element with a sequence of child elements and attributes</span></span>  
  
7. <span data-ttu-id="47b50-114">子要素のシーケンスと choice を持つ要素</span><span class="sxs-lookup"><span data-stu-id="47b50-114">Element with a sequence of choices of child elements</span></span>  
  
8. <span data-ttu-id="47b50-115">子要素のシーケンスと choice を持つ要素</span><span class="sxs-lookup"><span data-stu-id="47b50-115">Element with a sequence of choices of child elements and attributes</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47b50-116">すべての `complexType` 宣言は匿名型として推論されます。</span><span class="sxs-lookup"><span data-stu-id="47b50-116">All `complexType` declarations are inferred as anonymous types.</span></span> <span data-ttu-id="47b50-117">推論されるグローバル要素はルート要素だけであり、その他すべての要素はローカル要素です。</span><span class="sxs-lookup"><span data-stu-id="47b50-117">The only global element inferred is the root element; all other elements are local.</span></span>  
  
 <span data-ttu-id="47b50-118">スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](inferring-schemas-from-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47b50-118">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
### <a name="simple-typed-element"></a><span data-ttu-id="47b50-119">単純型要素</span><span class="sxs-lookup"><span data-stu-id="47b50-119">Simple Typed Element</span></span>  

 <span data-ttu-id="47b50-120"><xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="47b50-120">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="47b50-121">太字になっている要素は、単純型要素から推論されるスキーマです。</span><span class="sxs-lookup"><span data-stu-id="47b50-121">The bolded element shows the schema inferred for the simple type element.</span></span>  
  
 <span data-ttu-id="47b50-122">スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](inferring-schemas-from-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47b50-122">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="47b50-123">XML</span><span class="sxs-lookup"><span data-stu-id="47b50-123">XML</span></span>|<span data-ttu-id="47b50-124">Schema</span><span class="sxs-lookup"><span data-stu-id="47b50-124">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>text</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root" type="xs:string" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element"></a><span data-ttu-id="47b50-125">空の要素</span><span class="sxs-lookup"><span data-stu-id="47b50-125">Empty Element</span></span>  

 <span data-ttu-id="47b50-126"><xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="47b50-126">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="47b50-127">太字になっている要素は、空要素から推論されるスキーマです。</span><span class="sxs-lookup"><span data-stu-id="47b50-127">The bolded element shows the schema inferred for the empty element.</span></span>  
  
 <span data-ttu-id="47b50-128">スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](inferring-schemas-from-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47b50-128">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="47b50-129">XML</span><span class="sxs-lookup"><span data-stu-id="47b50-129">XML</span></span>|<span data-ttu-id="47b50-130">Schema</span><span class="sxs-lookup"><span data-stu-id="47b50-130">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element-with-attributes"></a><span data-ttu-id="47b50-131">属性を持つ空要素</span><span class="sxs-lookup"><span data-stu-id="47b50-131">Empty Element with Attributes</span></span>  

 <span data-ttu-id="47b50-132"><xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="47b50-132">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="47b50-133">太字になっている要素は、属性を持つ空要素から推論されるスキーマです。</span><span class="sxs-lookup"><span data-stu-id="47b50-133">The bolded elements show the schema inferred for the empty element with attributes.</span></span>  
  
 <span data-ttu-id="47b50-134">スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](inferring-schemas-from-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47b50-134">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="47b50-135">XML</span><span class="sxs-lookup"><span data-stu-id="47b50-135">XML</span></span>|<span data-ttu-id="47b50-136">Schema</span><span class="sxs-lookup"><span data-stu-id="47b50-136">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty attribute1="text"/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-attributes-and-simple-content"></a><span data-ttu-id="47b50-137">属性と単純内容を持つ要素</span><span class="sxs-lookup"><span data-stu-id="47b50-137">Element with Attributes and Simple Content</span></span>  

 <span data-ttu-id="47b50-138"><xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="47b50-138">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="47b50-139">太字になっている要素は、属性と単純内容を持つ要素から推論されるスキーマです。</span><span class="sxs-lookup"><span data-stu-id="47b50-139">The bolded elements show the schema inferred for an element with attributes and simple content.</span></span>  
  
 <span data-ttu-id="47b50-140">スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](inferring-schemas-from-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47b50-140">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="47b50-141">XML</span><span class="sxs-lookup"><span data-stu-id="47b50-141">XML</span></span>|<span data-ttu-id="47b50-142">Schema</span><span class="sxs-lookup"><span data-stu-id="47b50-142">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">value</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:simpleContent>`<br /><br /> `<xs:extension base="xs:string">`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:extension>`<br /><br /> `</xs:simpleContent>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements"></a><span data-ttu-id="47b50-143">子要素のシーケンスを持つ要素</span><span class="sxs-lookup"><span data-stu-id="47b50-143">Element with a Sequence of Child Elements</span></span>  

 <span data-ttu-id="47b50-144"><xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="47b50-144">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="47b50-145">太字になっている要素は、子要素のシーケンスを持つ要素から推論されるスキーマです。</span><span class="sxs-lookup"><span data-stu-id="47b50-145">The bolded elements show the schema inferred for an element with a sequence of child elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47b50-146">要素が子要素を 1 つしか持っていない場合でも、子要素はシーケンスとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="47b50-146">Even if an element has only one child element, it is still treated as a sequence.</span></span>  
  
 <span data-ttu-id="47b50-147">スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](inferring-schemas-from-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47b50-147">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="47b50-148">XML</span><span class="sxs-lookup"><span data-stu-id="47b50-148">XML</span></span>|<span data-ttu-id="47b50-149">Schema</span><span class="sxs-lookup"><span data-stu-id="47b50-149">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement" />`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements-and-attributes"></a><span data-ttu-id="47b50-150">子要素のシーケンスと属性を持つ要素</span><span class="sxs-lookup"><span data-stu-id="47b50-150">Element with a Sequence of Child Elements and Attributes</span></span>  

 <span data-ttu-id="47b50-151"><xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="47b50-151">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="47b50-152">太字になっている要素は、子要素のシーケンスと属性を持つ要素から推論されるスキーマです。</span><span class="sxs-lookup"><span data-stu-id="47b50-152">The bolded elements show the schema inferred for an element with a sequence of child elements and attributes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47b50-153">要素が子要素を 1 つしか持っていない場合でも、子要素はシーケンスとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="47b50-153">Even if an element has only one child element, it is still treated as a sequence.</span></span>  
  
 <span data-ttu-id="47b50-154">スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](inferring-schemas-from-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47b50-154">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="47b50-155">XML</span><span class="sxs-lookup"><span data-stu-id="47b50-155">XML</span></span>|<span data-ttu-id="47b50-156">Schema</span><span class="sxs-lookup"><span data-stu-id="47b50-156">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choices-of-child-elements"></a><span data-ttu-id="47b50-157">子要素のシーケンスと choice を持つ要素</span><span class="sxs-lookup"><span data-stu-id="47b50-157">Element with a Sequence and Choices of Child Elements</span></span>  

 <span data-ttu-id="47b50-158"><xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="47b50-158">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="47b50-159">太字になっているスキーマは、子要素のシーケンスと choice を持つ要素から推論されるスキーマです。</span><span class="sxs-lookup"><span data-stu-id="47b50-159">The bolded elements show the schema inferred for an element with a sequence and choice of child elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47b50-160">`maxOccurs` 要素の `xs:choice` 属性は、推論されるスキーマでは `"unbounded"` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="47b50-160">The `maxOccurs` attribute of the `xs:choice` element is set to `"unbounded"` in the inferred schema.</span></span>  
  
 <span data-ttu-id="47b50-161">スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](inferring-schemas-from-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47b50-161">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="47b50-162">XML</span><span class="sxs-lookup"><span data-stu-id="47b50-162">XML</span></span>|<span data-ttu-id="47b50-163">Schema</span><span class="sxs-lookup"><span data-stu-id="47b50-163">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choice-of-child-elements-and-attributes"></a><span data-ttu-id="47b50-164">子要素のシーケンスと choice および属性を持つ要素</span><span class="sxs-lookup"><span data-stu-id="47b50-164">Element with a Sequence and Choice of Child Elements and Attributes</span></span>  

 <span data-ttu-id="47b50-165"><xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="47b50-165">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="47b50-166">太字になっている要素は、子要素のシーケンスと choice および属性を持つ要素から推論されるスキーマです。</span><span class="sxs-lookup"><span data-stu-id="47b50-166">The bolded elements show the schema inferred for an element with a sequence and choice of child elements and attributes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47b50-167">`maxOccurs` 要素の `xs:choice` 属性は、推論されるスキーマでは `"unbounded"` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="47b50-167">The `maxOccurs` attribute of the `xs:choice` element is set to `"unbounded"` in the inferred schema.</span></span>  
  
 <span data-ttu-id="47b50-168">スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](inferring-schemas-from-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47b50-168">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="47b50-169">XML</span><span class="sxs-lookup"><span data-stu-id="47b50-169">XML</span></span>|<span data-ttu-id="47b50-170">Schema</span><span class="sxs-lookup"><span data-stu-id="47b50-170">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="attribute-processing"></a><span data-ttu-id="47b50-171">属性の処理</span><span class="sxs-lookup"><span data-stu-id="47b50-171">Attribute Processing</span></span>  

 <span data-ttu-id="47b50-172">ノード内で新しい属性が検出されるたびに、その属性は推論されるノードの定義に `use="required"` として追加されます。</span><span class="sxs-lookup"><span data-stu-id="47b50-172">Whenever a new attribute is encountered within a node, it is added to the inferred definition of the node with `use="required"`.</span></span> <span data-ttu-id="47b50-173">そのインスタンスで同じノードが再び検出されると、推論プロセスでは、現在のインスタンスの属性と、既に推論されている属性を比較します。</span><span class="sxs-lookup"><span data-stu-id="47b50-173">The next time the same node is found in the instance, the inference process will compare attributes of the current instance with the ones already inferred.</span></span> <span data-ttu-id="47b50-174">既に推論されている属性の一部がインスタンスにない場合は、属性の定義に `use="optional"` が追加されます。</span><span class="sxs-lookup"><span data-stu-id="47b50-174">If some of the already inferred ones are missing in the instance, `use="optional"` is added to the attribute definition.</span></span> <span data-ttu-id="47b50-175">新しい属性は、既存の宣言に `use="optional"` として追加されます。</span><span class="sxs-lookup"><span data-stu-id="47b50-175">New attributes are added to existing declarations with `use="optional"`.</span></span>  
  
### <a name="occurrence-constraints"></a><span data-ttu-id="47b50-176">出現回数に関する制約</span><span class="sxs-lookup"><span data-stu-id="47b50-176">Occurrence Constraints</span></span>  

 <span data-ttu-id="47b50-177">スキーマ推論プロセスでは、推論されるスキーマのコンポーネントに対して、値が `minOccurs` または `maxOccurs` の `"0"` 属性と、値が `"1"` または `"1"` の `"unbounded"` 属性が生成されます。</span><span class="sxs-lookup"><span data-stu-id="47b50-177">During the schema inference process, the `minOccurs` and `maxOccurs` attributes are generated, for inferred components of a schema, with the values `"0"` or `"1"` and `"1"` or `"unbounded"`.</span></span> <span data-ttu-id="47b50-178">値 `"1"` および `"unbounded"` は、値 `"0"` および `"1"` では XML ドキュメントを検証できない場合にのみ使われます (たとえば、`MinOccurs="0"` では要素を正確に記述できない場合は、`minOccurs="1"` が使われます)。</span><span class="sxs-lookup"><span data-stu-id="47b50-178">The values `"1"` and `"unbounded"` are used only when the values `"0"` and `"1"` cannot validate the XML document (for example, if `MinOccurs="0"` does not accurately describe an element, `minOccurs="1"` is used).</span></span>  
  
### <a name="mixed-content"></a><span data-ttu-id="47b50-179">混合コンテンツ</span><span class="sxs-lookup"><span data-stu-id="47b50-179">Mixed Content</span></span>  

 <span data-ttu-id="47b50-180">テキストに要素が混じっているなど、要素に混合コンテンツが含まれている場合は、推論される複合型の定義に対して `mixed="true"` 属性が生成されます。</span><span class="sxs-lookup"><span data-stu-id="47b50-180">If an element contains mixed content (for example text interspersed with elements), the `mixed="true"` attribute is generated for the inferred complex type definition.</span></span>  
  
## <a name="other-node-type-inference-rules"></a><span data-ttu-id="47b50-181">その他のノードの型推論規則</span><span class="sxs-lookup"><span data-stu-id="47b50-181">Other Node Type Inference Rules</span></span>  

 <span data-ttu-id="47b50-182">処理命令、コメント、エンティティ参照、CDATA、ドキュメント型、名前空間の各ノード型に関する推論の規則を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="47b50-182">The following table describes the inference rules for processing instruction, comment, entity reference, CDATA, document type, and namespace nodes.</span></span>  
  
|<span data-ttu-id="47b50-183">ノード型</span><span class="sxs-lookup"><span data-stu-id="47b50-183">Node Type</span></span>|<span data-ttu-id="47b50-184">変換</span><span class="sxs-lookup"><span data-stu-id="47b50-184">Translation</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="47b50-185">処理命令</span><span class="sxs-lookup"><span data-stu-id="47b50-185">Processing instruction</span></span>|<span data-ttu-id="47b50-186">無視されます。</span><span class="sxs-lookup"><span data-stu-id="47b50-186">Ignored.</span></span>|  
|<span data-ttu-id="47b50-187">コメント</span><span class="sxs-lookup"><span data-stu-id="47b50-187">Comment</span></span>|<span data-ttu-id="47b50-188">無視されます。</span><span class="sxs-lookup"><span data-stu-id="47b50-188">Ignored.</span></span>|  
|<span data-ttu-id="47b50-189">エンティティ参照</span><span class="sxs-lookup"><span data-stu-id="47b50-189">Entity reference</span></span>|<span data-ttu-id="47b50-190"><xref:System.Xml.Schema.XmlSchemaInference> クラスではエンティティ参照を処理しません。</span><span class="sxs-lookup"><span data-stu-id="47b50-190">The <xref:System.Xml.Schema.XmlSchemaInference> class does not handle entity references.</span></span> <span data-ttu-id="47b50-191">XML ドキュメントにエンティティ参照が含まれている場合は、エンティティを展開するリーダーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47b50-191">If an XML document contains entity references, you need to use a reader that expands the entities.</span></span> <span data-ttu-id="47b50-192">たとえば、<xref:System.Xml.XmlTextReader> プロパティを <xref:System.Xml.XmlTextReader.EntityHandling%2A> に設定した <xref:System.Xml.EntityHandling.ExpandEntities> をパラメーターとして渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="47b50-192">For example, you can pass an <xref:System.Xml.XmlTextReader> with the <xref:System.Xml.XmlTextReader.EntityHandling%2A> property set to <xref:System.Xml.EntityHandling.ExpandEntities> as a parameter.</span></span> <span data-ttu-id="47b50-193">エンティティ参照が検出されたにもかかわらず、リーダーがエンティティを展開しない場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="47b50-193">If entity references are encountered and the reader does not expand entities, an exception is throw.</span></span>|  
|<span data-ttu-id="47b50-194">CDATA</span><span class="sxs-lookup"><span data-stu-id="47b50-194">CDATA</span></span>|<span data-ttu-id="47b50-195">XML ドキュメント内のすべての `<![CDATA[ … ]]` セクションが `xs:string` として推論されます。</span><span class="sxs-lookup"><span data-stu-id="47b50-195">Any `<![CDATA[ … ]]` sections in an XML document will be inferred as `xs:string`.</span></span>|  
|<span data-ttu-id="47b50-196">ドキュメント型</span><span class="sxs-lookup"><span data-stu-id="47b50-196">Document type</span></span>|<span data-ttu-id="47b50-197">無視されます。</span><span class="sxs-lookup"><span data-stu-id="47b50-197">Ignored.</span></span>|  
|<span data-ttu-id="47b50-198">名前空間</span><span class="sxs-lookup"><span data-stu-id="47b50-198">Namespaces</span></span>|<span data-ttu-id="47b50-199">無視されます。</span><span class="sxs-lookup"><span data-stu-id="47b50-199">Ignored.</span></span>|  
  
 <span data-ttu-id="47b50-200">スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](inferring-schemas-from-xml-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47b50-200">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b50-201">関連項目</span><span class="sxs-lookup"><span data-stu-id="47b50-201">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaInference>
- [<span data-ttu-id="47b50-202">XML スキーマ オブジェクト モデル (SOM)</span><span class="sxs-lookup"><span data-stu-id="47b50-202">XML Schema Object Model (SOM)</span></span>](xml-schema-object-model-som.md)
- [<span data-ttu-id="47b50-203">XML スキーマの推論</span><span class="sxs-lookup"><span data-stu-id="47b50-203">Inferring an XML Schema</span></span>](inferring-an-xml-schema.md)
- [<span data-ttu-id="47b50-204">XML ドキュメントからのスキーマの推論</span><span class="sxs-lookup"><span data-stu-id="47b50-204">Inferring Schemas from XML Documents</span></span>](inferring-schemas-from-xml-documents.md)
- [<span data-ttu-id="47b50-205">単純型を推論するときの規則</span><span class="sxs-lookup"><span data-stu-id="47b50-205">Rules for Inferring Simple Types</span></span>](rules-for-inferring-simple-types.md)
