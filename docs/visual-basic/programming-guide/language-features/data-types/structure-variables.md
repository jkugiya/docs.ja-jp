---
description: '詳細情報: 構造体の変数 (Visual Basic)'
title: 構造体の変数
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 64c53b06369bc7d7d0c46bc87d4c73ce90b4011f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100484159"
---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="d67e4-103">構造体の変数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d67e4-103">Structure Variables (Visual Basic)</span></span>

<span data-ttu-id="d67e4-104">構造体を作成したら、プロシージャ レベルとモジュール レベルの変数をその型として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="d67e4-104">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="d67e4-105">たとえば、コンピューター システムに関する情報を記録する構造体を作成できます。</span><span class="sxs-lookup"><span data-stu-id="d67e4-105">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="d67e4-106">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d67e4-106">The following example demonstrates this.</span></span>

```vb
Public Structure systemInfo
    Public cPU As String
    Public memory As Long
    Public purchaseDate As Date
End Structure
```

<span data-ttu-id="d67e4-107">これで、その型の変数を宣言できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="d67e4-107">You can now declare variables of that type.</span></span> <span data-ttu-id="d67e4-108">これを次の宣言に示します。</span><span class="sxs-lookup"><span data-stu-id="d67e4-108">The following declaration illustrates this.</span></span>

```vb
Dim mySystem, yourSystem As systemInfo
```

> [!NOTE]
> <span data-ttu-id="d67e4-109">クラスとモジュールで、[Dim ステートメント](../../../language-reference/statements/dim-statement.md)を使用して宣言された構造体は、既定でパブリック アクセスになります。</span><span class="sxs-lookup"><span data-stu-id="d67e4-109">In classes and modules, structures declared using the [Dim Statement](../../../language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="d67e4-110">構造体をプライベートにする場合は、[Private](../../../language-reference/modifiers/private.md) キーワードを使用して宣言してください。</span><span class="sxs-lookup"><span data-stu-id="d67e4-110">If you intend a structure to be private, make sure you declare it using the [Private](../../../language-reference/modifiers/private.md) keyword.</span></span>

## <a name="access-to-structure-values"></a><span data-ttu-id="d67e4-111">構造体の値へのアクセス</span><span class="sxs-lookup"><span data-stu-id="d67e4-111">Access to Structure Values</span></span>

<span data-ttu-id="d67e4-112">構造体変数の要素の値を代入したり取得したりするには、オブジェクトのプロパティの設定と取得に使用するのと同じ構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="d67e4-112">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="d67e4-113">構造体変数名と要素名の間に、メンバー アクセス演算子 (`.`) を指定します。</span><span class="sxs-lookup"><span data-stu-id="d67e4-113">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="d67e4-114">次の例は、前に型 `systemInfo` として宣言された変数の要素にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="d67e4-114">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>

```vb
mySystem.cPU = "486"
Dim tooOld As Boolean
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True
```

## <a name="assigning-structure-variables"></a><span data-ttu-id="d67e4-115">構造体の変数の代入</span><span class="sxs-lookup"><span data-stu-id="d67e4-115">Assigning Structure Variables</span></span>

<span data-ttu-id="d67e4-116">また、両方が同じ構造体型である場合は、1 つの変数を別の変数に代入することもできます。</span><span class="sxs-lookup"><span data-stu-id="d67e4-116">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="d67e4-117">これにより、1 つの構造体のすべての要素が、もう一方の対応する要素にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="d67e4-117">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="d67e4-118">これを次の宣言に示します。</span><span class="sxs-lookup"><span data-stu-id="d67e4-118">The following declaration illustrates this.</span></span>

```vb
yourSystem = mySystem
```

<span data-ttu-id="d67e4-119">構造体要素が `String`、`Object`、配列などの参照型である場合は、データへのポインターがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="d67e4-119">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="d67e4-120">前の例で、`systemInfo` にオブジェクト変数が含まれているとすると、ポインターが `mySystem` から `yourSystem` にコピーされています。また、1 つの構造体を介してオブジェクトのデータを変更すると、他の構造体を使用してアクセスしたときに有効になります。</span><span class="sxs-lookup"><span data-stu-id="d67e4-120">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="d67e4-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d67e4-121">See also</span></span>

- [<span data-ttu-id="d67e4-122">データの種類</span><span class="sxs-lookup"><span data-stu-id="d67e4-122">Data Types</span></span>](index.md)
- [<span data-ttu-id="d67e4-123">基本データ型</span><span class="sxs-lookup"><span data-stu-id="d67e4-123">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="d67e4-124">複合データ型</span><span class="sxs-lookup"><span data-stu-id="d67e4-124">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="d67e4-125">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="d67e4-125">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="d67e4-126">構造体</span><span class="sxs-lookup"><span data-stu-id="d67e4-126">Structures</span></span>](structures.md)
- [<span data-ttu-id="d67e4-127">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="d67e4-127">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="d67e4-128">方法: 構造体を宣言する</span><span class="sxs-lookup"><span data-stu-id="d67e4-128">How to: Declare a Structure</span></span>](how-to-declare-a-structure.md)
- [<span data-ttu-id="d67e4-129">構造体とその他のプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="d67e4-129">Structures and Other Programming Elements</span></span>](structures-and-other-programming-elements.md)
- [<span data-ttu-id="d67e4-130">構造体とクラス</span><span class="sxs-lookup"><span data-stu-id="d67e4-130">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="d67e4-131">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="d67e4-131">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
