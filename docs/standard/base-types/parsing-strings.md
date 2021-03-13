---
title: 文字列を型に変換する
description: .NET での文字列の解析について理解します。 解析では、.NET の基本データ型を表す文字列をその基本データ型に変換します。 解析は書式設定の逆の操作です。
ms.date: 03/30/2017
ms.topic: conceptual
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: ff357f8b8225c84e2f6c0e022b269f0ab774dfed
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2021
ms.locfileid: "98692852"
---
# <a name="parse-strings-in-net"></a><span data-ttu-id="fb2a6-105">.NET で文字列を解析する</span><span class="sxs-lookup"><span data-stu-id="fb2a6-105">Parse strings in .NET</span></span>

<span data-ttu-id="fb2a6-106">"*解析*" 操作により、.NET の基本データ型を表す文字列が、その基本データ型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="fb2a6-106">A *parsing* operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="fb2a6-107">たとえば、文字列を浮動小数点数や日付と時刻の値に変換するには、解析操作を使用します。</span><span class="sxs-lookup"><span data-stu-id="fb2a6-107">For example, a parsing operation is used to convert a string to a floating-point number or to a date-and-time value.</span></span> <span data-ttu-id="fb2a6-108">解析操作を実行するには、`Parse` メソッドがよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="fb2a6-108">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="fb2a6-109">解析は書式設定の逆の操作 (基本データ型のその文字列形式への変換を含む) であるため、多くの同じ規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="fb2a6-109">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="fb2a6-110">カルチャに依存する書式情報を指定するために、書式設定で <xref:System.IFormatProvider> インターフェイスを実装するオブジェクトを使用するのと同じように、解析でも <xref:System.IFormatProvider> インターフェイスを実装するオブジェクトを使用し、文字列形式を解釈する方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="fb2a6-110">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="fb2a6-111">詳細については、[型の書式設定](formatting-types.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fb2a6-111">For more information, see [Format types](formatting-types.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="fb2a6-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="fb2a6-112">In This Section</span></span>

 <span data-ttu-id="fb2a6-113">[数値文字列の解析](parsing-numeric.md)</span><span class="sxs-lookup"><span data-stu-id="fb2a6-113">[Parsing Numeric Strings](parsing-numeric.md)</span></span>\
 <span data-ttu-id="fb2a6-114">文字列を .NET 数値型に変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fb2a6-114">Describes how to convert strings into .NET numeric types.</span></span>

 <span data-ttu-id="fb2a6-115">[日付と時刻文字列の解析](parsing-datetime.md)</span><span class="sxs-lookup"><span data-stu-id="fb2a6-115">[Parsing Date and Time Strings](parsing-datetime.md)</span></span>\
 <span data-ttu-id="fb2a6-116">文字列を .NET **DateTime** 型に変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fb2a6-116">Describes how to convert strings into .NET **DateTime** types.</span></span>

 <span data-ttu-id="fb2a6-117">[その他の文字列の解析](parsing-other.md)</span><span class="sxs-lookup"><span data-stu-id="fb2a6-117">[Parsing Other Strings](parsing-other.md)</span></span>\
 <span data-ttu-id="fb2a6-118">文字列を **Char** 型、**Boolean** 型、**Enum** 型に変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fb2a6-118">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>

## <a name="related-sections"></a><span data-ttu-id="fb2a6-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb2a6-119">Related Sections</span></span>

 <span data-ttu-id="fb2a6-120">[型の書式設定](formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="fb2a6-120">[Formatting Types](formatting-types.md)</span></span>\
 <span data-ttu-id="fb2a6-121">書式指定子や書式プロバイダーなどの基本書式の概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="fb2a6-121">Describes basic formatting concepts like format specifiers and format providers.</span></span>

 <span data-ttu-id="fb2a6-122">[.NET での型変換](type-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="fb2a6-122">[Type Conversion in .NET](type-conversion.md)</span></span>\
 <span data-ttu-id="fb2a6-123">型に変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fb2a6-123">Describes how to convert types.</span></span>
