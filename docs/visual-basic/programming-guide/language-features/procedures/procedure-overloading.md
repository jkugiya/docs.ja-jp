---
description: '詳細情報: プロシージャのオーバーロード (Visual Basic)'
title: プロシージャのオーバーロード
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: 27e79e12153bc7ac6a9e3b3b5997a50c1c354195
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466641"
---
# <a name="procedure-overloading-visual-basic"></a><span data-ttu-id="a370f-103">プロシージャのオーバーロード (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a370f-103">Procedure Overloading (Visual Basic)</span></span>

<span data-ttu-id="a370f-104">プロシージャの "*オーバーロード*" は、同じ名前と異なるパラメーター リストを使用して、複数のバージョンでプロシージャを定義することを意味します。</span><span class="sxs-lookup"><span data-stu-id="a370f-104">*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists.</span></span> <span data-ttu-id="a370f-105">オーバーロードの目的は、名前で区別する必要なく、プロシージャの密接に関連する複数のバージョンを定義することです。</span><span class="sxs-lookup"><span data-stu-id="a370f-105">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span> <span data-ttu-id="a370f-106">これを行うには、異なるパラメーター リストを使用します。</span><span class="sxs-lookup"><span data-stu-id="a370f-106">You do this by varying the parameter list.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="a370f-107">オーバーロードのルール</span><span class="sxs-lookup"><span data-stu-id="a370f-107">Overloading Rules</span></span>

<span data-ttu-id="a370f-108">プロシージャをオーバーロードするときは、次のルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="a370f-108">When you overload a procedure, the following rules apply:</span></span>

- <span data-ttu-id="a370f-109">**同じ名前**:</span><span class="sxs-lookup"><span data-stu-id="a370f-109">**Same Name**.</span></span> <span data-ttu-id="a370f-110">各オーバーロードされたバージョンでは、同じプロシージャ名を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a370f-110">Each overloaded version must use the same procedure name.</span></span>

- <span data-ttu-id="a370f-111">**異なるシグネチャ**:</span><span class="sxs-lookup"><span data-stu-id="a370f-111">**Different Signature**.</span></span> <span data-ttu-id="a370f-112">各オーバーロードされたバージョンは、次の項目の少なくとも 1 つが、他のすべてのオーバーロードされたバージョンと異なる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a370f-112">Each overloaded version must differ from all other overloaded versions in at least one of the following respects:</span></span>

  - <span data-ttu-id="a370f-113">パラメーターの数</span><span class="sxs-lookup"><span data-stu-id="a370f-113">Number of parameters</span></span>

  - <span data-ttu-id="a370f-114">パラメーターの順序</span><span class="sxs-lookup"><span data-stu-id="a370f-114">Order of the parameters</span></span>

  - <span data-ttu-id="a370f-115">パラメーターのデータ型</span><span class="sxs-lookup"><span data-stu-id="a370f-115">Data types of the parameters</span></span>

  - <span data-ttu-id="a370f-116">型パラメーターの数 (ジェネリック プロシージャの場合)</span><span class="sxs-lookup"><span data-stu-id="a370f-116">Number of type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="a370f-117">戻り値の型 (変換演算子の場合のみ)</span><span class="sxs-lookup"><span data-stu-id="a370f-117">Return type (only for a conversion operator)</span></span>

  <span data-ttu-id="a370f-118">プロシージャ名と組み合わされた上記の項目を総称して、プロシージャの "*シグネチャ*" と呼びます。</span><span class="sxs-lookup"><span data-stu-id="a370f-118">Together with the procedure name, the preceding items are collectively called the *signature* of the procedure.</span></span> <span data-ttu-id="a370f-119">オーバーロードされたプロシージャを呼び出すと、コンパイラはシグネチャを使用して、その呼び出しが定義と正しく一致することを確認します。</span><span class="sxs-lookup"><span data-stu-id="a370f-119">When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.</span></span>

- <span data-ttu-id="a370f-120">**シグネチャに含まれない項目**:</span><span class="sxs-lookup"><span data-stu-id="a370f-120">**Items Not Part of Signature**.</span></span> <span data-ttu-id="a370f-121">シグネチャを変えずにプロシージャをオーバーロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a370f-121">You cannot overload a procedure without varying the signature.</span></span> <span data-ttu-id="a370f-122">具体的には、次の 1 つ以上の項目が異なるだけでは、プロシージャをオーバーロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a370f-122">In particular, you cannot overload a procedure by varying only one or more of the following items:</span></span>

  - <span data-ttu-id="a370f-123">プロシージャ修飾子キーワード (`Public`、`Shared`、`Static` など)</span><span class="sxs-lookup"><span data-stu-id="a370f-123">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>

  - <span data-ttu-id="a370f-124">パラメーター名または型パラメーター名</span><span class="sxs-lookup"><span data-stu-id="a370f-124">Parameter or type parameter names</span></span>

  - <span data-ttu-id="a370f-125">型パラメーターの制約 (ジェネリック プロシージャの場合)</span><span class="sxs-lookup"><span data-stu-id="a370f-125">Type parameter constraints (for a generic procedure)</span></span>

  - <span data-ttu-id="a370f-126">パラメーター修飾子キーワード (`ByRef` や `Optional` など)</span><span class="sxs-lookup"><span data-stu-id="a370f-126">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>

  - <span data-ttu-id="a370f-127">値を返すかどうか</span><span class="sxs-lookup"><span data-stu-id="a370f-127">Whether it returns a value</span></span>

  - <span data-ttu-id="a370f-128">戻り値のデータ型 (変換演算子を除く)</span><span class="sxs-lookup"><span data-stu-id="a370f-128">The data type of the return value (except for a conversion operator)</span></span>

  <span data-ttu-id="a370f-129">上記の一覧の項目は、シグネチャには含まれません。</span><span class="sxs-lookup"><span data-stu-id="a370f-129">The items in the preceding list are not part of the signature.</span></span> <span data-ttu-id="a370f-130">これらを使用してオーバーロードされたバージョンを区別することはできませんが、シグネチャによって適切に区別されているオーバーロードされたバージョン間でこれらを変えることは可能です。</span><span class="sxs-lookup"><span data-stu-id="a370f-130">Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.</span></span>

