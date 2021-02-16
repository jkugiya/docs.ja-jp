---
description: '詳細情報: オーバーロードの解決法 (Visual Basic)'
title: Overload Resolution
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- overload resolution
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedure overloading [Visual Basic], overload resolution
- signatures [Visual Basic], procedure
- overloads [Visual Basic], resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
ms.openlocfilehash: 71375083e661ee156339abf13e1a5b8da21b9358
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480038"
---
# <a name="overload-resolution-visual-basic"></a><span data-ttu-id="71c77-103">オーバーロードの解決法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71c77-103">Overload Resolution (Visual Basic)</span></span>

<span data-ttu-id="71c77-104">Visual Basic コンパイラは、複数のオーバーロードされたバージョンで定義されているプロシージャの呼び出しを検出したときに、呼び出すオーバーロードを決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71c77-104">When the Visual Basic compiler encounters a call to a procedure that is defined in several overloaded versions, the compiler must decide which of the overloads to call.</span></span> <span data-ttu-id="71c77-105">そのために、次の手順が実行されます。</span><span class="sxs-lookup"><span data-stu-id="71c77-105">It does this by performing the following steps:</span></span>  
  
1. <span data-ttu-id="71c77-106">**アクセシビリティ。**</span><span class="sxs-lookup"><span data-stu-id="71c77-106">**Accessibility.**</span></span> <span data-ttu-id="71c77-107">呼び出し元のコードから呼び出すことができないようにするためのアクセス レベルが設定されたオーバーロードが排除されます。</span><span class="sxs-lookup"><span data-stu-id="71c77-107">It eliminates any overload with an access level that prevents the calling code from calling it.</span></span>  
  
2. <span data-ttu-id="71c77-108">**パラメーターの数。**</span><span class="sxs-lookup"><span data-stu-id="71c77-108">**Number of Parameters.**</span></span> <span data-ttu-id="71c77-109">呼び出しで指定されているパラメーターとは異なる数のパラメーターが定義されているオーバーロードが排除されます。</span><span class="sxs-lookup"><span data-stu-id="71c77-109">It eliminates any overload that defines a different number of parameters than are supplied in the call.</span></span>  
  
3. <span data-ttu-id="71c77-110">**パラメーターのデータ型。**</span><span class="sxs-lookup"><span data-stu-id="71c77-110">**Parameter Data Types.**</span></span> <span data-ttu-id="71c77-111">コンパイラは、拡張メソッドよりもインスタンス メソッドを優先します。</span><span class="sxs-lookup"><span data-stu-id="71c77-111">The compiler gives instance methods preference over extension methods.</span></span> <span data-ttu-id="71c77-112">プロシージャ呼び出しに一致させるために拡大変換のみを必要とするインスタンス メソッドが見つかった場合は、すべての拡張メソッドが破棄され、コンパイラはインスタンス メソッドの候補のみを使用して手順を続行します。</span><span class="sxs-lookup"><span data-stu-id="71c77-112">If any instance method is found that requires only widening conversions to match the procedure call, all extension methods are dropped and the compiler continues with only the instance method candidates.</span></span> <span data-ttu-id="71c77-113">そのようなインスタンス メソッドが見つからない場合は、インスタンス メソッドと拡張メソッドの両方を使用して手順を続行します。</span><span class="sxs-lookup"><span data-stu-id="71c77-113">If no such instance method is found, it continues with both instance and extension methods.</span></span>  
  
     <span data-ttu-id="71c77-114">この手順では、呼び出し元の引数のデータ型を、オーバーロードで定義されたパラメーターの型に変換できないオーバーロードが排除されます。</span><span class="sxs-lookup"><span data-stu-id="71c77-114">In this step, it eliminates any overload for which the data types of the calling arguments cannot be converted to the parameter types defined in the overload.</span></span>  
  
4. <span data-ttu-id="71c77-115">**縮小変換。**</span><span class="sxs-lookup"><span data-stu-id="71c77-115">**Narrowing Conversions.**</span></span> <span data-ttu-id="71c77-116">呼び出し元の引数の型から定義されているパラメーターの型への縮小変換を必要とするオーバーロードが排除されます。</span><span class="sxs-lookup"><span data-stu-id="71c77-116">It eliminates any overload that requires a narrowing conversion from the calling argument types to the defined parameter types.</span></span> <span data-ttu-id="71c77-117">これは、型チェック スイッチ ([Option Strict ステートメント](../../../language-reference/statements/option-strict-statement.md)) が `On` か `Off` かに関係なく適用されます。</span><span class="sxs-lookup"><span data-stu-id="71c77-117">This is true whether the type checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) is `On` or `Off`.</span></span>  
  
