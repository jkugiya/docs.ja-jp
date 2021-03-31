---
description: '詳細情報: 文字列を .NET データ型に変換する'
title: 文字列から .NET データ型への変換
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
ms.openlocfilehash: 2960657dc4d4a31eed85a9b8af04976692a4dc9f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713937"
---
# <a name="convert-strings-to-net-data-types"></a><span data-ttu-id="9a8a1-103">文字列を .NET データ型に変換する</span><span class="sxs-lookup"><span data-stu-id="9a8a1-103">Convert strings to .NET data types</span></span>

<span data-ttu-id="9a8a1-104">文字列を .NET データ型に変換する場合は、アプリケーションの要件に適合する **XmlConvert** メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-104">If you want to convert a string to a .NET data type, use the **XmlConvert** method that fits the application requirements.</span></span> <span data-ttu-id="9a8a1-105">**XmlConvert** クラスで利用可能なすべての変換メソッドの一覧については、「<xref:System.Xml.XmlConvert>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-105">For a list of all conversion methods available in the **XmlConvert** class, see <xref:System.Xml.XmlConvert>.</span></span>  
  
 <span data-ttu-id="9a8a1-106">**ToString** メソッドから返される文字列は、渡したデータを文字列に変換したものです。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-106">The string returned from the **ToString** method is a string version of the data that is passed in.</span></span> <span data-ttu-id="9a8a1-107">さらに、変換に **XmlConvert** クラスを使用する .NET 型の中には、**System.Convert** クラスのメソッドを使用しないものがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-107">Additionally, there are several .NET types that convert using the **XmlConvert** class yet they do not use the methods in the **System.Convert** class.</span></span> <span data-ttu-id="9a8a1-108">**XmlConvert** クラスは XML Schema (XSD) のデータ型に準拠しており、**XmlConvert** によって変換できるデータ型は決まっています。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-108">The **XmlConvert** class follows the XML Schema (XSD) data type specification and has a data type that the **XmlConvert** can map to.</span></span>  
  
 <span data-ttu-id="9a8a1-109">次の表に、.NET データ型と、XML スキーマ (XSD) のデータ型マッピングを使用した場合に返される文字列を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-109">The following table lists .NET data types and the string types that are returned using XML Schema (XSD) data type mapping.</span></span> <span data-ttu-id="9a8a1-110">これらの .NET 型は、**System.Convert** で処理することはできません。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-110">These .NET types cannot be processed using **System.Convert**.</span></span>  
  
|<span data-ttu-id="9a8a1-111">.NET の種類</span><span class="sxs-lookup"><span data-stu-id="9a8a1-111">.NET type</span></span>|<span data-ttu-id="9a8a1-112">返される文字列</span><span class="sxs-lookup"><span data-stu-id="9a8a1-112">String returned</span></span>|  
|-------------------------|---------------------|  
|<span data-ttu-id="9a8a1-113">ブール型</span><span class="sxs-lookup"><span data-stu-id="9a8a1-113">Boolean</span></span>|<span data-ttu-id="9a8a1-114">"true"、"false"</span><span class="sxs-lookup"><span data-stu-id="9a8a1-114">"true", "false"</span></span>|  
|<span data-ttu-id="9a8a1-115">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="9a8a1-115">Single.PositiveInfinity</span></span>|<span data-ttu-id="9a8a1-116">"INF"</span><span class="sxs-lookup"><span data-stu-id="9a8a1-116">"INF"</span></span>|  
|<span data-ttu-id="9a8a1-117">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="9a8a1-117">Single.NegativeInfinity</span></span>|<span data-ttu-id="9a8a1-118">"-INF"</span><span class="sxs-lookup"><span data-stu-id="9a8a1-118">"-INF"</span></span>|  
|<span data-ttu-id="9a8a1-119">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="9a8a1-119">Double.PositiveInfinity</span></span>|<span data-ttu-id="9a8a1-120">"INF"</span><span class="sxs-lookup"><span data-stu-id="9a8a1-120">"INF"</span></span>|  
|<span data-ttu-id="9a8a1-121">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="9a8a1-121">Double.NegativeInfinity</span></span>|<span data-ttu-id="9a8a1-122">"-INF"</span><span class="sxs-lookup"><span data-stu-id="9a8a1-122">"-INF"</span></span>|  
|<span data-ttu-id="9a8a1-123">DateTime</span><span class="sxs-lookup"><span data-stu-id="9a8a1-123">DateTime</span></span>|<span data-ttu-id="9a8a1-124">形式は、yyyy-MM-ddTHH:mm:sszzzzzz およびそのサブセットです。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-124">Format is "yyyy-MM-ddTHH:mm:sszzzzzz" and its subsets.</span></span>|  
|<span data-ttu-id="9a8a1-125">Timespan</span><span class="sxs-lookup"><span data-stu-id="9a8a1-125">Timespan</span></span>|<span data-ttu-id="9a8a1-126">PnYnMnTnHnMnS の形式。つまり、`P2Y10M15DT10H30M20S` は 2 年 10 か月 15 日 10 時間 30 分 20 秒の期間です。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-126">Format is PnYnMnTnHnMnS that is, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10 hours, 30 minutes, and 20 seconds.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="9a8a1-127">表中の .NET 型を **ToString** メソッドを使用して文字列に変換したときに返される文字列は基本型ではなく、XML スキーマ (XSD) 文字列型です。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-127">If converting any of the .NET types listed in the table to a string using the **ToString** method, the returned string is not the base type, but the XML Schema (XSD) string type.</span></span>  
  
 <span data-ttu-id="9a8a1-128">**DateTime** 値型と **Timespan** 値型の違いは、**DateTime** が瞬間を表すのに対して、**TimeSpan** が時間間隔を表すことです。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-128">The **DateTime** and **Timespan** value type differs in that a **DateTime** represents an instant in time, whereas a **TimeSpan** represents a time interval.</span></span> <span data-ttu-id="9a8a1-129">**DateTime** および **Timespan** の形式は、XML スキーマ (XSD) のデータ型仕様で指定されています。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-129">The **DateTime** and **Timespan** formats are specified in the XML Schema (XSD) data types specification.</span></span> <span data-ttu-id="9a8a1-130">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-130">For example:</span></span>  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim [date] As New DateTime(2001, 8, 4)  
