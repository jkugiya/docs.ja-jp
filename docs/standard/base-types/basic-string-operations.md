---
title: .NET の基本的な文字列操作
description: 文字列で実行できる基本的な操作について説明します。
ms.date: 03/30/2017
ms.topic: conceptual
helpviewer_keywords:
- strings [.NET], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
ms.custom: seadec18
ms.openlocfilehash: 92cdba893bee3d4c3e14c73fbf35bdd46da998fb
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2021
ms.locfileid: "98692917"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="a8f4e-103">.NET の基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="a8f4e-103">Basic string operations in .NET</span></span>

<span data-ttu-id="a8f4e-104">アプリケーションは、多くの場合、ユーザー入力に基づいてメッセージを構築することによってユーザーに応答します。</span><span class="sxs-lookup"><span data-stu-id="a8f4e-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="a8f4e-105">たとえば、Web サイトで、新たにログオンしたユーザーに対して、ユーザーの名前を含む特別なメッセージで応答することは珍しいことではありません。</span><span class="sxs-lookup"><span data-stu-id="a8f4e-105">For example, it is not uncommon for websites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span>

<span data-ttu-id="a8f4e-106"><xref:System.String?displayProperty=nameWithType> クラスと <xref:System.Text.StringBuilder?displayProperty=nameWithType> クラスのいくつかのメソッドを使用すると、ユーザー インターフェイスに表示するカスタム文字列を動的に構築できます。</span><span class="sxs-lookup"><span data-stu-id="a8f4e-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="a8f4e-107">これらのメソッドでは、バイト配列から新しい文字列を作成する、文字列の値を比較する、既存の文字列を変更するなどのいくつかの基本的な文字列操作を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="a8f4e-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>

## <a name="related-sections"></a><span data-ttu-id="a8f4e-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8f4e-108">Related sections</span></span>

<span data-ttu-id="a8f4e-109">[.NET での型変換](type-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="a8f4e-109">[Type Conversion in .NET](type-conversion.md)</span></span>\
<span data-ttu-id="a8f4e-110">型を変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8f4e-110">Describes how to convert one type into another type.</span></span>

<span data-ttu-id="a8f4e-111">[型の書式設定](formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="a8f4e-111">[Formatting Types](formatting-types.md)</span></span>\
<span data-ttu-id="a8f4e-112">書式指定子を使用して文字列の書式を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8f4e-112">Describes how to format strings using format specifiers.</span></span>
