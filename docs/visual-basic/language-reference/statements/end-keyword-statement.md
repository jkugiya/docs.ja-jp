---
description: '詳細情報: End <keyword> ステートメント (Visual Basic)'
title: End <keyword> ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: ba21d4ba68a054d77d4f29307d49ed8e82bb6b50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769196"
---
# <a name="end-keyword-statement-visual-basic"></a><span data-ttu-id="de5b7-103">End \<keyword> ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de5b7-103">End \<keyword> Statement (Visual Basic)</span></span>

<span data-ttu-id="de5b7-104">追加のキーワードが後に続く場合に、そのキーワードによって導入されたステートメント ブロックの定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="de5b7-104">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>

## <a name="syntax"></a><span data-ttu-id="de5b7-105">構文</span><span class="sxs-lookup"><span data-stu-id="de5b7-105">Syntax</span></span>

```vb
End AddHandler
End Class
End Enum
End Event
End Function
End Get
End If
End Interface
End Module
End Namespace
End Operator
End Property
End RaiseEvent  
End RemoveHandler  
End Select
End Set
End Structure
End Sub
End SyncLock
End Try
End While
End With  
```  
  
## <a name="parts"></a><span data-ttu-id="de5b7-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="de5b7-106">Parts</span></span>

|<span data-ttu-id="de5b7-107">パーツ</span><span class="sxs-lookup"><span data-stu-id="de5b7-107">Part</span></span>|<span data-ttu-id="de5b7-108">説明</span><span class="sxs-lookup"><span data-stu-id="de5b7-108">Description</span></span>|
|---|---|
|`End`|<span data-ttu-id="de5b7-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-109">Required.</span></span> <span data-ttu-id="de5b7-110">プログラミング要素の定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="de5b7-110">Terminates the definition of the programming element.</span></span>|
|`AddHandler`|<span data-ttu-id="de5b7-111">カスタム [Event ステートメント](event-statement.md)で、一致する `AddHandler` ステートメントによって開始された `AddHandler` アクセサーを終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-111">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Class`|<span data-ttu-id="de5b7-112">一致する [Class ステートメント](class-statement.md)によって開始されたクラス定義を終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-112">Required to terminate a class definition begun by a matching [Class Statement](class-statement.md).</span></span>|
|`Enum`|<span data-ttu-id="de5b7-113">一致する [Enum ステートメント](enum-statement.md)によって開始された列挙型定義を終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-113">Required to terminate an enumeration definition begun by a matching [Enum Statement](enum-statement.md).</span></span>|
|`Event`|<span data-ttu-id="de5b7-114">一致する [Event ステートメント](event-statement.md)によって開始された `Custom` イベント定義を終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-114">Required to terminate a `Custom` event definition begun by a matching [Event Statement](event-statement.md).</span></span>|  
|`Function`|<span data-ttu-id="de5b7-115">一致する [Function ステートメント](function-statement.md)によって開始された `Function` プロシージャ定義を終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-115">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](function-statement.md).</span></span> <span data-ttu-id="de5b7-116">実行時に `End Function` ステートメントが発生すると、呼び出し元のコードに制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="de5b7-116">If execution encounters an `End Function` statement, control returns to the calling code.</span></span>|
|`Get`|<span data-ttu-id="de5b7-117">一致する [Get ステートメント](get-statement.md)によって開始された `Property` プロシージャ定義を終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-117">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](get-statement.md).</span></span> <span data-ttu-id="de5b7-118">実行時に `End Get` ステートメントが発生すると、プロパティの値を要求するステートメントに制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="de5b7-118">If execution encounters an `End Get` statement, control returns to the statement requesting the property's value.</span></span>|
|`If`|<span data-ttu-id="de5b7-119">一致する `If` ステートメントによって開始された `If`...`Then`...`Else` ブロック定義を終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-119">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="de5b7-120">「[If...Then...Else ステートメント](if-then-else-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de5b7-120">See [If...Then...Else Statement](if-then-else-statement.md).</span></span>|
|`Interface`|<span data-ttu-id="de5b7-121">一致する [Interface ステートメント](interface-statement.md)によって開始されたインターフェイス定義を終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-121">Required to terminate an interface definition begun by a matching [Interface Statement](interface-statement.md).</span></span>|
|`Module`|<span data-ttu-id="de5b7-122">一致する [Module ステートメント](module-statement.md)によって開始されたモジュール定義を終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-122">Required to terminate a module definition begun by a matching [Module Statement](module-statement.md).</span></span>|
|`Namespace`|<span data-ttu-id="de5b7-123">一致する [Namespace ステートメント](namespace-statement.md)によって開始された名前空間定義を終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-123">Required to terminate a namespace definition begun by a matching [Namespace Statement](namespace-statement.md).</span></span>|
|`Operator`|<span data-ttu-id="de5b7-124">一致する [Operator ステートメント](operator-statement.md)によって開始された演算子定義を終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-124">Required to terminate an operator definition begun by a matching [Operator Statement](operator-statement.md).</span></span>|
|`Property`|<span data-ttu-id="de5b7-125">一致する [Property ステートメント](property-statement.md)によって開始されたプロパティ定義を終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-125">Required to terminate a property definition begun by a matching [Property Statement](property-statement.md).</span></span>|
|`RaiseEvent`|<span data-ttu-id="de5b7-126">カスタム [Event ステートメント](event-statement.md)で、一致する `RaiseEvent` ステートメントによって開始された `RaiseEvent` アクセサーを終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-126">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`RemoveHandler`|<span data-ttu-id="de5b7-127">カスタム [Event ステートメント](event-statement.md)で、一致する `RemoveHandler` ステートメントによって開始された `RemoveHandler` アクセサーを終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-127">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Select`|<span data-ttu-id="de5b7-128">一致する `Select` ステートメントによって開始された `Select`...`Case` ブロック定義を終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-128">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="de5b7-129">「[Select...Case ステートメント](select-case-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de5b7-129">See [Select...Case Statement](select-case-statement.md).</span></span>  
|`Set`|<span data-ttu-id="de5b7-130">一致する [Set ステートメント](set-statement.md)によって開始された `Property` プロシージャ定義を終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-130">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](set-statement.md).</span></span> <span data-ttu-id="de5b7-131">実行時に `End Set` ステートメントが発生すると、プロパティの値を設定するステートメントに制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="de5b7-131">If execution encounters an `End Set` statement, control returns to the statement setting the property's value.</span></span>  
|`Structure`|<span data-ttu-id="de5b7-132">一致する [Structure ステートメント](structure-statement.md)によって開始された構造体定義を終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-132">Required to terminate a structure definition begun by a matching [Structure Statement](structure-statement.md).</span></span>  
|`Sub`|<span data-ttu-id="de5b7-133">一致する [Sub ステートメント](sub-statement.md)によって開始された `Sub` プロシージャ定義を終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-133">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](sub-statement.md).</span></span> <span data-ttu-id="de5b7-134">実行時に `End Sub` ステートメントが発生すると、呼び出し元のコードに制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="de5b7-134">If execution encounters an `End Sub` statement, control returns to the calling code.</span></span>  
|`SyncLock`|<span data-ttu-id="de5b7-135">一致する `SyncLock` ステートメントによって開始された `SyncLock` ブロック定義を終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-135">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="de5b7-136">「[SyncLock ステートメント](synclock-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de5b7-136">See [SyncLock Statement](synclock-statement.md).</span></span>  
|`Try`|<span data-ttu-id="de5b7-137">一致する `Try` ステートメントによって開始された `Try`...`Catch`...`Finally` ブロック定義を終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-137">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="de5b7-138">「[Try...Catch...Finally ステートメント](try-catch-finally-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de5b7-138">See [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
|`While`|<span data-ttu-id="de5b7-139">一致する `While` ステートメントによって開始された `While` ループ定義を終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-139">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="de5b7-140">「[While...End While ステートメント](while-end-while-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de5b7-140">See [While...End While Statement](while-end-while-statement.md).</span></span>  
|`With`| <span data-ttu-id="de5b7-141">一致する `With` ステートメントによって開始された `With` ブロック定義を終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-141">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="de5b7-142">「[With...End With ステートメント](with-end-with-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de5b7-142">See [With...End With Statement](with-end-with-statement.md).</span></span>  
|||
  
## <a name="directives"></a><span data-ttu-id="de5b7-143">ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="de5b7-143">Directives</span></span>

<span data-ttu-id="de5b7-144">先頭に番号記号 (`#`) がある場合は、`End` キーワードにより、対応するディレクティブによって導入された前処理ブロックが終了します。</span><span class="sxs-lookup"><span data-stu-id="de5b7-144">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  