5. <span data-ttu-id="71c77-118">**最少の拡大変換。**</span><span class="sxs-lookup"><span data-stu-id="71c77-118">**Least Widening.**</span></span> <span data-ttu-id="71c77-119">コンパイラは、残りのオーバーロードをペアで検討します。</span><span class="sxs-lookup"><span data-stu-id="71c77-119">The compiler considers the remaining overloads in pairs.</span></span> <span data-ttu-id="71c77-120">各ペアについて、定義されているパラメーターのデータ型を比較します。</span><span class="sxs-lookup"><span data-stu-id="71c77-120">For each pair, it compares the data types of the defined parameters.</span></span> <span data-ttu-id="71c77-121">一方のオーバーロードの型が、もう一方の対応する型にすべて拡大変換される場合、コンパイラは後者を排除します。</span><span class="sxs-lookup"><span data-stu-id="71c77-121">If the types in one of the overloads all widen to the corresponding types in the other, the compiler eliminates the latter.</span></span> <span data-ttu-id="71c77-122">つまり、必要な拡大変換が最も少ないオーバーロードが保持されます。</span><span class="sxs-lookup"><span data-stu-id="71c77-122">That is, it retains the overload that requires the least amount of widening.</span></span>  
  
6. <span data-ttu-id="71c77-123">**単一の候補。**</span><span class="sxs-lookup"><span data-stu-id="71c77-123">**Single Candidate.**</span></span> <span data-ttu-id="71c77-124">オーバーロードが引き続きペアで検討され、残りのオーバーロードが 1 つになったら、呼び出しがそのオーバーロードに解決されます。</span><span class="sxs-lookup"><span data-stu-id="71c77-124">It continues considering overloads in pairs until only one overload remains, and it resolves the call to that overload.</span></span> <span data-ttu-id="71c77-125">コンパイラがオーバーロードを 1 つの候補に絞り込むことができない場合は、エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="71c77-125">If the compiler cannot reduce the overloads to a single candidate, it generates an error.</span></span>  
  
 <span data-ttu-id="71c77-126">次の図は、一連のオーバーロードされたバージョンの中から呼び出すバージョンを決定するプロセスを示しています。</span><span class="sxs-lookup"><span data-stu-id="71c77-126">The following illustration shows the process that determines which of a set of overloaded versions to call.</span></span>  
  
 <span data-ttu-id="71c77-127">![オーバーロード解決プロセスのフロー ダイアグラム](./media/overload-resolution/determine-overloaded-version.gif "オーバーロードされたバージョン間の解決")</span><span class="sxs-lookup"><span data-stu-id="71c77-127">![Flow diagram of overload resolution process](./media/overload-resolution/determine-overloaded-version.gif "Resolving among overloaded versions")</span></span>
  
 <span data-ttu-id="71c77-128">次の例は、このオーバーロード解決プロセスを示しています。</span><span class="sxs-lookup"><span data-stu-id="71c77-128">The following example illustrates this overload resolution process.</span></span>  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 <span data-ttu-id="71c77-129">最初の呼び出しでは、最初の引数の型 (`Short`) が対応するパラメーターの型 (`Byte`) に縮小変換されるため、コンパイラは最初のオーバーロードを排除します。</span><span class="sxs-lookup"><span data-stu-id="71c77-129">In the first call, the compiler eliminates the first overload because the type of the first argument (`Short`) narrows to the type of the corresponding parameter (`Byte`).</span></span> <span data-ttu-id="71c77-130">次に、2 番目のオーバーロードの各引数の型 (`Short` と `Single`) は、3 番目のオーバーロードの対応する型 (`Integer` と `Single`) に拡大変換されるため、3 番目のオーバーロードが排除されます。</span><span class="sxs-lookup"><span data-stu-id="71c77-130">It then eliminates the third overload because each argument type in the second overload (`Short` and `Single`) widens to the corresponding type in the third overload (`Integer` and `Single`).</span></span> <span data-ttu-id="71c77-131">2 番目のオーバーロードは必要な拡大変換が少ないため、コンパイラはこれを呼び出しに使用します。</span><span class="sxs-lookup"><span data-stu-id="71c77-131">The second overload requires less widening, so the compiler uses it for the call.</span></span>  
  
 <span data-ttu-id="71c77-132">2 番目の呼び出しでは、コンパイラは縮小変換に基づいてオーバーロードのいずれかを排除することができません。</span><span class="sxs-lookup"><span data-stu-id="71c77-132">In the second call, the compiler cannot eliminate any of the overloads on the basis of narrowing.</span></span> <span data-ttu-id="71c77-133">最初の呼び出しと同じ理由で、3 番目のオーバーロードが排除されます。引数の型の拡大変換が少ない 2 番目のオーバーロードを呼び出すことができるためです。</span><span class="sxs-lookup"><span data-stu-id="71c77-133">It eliminates the third overload for the same reason as in the first call, because it can call the second overload with less widening of the argument types.</span></span> <span data-ttu-id="71c77-134">ただし、コンパイラは最初と 2 番目のオーバーロード間で解決することはできません。</span><span class="sxs-lookup"><span data-stu-id="71c77-134">However, the compiler cannot resolve between the first and second overloads.</span></span> <span data-ttu-id="71c77-135">それぞれ、もう一方の対応する型に拡大変換されるパラメーターの型が定義されています (`Byte` から `Short`、`Single` から `Double`)。</span><span class="sxs-lookup"><span data-stu-id="71c77-135">Each has one defined parameter type that widens to the corresponding type in the other (`Byte` to `Short`, but `Single` to `Double`).</span></span> <span data-ttu-id="71c77-136">そのため、コンパイラはオーバーロード解決エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="71c77-136">The compiler therefore generates an overload resolution error.</span></span>  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a><span data-ttu-id="71c77-137">オーバーロードされた Optional および ParamArray 引数</span><span class="sxs-lookup"><span data-stu-id="71c77-137">Overloaded Optional and ParamArray Arguments</span></span>  

 <span data-ttu-id="71c77-138">最後のパラメーターが一方では [Optional](../../../language-reference/modifiers/optional.md)、もう一方では [ParamArray](../../../language-reference/modifiers/paramarray.md) として宣言されている点を除き、プロシージャの 2 つのオーバーロードが同じシグネチャを持つ場合、コンパイラはそのプロシージャの呼び出しを次のように解決します。</span><span class="sxs-lookup"><span data-stu-id="71c77-138">If two overloads of a procedure have identical signatures except that the last parameter is declared [Optional](../../../language-reference/modifiers/optional.md) in one and [ParamArray](../../../language-reference/modifiers/paramarray.md) in the other, the compiler resolves a call to that procedure as follows:</span></span>  
  
