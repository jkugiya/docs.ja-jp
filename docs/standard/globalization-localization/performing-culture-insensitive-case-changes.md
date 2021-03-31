---
description: '詳細情報: カルチャを認識しない大文字と小文字の変更の実行'
title: カルチャを認識しない大文字と小文字の変更の実行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.ToLower method
- culture, case sensitivity
- Char.ToLower method
- case, changing in culture-insensitive strings
- Char.ToUpper method
- culture-insensitive string operations, case changes
- String.ToUpper method
- culture parameter
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
ms.openlocfilehash: 293e221530c3aac64b708d909e3963baf039d02e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675755"
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="db918-103">カルチャを認識しない大文字と小文字の変更の実行</span><span class="sxs-lookup"><span data-stu-id="db918-103">Performing Culture-Insensitive Case Changes</span></span>

<span data-ttu-id="db918-104"><xref:System.String.ToUpper%2A?displayProperty=nameWithType>、<xref:System.String.ToLower%2A?displayProperty=nameWithType>、<xref:System.Char.ToUpper%2A?displayProperty=nameWithType>、<xref:System.Char.ToLower%2A?displayProperty=nameWithType> の各メソッドには、パラメーターを受け取らないオーバーロードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="db918-104">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="db918-105">既定では、パラメーターを使用しないこれらのオーバーロードは、<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> の値に基づいて大文字と小文字の変更を実行します。</span><span class="sxs-lookup"><span data-stu-id="db918-105">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="db918-106">このため、大文字と小文字を区別する結果がカルチャによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="db918-106">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="db918-107">大文字と小文字の変更がカルチャに依存するかどうかを明確にするには、`culture` パラメーターを明示的に指定する必要があるこれらのメソッドのオーバーロードを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db918-107">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="db918-108">大文字と小文字の変更がカルチャに依存する場合は、`CultureInfo.CurrentCulture` パラメーターとして `culture` を指定します。</span><span class="sxs-lookup"><span data-stu-id="db918-108">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="db918-109">大文字と小文字の変更がカルチャに依存しない場合は、`CultureInfo.InvariantCulture` パラメーターとして `culture` を指定します。</span><span class="sxs-lookup"><span data-stu-id="db918-109">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="db918-110">後で検索しやすいように文字列の大文字と小文字を変換する場合があります。</span><span class="sxs-lookup"><span data-stu-id="db918-110">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="db918-111">文字列をこのように使用する場合は、`CultureInfo.InvariantCulture` パラメーターとして `culture` を指定する必要があります。<xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> の値が、大文字と小文字を変更してから検索が実行されるまでの間に変更される可能性があるからです。</span><span class="sxs-lookup"><span data-stu-id="db918-111">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="db918-112">セキュリティに関する決定が文字列の大文字と小文字の変更操作に基づいて行われる場合は、この操作がカルチャに依存しないようにして、操作の結果が `CultureInfo.CurrentCulture` の値により影響されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="db918-112">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="db918-113">カルチャに依存した文字列操作によって矛盾した結果がどのように生成されるかを示す例については、「[文字列を使用するためのベスト プラクティス](../base-types/best-practices-strings.md)」の記事の「現在のカルチャを使用する文字列比較」の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db918-113">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="db918-114">String.ToUpper メソッドと String.ToLower メソッドの使用</span><span class="sxs-lookup"><span data-stu-id="db918-114">Using the String.ToUpper and String.ToLower Methods</span></span>  

 <span data-ttu-id="db918-115">コードをわかりやすくするために、`String.ToUpper` パラメーターを明示的に指定できる `String.ToLower` メソッドと `culture` メソッドのオーバーロードを常に使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="db918-115">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="db918-116">識別子の検索を実行するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="db918-116">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="db918-117">`key.ToLower` 操作は既定ではカルチャを認識しますが、この動作はコードを見ても明確ではありません。</span><span class="sxs-lookup"><span data-stu-id="db918-117">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="db918-118">例</span><span class="sxs-lookup"><span data-stu-id="db918-118">Example</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
   Return internalHashtable(key.ToLower())  
End Function  
```  
  
```csharp  
static object LookupKey(string key)
{  
    return internalHashtable[key.ToLower()];  
}  
```  
  
 <span data-ttu-id="db918-119">`key.ToLower` 操作がカルチャに依存しないようにする場合は、前の例を次のように変更して、大文字と小文字を変更するときに明示的に `CultureInfo.InvariantCulture` を使用します。</span><span class="sxs-lookup"><span data-stu-id="db918-119">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
    Return internalHashtable(key.ToLower(CultureInfo.InvariantCulture))  
End Function  
```  
  
```csharp  
static object LookupKey(string key)
{  
    return internalHashtable[key.ToLower(CultureInfo.InvariantCulture)];  
}  
```  
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="db918-120">Char.ToUpper メソッドと Char.ToLower メソッドの使用</span><span class="sxs-lookup"><span data-stu-id="db918-120">Using the Char.ToUpper and Char.ToLower Methods</span></span>  

 <span data-ttu-id="db918-121">`Char.ToUpper` メソッドおよび `Char.ToLower` メソッドはそれぞれ `String.ToUpper` メソッドおよび `String.ToLower` メソッドと同じ特性を持っていますが、影響を受けるカルチャはトルコ語 (トルコ) およびアゼルバイジャン語 (ラテン、アゼルバイジャン) だけです。</span><span class="sxs-lookup"><span data-stu-id="db918-121">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="db918-122">単一の文字の大文字と小文字の区別が異なるのは、この 2 つのカルチャだけです。</span><span class="sxs-lookup"><span data-stu-id="db918-122">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="db918-123">この固有の大文字と小文字の対応の詳細については、<xref:System.String> クラスに関するトピックの「Casing (大文字と小文字の指定)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db918-123">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="db918-124">コードをわかりやすくし、結果の一貫性を確保するために、`culture` パラメーターを明示的に指定できるこれらのメソッドのオーバーロードを常に使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="db918-124">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db918-125">参照</span><span class="sxs-lookup"><span data-stu-id="db918-125">See also</span></span>

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [<span data-ttu-id="db918-126">カルチャを認識しない文字列操作の実行</span><span class="sxs-lookup"><span data-stu-id="db918-126">Performing Culture-Insensitive String Operations</span></span>](performing-culture-insensitive-string-operations.md)
