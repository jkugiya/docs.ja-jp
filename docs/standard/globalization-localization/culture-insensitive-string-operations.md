---
description: '詳細情報: カルチャを認識しない文字列操作'
title: カルチャを認識しない文字列操作
ms.date: 03/30/2017
helpviewer_keywords:
- culture, culture-insensitive string operations
- case-sensitive comparisons
- globalization [.NET], culture-insensitive string operations
- strings [.NET], culture-insensitive string operations
- localization [.NET], culture-insensitive string operations
- world-ready applications, culture-insensitive string operations
- culture-sensitive string operations
- culture-insensitive string operations
ms.assetid: e6e2bb94-a95d-44e2-b68c-cfdd1db77784
ms.openlocfilehash: 40109f7b276b53605634dbb38c265eaee677b76a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702276"
---
# <a name="culture-insensitive-string-operations"></a><span data-ttu-id="f9f3d-103">カルチャを認識しない文字列操作</span><span class="sxs-lookup"><span data-stu-id="f9f3d-103">Culture-insensitive string operations</span></span>

<span data-ttu-id="f9f3d-104">カルチャを認識する文字列操作は、カルチャごとにユーザーに結果を表示するようデザインされたアプリケーションを作成する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f9f3d-104">Culture-sensitive string operations can be an advantage if you are creating applications designed to display results to users on a per-culture basis.</span></span> <span data-ttu-id="f9f3d-105">既定では、カルチャを認識するメソッドは、使用するカルチャを現在のスレッドの <xref:System.Globalization.CultureInfo.CurrentCulture%2A> プロパティから取得します。</span><span class="sxs-lookup"><span data-stu-id="f9f3d-105">By default, culture-sensitive methods obtain the culture to use from the <xref:System.Globalization.CultureInfo.CurrentCulture%2A> property for the current thread.</span></span>

<span data-ttu-id="f9f3d-106">ただし、カルチャを認識する文字列操作が望ましい動作であるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="f9f3d-106">Sometimes, culture-sensitive string operations are not the desired behavior.</span></span> <span data-ttu-id="f9f3d-107">結果をカルチャに依存させない場合に、カルチャを認識する操作を使用すると、カスタムの大文字と小文字の対応規則および並べ替え規則を使用するカルチャでのアプリケーション コードの実行が失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="f9f3d-107">Using culture-sensitive operations when results should be independent of culture can cause application code to fail on cultures with custom case mappings and sorting rules.</span></span> <span data-ttu-id="f9f3d-108">たとえば、「[.NET の文字列を使用するためのベスト プラクティス](../base-types/best-practices-strings.md)」の記事の「[現在のカルチャを使用する文字列比較](../base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9f3d-108">For an example, see the ["String Comparisons that Use the Current Culture"](../base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) section in the [Best Practices for Using Strings](../base-types/best-practices-strings.md) article.</span></span>

<span data-ttu-id="f9f3d-109">文字列操作でカルチャに依存するかどうかは、アプリケーションで結果をどのように使用するかに基づいて決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9f3d-109">Whether string operations should be culture-sensitive or culture-insensitive depends on how your application uses the results.</span></span> <span data-ttu-id="f9f3d-110">ユーザーに結果を表示する場合は、通常、カルチャを認識する文字列操作を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9f3d-110">String operations that display results to the user should typically be culture-sensitive.</span></span> <span data-ttu-id="f9f3d-111">たとえば、アプリケーションがローカライズされた文字列を並べ替えてリスト ボックスに表示する場合は、カルチャを認識する並べ替えを実行します。</span><span class="sxs-lookup"><span data-stu-id="f9f3d-111">For example, if an application displays a sorted list of localized strings in a list box, the application should perform a culture-sensitive sort.</span></span>

<span data-ttu-id="f9f3d-112">内部的に使用される文字列に対する操作は、通常、カルチャを認識しないようにします。</span><span class="sxs-lookup"><span data-stu-id="f9f3d-112">Results of string operations that are used internally should typically be culture-insensitive.</span></span> <span data-ttu-id="f9f3d-113">一般的に、アプリケーションがファイル名、永続形式、エンド ユーザーに表示されないシンボル情報などの処理を実行する場合には、文字列操作の結果がカルチャごとに変わらないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9f3d-113">In general, if the application is working with file names, persistence formats, or symbolic information that is not displayed to the user, results of string operations should not vary by culture.</span></span> <span data-ttu-id="f9f3d-114">たとえば、XML タグとして認識されるかどうかを調べるために文字列を比較するアプリケーションでは、比較操作でカルチャを認識しないでください。</span><span class="sxs-lookup"><span data-stu-id="f9f3d-114">For example, if an application compares a string to determine whether it is a recognized XML tag, the comparison should not be culture-sensitive.</span></span> <span data-ttu-id="f9f3d-115">また、セキュリティに関する決定が文字列の比較操作や大文字と小文字の変更操作の結果に基づいて行われる場合は、この操作がカルチャを認識しないようにして、操作の結果が <xref:System.Globalization.CultureInfo.CurrentCulture%2A> の値に影響されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9f3d-115">In addition, if a security decision is based on the result of a string comparison or case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of <xref:System.Globalization.CultureInfo.CurrentCulture%2A>.</span></span>

<span data-ttu-id="f9f3d-116">開発するアプリケーションにローカリゼーションとグローバリゼーションに対応するためのコードが含まれているかどうかに関係なく、.NET のメソッドは既定ではカルチャを認識する結果を取得することにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="f9f3d-116">Whether or not you're developing an application that includes code to handle localization and globalization issues, you should be aware of the .NET methods that retrieve culture-sensitive results by default.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9f3d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9f3d-117">See also</span></span>

- [<span data-ttu-id="f9f3d-118">グローバライズとローカライズ</span><span class="sxs-lookup"><span data-stu-id="f9f3d-118">Globalization and Localization</span></span>](index.md)
