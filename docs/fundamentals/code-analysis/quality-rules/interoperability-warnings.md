---
title: 移植性と相互運用性の規則 (コード分析)
description: コード分析規則の移植性と相互運用性の規則について
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis rules, interoperability rules, portability rules
- portability rules
- warnings, portability
- interoperability rules
- warnings, interoperability
author: gewarren
ms.author: gewarren
ms.openlocfilehash: a20cd77e13c4a8b95633d129990667f0a8de3ee8
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96591195"
---
# <a name="portability-and-interoperability-rules"></a><span data-ttu-id="6bf4a-103">移植性と相互運用性の規則</span><span class="sxs-lookup"><span data-stu-id="6bf4a-103">Portability and interoperability rules</span></span>

<span data-ttu-id="6bf4a-104">移植性の規則は、異なるプラットフォーム間の移植性をサポートします。</span><span class="sxs-lookup"><span data-stu-id="6bf4a-104">Portability rules support portability across different platforms.</span></span> <span data-ttu-id="6bf4a-105">相互運用性の規則は、COM クライアントとの対話をサポートします。</span><span class="sxs-lookup"><span data-stu-id="6bf4a-105">Interoperability rules support interaction with COM clients.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="6bf4a-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6bf4a-106">In this section</span></span>

| <span data-ttu-id="6bf4a-107">ルール</span><span class="sxs-lookup"><span data-stu-id="6bf4a-107">Rule</span></span> | <span data-ttu-id="6bf4a-108">説明</span><span class="sxs-lookup"><span data-stu-id="6bf4a-108">Description</span></span> |
| - | - |
| [<span data-ttu-id="6bf4a-109">CA1401: P/Invoke は参照可能になりません</span><span class="sxs-lookup"><span data-stu-id="6bf4a-109">CA1401: P/Invokes should not be visible</span></span>](ca1401.md) | <span data-ttu-id="6bf4a-110">パブリック型のパブリック メソッドまたはプロテクト メソッドに、System.Runtime.InteropServices.DllImportAttribute 属性があります (Visual Basic では Declare キーワードでも実装されます)。</span><span class="sxs-lookup"><span data-stu-id="6bf4a-110">A public or protected method in a public type has the System.Runtime.InteropServices.DllImportAttribute attribute (also implemented by the Declare keyword in Visual Basic).</span></span> <span data-ttu-id="6bf4a-111">このようなメソッドは公開しないでください。</span><span class="sxs-lookup"><span data-stu-id="6bf4a-111">Such methods should not be exposed.</span></span> |
| [<span data-ttu-id="6bf4a-112">CA1416:プラットフォームの互換性を検証する</span><span class="sxs-lookup"><span data-stu-id="6bf4a-112">CA1416: Validate platform compatibility</span></span>](ca1416.md) | <span data-ttu-id="6bf4a-113">プラットフォーム依存 API をコンポーネント上で使用すると、一部のプラットフォームでコードが動作しなくなります。</span><span class="sxs-lookup"><span data-stu-id="6bf4a-113">Using platform-dependent APIs on a component makes the code no longer work across all platforms.</span></span> |
| [<span data-ttu-id="6bf4a-114">CA1417: P/Invokes の文字列パラメーターに `OutAttribute` を使用しません</span><span class="sxs-lookup"><span data-stu-id="6bf4a-114">CA1417: Do not use `OutAttribute` on string parameters for P/Invokes</span></span>](ca1417.md) | <span data-ttu-id="6bf4a-115">文字列がインターン処理された文字列で、文字列パラメーターが `OutAttribute` の値で渡された場合、ランタイムが不安定になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6bf4a-115">String parameters passed by value with the `OutAttribute` can destabilize the runtime if the string is an interned string.</span></span> |
