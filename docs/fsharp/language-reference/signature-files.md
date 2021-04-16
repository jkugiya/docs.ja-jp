---
title: シグネチャ ファイル
description: F# シグネチャ ファイルを使用して、型、名前空間、モジュールなど F# プログラムの一連の要素のパブリック シグネチャに関する情報を保持する方法について説明します。
ms.date: 06/15/2018
ms.openlocfilehash: c04ac8bf4ee360a2caa15be8f2bbea41105bd160
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627152"
---
# <a name="signatures"></a><span data-ttu-id="91deb-103">シグネチャ</span><span class="sxs-lookup"><span data-stu-id="91deb-103">Signatures</span></span>

<span data-ttu-id="91deb-104">シグネチャ ファイルには、型、名前空間、モジュールなど F# プログラムの一連の要素のパブリック シグネチャに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="91deb-104">A signature file contains information about the public signatures of a set of F# program elements, such as types, namespaces, and modules.</span></span> <span data-ttu-id="91deb-105">これらのプログラム要素のアクセシビリティを指定するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="91deb-105">It can be used to specify the accessibility of these program elements.</span></span>

## <a name="remarks"></a><span data-ttu-id="91deb-106">解説</span><span class="sxs-lookup"><span data-stu-id="91deb-106">Remarks</span></span>

<span data-ttu-id="91deb-107">それぞれの F# コード ファイルでは、 *シグネチャ ファイル*(.fs の代わりに .fsi の拡張子を持つ、コード ファイルと同じ名前のファイル) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="91deb-107">For each F# code file, you can have a *signature file*, which is a file that has the same name as the code file but with the extension .fsi instead of .fs.</span></span> <span data-ttu-id="91deb-108">コマンド ラインを直接使用する場合に、シグネチャ ファイルをコンパイル コマンド ラインに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="91deb-108">Signature files can also be added to the compilation command-line if you are using the command line directly.</span></span> <span data-ttu-id="91deb-109">コード ファイルとシグネチャ ファイルを区別するために、コード ファイルは " *実装ファイル*" と呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="91deb-109">To distinguish between code files and signature files, code files are sometimes referred to as *implementation files*.</span></span> <span data-ttu-id="91deb-110">プロジェクトでは、シグネチャ ファイルが、関連するコード ファイルよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="91deb-110">In a project, the signature file should precede the associated code file.</span></span>

<span data-ttu-id="91deb-111">シグネチャ ファイルは、対応する実装ファイル内の名前空間、モジュール、型、およびメンバーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="91deb-111">A signature file describes the namespaces, modules, types, and members in the corresponding implementation file.</span></span> <span data-ttu-id="91deb-112">シグネチャ ファイルの情報を使用して、対応する実装ファイルのどのコードの部分に、実装ファイルの外部コードからアクセスできるのか、また、どの部分が実装ファイルの内部用なのかを指定します。</span><span class="sxs-lookup"><span data-stu-id="91deb-112">You use the information in a signature file to specify what parts of the code in the corresponding implementation file can be accessed from code outside the implementation file, and what parts are internal to the implementation file.</span></span> <span data-ttu-id="91deb-113">シグネチャ ファイルに含まれる名前空間、モジュール、型は、実装ファイルに含まれている名前空間、モジュール、型のサブセットである必要があります。</span><span class="sxs-lookup"><span data-stu-id="91deb-113">The namespaces, modules, and types that are included in the signature file must be a subset of the namespaces, modules, and types that are included in the implementation file.</span></span> <span data-ttu-id="91deb-114">このトピックの後半で例外をいくつか挙げますが、シグネチャ ファイルにリストされていない言語要素は、実装ファイルのプライベートな要素と見なされます。</span><span class="sxs-lookup"><span data-stu-id="91deb-114">With some exceptions noted later in this topic, those language elements that are not listed in the signature file are considered private to the implementation file.</span></span> <span data-ttu-id="91deb-115">プロジェクトまたはコマンド ラインでシグネチャ ファイルが見つからない場合は、既定のアクセシビリティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="91deb-115">If no signature file is found in the project or command line, the default accessibility is used.</span></span>

