---
title: 抽象クラス
description: 一部またはすべてのメンバーを実装しないままにして、さまざまなオブジェクト型のセットに共通の機能を表現するための F# の抽象クラスについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: d7fc87178cff7c5c824992c97198b49f87025f00
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082949"
---
# <a name="abstract-classes"></a><span data-ttu-id="6ca8a-103">抽象クラス</span><span class="sxs-lookup"><span data-stu-id="6ca8a-103">Abstract Classes</span></span>

<span data-ttu-id="6ca8a-104">"*抽象クラス*" は、一部またはすべてのメンバーを実装しないままにして、派生クラスによって実装できるようにするためのクラスです。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-104">*Abstract classes* are classes that leave some or all members unimplemented, so that implementations can be provided by derived classes.</span></span>

## <a name="syntax"></a><span data-ttu-id="6ca8a-105">構文</span><span class="sxs-lookup"><span data-stu-id="6ca8a-105">Syntax</span></span>

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a><span data-ttu-id="6ca8a-106">解説</span><span class="sxs-lookup"><span data-stu-id="6ca8a-106">Remarks</span></span>

<span data-ttu-id="6ca8a-107">オブジェクト指向プログラミングでは、抽象クラスは、階層の基底クラスとして使用され、さまざまなオブジェクト型のセットに共通の機能を表します。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-107">In object-oriented programming, an abstract class is used as a base class of a hierarchy, and represents common functionality of a diverse set of object types.</span></span> <span data-ttu-id="6ca8a-108">"抽象" という名前が示すとおり、多くの場合、抽象クラスは問題ドメインの具象エンティティに直接対応していません。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-108">As the name "abstract" implies, abstract classes often do not correspond directly onto concrete entities in the problem domain.</span></span> <span data-ttu-id="6ca8a-109">ただし、これらはさまざまな具象エンティティが共通して持つものを表しています。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-109">However, they do represent what many different concrete entities have in common.</span></span>

<span data-ttu-id="6ca8a-110">抽象クラスには `AbstractClass` 属性が必要です。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-110">Abstract classes must have the `AbstractClass` attribute.</span></span> <span data-ttu-id="6ca8a-111">メンバーは実装されているものと実装されていないものがあります。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-111">They can have implemented and unimplemented members.</span></span> <span data-ttu-id="6ca8a-112">クラスについて "*抽象*" という用語を使用する場合の意味は、他の .NET 言語の場合と同じです。ただし、メソッド (およびプロパティ) について "*抽象*" という用語を使用する場合の意味は、F# と他の .NET 言語とで少し異なります。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-112">The use of the term *abstract* when applied to a class is the same as in other .NET languages; however, the use of the term *abstract* when applied to methods (and properties) is a little different in F# from its use in other .NET languages.</span></span> <span data-ttu-id="6ca8a-113">F# では、メソッドが `abstract` キーワードでマークされている場合は、メンバーが、その型の仮想関数の内部テーブルに "*仮想ディスパッチ スロット*" と呼ばれるエントリを持っていることを示します。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-113">In F#, when a method is marked with the `abstract` keyword, this indicates that a member has an entry, known as a *virtual dispatch slot*, in the internal table of virtual functions for that type.</span></span> <span data-ttu-id="6ca8a-114">つまり、メソッドは仮想ですが、F# 言語では `virtual` キーワードは使用されません。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-114">In other words, the method is virtual, although the `virtual` keyword is not used in the F# language.</span></span> <span data-ttu-id="6ca8a-115">キーワード `abstract` は、そのメソッドが実装されているかどうかに関係なく、仮想メソッドに対して使用されます。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-115">The keyword `abstract` is used on virtual methods regardless of whether the method is implemented.</span></span> <span data-ttu-id="6ca8a-116">仮想ディスパッチ スロットの宣言は、そのディスパッチ スロットのメソッドの定義とは別個のものです。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-116">The declaration of a virtual dispatch slot is separate from the definition of a method for that dispatch slot.</span></span> <span data-ttu-id="6ca8a-117">したがって、別の .NET 言語の場合に相当する F# での仮想メソッドの宣言と定義は、`default` キーワードまたは `override` キーワードのいずれかを使用した抽象メソッド宣言と別個の定義の両方を組み合わせたものになります。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-117">Therefore, the F# equivalent of a virtual method declaration and definition in another .NET language is a combination of both an abstract method declaration and a separate definition, with either the `default` keyword or the `override` keyword.</span></span> <span data-ttu-id="6ca8a-118">詳細と例については、「[メソッド](./members/methods.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-118">For more information and examples, see [Methods](./members/methods.md).</span></span>

<span data-ttu-id="6ca8a-119">クラスは、宣言されているが定義されていない抽象メソッドがある場合にのみ、抽象と見なされます。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-119">A class is considered abstract only if there are abstract methods that are declared but not defined.</span></span> <span data-ttu-id="6ca8a-120">したがって、抽象メソッドを持つクラスは、必ずしも抽象クラスではありません。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-120">Therefore, classes that have abstract methods are not necessarily abstract classes.</span></span> <span data-ttu-id="6ca8a-121">クラスに未定義の抽象メソッドがある場合を除き、**AbstractClass** 属性は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-121">Unless a class has undefined abstract methods, do not use the **AbstractClass** attribute.</span></span>

