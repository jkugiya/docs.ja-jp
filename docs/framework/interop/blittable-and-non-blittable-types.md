---
title: Blittable 型と非 Blittable 型
description: Blittable 型と非 Blittable 型について説明します。 Blittable データ型の表現は、マネージド メモリとアンマネージド メモリで共通しており、特別な処理は必要ありません。
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
ms.openlocfilehash: c9168bd245e10232a798b3e6f3b9448b24996a77
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436124"
---
# <a name="blittable-and-non-blittable-types"></a><span data-ttu-id="7f946-104">Blittable 型と非 Blittable 型</span><span class="sxs-lookup"><span data-stu-id="7f946-104">Blittable and Non-Blittable Types</span></span>

<span data-ttu-id="7f946-105">ほとんどのデータ型の表現はマネージド メモリとアンマネージド メモリの両方で共通しているため、相互運用マーシャラーによる特別な処理は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="7f946-105">Most data types have a common representation in both managed and unmanaged memory and do not require special handling by the interop marshaler.</span></span> <span data-ttu-id="7f946-106">これらの型は、マネージド コードとアンマネージド コード間での受け渡しの際に変換が必要でないため、*blittable 型* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="7f946-106">These types are called *blittable types* because they do not require conversion when they are passed between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="7f946-107">プラットフォーム呼び出しから返される構造体は blittable 型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f946-107">Structures that are returned from platform invoke calls must be blittable types.</span></span> <span data-ttu-id="7f946-108">プラットフォーム呼び出しでは、戻り値の型として非 blittable 型の構造体はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="7f946-108">Platform invoke does not support non-blittable structures as return types.</span></span>  
  
 <span data-ttu-id="7f946-109"><xref:System> 名前空間に属する次の型は blittable 型です。</span><span class="sxs-lookup"><span data-stu-id="7f946-109">The following types from the <xref:System> namespace are blittable types:</span></span>  
  
- <xref:System.Byte?displayProperty=nameWithType>  
  
- <xref:System.SByte?displayProperty=nameWithType>  
  
- <xref:System.Int16?displayProperty=nameWithType>  
  
- <xref:System.UInt16?displayProperty=nameWithType>  
  
- <xref:System.Int32?displayProperty=nameWithType>  
  
- <xref:System.UInt32?displayProperty=nameWithType>  
  
- <xref:System.Int64?displayProperty=nameWithType>  
  
- <xref:System.UInt64?displayProperty=nameWithType>  
  
- <xref:System.IntPtr?displayProperty=nameWithType>  
  
- <xref:System.UIntPtr?displayProperty=nameWithType>  
  
- <xref:System.Single?displayProperty=nameWithType>  
  
- <xref:System.Double?displayProperty=nameWithType>  
  
 <span data-ttu-id="7f946-110">次の複合型も blittable 型です。</span><span class="sxs-lookup"><span data-stu-id="7f946-110">The following complex types are also blittable types:</span></span>  
  
- <span data-ttu-id="7f946-111">整数の配列など、blittable プリミティブ型の 1 次元配列。</span><span class="sxs-lookup"><span data-stu-id="7f946-111">One-dimensional arrays of blittable primitive types, such as an array of integers.</span></span> <span data-ttu-id="7f946-112">ただし、blittable 型の可変配列を含む型自体は blittable ではありません。</span><span class="sxs-lookup"><span data-stu-id="7f946-112">However, a type that contains a variable array of blittable types is not itself blittable.</span></span>
  