<span data-ttu-id="91deb-116">既定のアクセシビリティの詳細については、「[アクセスの制御](access-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91deb-116">For more information about the default accessibility, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="91deb-117">シグネチャ ファイルでは、各メソッドおよび関数の型および実装の定義は繰り返しません。</span><span class="sxs-lookup"><span data-stu-id="91deb-117">In a signature file, you do not repeat the definition of the types and the implementations of each method or function.</span></span> <span data-ttu-id="91deb-118">代わりに、各メソッドおよび関数のシグネチャを使用します。これは、モジュールまたは名前空間のフラグメントによって実装されている機能の完全な仕様として機能します。</span><span class="sxs-lookup"><span data-stu-id="91deb-118">Instead, you use the signature for each method and function, which acts as a complete specification of the functionality that is implemented by a module or namespace fragment.</span></span> <span data-ttu-id="91deb-119">型シグネチャの構文は、インターフェイスと抽象クラスの抽象メソッドの宣言で使用される構文と同じです。また、正しくコンパイルされた入力を表示するとき、IntelliSense および F# インタープリター fsi.exe によっても表示されます。</span><span class="sxs-lookup"><span data-stu-id="91deb-119">The syntax for a type signature is the same as that used in abstract method declarations in interfaces and abstract classes, and is also shown by IntelliSense and by the F# interpreter fsi.exe when it displays correctly compiled input.</span></span>

<span data-ttu-id="91deb-120">型がシールされているかどうか、またはインターフェイス型であるかどうかを示す十分な情報が型シグネチャにない場合、コンパイラに型の性質を示す属性を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91deb-120">If there is not enough information in the type signature to indicate whether a type is sealed, or whether it is an interface type, you must add an attribute that indicates the nature of the type to the compiler.</span></span> <span data-ttu-id="91deb-121">次の表に、この目的で使用する属性を示します。</span><span class="sxs-lookup"><span data-stu-id="91deb-121">Attributes that you use for this purpose are described in the following table.</span></span>

|<span data-ttu-id="91deb-122">属性</span><span class="sxs-lookup"><span data-stu-id="91deb-122">Attribute</span></span>|<span data-ttu-id="91deb-123">説明</span><span class="sxs-lookup"><span data-stu-id="91deb-123">Description</span></span>|
|---------|-----------|
|`[<Sealed>]`|<span data-ttu-id="91deb-124">抽象メンバーを持たない型、または拡張する必要がない型の場合。</span><span class="sxs-lookup"><span data-stu-id="91deb-124">For a type that has no abstract members, or that should not be extended.</span></span>|
|`[<Interface>]`|<span data-ttu-id="91deb-125">インターフェイスである型の場合。</span><span class="sxs-lookup"><span data-stu-id="91deb-125">For a type that is an interface.</span></span>|

<span data-ttu-id="91deb-126">シグネチャと実装ファイルの宣言との間で属性が一致しない場合、コンパイラはエラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="91deb-126">The compiler produces an error if the attributes are not consistent between the signature and the declaration in the implementation file.</span></span>

<span data-ttu-id="91deb-127">キーワード `val` を使用して、値または関数値のシグネチャを作成します。</span><span class="sxs-lookup"><span data-stu-id="91deb-127">Use the keyword `val` to create a signature for a value or function value.</span></span> <span data-ttu-id="91deb-128">キーワード `type` は、型シグネチャを導入します。</span><span class="sxs-lookup"><span data-stu-id="91deb-128">The keyword `type` introduces a type signature.</span></span>

<span data-ttu-id="91deb-129">`--sig` コンパイラ オプション使用して、シグネチャ ファイルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="91deb-129">You can generate a signature file by using the `--sig` compiler option.</span></span> <span data-ttu-id="91deb-130">通常、.fsi ファイルは手動で作成しません。</span><span class="sxs-lookup"><span data-stu-id="91deb-130">Generally, you do not write .fsi files manually.</span></span> <span data-ttu-id="91deb-131">代わりに、コンパイラを使用して .fsi ファイルを生成し、そのファイルをプロジェクトに追加します。既にファイルが存在する場合、アクセスできるようにしたくないメソッドや関数を削除することによって編集します。</span><span class="sxs-lookup"><span data-stu-id="91deb-131">Instead, you generate .fsi files by using the compiler, add them to your project, if you have one, and edit them by removing methods and functions that you do not want to be accessible.</span></span>

<span data-ttu-id="91deb-132">型シグネチャには、以下のようないくつかのルールがあります。</span><span class="sxs-lookup"><span data-stu-id="91deb-132">There are several rules for type signatures:</span></span>

- <span data-ttu-id="91deb-133">実装ファイルの型略称は、シグネチャ ファイルの省略しない型と一致してはなりません。</span><span class="sxs-lookup"><span data-stu-id="91deb-133">Type abbreviations in an implementation file must not match a type without an abbreviation in a signature file.</span></span>

- <span data-ttu-id="91deb-134">レコードと、判別された共用体は、フィールドとコンストラクターをすべて公開するか、または一切公開しない必要があります。また、シグネチャの順序は、実装ファイルの順序と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="91deb-134">Records and discriminated unions must expose either all or none of their fields and constructors, and the order in the signature must match the order in the implementation file.</span></span> <span data-ttu-id="91deb-135">クラスは、シグネチャのフィールドとメソッドの一部またはすべてを表示することも、あるいは一切表示しないこともできます。</span><span class="sxs-lookup"><span data-stu-id="91deb-135">Classes can reveal some, all, or none of their fields and methods in the signature.</span></span>

- <span data-ttu-id="91deb-136">コンストラクターを持つクラスと構造体は、基底クラスの宣言 ( `inherits` の宣言) を公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91deb-136">Classes and structures that have constructors must expose the declarations of their base classes (the `inherits` declaration).</span></span> <span data-ttu-id="91deb-137">また、コンストラクターを持つクラスと構造体は、抽象メソッドとインターフェイス宣言すべてを公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91deb-137">Also, classes and structures that have constructors must expose all of their abstract methods and interface declarations.</span></span>

- <span data-ttu-id="91deb-138">インターフェイスの型は、すべてのメソッドとインターフェイスを表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91deb-138">Interface types must reveal all their methods and interfaces.</span></span>

<span data-ttu-id="91deb-139">値シグネチャの規則は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="91deb-139">The rules for value signatures are as follows:</span></span>

- <span data-ttu-id="91deb-140">アクセシビリティの修飾子 (`public`、 `internal`など) およびシグネチャにおける `inline` と `mutable` の修飾子は、実装の修飾子と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="91deb-140">Modifiers for accessibility (`public`, `internal`, and so on) and the `inline` and `mutable` modifiers in the signature must match those in the implementation.</span></span>

- <span data-ttu-id="91deb-141">ジェネリック型パラメーターの数 (暗黙的に推定される、または明示的に宣言される) は一致している必要があります。また、ジェネリック型パラメーターの型と型制約は一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="91deb-141">The number of generic type parameters (either implicitly inferred or explicitly declared) must match, and the types and type constraints in generic type parameters must match.</span></span>

- <span data-ttu-id="91deb-142">`Literal` 属性を使用する場合、その属性はシグネチャと実装の両方に表示される必要があります。また、同じリテラル値を両方に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91deb-142">If the `Literal` attribute is used, it must appear in both the signature and the implementation, and the same literal value must be used for both.</span></span>

- <span data-ttu-id="91deb-143">シグネチャと実装のパラメーターのパターン ( *アリティ* とも呼ばれます) は、一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="91deb-143">The pattern of parameters (also known as the *arity*) of signatures and implementations must be consistent.</span></span>

- <span data-ttu-id="91deb-144">シグネチャ ファイル内のパラメーター名が対応する実装ファイルと異なる場合は、シグネチャ ファイル内の名前が代わりに使用されます。これにより、デバッグまたはプロファイル時に問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="91deb-144">If parameter names in a signature file differ from the corresponding implementation file, the name in the signature file will be used instead, which may cause issues when debugging or profiling.</span></span> <span data-ttu-id="91deb-145">このような不一致について通知されるようにするには、プロジェクト ファイルで、またはコンパイラを呼び出す際に警告 3218 を有効にします (「[コンパイラ オプション](compiler-options.md)」で `--warnon` を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="91deb-145">If you wish to be notified of such mismatches, enable warning 3218 in your project file or when invoking the compiler (see `--warnon` under [Compiler Options](compiler-options.md)).</span></span>

<span data-ttu-id="91deb-146">次のコード例では、適切な属性と共に名前空間、モジュール、関数値、型シグネチャを持つシグネチャ ファイルの例を示します。</span><span class="sxs-lookup"><span data-stu-id="91deb-146">The following code example shows an example of a signature file that has namespace, module, function value, and type signatures together with the appropriate attributes.</span></span> <span data-ttu-id="91deb-147">また、対応する実装ファイルも示します。</span><span class="sxs-lookup"><span data-stu-id="91deb-147">It also shows the corresponding implementation file.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssignatures/snippet9002.fs)]

<span data-ttu-id="91deb-148">次のコードは実装ファイルを示します。</span><span class="sxs-lookup"><span data-stu-id="91deb-148">The following code shows the implementation file.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssignatures/snippet9001.fs)]

## <a name="see-also"></a><span data-ttu-id="91deb-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="91deb-149">See also</span></span>

- [<span data-ttu-id="91deb-150">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="91deb-150">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="91deb-151">アクセス制御</span><span class="sxs-lookup"><span data-stu-id="91deb-151">Access Control</span></span>](access-control.md)
- [<span data-ttu-id="91deb-152">コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="91deb-152">Compiler Options</span></span>](compiler-options.md)
