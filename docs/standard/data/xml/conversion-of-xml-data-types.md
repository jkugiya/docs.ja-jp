---
description: '詳細情報: XML データ型の変換'
title: XML データ型の変換
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
ms.openlocfilehash: 7f7657f3ee290ff88dff1ef869a723c947cbce5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713950"
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="3b7f3-103">XML データ型の変換</span><span class="sxs-lookup"><span data-stu-id="3b7f3-103">Conversion of XML Data Types</span></span>

<span data-ttu-id="3b7f3-104">**XmlConvert** クラスのメソッドのほとんどは、文字列と厳密に型指定された形式との間のデータ変換に使われます。</span><span class="sxs-lookup"><span data-stu-id="3b7f3-104">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly typed formats.</span></span> <span data-ttu-id="3b7f3-105">これらのメソッドはロケールに依存しません。</span><span class="sxs-lookup"><span data-stu-id="3b7f3-105">Methods are locale independent.</span></span> <span data-ttu-id="3b7f3-106">つまり、変換の実行時にはロケールの設定は考慮されません。</span><span class="sxs-lookup"><span data-stu-id="3b7f3-106">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="3b7f3-107">文字列を型として読み込む</span><span class="sxs-lookup"><span data-stu-id="3b7f3-107">Reading String as types</span></span>  

 <span data-ttu-id="3b7f3-108">文字列を読み込んで **DateTime** 型に変換するサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3b7f3-108">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="3b7f3-109">入力として次の XML を使用します。</span><span class="sxs-lookup"><span data-stu-id="3b7f3-109">Given the following XML input:</span></span>  
  
 <span data-ttu-id="3b7f3-110">**入力**</span><span class="sxs-lookup"><span data-stu-id="3b7f3-110">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="3b7f3-111">次のコードは、文字列を **DateTime** 形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="3b7f3-111">This code converts the string to the **DateTime** format:</span></span>  
  
```vb  
reader.ReadStartElement()  
Dim vDateTime As DateTime = XmlConvert.ToDateTime(reader.ReadString())  
Console.WriteLine(vDateTime)  
```  
  
```csharp  
reader.ReadStartElement();  
DateTime vDateTime = XmlConvert.ToDateTime(reader.ReadString());  
Console.WriteLine(vDateTime);  
```  
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="3b7f3-112">文字列を型として書き込む</span><span class="sxs-lookup"><span data-stu-id="3b7f3-112">Writing Strings as types</span></span>  

 <span data-ttu-id="3b7f3-113">**Int32** を読み込んで文字列に変換するサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3b7f3-113">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="3b7f3-114">入力として次の XML を使用します。</span><span class="sxs-lookup"><span data-stu-id="3b7f3-114">Given the following XML input:</span></span>  
  
 <span data-ttu-id="3b7f3-115">**入力**</span><span class="sxs-lookup"><span data-stu-id="3b7f3-115">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="3b7f3-116">次のコードは、**Int32** を **String** に変換します。</span><span class="sxs-lookup"><span data-stu-id="3b7f3-116">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b7f3-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b7f3-117">See also</span></span>

- [<span data-ttu-id="3b7f3-118">文字列の .NET Framework データ型への変換</span><span class="sxs-lookup"><span data-stu-id="3b7f3-118">Converting Strings to .NET Framework Data Types</span></span>](converting-strings-to-dotnet-data-types.md)
- [<span data-ttu-id="3b7f3-119">.NET Framework 型の文字列への変換</span><span class="sxs-lookup"><span data-stu-id="3b7f3-119">Converting .NET Framework Types to Strings</span></span>](converting-dotnet-types-to-strings.md)
