---
title: 注釈 - LINQ to XML
description: LINQ to XML で注釈を使用して、任意の型の任意のオブジェクトを XML ツリー内の任意の XML コンポーネントに関連付ける方法について学習します。
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 80710b3596fc37ed76f23e31d1d781c64d0bc909
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412029"
---
# <a name="linq-to-xml-annotations-linq-to-xml"></a><span data-ttu-id="b5092-103">LINQ to XML の注釈 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="b5092-103">LINQ to XML annotations (LINQ to XML)</span></span>

<span data-ttu-id="b5092-104">LINQ to XML で注釈を使用すると、任意の型の任意のオブジェクトを XML ツリー内の任意の XML コンポーネントに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="b5092-104">Annotations in LINQ to XML enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>

<span data-ttu-id="b5092-105"><xref:System.Xml.Linq.XElement> や <xref:System.Xml.Linq.XAttribute> などの XML コンポーネントに注釈を追加するには、<xref:System.Xml.Linq.XObject.AddAnnotation%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b5092-105">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="b5092-106">注釈は型によって取得します。</span><span class="sxs-lookup"><span data-stu-id="b5092-106">You retrieve annotations by type.</span></span>

<span data-ttu-id="b5092-107">注釈は XML 情報セットの一部ではないことに注意してください。注釈はシリアル化も逆シリアル化もされません。</span><span class="sxs-lookup"><span data-stu-id="b5092-107">Note that annotations aren't part of the XML infoset; they're not serialized or deserialized.</span></span>

## <a name="methods"></a><span data-ttu-id="b5092-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="b5092-108">Methods</span></span>

<span data-ttu-id="b5092-109">注釈を操作する場合は、次のメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b5092-109">You can use the following methods when working with annotations:</span></span>

|<span data-ttu-id="b5092-110">メソッド</span><span class="sxs-lookup"><span data-stu-id="b5092-110">Method</span></span>|<span data-ttu-id="b5092-111">説明</span><span class="sxs-lookup"><span data-stu-id="b5092-111">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="b5092-112">オブジェクトを <xref:System.Xml.Linq.XObject> の注釈の一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="b5092-112">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="b5092-113">指定された型の最初の注釈オブジェクトを <xref:System.Xml.Linq.XObject> から取得します。</span><span class="sxs-lookup"><span data-stu-id="b5092-113">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="b5092-114"><xref:System.Xml.Linq.XObject> について指定された型の注釈のコレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="b5092-114">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="b5092-115">指定された型の注釈を <xref:System.Xml.Linq.XObject> から削除します。</span><span class="sxs-lookup"><span data-stu-id="b5092-115">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
