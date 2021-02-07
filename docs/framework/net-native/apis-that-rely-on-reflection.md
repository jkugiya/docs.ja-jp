---
description: 詳細については、「リフレクションに依存する Api」を参照してください。
title: リフレクションに依存する API
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
ms.openlocfilehash: a5661719e47a0a9ecb9f0fe9d188b8a67d1068eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738742"
---
# <a name="apis-that-rely-on-reflection"></a><span data-ttu-id="5475c-103">リフレクションに依存する API</span><span class="sxs-lookup"><span data-stu-id="5475c-103">APIs That Rely on Reflection</span></span>

<span data-ttu-id="5475c-104">場合によっては、コードでのリフレクションの使用は明確ではないため、.NET Native ツールチェーンは実行時に必要なメタデータを保持しません。</span><span class="sxs-lookup"><span data-stu-id="5475c-104">In some cases, the use of reflection in code isn't obvious, and so the .NET Native tool chain doesn't preserve metadata that is needed at run time.</span></span> <span data-ttu-id="5475c-105">このトピックでは、リフレクション API の一部であるとは見なされないが、正常に実行するためにリフレクションを必要とする、一般的な API と一般的なプログラミング パターンについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5475c-105">This topic covers some common APIs or common programming patterns that aren't considered part of the reflection API but that rely on reflection to execute successfully.</span></span> <span data-ttu-id="5475c-106">これらをソース コードで使用している場合、これらに関する情報をランタイム ディレクティブ (.rd.xml) ファイルに追加して、これらの API を呼び出しても [MissingMetadataException](missingmetadataexception-class-net-native.md) 例外やその他の例外が実行時にスローされないようにできます。</span><span class="sxs-lookup"><span data-stu-id="5475c-106">If you use them in your source code, you can add information about them to the runtime directives (.rd.xml) file so that calls to these APIs do not throw a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception or some other exception at run time.</span></span>  
  
## <a name="typemakegenerictype-method"></a><span data-ttu-id="5475c-107">Type.MakeGenericType メソッド</span><span class="sxs-lookup"><span data-stu-id="5475c-107">Type.MakeGenericType method</span></span>  

 <span data-ttu-id="5475c-108">ジェネリック型 `AppClass<T>` を動的にインスタンス化するには、次のようなコードを使用して <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5475c-108">You can dynamically instantiate a generic type `AppClass<T>` by calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 <span data-ttu-id="5475c-109">このコードが実行時に成功するためには、いくつかのメタデータ項目が必要です。</span><span class="sxs-lookup"><span data-stu-id="5475c-109">For this code to succeed at run time, several items of metadata are required.</span></span> <span data-ttu-id="5475c-110">1 つ目は、インスタンス化されていないジェネリック型 `Browse` の `AppClass<T>` メタデータです。</span><span class="sxs-lookup"><span data-stu-id="5475c-110">The first is `Browse` metadata for the uninstantiated generic type, `AppClass<T>`:</span></span>  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="5475c-111">これにより、<xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> メソッド呼び出しが成功し、有効な <xref:System.Type> オブジェクトが返されます。</span><span class="sxs-lookup"><span data-stu-id="5475c-111">This allows the <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> method call to succeed and return a valid <xref:System.Type> object.</span></span>  
  
 <span data-ttu-id="5475c-112">ただし、インスタンス化されていないジェネリック型のメタデータを追加した場合でも、<xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> メソッドを呼び出すと、次のような [MissingMetadataException](missingmetadataexception-class-net-native.md) 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="5475c-112">But even when you add metadata for the uninstantiated generic type, calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method throws a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception:</span></span>  
  
<span data-ttu-id="5475c-113">パフォーマンス上の理由から、次の種類のメタデータが削除されたため、この操作を実行できません:</span><span class="sxs-lookup"><span data-stu-id="5475c-113">This operation cannot be carried out as metadata for the following type was removed for performance reasons:</span></span>  
  
<span data-ttu-id="5475c-114">`App1.AppClass`1<system.string>'。</span><span class="sxs-lookup"><span data-stu-id="5475c-114">`App1.AppClass`1<System.Int32>\`.</span></span>  
  
 <span data-ttu-id="5475c-115">次のランタイム ディレクティブをランタイム ディレクティブ ファイルに追加すると、`Activate` の `AppClass<T>` に対する特定のインスタンス化の <xref:System.Int32?displayProperty=nameWithType> メタデータを追加できます。</span><span class="sxs-lookup"><span data-stu-id="5475c-115">You can add the following run-time directive to the runtime directives file to add `Activate` metadata for the specific instantiation over `AppClass<T>` of <xref:System.Int32?displayProperty=nameWithType>:</span></span>  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"
                   Activate="Required Public" />  
