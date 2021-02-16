---
description: '詳細情報: ユーザー定義定数 (Visual Basic)'
title: ユーザー定義定数
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: 290d4122249315ae3c6dc5e18ca4faefecb72044
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100485225"
---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="36f13-103">ユーザー定義定数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36f13-103">User-Defined Constants (Visual Basic)</span></span>

<span data-ttu-id="36f13-104">定数とは、不変の数値または文字列の代わりとなるわかりやすい名前です。</span><span class="sxs-lookup"><span data-stu-id="36f13-104">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="36f13-105">定数に格納された値は、その名が示すとおり、アプリケーションの実行中に変わることはありません。</span><span class="sxs-lookup"><span data-stu-id="36f13-105">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="36f13-106">処理するコントロールまたはコンポーネントで定義されている定数を使用するか、または独自に作成できます。</span><span class="sxs-lookup"><span data-stu-id="36f13-106">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="36f13-107">独自に作成した定数は、"*ユーザー定義*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="36f13-107">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="36f13-108">定数の宣言は、変数名を作成するときと同じガイドラインに従い、`Const` ステートメントを使用して行います。</span><span class="sxs-lookup"><span data-stu-id="36f13-108">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="36f13-109">`Option Strict` に `On` を指定した場合、定数の型を明示的に宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36f13-109">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="36f13-110">Const ステートメントの使用法</span><span class="sxs-lookup"><span data-stu-id="36f13-110">Const Statement Usage</span></span>  

 <span data-ttu-id="36f13-111">`Const` ステートメントでは、数学的な数量または日時の値を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="36f13-111">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 <span data-ttu-id="36f13-112">また、`String` 型の定数を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="36f13-112">It also can define `String` constants:</span></span>  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 <span data-ttu-id="36f13-113">通常、等号右側の式 ( `=` ) には数値またはリテラル文字列を指定しますが、数値または文字列が返される式を指定することもできます (ただし、式に関数の呼び出しは含められません)。</span><span class="sxs-lookup"><span data-stu-id="36f13-113">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="36f13-114">以前に定義した定数をもとに、定数を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="36f13-114">You can even define constants in terms of previously defined constants:</span></span>  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="36f13-115">ユーザー定義定数のスコープ</span><span class="sxs-lookup"><span data-stu-id="36f13-115">Scope of User-Defined Constants</span></span>  

 <span data-ttu-id="36f13-116">`Const` ステートメントのスコープは、同じ場所で宣言されている変数と同じです。</span><span class="sxs-lookup"><span data-stu-id="36f13-116">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="36f13-117">次のいずれかの方法で、スコープを指定できます。</span><span class="sxs-lookup"><span data-stu-id="36f13-117">You can specify scope in any of the following ways:</span></span>  
  
- <span data-ttu-id="36f13-118">プロシージャ内にのみ存在する定数を作成するには、該当するプロシージャ内で宣言します。</span><span class="sxs-lookup"><span data-stu-id="36f13-118">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
- <span data-ttu-id="36f13-119">クラス内のすべてのプロシージャで利用可能で、モジュール外のコードでは利用できない定数を作成するには、そのクラスの宣言セクションで宣言します。</span><span class="sxs-lookup"><span data-stu-id="36f13-119">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="36f13-120">アセンブリのすべてのメンバーで利用可能で、アセンブリのクライアント以外では利用できない定数を作成するには、クラスの宣言セクションで `Friend` キーワードを使用して宣言します。</span><span class="sxs-lookup"><span data-stu-id="36f13-120">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="36f13-121">アプリケーション全体で利用可能な定数を作成するには、クラスの宣言セクションで `Public` キーワードを使用して宣言します。</span><span class="sxs-lookup"><span data-stu-id="36f13-121">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="36f13-122">詳細については、[定数の宣言方法](how-to-declare-a-constant.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="36f13-122">For more information, see [How to: Declare A Constant](how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="36f13-123">循環参照の回避</span><span class="sxs-lookup"><span data-stu-id="36f13-123">Avoiding Circular References</span></span>  

 <span data-ttu-id="36f13-124">定数は別の定数をもとに定義できるため、2 つ以上の定数間で "*サイクル*"、つまり循環参照を生み出してしまうことがあります。</span><span class="sxs-lookup"><span data-stu-id="36f13-124">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="36f13-125">循環参照は、次の例に示すように、パブリック定数が 2 つ以上あり、それぞれが他の定数をもとに定義されている場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="36f13-125">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 <span data-ttu-id="36f13-126">循環参照が発生すると、Visual Basic からコンパイラ エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="36f13-126">If a cycle occurs, Visual Basic generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36f13-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="36f13-127">See also</span></span>

- [<span data-ttu-id="36f13-128">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="36f13-128">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)
- [<span data-ttu-id="36f13-129">定数とリテラルのデータ型</span><span class="sxs-lookup"><span data-stu-id="36f13-129">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="36f13-130">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="36f13-130">Constants and Enumerations</span></span>](index.md)
- [<span data-ttu-id="36f13-131">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="36f13-131">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="36f13-132">列挙型の概要</span><span class="sxs-lookup"><span data-stu-id="36f13-132">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="36f13-133">定数の概要</span><span class="sxs-lookup"><span data-stu-id="36f13-133">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="36f13-134">方法: 列挙型を宣言する</span><span class="sxs-lookup"><span data-stu-id="36f13-134">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="36f13-135">列挙型と名前の修飾</span><span class="sxs-lookup"><span data-stu-id="36f13-135">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="36f13-136">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="36f13-136">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
