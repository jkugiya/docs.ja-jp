---
title: "\"Null\" 検査設定"
description: Null チェックの基本設定のコード分析言語規則について説明します
ms.date: 09/30/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 86d5f4c9b640c92b11706b56a9d14955d6e24857
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2020
ms.locfileid: "96593773"
---
# <a name="null-checking-preferences"></a><span data-ttu-id="0e23c-103">"Null" 検査設定</span><span class="sxs-lookup"><span data-stu-id="0e23c-103">Null-checking preferences</span></span>

## <a name="net-null-checking-preferences"></a><span data-ttu-id="0e23c-104">.NET の null チェックの基本設定</span><span class="sxs-lookup"><span data-stu-id="0e23c-104">.NET null-checking preferences</span></span>

<span data-ttu-id="0e23c-105">このセクションのスタイルルールでは、C# と Visual Basic に共通する次の null チェック設定について考慮します。</span><span class="sxs-lookup"><span data-stu-id="0e23c-105">The style rules in this section concern the following null-checking preferences that are common to C# and Visual Basic:</span></span>

- [<span data-ttu-id="0e23c-106">結合式を使用する (IDE0029 および IDE0030)</span><span class="sxs-lookup"><span data-stu-id="0e23c-106">Use coalesce expression (IDE0029 and IDE0030)</span></span>](ide0029-ide0030.md)
- [<span data-ttu-id="0e23c-107">Null の反映を使用する (IDE0031)</span><span class="sxs-lookup"><span data-stu-id="0e23c-107">Use null propagation (IDE0031)</span></span>](ide0031.md)
- [<span data-ttu-id="0e23c-108">Is null チェックを使用する (IDE0041)</span><span class="sxs-lookup"><span data-stu-id="0e23c-108">Use is null check (IDE0041)</span></span>](ide0041.md)

## <a name="c-null-checking-preferences"></a><span data-ttu-id="0e23c-109">C# の null チェックのユーザー設定</span><span class="sxs-lookup"><span data-stu-id="0e23c-109">C# null-checking preferences</span></span>

<span data-ttu-id="0e23c-110">このセクションのスタイルルールでは、C# に固有の次の null チェック設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="0e23c-110">The style rules in this section concern the following null-checking preferences that are specific to C#:</span></span>

- [<span data-ttu-id="0e23c-111">Throw 式 (IDE0016) を使用する</span><span class="sxs-lookup"><span data-stu-id="0e23c-111">Use throw expression (IDE0016)</span></span>](ide0016.md)
- [<span data-ttu-id="0e23c-112">条件付き代理呼び出しを使用する (IDE1005)</span><span class="sxs-lookup"><span data-stu-id="0e23c-112">Use conditional delegate call (IDE1005)</span></span>](ide1005.md)

## <a name="see-also"></a><span data-ttu-id="0e23c-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e23c-113">See also</span></span>

- [<span data-ttu-id="0e23c-114">コードスタイル規則のリファレンス</span><span class="sxs-lookup"><span data-stu-id="0e23c-114">Code style rules reference</span></span>](index.md)
- [<span data-ttu-id="0e23c-115">コードスタイルの言語規則</span><span class="sxs-lookup"><span data-stu-id="0e23c-115">Code style language rules</span></span>](language-rules.md)