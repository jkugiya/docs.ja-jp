---
description: '詳細情報: リフレクション (Visual Basic)'
title: リフレクション
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: 532087f2ac32242b473d4524a6026519951d96d2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100486811"
---
# <a name="reflection-visual-basic"></a><span data-ttu-id="810fc-103">リフレクション (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="810fc-103">Reflection (Visual Basic)</span></span>

<span data-ttu-id="810fc-104">リフレクションは、アセンブリ、モジュール、および型を記述する (<xref:System.Type> 型の) オブジェクトを提供します。</span><span class="sxs-lookup"><span data-stu-id="810fc-104">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="810fc-105">リフレクションを使用すると、動的に型のインスタンスを作成したり、作成したインスタンスを既存のオブジェクトにバインドしたり、さらに既存のオブジェクトから型を取得してそのオブジェクトのメソッドを呼び出したり、フィールドやプロパティにアクセスしたりできます。</span><span class="sxs-lookup"><span data-stu-id="810fc-105">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="810fc-106">コードで属性を使用している場合は、リフレクションを使用してそれらにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="810fc-106">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="810fc-107">詳細については、「[属性](../../../standard/attributes/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="810fc-107">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="810fc-108">次の例は、`GetType` メソッドを使用して変数の型を取得する簡単なリフレクションを示しています。このメソッドは、`Object` 基底クラスからすべての型に継承される静的メソッドです。</span><span class="sxs-lookup"><span data-stu-id="810fc-108">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="810fc-109">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="810fc-109">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="810fc-110">次の例では、リフレクションを使用して、読み込まれたアセンブリの完全名を取得します。</span><span class="sxs-lookup"><span data-stu-id="810fc-110">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="810fc-111">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="810fc-111">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="810fc-112">リフレクションの概要</span><span class="sxs-lookup"><span data-stu-id="810fc-112">Reflection Overview</span></span>  

 <span data-ttu-id="810fc-113">リフレクションは、次の場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="810fc-113">Reflection is useful in the following situations:</span></span>  
  
- <span data-ttu-id="810fc-114">プログラムのメタデータ内の属性にアクセスする必要がある。</span><span class="sxs-lookup"><span data-stu-id="810fc-114">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="810fc-115">詳細については、「[属性に格納されている情報の取得](../../../standard/attributes/retrieving-information-stored-in-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="810fc-115">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
- <span data-ttu-id="810fc-116">アセンブリの型をチェックし、インスタンス化する。</span><span class="sxs-lookup"><span data-stu-id="810fc-116">For examining and instantiating types in an assembly.</span></span>  
  
- <span data-ttu-id="810fc-117">実行時に新しい型を作成する。</span><span class="sxs-lookup"><span data-stu-id="810fc-117">For building new types at runtime.</span></span> <span data-ttu-id="810fc-118"><xref:System.Reflection.Emit> でクラスを使います。</span><span class="sxs-lookup"><span data-stu-id="810fc-118">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
- <span data-ttu-id="810fc-119">遅延バインディングを実行するために、実行時に作成された型でメソッドにアクセスする。</span><span class="sxs-lookup"><span data-stu-id="810fc-119">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="810fc-120">「[型の動的な読み込みおよび使用](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="810fc-120">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="810fc-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="810fc-121">Related Sections</span></span>  

 <span data-ttu-id="810fc-122">詳細情報</span><span class="sxs-lookup"><span data-stu-id="810fc-122">For more information:</span></span>  
  
- [<span data-ttu-id="810fc-123">リフレクション</span><span class="sxs-lookup"><span data-stu-id="810fc-123">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
- [<span data-ttu-id="810fc-124">型情報の表示</span><span class="sxs-lookup"><span data-stu-id="810fc-124">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [<span data-ttu-id="810fc-125">リフレクションとジェネリック型</span><span class="sxs-lookup"><span data-stu-id="810fc-125">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [<span data-ttu-id="810fc-126">属性に格納されている情報の取得</span><span class="sxs-lookup"><span data-stu-id="810fc-126">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="810fc-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="810fc-127">See also</span></span>

- [<span data-ttu-id="810fc-128">Visual Basic プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="810fc-128">Visual Basic Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="810fc-129">.NET のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="810fc-129">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