```vb
#End ExternalSource
#End If
#End Region
```

|<span data-ttu-id="de5b7-145">パーツ</span><span class="sxs-lookup"><span data-stu-id="de5b7-145">Part</span></span>|<span data-ttu-id="de5b7-146">説明</span><span class="sxs-lookup"><span data-stu-id="de5b7-146">Description</span></span>|
|---|---|
|`#End`|<span data-ttu-id="de5b7-147">必須です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-147">Required.</span></span> <span data-ttu-id="de5b7-148">前処理ブロックの定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="de5b7-148">Terminates the definition of the preprocessing block.</span></span>|
|`ExternalSource`|<span data-ttu-id="de5b7-149">一致する [#ExternalSource ディレクティブ](../directives/externalsource-directive.md)によって開始された外部ソース ブロックを終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-149">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../directives/externalsource-directive.md).</span></span>|
|`If`|<span data-ttu-id="de5b7-150">一致する `#If` ディレクティブによって開始された条件付きコンパイル ブロックを終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-150">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="de5b7-151">「[#If...Then...#Else ディレクティブ](../directives/if-then-else-directives.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de5b7-151">See [#If...Then...#Else Directives](../directives/if-then-else-directives.md).</span></span>|
|`Region`|<span data-ttu-id="de5b7-152">一致する [#Region ディレクティブ](../directives/region-directive.md)によって開始されたソース リージョン ブロックを終了するために必要です。</span><span class="sxs-lookup"><span data-stu-id="de5b7-152">Required to terminate a source region block begun by a matching [#Region Directive](../directives/region-directive.md).</span></span>|
|||

## <a name="remarks"></a><span data-ttu-id="de5b7-153">Remarks</span><span class="sxs-lookup"><span data-stu-id="de5b7-153">Remarks</span></span>

<span data-ttu-id="de5b7-154">追加のキーワードを使用しない [End ステートメント](end-statement.md)では、すぐに実行が終了します。</span><span class="sxs-lookup"><span data-stu-id="de5b7-154">The [End Statement](end-statement.md), without an additional keyword, terminates execution immediately.</span></span>

## <a name="smart-device-developer-notes"></a><span data-ttu-id="de5b7-155">スマート デバイス開発者向けのメモ</span><span class="sxs-lookup"><span data-stu-id="de5b7-155">Smart Device Developer Notes</span></span>  

<span data-ttu-id="de5b7-156">追加のキーワードを使用しない `End` ステートメントはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="de5b7-156">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de5b7-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="de5b7-157">See also</span></span>

- [<span data-ttu-id="de5b7-158">End ステートメント</span><span class="sxs-lookup"><span data-stu-id="de5b7-158">End Statement</span></span>](end-statement.md)
