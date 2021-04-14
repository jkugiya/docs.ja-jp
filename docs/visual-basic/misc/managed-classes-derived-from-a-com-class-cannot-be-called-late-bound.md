---
description: '詳細情報: COM クラスから派生したマネージド クラスは、遅延バインディングされた呼び出しはできません。'
title: COM クラスから派生したマネージド クラスは、遅延バインディングされた呼び出しはできません。
ms.date: 07/20/2015
f1_keywords:
- vbrLateboundCallToInheritedComClass
ms.assetid: 7bc16e84-8d29-4f8e-bc4f-002c65c71099
ms.openlocfilehash: bde124c3e5c52d4c0dbb0e6e1f7250574c83be8d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100430041"
---
# <a name="managed-classes-derived-from-a-com-class-cannot-be-called-late-bound"></a><span data-ttu-id="979f4-103">COM クラスから派生したマネージド クラスは、遅延バインディングされた呼び出しはできません。</span><span class="sxs-lookup"><span data-stu-id="979f4-103">Managed classes derived from a COM class cannot be called late-bound.</span></span>

<span data-ttu-id="979f4-104">COM クラスから派生したマネージド クラスに対して遅延バインディング呼び出しを実施しようとしましたが、このような呼び出しはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="979f4-104">You attempted to make a late-bound call to a managed class derived from a COM Class; such calls are not supported.</span></span>

## <a name="to-correct-the-problem"></a><span data-ttu-id="979f4-105">この問題を解決するには</span><span class="sxs-lookup"><span data-stu-id="979f4-105">To correct the problem</span></span>

<span data-ttu-id="979f4-106">呼び出しを事前バインディングにします。</span><span class="sxs-lookup"><span data-stu-id="979f4-106">Make the call early bound.</span></span>

## <a name="see-also"></a><span data-ttu-id="979f4-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="979f4-107">See also</span></span>

- [<span data-ttu-id="979f4-108">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="979f4-108">Error Types</span></span>](../programming-guide/language-features/error-types.md)
