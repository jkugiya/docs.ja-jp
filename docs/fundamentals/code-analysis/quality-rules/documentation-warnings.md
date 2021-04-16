---
title: ドキュメント規則 (コード分析)
description: コード分析規則のドキュメント規則について
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation rules
- managed code analysis rules, documentation rules
- warnings, documentation
author: mavasani
ms.author: mavasani
ms.openlocfilehash: 29d1734eec29bd00d456b4b00c48c2e8ef223441
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96591280"
---
# <a name="documentation-rules"></a><span data-ttu-id="a6ce1-103">ドキュメント規則</span><span class="sxs-lookup"><span data-stu-id="a6ce1-103">Documentation rules</span></span>

<span data-ttu-id="a6ce1-104">ドキュメント規則では、外部から参照可能な API に [XML ドキュメント コメント](../../../csharp/codedoc.md)を正しく使用することによって、適切にドキュメント化されたライブラリの作成をサポートします。</span><span class="sxs-lookup"><span data-stu-id="a6ce1-104">Documentation rules support writing well-documented libraries through the correct use of [XML documentation comments](../../../csharp/codedoc.md) for externally visible APIs.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a6ce1-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a6ce1-105">In this section</span></span>

| <span data-ttu-id="a6ce1-106">ルール</span><span class="sxs-lookup"><span data-stu-id="a6ce1-106">Rule</span></span> | <span data-ttu-id="a6ce1-107">説明</span><span class="sxs-lookup"><span data-stu-id="a6ce1-107">Description</span></span> |
| - | - |
| [<span data-ttu-id="a6ce1-108">CA1200:プレフィックスで cref タグを使用しません</span><span class="sxs-lookup"><span data-stu-id="a6ce1-108">CA1200: Avoid using cref tags with a prefix</span></span>](ca1200.md) | <span data-ttu-id="a6ce1-109">XML ドキュメント タグの [cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) 属性は "コード参照" を意味します。</span><span class="sxs-lookup"><span data-stu-id="a6ce1-109">The [cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) attribute in an XML documentation tag means "code reference".</span></span> <span data-ttu-id="a6ce1-110">タグの内部テキストが、型、メソッド、プロパティなど、コード要素であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="a6ce1-110">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="a6ce1-111">`cref` タグとプレフィックスを一緒に使用すると、コンパイラで参照を検証できなくなるため、一緒に使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="a6ce1-111">Avoid using `cref` tags with prefixes, because it prevents the compiler from verifying references.</span></span> <span data-ttu-id="a6ce1-112">また、Visual Studio 統合開発環境 (IDE) でリファクタリング中にこれらのシンボル参照を見つけたり、更新したりすることもできなくなります。</span><span class="sxs-lookup"><span data-stu-id="a6ce1-112">It also prevents the Visual Studio integrated development environment (IDE) from finding and updating these symbol references during refactorings.</span></span> |