writer.WriteElementString("Date", XmlConvert.ToString([date]))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
DateTime date = new DateTime (2001, 08, 04);  
writer.WriteElementString("Date", XmlConvert.ToString(date));  
```  
  
 <span data-ttu-id="9a8a1-131">**出力**</span><span class="sxs-lookup"><span data-stu-id="9a8a1-131">**Output**</span></span>  
  
 <span data-ttu-id="9a8a1-132">`<Date>2001-08-04T00:00:00</Date>`.</span><span class="sxs-lookup"><span data-stu-id="9a8a1-132">`<Date>2001-08-04T00:00:00</Date>`.</span></span>  
  
 <span data-ttu-id="9a8a1-133">整数を文字列に変換するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-133">The following code converts an integer to a string:</span></span>  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim value As Int32 = 200  
writer.WriteElementString("Number", XmlConvert.ToString(value))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
Int32 value = 200;  
writer.WriteElementString("Number", XmlConvert.ToString(value));  
```  
  
 <span data-ttu-id="9a8a1-134">**出力**</span><span class="sxs-lookup"><span data-stu-id="9a8a1-134">**Output**</span></span>  
  
 `<Number>200</Number>`  
  
 <span data-ttu-id="9a8a1-135">ただし、文字列を **Boolean**、**Single**、または **Double** に変換する場合、返される .NET 型は、**System.Convert** クラスを使用したときに返される型とは異なります。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-135">However, if you are converting a string to **Boolean**, **Single**, or **Double**, the .NET type that's returned is not the same as the type returned when using the **System.Convert** class.</span></span>  
  
## <a name="string-to-boolean"></a><span data-ttu-id="9a8a1-136">String から Boolean</span><span class="sxs-lookup"><span data-stu-id="9a8a1-136">String to Boolean</span></span>  

 <span data-ttu-id="9a8a1-137">**ToBoolean** メソッドを使用して文字列を **Boolean** に変換するときの入力文字列と生成される型の対応を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-137">The following table shows what type is generated for the given input strings, when converting a string to **Boolean** using the **ToBoolean** method.</span></span>  
  
