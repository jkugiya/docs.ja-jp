---
description: '詳細情報: BC30068:Expression は値であるため、代入式のターゲットにすることはできません。'
title: Expression は値であるため、代入式のターゲットにすることはできません。
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: 424ce9cb0183153454bc068e9da940948b737c47
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796367"
---
# <a name="bc30068-expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="a3598-103">BC30068:Expression は値であるため、代入式のターゲットにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a3598-103">BC30068: Expression is a value and therefore cannot be the target of an assignment</span></span>

<span data-ttu-id="a3598-104">ステートメントで式に値を代入しようとしています。</span><span class="sxs-lookup"><span data-stu-id="a3598-104">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="a3598-105">実行時に値を代入できるのは、書き込み可能な変数、プロパティ、または配列要素だけです。</span><span class="sxs-lookup"><span data-stu-id="a3598-105">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="a3598-106">次の例では、このエラーがどのように発生する可能性があるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="a3598-106">The following example illustrates how this error can occur.</span></span>

```vb
Dim yesterday As Integer
ReadOnly maximum As Integer = 45
yesterday + 1 = DatePart(DateInterval.Day, Now)
' The preceding line is an ERROR because of an expression on the left.
maximum = 50
' The preceding line is an ERROR because maximum is declared ReadOnly.
```

<span data-ttu-id="a3598-107">同様の例は、プロパティや配列要素にも当てはまる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a3598-107">Similar examples could apply to properties and array elements.</span></span>

<span data-ttu-id="a3598-108">**間接アクセス。**</span><span class="sxs-lookup"><span data-stu-id="a3598-108">**Indirect Access.**</span></span> <span data-ttu-id="a3598-109">値の型による間接アクセスによって、このエラーが発生することもあります。</span><span class="sxs-lookup"><span data-stu-id="a3598-109">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="a3598-110">次のコード例を考えてみます。ここでは、<xref:System.Windows.Forms.Control.Location%2A> 経由で間接的にアクセスすることによって、<xref:System.Drawing.Point> の値を設定しようとしています。</span><span class="sxs-lookup"><span data-stu-id="a3598-110">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>

```vb
' Assume this code runs inside Form1.
Dim exitButton As New System.Windows.Forms.Button()
exitButton.Text = "Exit this form"
exitButton.Location.X = 140
' The preceding line is an ERROR because of no storage for Location.
```

<span data-ttu-id="a3598-111">前の例の最後のステートメントは、<xref:System.Windows.Forms.Control.Location%2A> プロパティによって返される <xref:System.Drawing.Point> 構造体の一時的な割り当てのみを作成しているため、失敗します。</span><span class="sxs-lookup"><span data-stu-id="a3598-111">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="a3598-112">構造体は値の型であり、一時的な構造体は、ステートメントの実行後に保持されません。</span><span class="sxs-lookup"><span data-stu-id="a3598-112">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="a3598-113">この問題を解決するには、<xref:System.Windows.Forms.Control.Location%2A> の変数を宣言して使用します。これにより、<xref:System.Drawing.Point> 構造体のより永続的な割り当てが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a3598-113">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="a3598-114">次の例に、前の例の最後のステートメントを置き換えることができるコードを示しています。</span><span class="sxs-lookup"><span data-stu-id="a3598-114">The following example shows code that can replace the last statement of the preceding example.</span></span>

```vb
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)
exitButton.Location = exitLocation
```

<span data-ttu-id="a3598-115">**エラー ID:** BC30068</span><span class="sxs-lookup"><span data-stu-id="a3598-115">**Error ID:** BC30068</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="a3598-116">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="a3598-116">To correct this error</span></span>

- <span data-ttu-id="a3598-117">ステートメントで式に値を代入している場合は、式を 1 つの書き込み可能な変数、プロパティ、または配列要素に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a3598-117">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>

- <span data-ttu-id="a3598-118">ステートメントで値の型 (通常は構造体) を介して間接的にアクセスしている場合は、値の型を保持する変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="a3598-118">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>

- <span data-ttu-id="a3598-119">変数に適切な構造体 (またはその他の値の型) を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a3598-119">Assign the appropriate structure (or other value type) to the variable.</span></span>

- <span data-ttu-id="a3598-120">変数を使用してプロパティにアクセスし、それに値を代入します。</span><span class="sxs-lookup"><span data-stu-id="a3598-120">Use the variable to access the property to assign it a value.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3598-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3598-121">See also</span></span>

- [<span data-ttu-id="a3598-122">演算子および式</span><span class="sxs-lookup"><span data-stu-id="a3598-122">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="a3598-123">ステートメント</span><span class="sxs-lookup"><span data-stu-id="a3598-123">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="a3598-124">プロシージャのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="a3598-124">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
