---
description: '詳細情報: Ansi (Visual Basic)'
title: Ansi
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: c93472cbf6a8203f05353e0394b52c44686c0070
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701197"
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="67f20-103">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67f20-103">Ansi (Visual Basic)</span></span>

<span data-ttu-id="67f20-104">Visual Basic では、宣言する外部プロシージャの名前に関係なく、すべての文字列を米国規格協会 (ANSI) 値にマーシャリングする必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="67f20-104">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="67f20-105">プロジェクトの外部で定義されたプロシージャを呼び出すと、Visual Basic コンパイラが、プロシージャを正しく呼び出すために必要な情報にアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="67f20-105">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="67f20-106">この情報には、プロシージャの配置場所、識別方法、呼び出しシーケンスと戻り値の型、および使用される文字列の文字セットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="67f20-106">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="67f20-107">[Declare ステートメント](../statements/declare-statement.md)は、外部プロシージャへの参照を作成し、この必要な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="67f20-107">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="67f20-108">`Declare` ステートメントの `charsetmodifier` 部分では、外部プロシージャの呼び出し時に、文字列をマーシャリングするための文字セット情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="67f20-108">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="67f20-109">また、Visual Basic が外部ファイルで外部プロシージャ名を検索する方法にも影響します。</span><span class="sxs-lookup"><span data-stu-id="67f20-109">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="67f20-110">`Ansi` 修飾子は、Visual Basic がすべての文字列を ANSI 値にマーシャリングする必要があり、検索時に名前を変更せずにプロシージャを検索する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="67f20-110">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="67f20-111">文字セット修飾子が指定されていない場合は、`Ansi` が既定値になります。</span><span class="sxs-lookup"><span data-stu-id="67f20-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67f20-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="67f20-112">Remarks</span></span>  

 <span data-ttu-id="67f20-113">`Ansi` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="67f20-113">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="67f20-114">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="67f20-114">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="67f20-115">スマート デバイス開発者向けのメモ</span><span class="sxs-lookup"><span data-stu-id="67f20-115">Smart Device Developer Notes</span></span>  

 <span data-ttu-id="67f20-116">このキーワードはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="67f20-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67f20-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="67f20-117">See also</span></span>

- [<span data-ttu-id="67f20-118">Auto</span><span class="sxs-lookup"><span data-stu-id="67f20-118">Auto</span></span>](auto.md)
- [<span data-ttu-id="67f20-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="67f20-119">Unicode</span></span>](unicode.md)
- [<span data-ttu-id="67f20-120">キーワード</span><span class="sxs-lookup"><span data-stu-id="67f20-120">Keywords</span></span>](../keywords/index.md)