|<span data-ttu-id="9a8a1-138">有効な文字列入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9a8a1-138">Valid string input parameter</span></span>|<span data-ttu-id="9a8a1-139">.NET 出力の種類</span><span class="sxs-lookup"><span data-stu-id="9a8a1-139">.NET output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="9a8a1-140">"true"</span><span class="sxs-lookup"><span data-stu-id="9a8a1-140">"true"</span></span>|<span data-ttu-id="9a8a1-141">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="9a8a1-141">Boolean.True</span></span>|  
|<span data-ttu-id="9a8a1-142">"1"</span><span class="sxs-lookup"><span data-stu-id="9a8a1-142">"1"</span></span>|<span data-ttu-id="9a8a1-143">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="9a8a1-143">Boolean.True</span></span>|  
|<span data-ttu-id="9a8a1-144">"false"</span><span class="sxs-lookup"><span data-stu-id="9a8a1-144">"false"</span></span>|<span data-ttu-id="9a8a1-145">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="9a8a1-145">Boolean.False</span></span>|  
|<span data-ttu-id="9a8a1-146">"0"</span><span class="sxs-lookup"><span data-stu-id="9a8a1-146">"0"</span></span>|<span data-ttu-id="9a8a1-147">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="9a8a1-147">Boolean.False</span></span>|  
  
 <span data-ttu-id="9a8a1-148">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-148">For example, given the following XML:</span></span>  
  
 <span data-ttu-id="9a8a1-149">**入力**</span><span class="sxs-lookup"><span data-stu-id="9a8a1-149">**Input**</span></span>  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>
```  
  
 <span data-ttu-id="9a8a1-150">いずれも次のコードによって解釈することができ、**bvalue** は **System.Boolean.True** になります。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-150">Both can be understood by the following code, and **bvalue** is **System.Boolean.True**:</span></span>  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a><span data-ttu-id="9a8a1-151">String から Single</span><span class="sxs-lookup"><span data-stu-id="9a8a1-151">String to Single</span></span>  

 <span data-ttu-id="9a8a1-152">**ToSingle** メソッドを使用して文字列を **Single** に変換するときの入力文字列と生成される型の対応を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-152">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToSingle** method.</span></span>  
  
|<span data-ttu-id="9a8a1-153">有効な文字列入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9a8a1-153">Valid string input parameter</span></span>|<span data-ttu-id="9a8a1-154">.NET 出力の種類</span><span class="sxs-lookup"><span data-stu-id="9a8a1-154">.NET output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="9a8a1-155">"INF"</span><span class="sxs-lookup"><span data-stu-id="9a8a1-155">"INF"</span></span>|<span data-ttu-id="9a8a1-156">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="9a8a1-156">Single.PositiveInfinity</span></span>|  
|<span data-ttu-id="9a8a1-157">"-INF"</span><span class="sxs-lookup"><span data-stu-id="9a8a1-157">"-INF"</span></span>|<span data-ttu-id="9a8a1-158">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="9a8a1-158">Single.NegativeInfinity</span></span>|  
  
## <a name="string-to-double"></a><span data-ttu-id="9a8a1-159">String から Double</span><span class="sxs-lookup"><span data-stu-id="9a8a1-159">String to Double</span></span>  

 <span data-ttu-id="9a8a1-160">**ToDouble** メソッドを使用して文字列を **Single** に変換するときの入力文字列と生成される型の対応を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-160">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToDouble** method.</span></span>  
  
|<span data-ttu-id="9a8a1-161">有効な文字列入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9a8a1-161">Valid string input parameter</span></span>|<span data-ttu-id="9a8a1-162">.NET 出力の種類</span><span class="sxs-lookup"><span data-stu-id="9a8a1-162">.NET output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="9a8a1-163">"INF"</span><span class="sxs-lookup"><span data-stu-id="9a8a1-163">"INF"</span></span>|<span data-ttu-id="9a8a1-164">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="9a8a1-164">Double.PositiveInfinity</span></span>|  
|<span data-ttu-id="9a8a1-165">"-INF"</span><span class="sxs-lookup"><span data-stu-id="9a8a1-165">"-INF"</span></span>|<span data-ttu-id="9a8a1-166">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="9a8a1-166">Double.NegativeInfinity</span></span>|  
  
 <span data-ttu-id="9a8a1-167">次のコードは、`<Infinity>INF</Infinity>` を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="9a8a1-167">The following code writes `<Infinity>INF</Infinity>`:</span></span>  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a8a1-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a8a1-168">See also</span></span>

- [<span data-ttu-id="9a8a1-169">XML データ型の変換</span><span class="sxs-lookup"><span data-stu-id="9a8a1-169">Conversion of XML Data Types</span></span>](conversion-of-xml-data-types.md)
- [<span data-ttu-id="9a8a1-170">.NET 型から文字列への変換</span><span class="sxs-lookup"><span data-stu-id="9a8a1-170">Converting .NET Types to Strings</span></span>](converting-dotnet-types-to-strings.md)
