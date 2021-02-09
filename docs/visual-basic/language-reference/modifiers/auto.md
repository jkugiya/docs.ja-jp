---
description: '詳細情報: Auto (Visual Basic)'
title: Auto
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: 9601b6c253d4366c453950b4d8f3c5b2caf3805f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774682"
---
# <a name="auto-visual-basic"></a><span data-ttu-id="519ae-103">Auto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="519ae-103">Auto (Visual Basic)</span></span>

<span data-ttu-id="519ae-104">Visual Basic で、宣言されている外部プロシージャの外部名に基づいて、.NET Framework ルールに従い、文字列をマーシャリングする必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="519ae-104">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="519ae-105">プロジェクトの外部で定義されたプロシージャを呼び出すと、Visual Basic コンパイラが、プロシージャを正しく呼び出すために必要な情報にアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="519ae-105">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="519ae-106">この情報には、プロシージャの配置場所、識別方法、呼び出し元のシーケンスと戻り値の型、および使用されている文字列の文字セットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="519ae-106">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="519ae-107">[Declare ステートメント](../statements/declare-statement.md)は、外部プロシージャへの参照を作成し、この必要な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="519ae-107">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="519ae-108">`Declare` ステートメントの `charsetmodifier` 部分では、外部プロシージャの呼び出し時に、文字列をマーシャリングするための文字セット情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="519ae-108">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="519ae-109">これは、Visual Basic が外部ファイルで外部プロシージャ名を検索する方法にも影響します。</span><span class="sxs-lookup"><span data-stu-id="519ae-109">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="519ae-110">`Auto` 修飾子は、Visual Basic が .NET Framework の規則に従って文字列をマーシャリングし、実行時プラットフォームの基本文字セットを決定して、最初の検索が失敗した場合には外部プロシージャ名を変更する可能性があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="519ae-110">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="519ae-111">詳細については、「[Declare ステートメント](../statements/declare-statement.md)」の「文字セット」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="519ae-111">For more information, see "Character Sets" in [Declare Statement](../statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="519ae-112">文字セット修飾子が指定されていない場合は、`Ansi` が既定値になります。</span><span class="sxs-lookup"><span data-stu-id="519ae-112">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="519ae-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="519ae-113">Remarks</span></span>  

 <span data-ttu-id="519ae-114">`Auto` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="519ae-114">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="519ae-115">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="519ae-115">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="519ae-116">スマート デバイス開発者向けのメモ</span><span class="sxs-lookup"><span data-stu-id="519ae-116">Smart Device Developer Notes</span></span>  

 <span data-ttu-id="519ae-117">このキーワードはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="519ae-117">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="519ae-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="519ae-118">See also</span></span>

- [<span data-ttu-id="519ae-119">Ansi</span><span class="sxs-lookup"><span data-stu-id="519ae-119">Ansi</span></span>](ansi.md)
- [<span data-ttu-id="519ae-120">Unicode</span><span class="sxs-lookup"><span data-stu-id="519ae-120">Unicode</span></span>](unicode.md)
- [<span data-ttu-id="519ae-121">キーワード</span><span class="sxs-lookup"><span data-stu-id="519ae-121">Keywords</span></span>](../keywords/index.md)
