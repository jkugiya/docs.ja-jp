---
description: '詳細情報: Module ステートメント'
title: Module ステートメント
ms.date: 07/20/2015
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
ms.openlocfilehash: 2a19bcfa4521d34b5a91fbc9de412a6d8f6f39c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768871"
---
# <a name="module-statement"></a><span data-ttu-id="27cc8-103">Module ステートメント</span><span class="sxs-lookup"><span data-stu-id="27cc8-103">Module Statement</span></span>

<span data-ttu-id="27cc8-104">モジュールの名前を宣言し、モジュールを構成する変数、プロパティ、イベント、およびプロシージャの定義を提供します。</span><span class="sxs-lookup"><span data-stu-id="27cc8-104">Declares the name of a module and introduces the definition of the variables, properties, events, and procedures that the module comprises.</span></span>

## <a name="syntax"></a><span data-ttu-id="27cc8-105">構文</span><span class="sxs-lookup"><span data-stu-id="27cc8-105">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  Module name
    [ statements ]
End Module
```

## <a name="parts"></a><span data-ttu-id="27cc8-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="27cc8-106">Parts</span></span>

`attributelist`  
<span data-ttu-id="27cc8-107">任意。</span><span class="sxs-lookup"><span data-stu-id="27cc8-107">Optional.</span></span> <span data-ttu-id="27cc8-108">「[属性リスト](attribute-list.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27cc8-108">See [Attribute List](attribute-list.md).</span></span>

`accessmodifier`  
<span data-ttu-id="27cc8-109">任意。</span><span class="sxs-lookup"><span data-stu-id="27cc8-109">Optional.</span></span> <span data-ttu-id="27cc8-110">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="27cc8-110">Can be one of the following:</span></span>

- [<span data-ttu-id="27cc8-111">Public</span><span class="sxs-lookup"><span data-stu-id="27cc8-111">Public</span></span>](../modifiers/public.md)

- [<span data-ttu-id="27cc8-112">Friend</span><span class="sxs-lookup"><span data-stu-id="27cc8-112">Friend</span></span>](../modifiers/friend.md)

<span data-ttu-id="27cc8-113">「 [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27cc8-113">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

`name`  
<span data-ttu-id="27cc8-114">必須です。</span><span class="sxs-lookup"><span data-stu-id="27cc8-114">Required.</span></span> <span data-ttu-id="27cc8-115">このモジュールの名前です。</span><span class="sxs-lookup"><span data-stu-id="27cc8-115">Name of this module.</span></span> <span data-ttu-id="27cc8-116">「 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27cc8-116">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

`statements`  
<span data-ttu-id="27cc8-117">任意。</span><span class="sxs-lookup"><span data-stu-id="27cc8-117">Optional.</span></span> <span data-ttu-id="27cc8-118">このモジュールの変数、プロパティ、イベント、プロシージャ、および入れ子にされた型を定義するステートメントです。</span><span class="sxs-lookup"><span data-stu-id="27cc8-118">Statements which define the variables, properties, events, procedures, and nested types of this module.</span></span>

`End Module`  
<span data-ttu-id="27cc8-119">`Module` の定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="27cc8-119">Terminates the `Module` definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="27cc8-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="27cc8-120">Remarks</span></span>

<span data-ttu-id="27cc8-121">`Module` ステートメントは、名前空間全体で使用できる参照型を定義します。</span><span class="sxs-lookup"><span data-stu-id="27cc8-121">A `Module` statement defines a reference type available throughout its namespace.</span></span> <span data-ttu-id="27cc8-122">*モジュール* (*標準モジュール* と呼ばれることもあります) はクラスに似ていますが、いくつかの重要な違いがあります。</span><span class="sxs-lookup"><span data-stu-id="27cc8-122">A *module* (sometimes called a *standard module*) is similar to a class but with some important distinctions.</span></span> <span data-ttu-id="27cc8-123">すべてのモジュールにはインスタンスが 1 つだけあり、変数を作成したり、変数に割り当てたりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="27cc8-123">Every module has exactly one instance and does not need to be created or assigned to a variable.</span></span> <span data-ttu-id="27cc8-124">モジュールは、継承をサポートしたり、インターフェイスを実装したりしません。</span><span class="sxs-lookup"><span data-stu-id="27cc8-124">Modules do not support inheritance or implement interfaces.</span></span> <span data-ttu-id="27cc8-125">モジュールはクラスまたは構造体の意味で *型* ではないことに注意してください。モジュールのデータ型を持つようにプログラミング要素を宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="27cc8-125">Notice that a module is not a *type* in the sense that a class or structure is — you cannot declare a programming element to have the data type of a module.</span></span>

<span data-ttu-id="27cc8-126">`Module` は、名前空間レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="27cc8-126">You can use `Module` only at namespace level.</span></span> <span data-ttu-id="27cc8-127">つまり、モジュールの *宣言コンテキスト* は、ソース ファイルまたは名前空間である必要があり、クラス、構造体、モジュール、インターフェイス、プロシージャ、またはブロックにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="27cc8-127">This means the *declaration context* for a module must be a source file or namespace, and cannot be a class, structure, module, interface, procedure, or block.</span></span> <span data-ttu-id="27cc8-128">モジュールは、別のモジュール内、または任意の型の中で入れ子にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="27cc8-128">You cannot nest a module within another module, or within any type.</span></span> <span data-ttu-id="27cc8-129">詳細については、「[宣言コンテキストと既定のアクセス レベル](declaration-contexts-and-default-access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27cc8-129">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="27cc8-130">モジュールの有効期間はプログラムと同じです。</span><span class="sxs-lookup"><span data-stu-id="27cc8-130">A module has the same lifetime as your program.</span></span> <span data-ttu-id="27cc8-131">そのメンバーはすべて `Shared` であるため、有効期間もプログラムと同じになります。</span><span class="sxs-lookup"><span data-stu-id="27cc8-131">Because its members are all `Shared`, they also have lifetimes equal to that of the program.</span></span>

<span data-ttu-id="27cc8-132">モジュールは、既定で [Friend](../modifiers/friend.md) アクセスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="27cc8-132">Modules default to [Friend](../modifiers/friend.md) access.</span></span> <span data-ttu-id="27cc8-133">アクセス修飾子を使用してこれらのアクセス レベルを調整できます。</span><span class="sxs-lookup"><span data-stu-id="27cc8-133">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="27cc8-134">詳しくは、「[Visual Basic でのアクセス レベル](../../programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27cc8-134">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="27cc8-135">モジュールのすべてのメンバーは、暗黙的に `Shared` です。</span><span class="sxs-lookup"><span data-stu-id="27cc8-135">All members of a module are implicitly `Shared`.</span></span>

## <a name="classes-and-modules"></a><span data-ttu-id="27cc8-136">クラスとモジュール</span><span class="sxs-lookup"><span data-stu-id="27cc8-136">Classes and Modules</span></span>

<span data-ttu-id="27cc8-137">これらの要素には多くの類似点がありますが、重要な相違点もいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="27cc8-137">These elements have many similarities, but there are some important differences as well.</span></span>

- <span data-ttu-id="27cc8-138">**用語。**</span><span class="sxs-lookup"><span data-stu-id="27cc8-138">**Terminology.**</span></span> <span data-ttu-id="27cc8-139">以前のバージョンの Visual Basic では、*クラス モジュール* (.cls ファイル) と *標準モジュール* (.bas ファイル) の 2 種類のモジュールを認識します。</span><span class="sxs-lookup"><span data-stu-id="27cc8-139">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span></span> <span data-ttu-id="27cc8-140">現在のバージョンでは、これらの *クラス* と *モジュール* をそれぞれ呼び出します。</span><span class="sxs-lookup"><span data-stu-id="27cc8-140">The current version calls these *classes* and *modules*, respectively.</span></span>

- <span data-ttu-id="27cc8-141">**共有メンバー。**</span><span class="sxs-lookup"><span data-stu-id="27cc8-141">**Shared Members.**</span></span> <span data-ttu-id="27cc8-142">クラスのメンバーが共有メンバーかインスタンス メンバーかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="27cc8-142">You can control whether a member of a class is a shared or instance member.</span></span>

- <span data-ttu-id="27cc8-143">**オブジェクト指向。**</span><span class="sxs-lookup"><span data-stu-id="27cc8-143">**Object Orientation.**</span></span> <span data-ttu-id="27cc8-144">クラスはオブジェクト指向ですが、モジュールはそうではありません。</span><span class="sxs-lookup"><span data-stu-id="27cc8-144">Classes are object-oriented, but modules are not.</span></span> <span data-ttu-id="27cc8-145">そのため、オブジェクトとしてインスタンス化できるのはクラスだけです。</span><span class="sxs-lookup"><span data-stu-id="27cc8-145">So only classes can be instantiated as objects.</span></span> <span data-ttu-id="27cc8-146">詳細については、[オブジェクトとクラス](../../programming-guide/language-features/objects-and-classes/index.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="27cc8-146">For more information, see [Objects and Classes](../../programming-guide/language-features/objects-and-classes/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="27cc8-147">ルール</span><span class="sxs-lookup"><span data-stu-id="27cc8-147">Rules</span></span>

- <span data-ttu-id="27cc8-148">**修飾子。**</span><span class="sxs-lookup"><span data-stu-id="27cc8-148">**Modifiers.**</span></span> <span data-ttu-id="27cc8-149">すべてのモジュール メンバーは、暗黙的に [Shared](../modifiers/shared.md) です。</span><span class="sxs-lookup"><span data-stu-id="27cc8-149">All module members are implicitly [Shared](../modifiers/shared.md).</span></span> <span data-ttu-id="27cc8-150">メンバーを宣言するときに `Shared` キーワードを使用することはできません。また、メンバーの共有ステータスを変更することもできません。</span><span class="sxs-lookup"><span data-stu-id="27cc8-150">You cannot use the `Shared` keyword when declaring a member, and you cannot alter the shared status of any member.</span></span>

- <span data-ttu-id="27cc8-151">**継承。**</span><span class="sxs-lookup"><span data-stu-id="27cc8-151">**Inheritance.**</span></span> <span data-ttu-id="27cc8-152">モジュールは、<xref:System.Object> 以外の型を継承できません。すべてのモジュールが、この型を継承します。</span><span class="sxs-lookup"><span data-stu-id="27cc8-152">A module cannot inherit from any type other than <xref:System.Object>, from which all modules inherit.</span></span> <span data-ttu-id="27cc8-153">特に、モジュールは別のモジュールからは継承できません。</span><span class="sxs-lookup"><span data-stu-id="27cc8-153">In particular, one module cannot inherit from another.</span></span>

  <span data-ttu-id="27cc8-154"><xref:System.Object> を指定する場合でも、モジュールの定義で [Inherits ステートメント](inherits-statement.md)を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="27cc8-154">You cannot use the [Inherits Statement](inherits-statement.md) in a module definition, even to specify <xref:System.Object>.</span></span>

- <span data-ttu-id="27cc8-155">**既定のプロパティ。**</span><span class="sxs-lookup"><span data-stu-id="27cc8-155">**Default Property.**</span></span> <span data-ttu-id="27cc8-156">モジュールでは、既定のプロパティを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="27cc8-156">You cannot define any default properties in a module.</span></span> <span data-ttu-id="27cc8-157">詳細については、「[Default](../modifiers/default.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27cc8-157">For more information, see [Default](../modifiers/default.md).</span></span>

## <a name="behavior"></a><span data-ttu-id="27cc8-158">動作</span><span class="sxs-lookup"><span data-stu-id="27cc8-158">Behavior</span></span>

- <span data-ttu-id="27cc8-159">**アクセス レベル。**</span><span class="sxs-lookup"><span data-stu-id="27cc8-159">**Access Level.**</span></span> <span data-ttu-id="27cc8-160">モジュールの内部では、各メンバーを独自のアクセス レベルで宣言できます。</span><span class="sxs-lookup"><span data-stu-id="27cc8-160">Within a module, you can declare each member with its own access level.</span></span> <span data-ttu-id="27cc8-161">モジュール メンバーは、既定で [Private](../modifiers/private.md) アクセスに設定される変数と定数を除き、既定で [Public](../modifiers/public.md) アクセスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="27cc8-161">Module members default to [Public](../modifiers/public.md) access, except variables and constants, which default to [Private](../modifiers/private.md) access.</span></span> <span data-ttu-id="27cc8-162">モジュールがそのメンバーのいずれかよりもアクセスが制限されている場合は、指定されたモジュールのアクセス レベルが優先されます。</span><span class="sxs-lookup"><span data-stu-id="27cc8-162">When a module has more restricted access than one of its members, the specified module access level takes precedence.</span></span>

- <span data-ttu-id="27cc8-163">**範囲**。</span><span class="sxs-lookup"><span data-stu-id="27cc8-163">**Scope.**</span></span> <span data-ttu-id="27cc8-164">モジュールは、その名前空間全体をスコープとします。</span><span class="sxs-lookup"><span data-stu-id="27cc8-164">A module is in scope throughout its namespace.</span></span>

  <span data-ttu-id="27cc8-165">すべてのモジュール メンバーのスコープは、モジュール全体になります。</span><span class="sxs-lookup"><span data-stu-id="27cc8-165">The scope of every module member is the entire module.</span></span> <span data-ttu-id="27cc8-166">すべてのメンバーで *型の上位変換* が行われることに注意してください。これにより、そのスコープがモジュールを含む名前空間に昇格します。</span><span class="sxs-lookup"><span data-stu-id="27cc8-166">Notice that all members undergo *type promotion*, which causes their scope to be promoted to the namespace containing the module.</span></span> <span data-ttu-id="27cc8-167">詳細については、「[型の上位変換](../../programming-guide/language-features/declared-elements/type-promotion.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27cc8-167">For more information, see [Type Promotion](../../programming-guide/language-features/declared-elements/type-promotion.md).</span></span>

- <span data-ttu-id="27cc8-168">**修飾。**</span><span class="sxs-lookup"><span data-stu-id="27cc8-168">**Qualification.**</span></span> <span data-ttu-id="27cc8-169">プロジェクトには複数のモジュールを含めることができ、2 つ以上のモジュールで同じ名前のメンバーを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="27cc8-169">You can have multiple modules in a project, and you can declare members with the same name in two or more modules.</span></span> <span data-ttu-id="27cc8-170">ただし、このようなメンバーへの参照は、そのモジュールの外部から参照されている場合は、適切なモジュール名で修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="27cc8-170">However, you must qualify any reference to such a member with the appropriate module name if the reference is from outside that module.</span></span> <span data-ttu-id="27cc8-171">詳細については、「 [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27cc8-171">For more information, see [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

## <a name="example"></a><span data-ttu-id="27cc8-172">例</span><span class="sxs-lookup"><span data-stu-id="27cc8-172">Example</span></span>

[!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]

## <a name="see-also"></a><span data-ttu-id="27cc8-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="27cc8-173">See also</span></span>

- [<span data-ttu-id="27cc8-174">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="27cc8-174">Class Statement</span></span>](class-statement.md)
- [<span data-ttu-id="27cc8-175">Namespace ステートメント</span><span class="sxs-lookup"><span data-stu-id="27cc8-175">Namespace Statement</span></span>](namespace-statement.md)
- [<span data-ttu-id="27cc8-176">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="27cc8-176">Structure Statement</span></span>](structure-statement.md)
- [<span data-ttu-id="27cc8-177">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="27cc8-177">Interface Statement</span></span>](interface-statement.md)
- [<span data-ttu-id="27cc8-178">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="27cc8-178">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="27cc8-179">型の上位変換</span><span class="sxs-lookup"><span data-stu-id="27cc8-179">Type Promotion</span></span>](../../programming-guide/language-features/declared-elements/type-promotion.md)
