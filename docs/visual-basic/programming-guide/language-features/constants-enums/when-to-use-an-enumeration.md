---
description: '詳細情報: 列挙型を使用する状況 (Visual Basic)'
title: 列挙型を使用する状況
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: a29d0e3bb8ac99baf5d43827a8b58701eddcfbdd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480740"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="3f8b7-103">列挙型を使用する状況 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f8b7-103">When to Use an Enumeration (Visual Basic)</span></span>

<span data-ttu-id="3f8b7-104">列挙型を使用すると、一連の関連する定数を簡単に操作できます。</span><span class="sxs-lookup"><span data-stu-id="3f8b7-104">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="3f8b7-105">列挙型 (`Enum`) は、一連の値のシンボリック名です。</span><span class="sxs-lookup"><span data-stu-id="3f8b7-105">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="3f8b7-106">列挙型はデータ型扱いであり、これを使用することで、変数やプロパティと共に使用する一連の定数を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="3f8b7-106">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="3f8b7-107">列挙型を使用する状況</span><span class="sxs-lookup"><span data-stu-id="3f8b7-107">When to Use an Enumeration</span></span>  

 <span data-ttu-id="3f8b7-108">プロシージャで受け取れる変数の個数が限られている場合には、必ず列挙型の使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="3f8b7-108">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="3f8b7-109">列挙型を使用すると、コードの明瞭さと読みやすさが増します。わかりやすい名前を使用すると特に効果的です。</span><span class="sxs-lookup"><span data-stu-id="3f8b7-109">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="3f8b7-110">列挙型を使用する利点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3f8b7-110">The benefits of using enumerations include:</span></span>  
  
- <span data-ttu-id="3f8b7-111">数の入れ替えや入力間違いによるエラーを減らせます。</span><span class="sxs-lookup"><span data-stu-id="3f8b7-111">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
- <span data-ttu-id="3f8b7-112">値を後で変更しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="3f8b7-112">Makes it easy to change values in the future.</span></span>  
  
- <span data-ttu-id="3f8b7-113">コードが読みやすくなり、コードにエラーが紛れ込む可能性を抑えられます。</span><span class="sxs-lookup"><span data-stu-id="3f8b7-113">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
- <span data-ttu-id="3f8b7-114">上位互換性を確保できます。</span><span class="sxs-lookup"><span data-stu-id="3f8b7-114">Ensures forward compatibility.</span></span> <span data-ttu-id="3f8b7-115">列挙型を使用すると、今後メンバー名に対応する値が変更された場合に、コードでエラーが発生する確率が小さくなります。</span><span class="sxs-lookup"><span data-stu-id="3f8b7-115">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="3f8b7-116">列挙型に名前を付ける</span><span class="sxs-lookup"><span data-stu-id="3f8b7-116">Naming Enumerations</span></span>  

 <span data-ttu-id="3f8b7-117">列挙型メンバーにはなんらかの名前付け規則を適用してください。</span><span class="sxs-lookup"><span data-stu-id="3f8b7-117">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="3f8b7-118">Visual Basic で列挙型メンバーを検出した場合、参照対象の別の型ライブラリに同じ名前が含まれていると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="3f8b7-118">When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="3f8b7-119">アプリケーションまたはコンポーネントの値を特定できる、一意の接頭辞を使用してください。</span><span class="sxs-lookup"><span data-stu-id="3f8b7-119">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="3f8b7-120">列挙型のメンバーを参照する場合は、列挙型名でメンバー名を修飾するか、`Imports` ステートメントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f8b7-120">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="3f8b7-121">詳細については、[列挙型と名前の修飾](enumerations-and-name-qualification.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f8b7-121">For more information, see [Enumerations and Name Qualification](enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="3f8b7-122">定義済みの列挙型</span><span class="sxs-lookup"><span data-stu-id="3f8b7-122">Predefined Enumerations</span></span>  

 <span data-ttu-id="3f8b7-123">Visual Basic には、コードを作成しやすいように定義済みの列挙型が多数用意されています (`FirstDayOfWeek` や `MsgBoxResult` など)。</span><span class="sxs-lookup"><span data-stu-id="3f8b7-123">Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="3f8b7-124">これらの一覧については、[定数と列挙型](../../../language-reference/constants-and-enumerations.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f8b7-124">For a list of these see [Constants and Enumerations](../../../language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f8b7-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f8b7-125">See also</span></span>

- [<span data-ttu-id="3f8b7-126">方法: 列挙型を宣言する</span><span class="sxs-lookup"><span data-stu-id="3f8b7-126">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="3f8b7-127">方法: 列挙型のメンバーを参照する</span><span class="sxs-lookup"><span data-stu-id="3f8b7-127">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="3f8b7-128">列挙型と名前の修飾</span><span class="sxs-lookup"><span data-stu-id="3f8b7-128">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="3f8b7-129">方法: Visual Basic で列挙型を反復処理する</span><span class="sxs-lookup"><span data-stu-id="3f8b7-129">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="3f8b7-130">方法: 列挙値に関連付けられている文字列を確認する</span><span class="sxs-lookup"><span data-stu-id="3f8b7-130">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="3f8b7-131">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="3f8b7-131">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="3f8b7-132">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="3f8b7-132">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