- <span data-ttu-id="7f946-113">blittable 型だけを含む、書式設定された値型 (および、それらが書式設定された型としてマーシャリングされる場合はクラス)。</span><span class="sxs-lookup"><span data-stu-id="7f946-113">Formatted value types that contain only blittable types (and classes if they are marshaled as formatted types).</span></span> <span data-ttu-id="7f946-114">書式設定された値型の詳細については、「[Default marshaling for value types](default-marshaling-behavior.md#default-marshaling-for-value-types)」(値型に対する既定のマーシャリング) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f946-114">For more information about formatted value types, see [Default marshaling for value types](default-marshaling-behavior.md#default-marshaling-for-value-types).</span></span>  
  
 <span data-ttu-id="7f946-115">オブジェクト参照は blittable ではありません。</span><span class="sxs-lookup"><span data-stu-id="7f946-115">Object references are not blittable.</span></span> <span data-ttu-id="7f946-116">これには、単独では blittable なオブジェクトへの参照の配列も含まれます。</span><span class="sxs-lookup"><span data-stu-id="7f946-116">This includes an array of references to objects that are blittable by themselves.</span></span> <span data-ttu-id="7f946-117">たとえば、blittable な構造体は定義できますが、それらの構造体への参照の配列を含む blittable 型は定義できません。</span><span class="sxs-lookup"><span data-stu-id="7f946-117">For example, you can define a structure that is blittable, but you cannot define a blittable type that contains an array of references to those structures.</span></span>  
  
 <span data-ttu-id="7f946-118">blittable 型の配列と、blittable プリミティブ型のメンバーだけを含むクラスは、最適化のために、マーシャリング時にコピーされるのではなく[固定](copying-and-pinning.md)されます。</span><span class="sxs-lookup"><span data-stu-id="7f946-118">As an optimization, arrays of blittable primitive types and classes that contain only blittable members are [pinned](copying-and-pinning.md) instead of copied during marshaling.</span></span> <span data-ttu-id="7f946-119">これらの型は、呼び出し元と呼び出し先が同じアパートメントに属する場合には、In/Out パラメーターとしてマーシャリングされるように見えることがあります。</span><span class="sxs-lookup"><span data-stu-id="7f946-119">These types can appear to be marshaled as In/Out parameters when the caller and callee are in the same apartment.</span></span> <span data-ttu-id="7f946-120">ただし、そのような型は実際には In パラメーターとしてマーシャリングされるため、引数を In/Out パラメーターとしてマーシャリングする必要がある場合には、<xref:System.Runtime.InteropServices.InAttribute> 属性と <xref:System.Runtime.InteropServices.OutAttribute> 属性を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f946-120">However, these types are actually marshaled as In parameters, and you must apply the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes if you want to marshal the argument as an In/Out parameter.</span></span>
  
 <span data-ttu-id="7f946-121">一部のマネージド データ型は、アンマネージド環境では異なる表現が必要です。</span><span class="sxs-lookup"><span data-stu-id="7f946-121">Some managed data types require a different representation in an unmanaged environment.</span></span> <span data-ttu-id="7f946-122">これらの非 blittable データ型は、マーシャリングできる形式に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f946-122">These non-blittable data types must be converted into a form that can be marshaled.</span></span> <span data-ttu-id="7f946-123">たとえば、マネージド文字列は、文字列オブジェクトに変換しないとマーシャリングできないので、非 blittable 型です。</span><span class="sxs-lookup"><span data-stu-id="7f946-123">For example, managed strings are non-blittable types because they must be converted into string objects before they can be marshaled.</span></span>  
  
 <span data-ttu-id="7f946-124"><xref:System> 名前空間に属する非 blittable 型を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="7f946-124">The following table lists non-blittable types from the <xref:System> namespace.</span></span> <span data-ttu-id="7f946-125">[デリゲート](default-marshaling-behavior.md#default-marshaling-for-delegates)は静的メソッドまたはクラス インスタンスを参照するデータ構造体であり、これも非 blittable 型です。</span><span class="sxs-lookup"><span data-stu-id="7f946-125">[Delegates](default-marshaling-behavior.md#default-marshaling-for-delegates), which are data structures that refer to a static method or to a class instance, are also non-blittable.</span></span>  
  
|<span data-ttu-id="7f946-126">非 blittable 型</span><span class="sxs-lookup"><span data-stu-id="7f946-126">Non-blittable type</span></span>|<span data-ttu-id="7f946-127">説明</span><span class="sxs-lookup"><span data-stu-id="7f946-127">Description</span></span>|  
|-------------------------|-----------------|  
|[<span data-ttu-id="7f946-128">System.Array</span><span class="sxs-lookup"><span data-stu-id="7f946-128">System.Array</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="7f946-129">C スタイルの配列または `SAFEARRAY` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="7f946-129">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|<span data-ttu-id="7f946-130">[System.Boolean](/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7f946-130">[System.Boolean](/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span></span>|<span data-ttu-id="7f946-131">1、2、または 4 バイトの値に変換されます。`true` の場合は 1 または -1 になります。</span><span class="sxs-lookup"><span data-stu-id="7f946-131">Converts to a 1, 2, or 4-byte value with `true` as 1 or -1.</span></span>|  
|<span data-ttu-id="7f946-132">[System.Char](/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7f946-132">[System.Char](/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span></span>|<span data-ttu-id="7f946-133">Unicode 文字または ANSI 文字に変換されます。</span><span class="sxs-lookup"><span data-stu-id="7f946-133">Converts to a Unicode or ANSI character.</span></span>|  
|<span data-ttu-id="7f946-134">[System.Class](/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7f946-134">[System.Class](/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span></span>|<span data-ttu-id="7f946-135">クラス インターフェイスに変換されます。</span><span class="sxs-lookup"><span data-stu-id="7f946-135">Converts to a class interface.</span></span>|  
|[<span data-ttu-id="7f946-136">System.Object</span><span class="sxs-lookup"><span data-stu-id="7f946-136">System.Object</span></span>](default-marshaling-for-objects.md)|<span data-ttu-id="7f946-137">バリアントまたはインターフェイスに変換されます。</span><span class="sxs-lookup"><span data-stu-id="7f946-137">Converts to a variant or an interface.</span></span>|  
|[<span data-ttu-id="7f946-138">System.Mdarray</span><span class="sxs-lookup"><span data-stu-id="7f946-138">System.Mdarray</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="7f946-139">C スタイルの配列または `SAFEARRAY` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="7f946-139">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="7f946-140">System.String</span><span class="sxs-lookup"><span data-stu-id="7f946-140">System.String</span></span>](default-marshaling-for-strings.md)|<span data-ttu-id="7f946-141">null 参照で終わる文字列または BSTR に変換されます。</span><span class="sxs-lookup"><span data-stu-id="7f946-141">Converts to a string terminating in a null reference or to a BSTR.</span></span>|  
|<span data-ttu-id="7f946-142">[System.Valuetype](/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7f946-142">[System.Valuetype](/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span></span>|<span data-ttu-id="7f946-143">固定メモリ レイアウトを持つ構造体に変換されます。</span><span class="sxs-lookup"><span data-stu-id="7f946-143">Converts to a structure with a fixed memory layout.</span></span>|  
|[<span data-ttu-id="7f946-144">System.Szarray</span><span class="sxs-lookup"><span data-stu-id="7f946-144">System.Szarray</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="7f946-145">C スタイルの配列または `SAFEARRAY` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="7f946-145">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
  
 <span data-ttu-id="7f946-146">クラス型とオブジェクト型は COM 相互運用でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7f946-146">Class and object types are supported only by COM interop.</span></span> <span data-ttu-id="7f946-147">Visual Basic、C#、および C++ の対応する型については、[クラス ライブラリの概要](../../standard/class-library-overview.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f946-147">For corresponding types in Visual Basic, C#, and C++, see the [Class Library Overview](../../standard/class-library-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f946-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f946-148">See also</span></span>

- [<span data-ttu-id="7f946-149">既定のマーシャリング動作</span><span class="sxs-lookup"><span data-stu-id="7f946-149">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
