---
description: 詳細については、「リフレクションと .NET Native」を参照してください。
title: リフレクションおよび .NET ネイティブ
ms.date: 03/30/2017
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
ms.openlocfilehash: 150afe5964cbf3a8983540d5948b246a8f330793
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738443"
---
# <a name="reflection-and-net-native"></a><span data-ttu-id="1b716-103">リフレクションおよび .NET ネイティブ</span><span class="sxs-lookup"><span data-stu-id="1b716-103">Reflection and .NET Native</span></span>

<span data-ttu-id="1b716-104">.NET Framework では、マネージド開発はリフレクション API を介してメタプログラミングをサポートします。</span><span class="sxs-lookup"><span data-stu-id="1b716-104">In the .NET Framework, managed development supports metaprogramming through the reflection API.</span></span> <span data-ttu-id="1b716-105">リフレクションによって、アプリ内のオブジェクトの検査、検査で検出されたオブジェクトでのメソッドの呼び出し、実行時の新しい型の生成、およびその他多数の動的コード シナリオのサポートが可能になります。</span><span class="sxs-lookup"><span data-stu-id="1b716-105">Reflection allows you to inspect objects in an app, call methods on objects discovered through inspection, generate new types at run time, and supports many other dynamic code scenarios.</span></span> <span data-ttu-id="1b716-106">シリアル化と逆シリアル化もサポートしているため、オブジェクトのフィールド値を保持して、後で復元できます。</span><span class="sxs-lookup"><span data-stu-id="1b716-106">It also supports serialization and deserialization, which allows an object's field values to be persisted and later restored.</span></span> <span data-ttu-id="1b716-107">これらすべてのシナリオで、使用可能なメタデータに基づいてネイティブ コードを生成するために .NET Framework Just-In-Time (JIT) コンパイラが必要です。</span><span class="sxs-lookup"><span data-stu-id="1b716-107">These scenarios all require the .NET Framework just-in-time (JIT) compiler to generate native code based on available metadata.</span></span>  
  
 <span data-ttu-id="1b716-108">.NET Native ランタイムには JIT コンパイラが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="1b716-108">The .NET Native runtime doesn't include a JIT compiler.</span></span> <span data-ttu-id="1b716-109">そのため、必要なネイティブ コードすべてを事前に生成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-109">As a result, all necessary native code must be generated in advance.</span></span> <span data-ttu-id="1b716-110">生成するコードを決定するために一連のヒューリスティックが使用されますが、これらのヒューリスティックでは、可能性のあるすべてのメタプログラミング シナリオに対処できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="1b716-110">A set of heuristics is used to determine what code should be generated, but these heuristics cannot cover all possible metaprogramming scenarios.</span></span>  <span data-ttu-id="1b716-111">このため、[ランタイム ディレクティブ](runtime-directives-rd-xml-configuration-file-reference.md)を使って、これらのメタプログラミング シナリオにヒントを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b716-111">Therefore, you must provide hints for these metaprogramming scenarios by using [runtime directives](runtime-directives-rd-xml-configuration-file-reference.md).</span></span> <span data-ttu-id="1b716-112">必要なメタデータまたは実装コードを実行時に使うことができない場合、アプリは [MissingMetadataException](missingmetadataexception-class-net-native.md)、[MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md)、または [MissingInteropDataException](missinginteropdataexception-class-net-native.md) 例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="1b716-112">If the necessary metadata or implementation code is not available at runtime, your app throws a [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md), or [MissingInteropDataException](missinginteropdataexception-class-net-native.md) exception.</span></span> <span data-ttu-id="1b716-113">次の 2 つのトラブルシューティング ツールを使用すると、この例外を排除するランタイム ディレクティブ ファイルの適切なエントリが生成されます。</span><span class="sxs-lookup"><span data-stu-id="1b716-113">Two troubleshooters are available that will generate the appropriate entry for your runtime directives file that eliminates the exception:</span></span>  
  
- <span data-ttu-id="1b716-114">[MissingMetadataException トラブルシューティング ツール](https://dotnet.github.io/native/troubleshooter/type.html) (型の場合)。</span><span class="sxs-lookup"><span data-stu-id="1b716-114">The [MissingMetadataException troubleshooter](https://dotnet.github.io/native/troubleshooter/type.html) for types.</span></span>  
  
- <span data-ttu-id="1b716-115">[MissingMetadataException トラブルシューティング ツール](https://dotnet.github.io/native/troubleshooter/method.html) (メソッドの場合)。</span><span class="sxs-lookup"><span data-stu-id="1b716-115">The [MissingMetadataException troubleshooter](https://dotnet.github.io/native/troubleshooter/method.html) for methods.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1b716-116">ランタイム ディレクティブ ファイルが必要となる理由の背景を含む .NET ネイティブのコンパイルの概要については、「 [.NET ネイティブとコンパイル](net-native-and-compilation.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1b716-116">For an overview of the .NET Native compilation process that provides background on why a runtime directives file is needed, see [.NET Native and Compilation](net-native-and-compilation.md).</span></span>  
  
 <span data-ttu-id="1b716-117">また、.NET Native では、.NET Framework クラスライブラリのプライベートメンバーを反映することはできません。</span><span class="sxs-lookup"><span data-stu-id="1b716-117">In addition, .NET Native doesn't allow you to reflect over private members of the .NET Framework class library.</span></span> <span data-ttu-id="1b716-118">たとえば、.NET Framework クラス ライブラリ型のフィールドを取得するために <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> プロパティを呼び出すと、パブリックまたはプロテクト フィールドのみが返されます。</span><span class="sxs-lookup"><span data-stu-id="1b716-118">For example, a call to the <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> property to retrieve the fields of a .NET Framework class library type returns only public or protected fields.</span></span>  
  
 <span data-ttu-id="1b716-119">次のトピックに、アプリでリフレクションとシリアル化をサポートするために必要な概念を説明したドキュメントとリファレンス ドキュメントを示します。</span><span class="sxs-lookup"><span data-stu-id="1b716-119">The following topics provide the conceptual and reference documentation that you need to support reflection and serialization in your apps:</span></span>  
  
- [<span data-ttu-id="1b716-120">リフレクションに依存する API</span><span class="sxs-lookup"><span data-stu-id="1b716-120">APIs That Rely on Reflection</span></span>](apis-that-rely-on-reflection.md)  
  
- [<span data-ttu-id="1b716-121">リフレクション API リファレンス</span><span class="sxs-lookup"><span data-stu-id="1b716-121">Reflection API Reference</span></span>](net-native-reflection-api-reference.md)  
  
- [<span data-ttu-id="1b716-122">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="1b716-122">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="1b716-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b716-123">See also</span></span>

- [<span data-ttu-id="1b716-124">.NET ネイティブによるアプリのコンパイル</span><span class="sxs-lookup"><span data-stu-id="1b716-124">Compiling Apps with .NET Native</span></span>](index.md)
- [<span data-ttu-id="1b716-125">.NET Native とコンパイル</span><span class="sxs-lookup"><span data-stu-id="1b716-125">.NET Native and Compilation</span></span>](net-native-and-compilation.md)