|<span data-ttu-id="71c77-139">呼び出しで指定されている最後の引数</span><span class="sxs-lookup"><span data-stu-id="71c77-139">If the call supplies the last argument as</span></span>|<span data-ttu-id="71c77-140">コンパイラは、最後の引数を次のように宣言するオーバーロードに呼び出しを解決する</span><span class="sxs-lookup"><span data-stu-id="71c77-140">The compiler resolves the call to the overload declaring the last argument as</span></span>|  
|---|---|  
|<span data-ttu-id="71c77-141">値なし (引数を省略)</span><span class="sxs-lookup"><span data-stu-id="71c77-141">No value (argument omitted)</span></span>|`Optional`|  
|<span data-ttu-id="71c77-142">単一の値</span><span class="sxs-lookup"><span data-stu-id="71c77-142">A single value</span></span>|`Optional`|  
|<span data-ttu-id="71c77-143">コンマ区切りリストの 2 つ以上の値</span><span class="sxs-lookup"><span data-stu-id="71c77-143">Two or more values in a comma-separated list</span></span>|`ParamArray`|  
|<span data-ttu-id="71c77-144">任意の長さの配列 (空の配列を含む)</span><span class="sxs-lookup"><span data-stu-id="71c77-144">An array of any length (including an empty array)</span></span>|`ParamArray`|  
  
## <a name="see-also"></a><span data-ttu-id="71c77-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="71c77-145">See also</span></span>

- [<span data-ttu-id="71c77-146">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="71c77-146">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="71c77-147">パラメーター配列</span><span class="sxs-lookup"><span data-stu-id="71c77-147">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="71c77-148">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="71c77-148">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="71c77-149">プロシージャのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="71c77-149">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="71c77-150">方法: プロシージャの複数のバージョンを定義する</span><span class="sxs-lookup"><span data-stu-id="71c77-150">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="71c77-151">方法: オーバーロードされたプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="71c77-151">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="71c77-152">方法: 省略可能なパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="71c77-152">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="71c77-153">方法: 不特定数のパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="71c77-153">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="71c77-154">プロシージャのオーバーロードに関する注意事項</span><span class="sxs-lookup"><span data-stu-id="71c77-154">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="71c77-155">Overloads</span><span class="sxs-lookup"><span data-stu-id="71c77-155">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
- [<span data-ttu-id="71c77-156">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="71c77-156">Extension Methods</span></span>](./extension-methods.md)
