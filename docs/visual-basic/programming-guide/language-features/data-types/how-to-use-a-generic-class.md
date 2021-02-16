---
description: '詳細情報: 方法:ジェネリック クラスを使用する (Visual Basic)'
title: '方法: ジェネリック クラスを使用する'
ms.date: 07/20/2015
helpviewer_keywords:
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters [Visual Basic], data type
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
ms.openlocfilehash: b21f29223c6a7f611fd4064a0df28ed72f599361
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483964"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a><span data-ttu-id="578ec-103">方法: ジェネリック クラスを使用する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="578ec-103">How to: Use a Generic Class (Visual Basic)</span></span>

<span data-ttu-id="578ec-104">*型パラメーター* を受け取るクラスは、 *ジェネリック クラス* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="578ec-104">A class that takes *type parameters* is called a *generic class*.</span></span> <span data-ttu-id="578ec-105">ジェネリック クラスを使用している場合は、このパラメーターのそれぞれに *型引数* を入力することで、ジェネリック クラスから *構築済みクラス* を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="578ec-105">If you are using a generic class, you can generate a *constructed class* from it by supplying a *type argument* for each of these parameters.</span></span> <span data-ttu-id="578ec-106">これで、構築済みクラス型の変数を宣言し、構築済みクラスのインスタンスを作成して、その変数に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="578ec-106">You can then declare a variable of the constructed class type, and you can create an instance of the constructed class and assign it to that variable.</span></span>  
  
 <span data-ttu-id="578ec-107">クラスに加えて、ジェネリックの構造体、インターフェイス、プロシージャ、デリゲートを定義して利用することもできます。</span><span class="sxs-lookup"><span data-stu-id="578ec-107">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
 <span data-ttu-id="578ec-108">次のプロシージャは、.NET Framework で定義されたジェネリック クラスを受け取り、そこからインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="578ec-108">The following procedure takes a generic class defined in the .NET Framework and creates an instance from it.</span></span>  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a><span data-ttu-id="578ec-109">型パラメーターを受け取るクラスを使用するには</span><span class="sxs-lookup"><span data-stu-id="578ec-109">To use a class that takes a type parameter</span></span>  
  
1. <span data-ttu-id="578ec-110">ソース ファイルの先頭に [Imports ステートメント (.NET 名前空間および型)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) を含めて、<xref:System.Collections.Generic?displayProperty=nameWithType> 名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="578ec-110">At the beginning of your source file, include an [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) to import the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="578ec-111">これにより、<xref:System.Collections.Queue?displayProperty=nameWithType> などの他のキュー クラスと区別するために完全修飾しなくても <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> クラスを参照できるようになります。</span><span class="sxs-lookup"><span data-stu-id="578ec-111">This allows you to refer to the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class without having to fully qualify it to differentiate it from other queue classes such as <xref:System.Collections.Queue?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="578ec-112">通常の方法でオブジェクトを作成し、クラス名の直後に `(Of type)` を追加します。</span><span class="sxs-lookup"><span data-stu-id="578ec-112">Create the object in the normal way, but add `(Of type)` immediately after the class name.</span></span>  
  
     <span data-ttu-id="578ec-113">次の例では、同じクラス (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) を使用して、異なるデータ型の項目を保持する 2 つのキュー オブジェクトを作成しています。</span><span class="sxs-lookup"><span data-stu-id="578ec-113">The following example uses the same class (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) to create two queue objects that hold items of different data types.</span></span> <span data-ttu-id="578ec-114">項目は各キューの末尾に追加された後に削除され、各キューの先頭から項目が表示されます。</span><span class="sxs-lookup"><span data-stu-id="578ec-114">It adds items to the end of each queue and then removes and displays items from the front of each queue.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="578ec-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="578ec-115">See also</span></span>

- [<span data-ttu-id="578ec-116">データの種類</span><span class="sxs-lookup"><span data-stu-id="578ec-116">Data Types</span></span>](index.md)
- [<span data-ttu-id="578ec-117">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="578ec-117">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="578ec-118">言語への非依存性、および言語非依存コンポーネント</span><span class="sxs-lookup"><span data-stu-id="578ec-118">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="578ec-119">Of</span><span class="sxs-lookup"><span data-stu-id="578ec-119">Of</span></span>](../../../language-reference/statements/of-clause.md)
- [<span data-ttu-id="578ec-120">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="578ec-120">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="578ec-121">方法: 複数のデータ型に同一の機能を提供できるクラスを定義する</span><span class="sxs-lookup"><span data-stu-id="578ec-121">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](how-to-define-a-class-that-can-provide-identical-functionality.md)
- [<span data-ttu-id="578ec-122">反復子</span><span class="sxs-lookup"><span data-stu-id="578ec-122">Iterators</span></span>](../../concepts/iterators.md)