```  
  
 <span data-ttu-id="5475c-116">`AppClass<T>` に対するそれぞれ異なるインスタンス化は、<xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> メソッドにより作成され、静的に使用されていない場合、個別のディレクティブを必要とします。</span><span class="sxs-lookup"><span data-stu-id="5475c-116">Each different instantiation over `AppClass<T>` requires a separate directive if it is being created with the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method and not used statically.</span></span>  
  
## <a name="methodinfomakegenericmethod-method"></a><span data-ttu-id="5475c-117">MethodInfo.MakeGenericMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="5475c-117">MethodInfo.MakeGenericMethod method</span></span>  

 <span data-ttu-id="5475c-118">ジェネリック メソッド `Class1` を持つクラス `GetMethod<T>(T t)` があるとすると、`GetMethod` は、次のようなコードを使用してリフレクションにより呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="5475c-118">Given a class `Class1` with a generic method `GetMethod<T>(T t)`, `GetMethod` can be invoked through reflection by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 <span data-ttu-id="5475c-119">このコードを正常に実行するには、次のようないくつかのメタデータ項目が必要です。</span><span class="sxs-lookup"><span data-stu-id="5475c-119">To run successfully, this code requires several items of metadata:</span></span>  
  
- <span data-ttu-id="5475c-120">呼び出すメソッドを持つ型の `Browse` メタデータ。</span><span class="sxs-lookup"><span data-stu-id="5475c-120">`Browse` metadata for the type whose method you want to call.</span></span>  
  
- <span data-ttu-id="5475c-121">呼び出すメソッドの `Browse` メタデータ。</span><span class="sxs-lookup"><span data-stu-id="5475c-121">`Browse` metadata for the method you want to call.</span></span>  <span data-ttu-id="5475c-122">パブリック メソッドの場合、それを含む型のパブリック `Browse` メタデータを追加しても、メソッドが含められます。</span><span class="sxs-lookup"><span data-stu-id="5475c-122">If it is a public method, adding public `Browse` metadata for the containing type includes the method, too.</span></span>  
  
- <span data-ttu-id="5475c-123">リフレクション呼び出しデリゲートが .NET Native ツールチェーンによって削除されないようにするために、呼び出すメソッドの動的メタデータ。</span><span class="sxs-lookup"><span data-stu-id="5475c-123">Dynamic metadata for the method you want to call, so that the reflection invocation delegate is not removed by the .NET Native tool chain.</span></span> <span data-ttu-id="5475c-124">メソッドの動的メタデータが欠落している場合、<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> メソッドを呼び出すと、次の例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="5475c-124">If dynamic metadata is missing for the method, the following exception is thrown when the <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method is called:</span></span>  
  
    ```output
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 <span data-ttu-id="5475c-125">次のランタイム ディレクティブは、必要なすべてのメタデータが必ず使用可能であるようにします。</span><span class="sxs-lookup"><span data-stu-id="5475c-125">The following runtime directives ensure that all required metadata is available:</span></span>  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 <span data-ttu-id="5475c-126">`MethodInstantiation` ディレクティブは、動的に呼び出されるメソッドの異なるインスタンス化ごとに必要です。`Arguments` 要素は、それぞれ異なるインスタンス化引数を反映するために更新されます。</span><span class="sxs-lookup"><span data-stu-id="5475c-126">A `MethodInstantiation` directive is required for each different instantiation of the method that is dynamically invoked, and the `Arguments` element is updated to reflect each different instantiation argument.</span></span>  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a><span data-ttu-id="5475c-127">Array.CreateInstance メソッドと Type.MakeTypeArray メソッド</span><span class="sxs-lookup"><span data-stu-id="5475c-127">Array.CreateInstance and Type.MakeTypeArray methods</span></span>  

 <span data-ttu-id="5475c-128">次の例は、<xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> 型で <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> メソッドと `Class1` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5475c-128">The following example calls the <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> methods on a type, `Class1`.</span></span>  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 <span data-ttu-id="5475c-129">配列メタデータが存在しない場合、次のエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="5475c-129">If no array metadata is present, the following error results:</span></span>  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 <span data-ttu-id="5475c-130">配列型の `Browse` メタデータは、配列を動的にインスタンス化するために必要です。</span><span class="sxs-lookup"><span data-stu-id="5475c-130">`Browse` metadata for the array type is required to dynamically instantiate it.</span></span>  <span data-ttu-id="5475c-131">次のランタイム ディレクティブにより、`Class1[]` を動的にインスタンス化できます。</span><span class="sxs-lookup"><span data-stu-id="5475c-131">The following runtime directive allows dynamic instantiation of `Class1[]`.</span></span>  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="5475c-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="5475c-132">See also</span></span>

- [<span data-ttu-id="5475c-133">はじめに</span><span class="sxs-lookup"><span data-stu-id="5475c-133">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="5475c-134">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="5475c-134">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
