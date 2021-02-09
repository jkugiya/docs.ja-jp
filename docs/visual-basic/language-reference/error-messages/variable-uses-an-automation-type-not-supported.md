---
description: '詳細情報: Visual Basic でサポートされていないオートメーションが変数で使用されています。'
title: サポートされていない Automation の型が変数で使用されています
ms.date: 07/20/2015
f1_keywords:
- vbrID458
ms.assetid: bde4f4da-493b-452c-b6e4-1d370edba4cd
ms.openlocfilehash: 9aa8f8a2a49e54c547dc47d38305d40f855b1815
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666148"
---
# <a name="variable-uses-an-automation-type-not-supported-in-visual-basic"></a><span data-ttu-id="771b0-103">Visual Basic でサポートされていないオートメーションが変数で使用されています。</span><span class="sxs-lookup"><span data-stu-id="771b0-103">Variable uses an Automation type not supported in Visual Basic</span></span>

<span data-ttu-id="771b0-104">Visual Basic でサポートされていないデータ型を持つタイプ ライブラリまたはオブジェクト ライブラリに定義された変数を使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="771b0-104">You tried to use a variable defined in a type library or object library that has a data type not supported by Visual Basic.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="771b0-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="771b0-105">To correct this error</span></span>

- <span data-ttu-id="771b0-106">Visual Basic によって認識される型の変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="771b0-106">Use a variable of a type recognized by Visual Basic.</span></span>

     <span data-ttu-id="771b0-107">\- または -</span><span class="sxs-lookup"><span data-stu-id="771b0-107">-or-</span></span>

- <span data-ttu-id="771b0-108">`FileGet` または `FileGetObject` の使用中にこのエラーが発生した場合は、使用しようとしているファイルが `FilePut` または `FilePutObject` と共に書き込まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="771b0-108">If you encounter this error while using `FileGet` or `FileGetObject`, make sure the file you are trying to use was written to with `FilePut` or `FilePutObject`.</span></span>

## <a name="see-also"></a><span data-ttu-id="771b0-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="771b0-109">See also</span></span>

- [<span data-ttu-id="771b0-110">データの種類</span><span class="sxs-lookup"><span data-stu-id="771b0-110">Data Types</span></span>](../data-types/index.md)