- <span data-ttu-id="a370f-131">**遅延バインディングされた引数**:</span><span class="sxs-lookup"><span data-stu-id="a370f-131">**Late-Bound Arguments**.</span></span> <span data-ttu-id="a370f-132">遅延バインディングされたオブジェクト変数をオーバーロードされたバージョンに渡す場合は、適切なパラメーターを <xref:System.Object> として宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a370f-132">If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.</span></span>

## <a name="multiple-versions-of-a-procedure"></a><span data-ttu-id="a370f-133">プロシージャの複数のバージョン</span><span class="sxs-lookup"><span data-stu-id="a370f-133">Multiple Versions of a Procedure</span></span>

<span data-ttu-id="a370f-134">顧客の残高に対してトランザクションを転記する `Sub` プロシージャを作成し、名前または口座番号で顧客を参照できるようにするとします。</span><span class="sxs-lookup"><span data-stu-id="a370f-134">Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number.</span></span> <span data-ttu-id="a370f-135">これに対応するために、次の例のように、2 つの異なる `Sub` プロシージャを定義できます。</span><span class="sxs-lookup"><span data-stu-id="a370f-135">To accommodate this, you can define two different `Sub` procedures, as in the following example:</span></span>

[!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]

### <a name="overloaded-versions"></a><span data-ttu-id="a370f-136">オーバーロードされたバージョン</span><span class="sxs-lookup"><span data-stu-id="a370f-136">Overloaded Versions</span></span>

<span data-ttu-id="a370f-137">別の方法として、単一のプロシージャ名をオーバーロードします。</span><span class="sxs-lookup"><span data-stu-id="a370f-137">An alternative is to overload a single procedure name.</span></span> <span data-ttu-id="a370f-138">次のように、[Overloads](../../../language-reference/modifiers/overloads.md) キーワードを使用して、パラメーター リストごとにプロシージャのバージョンを定義できます。</span><span class="sxs-lookup"><span data-stu-id="a370f-138">You can use the [Overloads](../../../language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:</span></span>

[!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]

#### <a name="additional-overloads"></a><span data-ttu-id="a370f-139">追加のオーバーロード</span><span class="sxs-lookup"><span data-stu-id="a370f-139">Additional Overloads</span></span>

<span data-ttu-id="a370f-140">取引金額を `Decimal` または `Single` で受け入れることも必要な場合は、`post` をさらにオーバーロードしてこのバリエーションに対応できます。</span><span class="sxs-lookup"><span data-stu-id="a370f-140">If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation.</span></span> <span data-ttu-id="a370f-141">前の例の各オーバーロードに対してこれを行う場合、すべて同じ名前で 4 つの異なるシグネチャを持つ 4 つの `Sub` プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="a370f-141">If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.</span></span>

## <a name="advantages-of-overloading"></a><span data-ttu-id="a370f-142">オーバーロードの利点</span><span class="sxs-lookup"><span data-stu-id="a370f-142">Advantages of Overloading</span></span>

<span data-ttu-id="a370f-143">プロシージャをオーバーロードする利点は、呼び出しの柔軟性にあります。</span><span class="sxs-lookup"><span data-stu-id="a370f-143">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="a370f-144">前の例で宣言された `post` プロシージャを使用する場合、呼び出し元のコードで `String` または `Integer` として顧客 ID を取得し、どちらの場合も同じプロシージャを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="a370f-144">To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case.</span></span> <span data-ttu-id="a370f-145">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a370f-145">The following example illustrates this:</span></span>

[!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]

[!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]

## <a name="see-also"></a><span data-ttu-id="a370f-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="a370f-146">See also</span></span>

- [<span data-ttu-id="a370f-147">手順</span><span class="sxs-lookup"><span data-stu-id="a370f-147">Procedures</span></span>](./index.md)
- [<span data-ttu-id="a370f-148">方法: プロシージャの複数のバージョンを定義する</span><span class="sxs-lookup"><span data-stu-id="a370f-148">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="a370f-149">方法: オーバーロードされたプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="a370f-149">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="a370f-150">方法: 省略可能なパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="a370f-150">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="a370f-151">方法: 不特定数のパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="a370f-151">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="a370f-152">プロシージャのオーバーロードに関する注意事項</span><span class="sxs-lookup"><span data-stu-id="a370f-152">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="a370f-153">オーバーロードの解決</span><span class="sxs-lookup"><span data-stu-id="a370f-153">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="a370f-154">Overloads</span><span class="sxs-lookup"><span data-stu-id="a370f-154">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
- [<span data-ttu-id="a370f-155">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a370f-155">Generic Types in Visual Basic</span></span>](../data-types/generic-types.md)
