---
title: グローバリゼーション規則 (コード分析)
description: コード分析規則のグローバリゼーション規則について
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- rules, globalization
- globalization rules
- globalization [Visual Studio], rules
- managed code analysis rules, globalization rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 83ecc52c5e20e074c6c1aed68204a574494f42d5
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96591595"
---
# <a name="globalization-rules"></a><span data-ttu-id="99801-103">グローバリゼーション規則</span><span class="sxs-lookup"><span data-stu-id="99801-103">Globalization rules</span></span>

<span data-ttu-id="99801-104">グローバリゼーション規則は、国際対応ライブラリおよびアプリケーションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="99801-104">Globalization rules support world-ready libraries and applications.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="99801-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="99801-105">In this section</span></span>

|<span data-ttu-id="99801-106">ルール</span><span class="sxs-lookup"><span data-stu-id="99801-106">Rule</span></span>|<span data-ttu-id="99801-107">説明</span><span class="sxs-lookup"><span data-stu-id="99801-107">Description</span></span>|
|----------|-----------------|
|[<span data-ttu-id="99801-108">CA1303:ローカライズされるパラメーターとしてリテラルを渡さない</span><span class="sxs-lookup"><span data-stu-id="99801-108">CA1303: Do not pass literals as localized parameters</span></span>](ca1303.md)|<span data-ttu-id="99801-109">外部から参照できるメソッドで、.NET コンストラクターまたはメソッドへのパラメーターとして、リテラル文字列を渡しています。その文字列はローカライズ可能です。</span><span class="sxs-lookup"><span data-stu-id="99801-109">An externally visible method passes a string literal as a parameter to a .NET constructor or method, and that string should be localizable.</span></span>|
|[<span data-ttu-id="99801-110">CA1304:CultureInfo を指定します</span><span class="sxs-lookup"><span data-stu-id="99801-110">CA1304: Specify CultureInfo</span></span>](ca1304.md)|<span data-ttu-id="99801-111">System.Globalization.CultureInfo パラメーターを受け入れるオーバーロードを持つメンバーを呼び出しているメソッドまたはコンストラクターが、CultureInfo パラメーターを使用するオーバーロードを呼び出していません。</span><span class="sxs-lookup"><span data-stu-id="99801-111">A method or constructor calls a member that has an overload that accepts a System.Globalization.CultureInfo parameter, and the method or constructor does not call the overload that takes the CultureInfo parameter.</span></span> <span data-ttu-id="99801-112">CultureInfo オブジェクトまたは System.IFormatProvider オブジェクトが指定されない場合、オーバーロードされたメンバーから提示された既定値は、すべてのロケールに効果が及ばない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="99801-112">When a CultureInfo or System.IFormatProvider object is not supplied, the default value that is supplied by the overloaded member might not have the effect that you want in all locales.</span></span>|
|[<span data-ttu-id="99801-113">CA1305:IFormatProvider を指定します</span><span class="sxs-lookup"><span data-stu-id="99801-113">CA1305: Specify IFormatProvider</span></span>](ca1305.md)|<span data-ttu-id="99801-114">System.IFormatProvider パラメーターを受け入れるオーバーロードを持つメンバーを 1 つ以上呼び出しているメソッドまたはコンストラクターが、IFormatProvider パラメーターを使用するオーバーロードを呼び出していません。</span><span class="sxs-lookup"><span data-stu-id="99801-114">A method or constructor calls one or more members that have overloads that accept a System.IFormatProvider parameter, and the method or constructor does not call the overload that takes the IFormatProvider parameter.</span></span> <span data-ttu-id="99801-115">System.Globalization.CultureInfo オブジェクトまたは IFormatProvider オブジェクトが指定されない場合、オーバーロードされたメンバーから提示された既定値は、すべてのロケールに効果が及ばない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="99801-115">When a System.Globalization.CultureInfo or IFormatProvider object is not supplied, the default value that is supplied by the overloaded member might not have the effect that you want in all locales.</span></span>|
|[<span data-ttu-id="99801-116">CA1307:意味を明確にするための StringComparison の指定</span><span class="sxs-lookup"><span data-stu-id="99801-116">CA1307: Specify StringComparison for clarity</span></span>](ca1307.md)|<span data-ttu-id="99801-117">文字列比較演算で、StringComparison パラメーターを設定しないメソッド オーバーロードが使用されています。</span><span class="sxs-lookup"><span data-stu-id="99801-117">A string comparison operation uses a method overload that does not set a StringComparison parameter.</span></span>|
|[<span data-ttu-id="99801-118">CA1308:文字列を大文字に標準化します</span><span class="sxs-lookup"><span data-stu-id="99801-118">CA1308: Normalize strings to uppercase</span></span>](ca1308.md)|<span data-ttu-id="99801-119">文字列は大文字に正規化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99801-119">Strings should be normalized to uppercase.</span></span> <span data-ttu-id="99801-120">小文字への変換時に 1 つの小さい文字グループをラウンド トリップさせることができません。</span><span class="sxs-lookup"><span data-stu-id="99801-120">A small group of characters cannot make a round trip when they are converted to lowercase.</span></span>|
|[<span data-ttu-id="99801-121">CA1309:順序を示す StringComparison を使用します</span><span class="sxs-lookup"><span data-stu-id="99801-121">CA1309: Use ordinal StringComparison</span></span>](ca1309.md)|<span data-ttu-id="99801-122">非言語的な文字列比較演算で、StringComparison パラメーターが Ordinal または OrdinalIgnoreCase に設定されていません。</span><span class="sxs-lookup"><span data-stu-id="99801-122">A string comparison operation that is nonlinguistic does not set the StringComparison parameter to either Ordinal or OrdinalIgnoreCase.</span></span> <span data-ttu-id="99801-123">パラメーターを StringComparison.Ordinal または StringComparison.OrdinalIgnoreCase に明示的に設定することによって、多くの場合、コードの速度、正確さ、および信頼性が向上します。</span><span class="sxs-lookup"><span data-stu-id="99801-123">By explicitly setting the parameter to either StringComparison.Ordinal or StringComparison.OrdinalIgnoreCase, your code often gains speed, becomes more correct, and becomes more reliable.</span></span>|
|[<span data-ttu-id="99801-124">CA1310:正確な StringComparison の指定</span><span class="sxs-lookup"><span data-stu-id="99801-124">CA1310: Specify StringComparison for correctness</span></span>](ca1310.md)|<span data-ttu-id="99801-125">文字列比較演算で、StringComparison パラメーターが設定されておらず、カルチャ固有の文字列比較が既定で使用されるメソッド オーバーロードを使用しています。</span><span class="sxs-lookup"><span data-stu-id="99801-125">A string comparison operation uses a method overload that does not set a StringComparison parameter and uses culture-specific string comparison by default.</span></span>|
|[<span data-ttu-id="99801-126">CA2101: P/Invoke 文字列引数に対してマーシャリングを指定します</span><span class="sxs-lookup"><span data-stu-id="99801-126">CA2101: Specify marshaling for P/Invoke string arguments</span></span>](ca2101.md)|<span data-ttu-id="99801-127">プラットフォーム呼び出しメンバーが、部分信頼の呼び出し元を許可し、文字列パラメーターを持ち、さらにその文字列を明示的にマーシャリングしていません。</span><span class="sxs-lookup"><span data-stu-id="99801-127">A platform invoke member allows for partially trusted callers, has a string parameter, and does not explicitly marshal the string.</span></span> <span data-ttu-id="99801-128">これはセキュリティ上の脆弱性となる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="99801-128">This can cause a potential security vulnerability.</span></span>|
