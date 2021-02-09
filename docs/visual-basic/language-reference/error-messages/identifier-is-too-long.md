---
description: '詳細情報: BC30033:識別子が長すぎます。'
title: 識別子が長すぎます。
ms.date: 07/20/2015
f1_keywords:
- bc30033
- vbc30033
helpviewer_keywords:
- BC30033
ms.assetid: 3d07f6d0-9a2f-49ca-94e8-1e354932e855
ms.openlocfilehash: f2439c4bfc53f906fdc277b0de1faac0941c8808
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796094"
---
# <a name="bc30033-identifier-is-too-long"></a><span data-ttu-id="8a44c-103">BC30033:識別子が長すぎます。</span><span class="sxs-lookup"><span data-stu-id="8a44c-103">BC30033: Identifier is too long</span></span>

<span data-ttu-id="8a44c-104">すべてのプログラミング要素の名前または識別子は、1023 文字に制限されています。</span><span class="sxs-lookup"><span data-stu-id="8a44c-104">The name, or identifier, of every programming element is limited to 1023 characters.</span></span> <span data-ttu-id="8a44c-105">さらに、完全修飾名は 1023 文字を超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="8a44c-105">In addition, a fully qualified name cannot exceed 1023 characters.</span></span> <span data-ttu-id="8a44c-106">つまり、識別子の文字列全体 (`<namespace>.<...>.<namespace>.<class>.<element>`) で、メンバーアクセス演算子 (`.`) 文字を含めて、1023 文字の長さを超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="8a44c-106">This means that the entire identifier string (`<namespace>.<...>.<namespace>.<class>.<element>`) cannot be more than 1023 characters long, including the member-access operator (`.`) characters.</span></span>

 <span data-ttu-id="8a44c-107">**エラー ID:** BC30033</span><span class="sxs-lookup"><span data-stu-id="8a44c-107">**Error ID:** BC30033</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8a44c-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="8a44c-108">To correct this error</span></span>

- <span data-ttu-id="8a44c-109">識別子の長さを短くします。</span><span class="sxs-lookup"><span data-stu-id="8a44c-109">Reduce the length of the identifier.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a44c-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a44c-110">See also</span></span>

- [<span data-ttu-id="8a44c-111">宣言された要素の名前</span><span class="sxs-lookup"><span data-stu-id="8a44c-111">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