<span data-ttu-id="6ca8a-122">上記の構文で、*accessibility-modifier* には `public`、`private`、または `internal` を指定できます。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-122">In the previous syntax, *accessibility-modifier* can be `public`, `private` or `internal`.</span></span> <span data-ttu-id="6ca8a-123">詳しくは、「[アクセス制御](access-control.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-123">For more information, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="6ca8a-124">他の型と同様に、抽象クラスは、1 つの基底クラスと 1 つ以上の基底インターフェイスを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-124">As with other types, abstract classes can have a base class and one or more base interfaces.</span></span> <span data-ttu-id="6ca8a-125">各基底クラスまたはインターフェイスは、`inherit` キーワードと共に別個の行に指定します。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-125">Each base class or interface appears on a separate line together with the `inherit` keyword.</span></span>

<span data-ttu-id="6ca8a-126">抽象クラスの型定義には、完全に定義されたメンバーを含めることができますが、抽象メンバーを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-126">The type definition of an abstract class can contain fully defined members, but it can also contain abstract members.</span></span> <span data-ttu-id="6ca8a-127">抽象メンバーの構文は、上記の構文で別個に示されています。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-127">The syntax for abstract members is shown separately in the previous syntax.</span></span> <span data-ttu-id="6ca8a-128">この構文で、メンバーの "*型シグネチャ*" は、順番に並べたパラメーター型と戻り値の型を、カリー化およびタプル化パラメーターに応じて `->` トークンまたは `*` トークンで区切ったものを含むリストです。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-128">In this syntax, the *type signature* of a member is a list that contains the parameter types in order and the return types, separated by `->` tokens and/or `*` tokens as appropriate for curried and tupled parameters.</span></span> <span data-ttu-id="6ca8a-129">抽象メンバーの型シグネチャの構文は、シグネチャ ファイルで使用されているもの、および Visual Studio Code エディターで IntelliSense によって示されるものと同じです。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-129">The syntax for abstract member type signatures is the same as that used in signature files and that shown by IntelliSense in the Visual Studio Code Editor.</span></span>

<span data-ttu-id="6ca8a-130">次のコードは、抽象クラス Shape と、2 つの抽象ではない派生クラス Square と Circle の例を示しています。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-130">The following code illustrates an abstract class Shape, which has two non-abstract derived classes, Square and Circle.</span></span> <span data-ttu-id="6ca8a-131">この例は、抽象クラス、メソッド、プロパティの使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-131">The example shows how to use abstract classes, methods, and properties.</span></span> <span data-ttu-id="6ca8a-132">この例で、抽象クラス Shape は、具象エンティティである円と正方形に共通の要素を表しています。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-132">In the example, the abstract class Shape represents the common elements of the concrete entities circle and square.</span></span> <span data-ttu-id="6ca8a-133">すべての図形の (2 次元座標系における) 共通の特徴が、Shape クラスに抽象化されています。グリッド上の位置、回転角度、面積、外周の各プロパティです。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-133">The common features of all shapes (in a two-dimensional coordinate system) are abstracted out into the Shape class: the position on the grid, an angle of rotation, and the area and perimeter properties.</span></span> <span data-ttu-id="6ca8a-134">これらのうち位置だけは個々の図形で動作を変更することはできませんが、それ以外はオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-134">These can be overridden, except for position, the behavior of which individual shapes cannot change.</span></span>

<span data-ttu-id="6ca8a-135">rotation メソッドは、Circle クラスのように、オーバーライドすることができます。円は対称形であるため、回転させても変化しません。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-135">The rotation method can be overridden, as in the Circle class, which is rotation invariant because of its symmetry.</span></span> <span data-ttu-id="6ca8a-136">そのため、Circle クラスでは、rotation メソッドは何も実行しないメソッドに置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="6ca8a-136">So in the Circle class, the rotation method is replaced by a method that does nothing.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

<span data-ttu-id="6ca8a-137">**出力:**</span><span class="sxs-lookup"><span data-stu-id="6ca8a-137">**Output:**</span></span>

```console
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a><span data-ttu-id="6ca8a-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ca8a-138">See also</span></span>

- [<span data-ttu-id="6ca8a-139">クラス</span><span class="sxs-lookup"><span data-stu-id="6ca8a-139">Classes</span></span>](classes.md)
- [<span data-ttu-id="6ca8a-140">メンバー</span><span class="sxs-lookup"><span data-stu-id="6ca8a-140">Members</span></span>](./members/index.md)
- [<span data-ttu-id="6ca8a-141">メソッド</span><span class="sxs-lookup"><span data-stu-id="6ca8a-141">Methods</span></span>](./members/methods.md)
- [<span data-ttu-id="6ca8a-142">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6ca8a-142">Properties</span></span>](./members/Properties.md)
