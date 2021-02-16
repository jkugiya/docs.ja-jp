---
description: '詳細情報: 列挙型と名前修飾 (Visual Basic)'
title: 列挙型と名前の修飾
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: 83f5b894dad821fea920386be905de0b51f9c42f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100477477"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="fc5c4-103">列挙型と名前修飾 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc5c4-103">Enumerations and Name Qualification (Visual Basic)</span></span>

<span data-ttu-id="fc5c4-104">通常、列挙型のメンバーを参照する場合は、列挙型名でメンバー名を修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc5c4-104">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="fc5c4-105">たとえば、`Days` 列挙型の `Sunday` メンバーを参照するには次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="fc5c4-105">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="fc5c4-106">Imports ステートメントを使用する</span><span class="sxs-lookup"><span data-stu-id="fc5c4-106">Using the Imports Statement</span></span>  

 <span data-ttu-id="fc5c4-107">次の例に示すように、`Imports` ステートメントを名前空間の宣言セクションに追加すれば、完全修飾名を使わずに済みます。</span><span class="sxs-lookup"><span data-stu-id="fc5c4-107">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 <span data-ttu-id="fc5c4-108">`Imports` ステートメントは、参照先のプロジェクトとアセンブリの名前空間名、およびこのステートメントが出現するモジュールと同じプロジェクトに含まれる名前空間名をインポートします。</span><span class="sxs-lookup"><span data-stu-id="fc5c4-108">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="fc5c4-109">このステートメントを追加すると、次の例に示すように、修飾を行うことなく列挙型メンバーを参照できるようになります。</span><span class="sxs-lookup"><span data-stu-id="fc5c4-109">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 <span data-ttu-id="fc5c4-110">関連する定数一式を列挙型にまとめることで、異なるコンテキストで同じ定数名を使用できます。</span><span class="sxs-lookup"><span data-stu-id="fc5c4-110">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="fc5c4-111">たとえば、`Days` 列挙型と `WorkDays` 列挙型の平日を表す定数に同じ名前を使用可能です。</span><span class="sxs-lookup"><span data-stu-id="fc5c4-111">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="fc5c4-112">列挙型と共に `Imports` ステートメントを使用する場合は、あいまいな参照を行わないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="fc5c4-112">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="fc5c4-113">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="fc5c4-113">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 <span data-ttu-id="fc5c4-114">`Monday` が `Days` 列挙型と `Workdays` 列挙型の両方のメンバーである場合、このコードではコンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="fc5c4-114">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="fc5c4-115">あいまいな参照を使うことなく各定数を参照するには、定数名をその列挙型で修飾します。</span><span class="sxs-lookup"><span data-stu-id="fc5c4-115">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="fc5c4-116">次のコードでは、`Days` 列挙型と `WorkDays` 列挙型の `Saturday` 定数を参照しています。</span><span class="sxs-lookup"><span data-stu-id="fc5c4-116">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="fc5c4-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc5c4-117">See also</span></span>

- [<span data-ttu-id="fc5c4-118">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="fc5c4-118">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="fc5c4-119">方法: 列挙型を宣言する</span><span class="sxs-lookup"><span data-stu-id="fc5c4-119">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="fc5c4-120">方法: 列挙型のメンバーを参照する</span><span class="sxs-lookup"><span data-stu-id="fc5c4-120">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="fc5c4-121">方法: Visual Basic で列挙型を反復処理する</span><span class="sxs-lookup"><span data-stu-id="fc5c4-121">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="fc5c4-122">方法: 列挙値に関連付けられている文字列を確認する</span><span class="sxs-lookup"><span data-stu-id="fc5c4-122">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="fc5c4-123">列挙型を使用する状況</span><span class="sxs-lookup"><span data-stu-id="fc5c4-123">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="fc5c4-124">定数とリテラルのデータ型</span><span class="sxs-lookup"><span data-stu-id="fc5c4-124">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="fc5c4-125">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="fc5c4-125">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="fc5c4-126">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="fc5c4-126">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="fc5c4-127">データの種類</span><span class="sxs-lookup"><span data-stu-id="fc5c4-127">Data Types</span></span>](../../../language-reference/data-types/index.md)
