---
description: '詳細情報: Unicode (Visual Basic)'
title: Unicode
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: b0c71d8fdefe3f0d240201e0d57265e5c6081d50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700716"
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="b76e0-103">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b76e0-103">Unicode (Visual Basic)</span></span>

<span data-ttu-id="b76e0-104">Visual Basic では、宣言する外部プロシージャの名前に関係なく、すべての文字列を Unicode 値にマーシャリングする必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="b76e0-104">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="b76e0-105">プロジェクトの外側に定義されたプロシージャを呼び出すと、Visual Basic コンパイラは、プロシージャを正しく呼び出すために必要な情報にアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="b76e0-105">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="b76e0-106">この情報には、プロシージャの配置場所、識別方法、呼び出し元のシーケンスと戻り値の型、および使用されている文字列の文字セットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b76e0-106">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="b76e0-107">[Declare ステートメント](../statements/declare-statement.md)は、外部プロシージャへの参照を作成し、この必要な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="b76e0-107">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="b76e0-108">`Declare` ステートメントの `charsetmodifier` 部分では、外部プロシージャの呼び出し時に文字列をマーシャリングするための文字セット情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="b76e0-108">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="b76e0-109">これは、Visual Basic が外部ファイルで外部プロシージャ名を検索する方法にも影響します。</span><span class="sxs-lookup"><span data-stu-id="b76e0-109">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="b76e0-110">`Unicode` 修飾子は、Visual Basic がすべての文字列を Unicode 値にマーシャリングする必要があり、検索時に名前を変更せずにプロシージャを検索する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b76e0-110">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="b76e0-111">文字セット修飾子が指定されていない場合は、`Ansi` が既定値になります。</span><span class="sxs-lookup"><span data-stu-id="b76e0-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b76e0-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="b76e0-112">Remarks</span></span>  

 <span data-ttu-id="b76e0-113">`Unicode` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b76e0-113">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="b76e0-114">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="b76e0-114">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="b76e0-115">スマート デバイス開発者向けのメモ</span><span class="sxs-lookup"><span data-stu-id="b76e0-115">Smart Device Developer Notes</span></span>  

 <span data-ttu-id="b76e0-116">このキーワードはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="b76e0-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b76e0-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b76e0-117">See also</span></span>

- [<span data-ttu-id="b76e0-118">Ansi</span><span class="sxs-lookup"><span data-stu-id="b76e0-118">Ansi</span></span>](ansi.md)
- [<span data-ttu-id="b76e0-119">Auto</span><span class="sxs-lookup"><span data-stu-id="b76e0-119">Auto</span></span>](auto.md)
- [<span data-ttu-id="b76e0-120">キーワード</span><span class="sxs-lookup"><span data-stu-id="b76e0-120">Keywords</span></span>](../keywords/index.md)
