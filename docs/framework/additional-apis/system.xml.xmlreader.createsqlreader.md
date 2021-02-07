---
description: 詳細については、「XmlReader」を参照してください。
title: XmlReader Qlreader メソッド (System.Xml)
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: 61d594c0438c86863ce4052387439f5483d8a34c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740435"
---
# <a name="xmlreadercreatesqlreader-method"></a><span data-ttu-id="14a08-103">XmlReader.CreateSqlReader  メソッド</span><span class="sxs-lookup"><span data-stu-id="14a08-103">XmlReader.CreateSqlReader Method</span></span>

<span data-ttu-id="14a08-104">解析のために指定されたストリーム、設定、およびコンテキスト情報を使用して、新しい <xref:System.Xml.XmlReader> インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="14a08-104">Creates a new <xref:System.Xml.XmlReader> instance using the specified stream, settings, and context information for parsing.</span></span>

```csharp
internal static XmlReader CreateSqlReader(Stream input,
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a><span data-ttu-id="14a08-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="14a08-105">Parameters</span></span>

- <span data-ttu-id="14a08-106">`input` <xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="14a08-106">`input` <xref:System.IO.Stream></span></span>  
  <span data-ttu-id="14a08-107">XML データを格納しているストリーム。</span><span class="sxs-lookup"><span data-stu-id="14a08-107">The stream that contains the XML data.</span></span>

- <span data-ttu-id="14a08-108">`settings` <xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="14a08-108">`settings` <xref:System.Xml.XmlReaderSettings></span></span>  
  <span data-ttu-id="14a08-109">新しい <xref:System.Xml.XmlReader> インスタンスの設定。</span><span class="sxs-lookup"><span data-stu-id="14a08-109">The settings for the new <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="14a08-110">この値は、`null` の場合もあります。</span><span class="sxs-lookup"><span data-stu-id="14a08-110">This value can be `null`.</span></span>

- <span data-ttu-id="14a08-111">`inputContext` <xref:System.Xml.XmlParserContext></span><span class="sxs-lookup"><span data-stu-id="14a08-111">`inputContext` <xref:System.Xml.XmlParserContext></span></span>  
  <span data-ttu-id="14a08-112">XML フラグメントの解析に必要なコンテキスト情報。</span><span class="sxs-lookup"><span data-stu-id="14a08-112">The context information required to parse the XML fragment.</span></span> <span data-ttu-id="14a08-113">この値は、`null` の場合もあります。</span><span class="sxs-lookup"><span data-stu-id="14a08-113">This value can be `null`.</span></span>

## <a name="returns"></a><span data-ttu-id="14a08-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="14a08-114">Returns</span></span>

<xref:System.Xml.XmlReader>  
<span data-ttu-id="14a08-115">ストリーム内の XML データの読み取りに使用するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="14a08-115">An object that is used to read the XML data in the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="14a08-116">解説</span><span class="sxs-lookup"><span data-stu-id="14a08-116">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="14a08-117">`XmlReader.CreateSqlReader`メソッドは内部であり、コードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="14a08-117">The `XmlReader.CreateSqlReader` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="14a08-118">Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="14a08-118">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="14a08-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="14a08-119">Requirements</span></span>

<span data-ttu-id="14a08-120">**名前空間:** <xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="14a08-120">**Namespace:** <xref:System.Xml></span></span>

<span data-ttu-id="14a08-121">**アセンブリ:** System.Xml.dll</span><span class="sxs-lookup"><span data-stu-id="14a08-121">**Assembly:** System.Xml.dll</span></span>

<span data-ttu-id="14a08-122">**.NET Framework のバージョン:** 2.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="14a08-122">**.NET Framework versions:** Available since 2.0.</span></span>
