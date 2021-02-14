---
description: '詳細情報: ?. および ?() Null 条件演算子 (Visual Basic)'
title: Null 条件演算子
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: 558b8921d0da4089505dd1035cb6039af24a2802
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665368"
---
# <a name="-and--null-conditional-operators-visual-basic"></a><span data-ttu-id="336e1-104">?.</span><span class="sxs-lookup"><span data-stu-id="336e1-104">?.</span></span> <span data-ttu-id="336e1-105">および ?() Null 条件演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="336e1-105">and ?() null-conditional operators (Visual Basic)</span></span>

<span data-ttu-id="336e1-106">メンバー アクセス (`?.`) またはインデックス (`?()`) 演算を実行する前に、左の演算子の値で null (`Nothing`) のテストを行います。左側のオペランドが `Nothing` に評価されると、`Nothing` が返されます。</span><span class="sxs-lookup"><span data-stu-id="336e1-106">Tests the value of the left-hand operand for null (`Nothing`) before performing a member access (`?.`) or index (`?()`) operation; returns `Nothing` if the left-hand operand evaluates to `Nothing`.</span></span> <span data-ttu-id="336e1-107">通常、値の型を返す式では、Null 条件演算子は <xref:System.Nullable%601> を返します。</span><span class="sxs-lookup"><span data-stu-id="336e1-107">Note that in expressions that ordinarily return value types, the null-conditional operator returns a <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="336e1-108">これらの演算子を使用すると、少ないコードで null チェックを処理することができます (特に、データ構造を下っていく場合)。</span><span class="sxs-lookup"><span data-stu-id="336e1-108">These operators help you write less code to handle null checks, especially when descending into data structures.</span></span> <span data-ttu-id="336e1-109">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="336e1-109">For example:</span></span>

```vb
' Nothing if customers is Nothing
Dim length As Integer? = customers?.Length

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()
```

<span data-ttu-id="336e1-110">比較のために、Null 条件演算子を使用しない最初の式の代替コードは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="336e1-110">For comparison, the alternative code for the first of these expressions without a null-conditional operator is:</span></span>

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

<span data-ttu-id="336e1-111">(次の例のブール型プロパティ `IsAllowedFreeShipping` のように、) オブジェクトのブール型メンバーの値に基づいて、null の可能性があるオブジェクトに対してアクションを実行する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="336e1-111">Sometimes you need to take an action on an object that may be null, based on the value of a Boolean member on that object (like the Boolean property `IsAllowedFreeShipping` in the following example):</span></span>

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer IsNot Nothing AndAlso customer.IsAllowedFreeShipping Then
  ApplyFreeShippingToOrders(customer)
End If
```

<span data-ttu-id="336e1-112">次のように Null 条件演算子を使用することで、コードを短縮し、手動での null のチェックを回避できます。</span><span class="sxs-lookup"><span data-stu-id="336e1-112">You can shorten your code and avoid manually checking for null by using the null-conditional operator as follows:</span></span>

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer?.IsAllowedFreeShipping Then ApplyFreeShippingToOrders(customer)
```

<span data-ttu-id="336e1-113">Null 条件演算子はショートサーキットです。</span><span class="sxs-lookup"><span data-stu-id="336e1-113">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="336e1-114">条件付きメンバー アクセスとインデックス演算のチェーンにある 1 つの演算で `Nothing` が返されると、チェーンの実行の残りの部分は停止します。</span><span class="sxs-lookup"><span data-stu-id="336e1-114">If one operation in a chain of conditional member access and index operations returns `Nothing`, the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="336e1-115">次の例で、`A`、`B`、または `C` が `Nothing` に評価されると、`C(E)` は評価されません。</span><span class="sxs-lookup"><span data-stu-id="336e1-115">In the following example, `C(E)` isn't evaluated if `A`, `B`, or `C` evaluates to `Nothing`.</span></span>

```vb
A?.B?.C?(E)
```

<span data-ttu-id="336e1-116">Null 条件メンバー アクセスのもう 1 つの用途は、はるかに少ないコードを使ってスレッドセーフな方法でデリゲートを呼び出すことです。</span><span class="sxs-lookup"><span data-stu-id="336e1-116">Another use for null-conditional member access is to invoke delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="336e1-117">次の例では、`NewsBroadcaster` と `NewsReceiver` の 2 つの型を定義しています。</span><span class="sxs-lookup"><span data-stu-id="336e1-117">The following example defines two types, a `NewsBroadcaster` and a `NewsReceiver`.</span></span> <span data-ttu-id="336e1-118">ニュース項目は、`NewsBroadcaster.SendNews` デリゲートによって受信者に送信されます。</span><span class="sxs-lookup"><span data-stu-id="336e1-118">News items are sent to the receiver by the `NewsBroadcaster.SendNews` delegate.</span></span>

```vb
Public Module NewsBroadcaster
   Dim SendNews As Action(Of String)

   Public Sub Main()
      Dim rec As New NewsReceiver()
      Dim rec2 As New NewsReceiver()
      SendNews?.Invoke("Just in: A newsworthy item...")
   End Sub

   Public Sub Register(client As Action(Of String))
      SendNews = SendNews.Combine({SendNews, client})
   End Sub
End Module

Public Class NewsReceiver
   Public Sub New()
      NewsBroadcaster.Register(AddressOf Me.DisplayNews)
   End Sub

   Public Sub DisplayNews(newsItem As String)
      Console.WriteLine(newsItem)
   End Sub
End Class
```

<span data-ttu-id="336e1-119">`SendNews` 呼び出しリストに要素がない場合、`SendNews` デリゲートは <xref:System.NullReferenceException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="336e1-119">If there are no elements in the `SendNews` invocation list, the `SendNews` delegate throws a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="336e1-120">Null 条件演算子の前は、次のようなコードによって、デリゲート呼び出しリストが `Nothing` でないことが確認されました。</span><span class="sxs-lookup"><span data-stu-id="336e1-120">Before null conditional operators, code like the following ensured that the delegate invocation list was not `Nothing`:</span></span>

```vb
SendNews = SendNews.Combine({SendNews, client})
If SendNews IsNot Nothing Then
   SendNews("Just in...")
End If
```

<span data-ttu-id="336e1-121">新しい方法は格段に単純です。</span><span class="sxs-lookup"><span data-stu-id="336e1-121">The new way is much simpler:</span></span>

```vb
SendNews = SendNews.Combine({SendNews, client})
SendNews?.Invoke("Just in...")
```

<span data-ttu-id="336e1-122">コンパイラが `SendNews` を評価するためのコードを一度しか生成せず、一時変数に結果が保持されるため、新しい方法はスレッド セーフです。</span><span class="sxs-lookup"><span data-stu-id="336e1-122">The new way is thread-safe because the compiler generates code to evaluate `SendNews` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="336e1-123">null 条件デリゲート呼び出し構文 `SendNews?(String)` がないため、`Invoke` メソッドを明示的に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="336e1-123">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `SendNews?(String)`.</span></span>

## <a name="see-also"></a><span data-ttu-id="336e1-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="336e1-124">See also</span></span>

- [<span data-ttu-id="336e1-125">演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="336e1-125">Operators (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="336e1-126">Visual Basic プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="336e1-126">Visual Basic Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="336e1-127">Visual Basic の言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="336e1-127">Visual Basic Language Reference</span></span>](../index.md)
