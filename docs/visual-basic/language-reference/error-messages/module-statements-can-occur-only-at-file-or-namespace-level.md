---
description: "詳細情報: BC30617:'Module' ステートメントは、ファイルまたは名前空間レベルでのみ発生します。"
title: "'Module' ステートメントは、ファイルまたは名前空間レベルでのみ発生します。"
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: f5c3ea0cd1c08fb0243043ae50e707e2c59b00f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795782"
---
# <a name="bc30617-module-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="ba3ec-103">BC30617:'Module' ステートメントは、ファイルまたは名前空間レベルでのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="ba3ec-103">BC30617: 'Module' statements can occur only at file or namespace level</span></span>

<span data-ttu-id="ba3ec-104">`Module` ステートメントは、ソース ファイルの先頭の、`Option` および `Imports` ステートメント、グローバル属性、および名前空間宣言の直後、ただし他のすべての宣言の前に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba3ec-104">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>

 <span data-ttu-id="ba3ec-105">**エラー ID:** BC30617</span><span class="sxs-lookup"><span data-stu-id="ba3ec-105">**Error ID:** BC30617</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ba3ec-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="ba3ec-106">To correct this error</span></span>

- <span data-ttu-id="ba3ec-107">`Module` ステートメントを名前空間の宣言またはソース ファイルの先頭に移動します。</span><span class="sxs-lookup"><span data-stu-id="ba3ec-107">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba3ec-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba3ec-108">See also</span></span>

- [<span data-ttu-id="ba3ec-109">Module ステートメント</span><span class="sxs-lookup"><span data-stu-id="ba3ec-109">Module Statement</span></span>](../statements/module-statement.md)
