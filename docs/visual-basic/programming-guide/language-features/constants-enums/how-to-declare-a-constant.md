---
description: '詳細情報: 方法:定数を宣言する (Visual Basic)'
title: '方法: 定数を宣言する'
ms.date: 07/20/2015
f1_keywords:
- vb.constant
helpviewer_keywords:
- Integer data type [Visual Basic], declaring constants
- Single data type [Visual Basic], declaring constants
- Const statement [Visual Basic], declaring constants
- procedures [Visual Basic], declaration
- data types [Visual Basic], constants
- Long data type [Visual Basic], declaring constants
- Visual Basic code, declaring variables and constants
- Double data type [Visual Basic], declaring constants
- Boolean data type [Visual Basic], declaring constants
- modules, declaring constants
- Byte data type [Visual Basic], declaring constants
- constants [Visual Basic], declaring
- Date data type [Visual Basic], declaring constants
- String data type [Visual Basic], declaring constants
- declaring constants [Visual Basic], const keyword
- Currency data type [Visual Basic], declaring constants and variants
- module-level constants and variables
- Object data type [Visual Basic], declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
ms.openlocfilehash: 42b0ecce90e12a7e777b8e51bc9a23ab454f433d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100477503"
---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="4d873-103">方法: 定数を宣言する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d873-103">How to: Declare A Constant (Visual Basic)</span></span>

<span data-ttu-id="4d873-104">定数とその値を宣言するには、`Const` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="4d873-104">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="4d873-105">定数を宣言することで、値にわかりやすい名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="4d873-105">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="4d873-106">宣言した定数を変更したり、新しい値を割り当てたりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="4d873-106">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="4d873-107">定数の宣言は、プロシージャ内、またはモジュール、クラス、構造体の宣言セクション内で行います。</span><span class="sxs-lookup"><span data-stu-id="4d873-107">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="4d873-108">既定では、クラスレベルまたは構造体レベルの定数は `Private` になりますが、適切なコード アクセス レベルで `Public`、`Friend`、`Protected`、または `Protected Friend` として宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="4d873-108">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="4d873-109">定数には、有効なシンボリック名 (ルールは変数名を作成する場合のものと同じ)、および数値型または文字列型の定数と演算子 (関数呼び出し以外) で構成される式を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d873-109">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="4d873-110">定数を宣言するには</span><span class="sxs-lookup"><span data-stu-id="4d873-110">To declare a constant</span></span>  
  
- <span data-ttu-id="4d873-111">次の例のように、アクセス指定子、`Const` キーワード、式を含んだ宣言を記述します。</span><span class="sxs-lookup"><span data-stu-id="4d873-111">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     <span data-ttu-id="4d873-112">[Option Infer](../../../language-reference/statements/option-infer-statement.md) に `Off` を指定し、[Option Strict](../../../language-reference/statements/option-strict-statement.md) に `On` を指定した場合は、データ型 (`Boolean`、`Byte`、`Char`、`DateTime`、`Decimal`、`Double`、`Integer`、`Long`、`Short`、`Single`、または `String`) を指定して明示的に定数を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d873-112">When [Option Infer](../../../language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="4d873-113">`Option Infer` に `On` を指定するか、`Option Strict` に `Off` を指定している場合は、`As` 句でデータ型を指定することなく定数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="4d873-113">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="4d873-114">コンパイラは、式の型から定数の型を判断します。</span><span class="sxs-lookup"><span data-stu-id="4d873-114">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="4d873-115">詳細については、[定数とリテラルのデータ型](constant-and-literal-data-types.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d873-115">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="4d873-116">データ型を明記した定数を宣言するには</span><span class="sxs-lookup"><span data-stu-id="4d873-116">To declare a constant that has an explicitly stated data type</span></span>  
  
- <span data-ttu-id="4d873-117">次の例のように、`As` キーワードと明示的なデータ型を含む宣言を記述します。</span><span class="sxs-lookup"><span data-stu-id="4d873-117">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     <span data-ttu-id="4d873-118">1 行で複数の定数を宣言することはできますが、1 行に 1 つのみ定数を宣言した方がコードは読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="4d873-118">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="4d873-119">1 行で複数の定数を宣言する場合、すべてに同じアクセス レベルを設定する必要があります (`Public`、`Private`、`Friend`、`Protected`、または `Protected Friend`)。</span><span class="sxs-lookup"><span data-stu-id="4d873-119">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="4d873-120">1 行で複数の定数を宣言するには</span><span class="sxs-lookup"><span data-stu-id="4d873-120">To declare multiple constants on a single line</span></span>  
  
- <span data-ttu-id="4d873-121">次の例に示すように、各宣言をコンマと空白で区切ります。</span><span class="sxs-lookup"><span data-stu-id="4d873-121">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```vb  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4d873-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d873-122">See also</span></span>

- [<span data-ttu-id="4d873-123">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="4d873-123">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)
- [<span data-ttu-id="4d873-124">定数とリテラルのデータ型</span><span class="sxs-lookup"><span data-stu-id="4d873-124">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="4d873-125">定数の概要</span><span class="sxs-lookup"><span data-stu-id="4d873-125">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="4d873-126">方法: 定数を宣言する</span><span class="sxs-lookup"><span data-stu-id="4d873-126">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="4d873-127">ユーザー定義定数</span><span class="sxs-lookup"><span data-stu-id="4d873-127">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="4d873-128">定数とリテラルのデータ型</span><span class="sxs-lookup"><span data-stu-id="4d873-128">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="4d873-129">方法: 関連する定数値をまとめてグループ化する</span><span class="sxs-lookup"><span data-stu-id="4d873-129">How to: Group Related Constant Values Together</span></span>](how-to-group-related-constant-values-together.md)
- [<span data-ttu-id="4d873-130">列挙型の概要</span><span class="sxs-lookup"><span data-stu-id="4d873-130">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="4d873-131">方法: 列挙型を宣言する</span><span class="sxs-lookup"><span data-stu-id="4d873-131">How to: Declare Enumerations</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="4d873-132">方法: 列挙型のメンバーを参照する</span><span class="sxs-lookup"><span data-stu-id="4d873-132">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="4d873-133">列挙型と名前の修飾</span><span class="sxs-lookup"><span data-stu-id="4d873-133">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="4d873-134">方法: 列挙型を反復処理する</span><span class="sxs-lookup"><span data-stu-id="4d873-134">How to: Iterate Through An Enumeration</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="4d873-135">方法: 列挙値に関連付けられている文字列を確認する</span><span class="sxs-lookup"><span data-stu-id="4d873-135">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="4d873-136">列挙型を使用する状況</span><span class="sxs-lookup"><span data-stu-id="4d873-136">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)

- [<span data-ttu-id="4d873-137">列挙型の概要</span><span class="sxs-lookup"><span data-stu-id="4d873-137">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="4d873-138">定数の概要</span><span class="sxs-lookup"><span data-stu-id="4d873-138">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="4d873-139">方法: 列挙型を宣言する</span><span class="sxs-lookup"><span data-stu-id="4d873-139">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="4d873-140">列挙型と名前の修飾</span><span class="sxs-lookup"><span data-stu-id="4d873-140">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="4d873-141">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="4d873-141">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="4d873-142">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="4d873-142">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
