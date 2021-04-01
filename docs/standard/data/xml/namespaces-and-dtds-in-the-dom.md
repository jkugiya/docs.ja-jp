---
description: '詳細情報: DOM における名前空間と DTD'
title: DOM における名前空間と DTD
ms.date: 03/30/2017
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
ms.openlocfilehash: 4445c1a33cca50707940758f812995c6b1db64cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775930"
---
# <a name="namespaces-and-dtds-in-the-dom"></a><span data-ttu-id="05154-103">DOM における名前空間と DTD</span><span class="sxs-lookup"><span data-stu-id="05154-103">Namespaces and DTDs in the DOM</span></span>

<span data-ttu-id="05154-104">ドキュメント型定義 (DTD) によって名前空間のサポートは複雑になります。</span><span class="sxs-lookup"><span data-stu-id="05154-104">Document type definitions (DTDs) complicate namespace support.</span></span> <span data-ttu-id="05154-105">たとえば、次の XML では、既定の属性の名前にコロンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="05154-105">For example, the following XML contains default attributes containing colons in their names.</span></span>  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 <span data-ttu-id="05154-106">この構造が許容される場合は、次のように解決される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="05154-106">The following are possible resolutions if this construct is allowed:</span></span>  
  
- <span data-ttu-id="05154-107">`x:` は名前空間プレフィックスとして扱われますが、このプレフィックスは `xmlns:x` という名前空間宣言によって解決されなければならないため、名前空間宣言を DTD のどこかに記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05154-107">The `x:` is treated as a namespace prefix, but this prefix must be resolvable using an `xmlns:x` namespace declaration, which must also exist somewhere in the DTD.</span></span> <span data-ttu-id="05154-108">このプレフィックスをインスタンス ドキュメント内の別の対象に割り当てるとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="05154-108">It is an error to map this prefix to something different in the instance document.</span></span>  
  
- <span data-ttu-id="05154-109">`x:` は名前空間プレフィックスとして扱われますが、このプレフィックスは常にインスタンス要素のコンテキストで解決されます。</span><span class="sxs-lookup"><span data-stu-id="05154-109">The `x:` is treated as a namespace prefix, but this prefix is always resolved in the context of the instance elements.</span></span> <span data-ttu-id="05154-110">つまり、`item` 要素が現れる名前空間スコープに応じて、プレフィックスが別々の名前空間 URI (Uniform Resource Identifier) に割り当てられる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="05154-110">This means the prefix could actually map to different namespace Uniform Resource Identifiers (URIs), depending on the namespace scope in which the `item` element appears.</span></span> <span data-ttu-id="05154-111">これは上記の解決よりも予測しやすい動作ですが、既定の属性を実体化する必要があるため、別の複雑な問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="05154-111">This behavior is more predictable than the resolution given in the earlier bullet, but it has other complicated ramifications because it requires the default attributes be materialized.</span></span>  
  
- <span data-ttu-id="05154-112">コロンは DTD 内にあるために無視され、属性の名前はプレフィックスと名前空間 URI のない `x:y` になります。</span><span class="sxs-lookup"><span data-stu-id="05154-112">The colon is ignored because it is in a DTD, and the name of the attribute is `x:y`, no prefix and no namespace URI.</span></span>  
  
- <span data-ttu-id="05154-113">既定の属性にコロンが含まれているため、DTD 内の名前でコロンを使用することはサポートされていないことを示す例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="05154-113">The colon in the default attribute throws an exception, saying that colons in names inside a DTD are not supported.</span></span> <span data-ttu-id="05154-114">これは予測可能な動作ですが、W3C (World Wide Web Consortium) が公開している DTD の多くは読み込めないことになります。</span><span class="sxs-lookup"><span data-stu-id="05154-114">This results in a predictable behavior, but means you cannot load many of the World Wide Web Consortium (W3C) published DTDs.</span></span>  
  
- <span data-ttu-id="05154-115">ユーザーが DTD 検証を要求すると、ドキュメント全体に対する名前空間のサポートがオフになります。</span><span class="sxs-lookup"><span data-stu-id="05154-115">When the user requests DTD validation, namespace support for the entire document is turned off.</span></span> <span data-ttu-id="05154-116">これによって W3C DTD の読み込みが可能になり、結果は予測可能な動作になります。</span><span class="sxs-lookup"><span data-stu-id="05154-116">This makes it possible to load W3C DTDs and results in a predictable behavior.</span></span>  
  
 <span data-ttu-id="05154-117">Microsoft .NET Framework の XML には、W3C との互換性を最大限に保つための第 2 のオプションが実装されています。</span><span class="sxs-lookup"><span data-stu-id="05154-117">The XML in the Microsoft .NET Framework implements the second option for maximum W3C compatibility.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05154-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="05154-118">See also</span></span>

- [<span data-ttu-id="05154-119">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="05154-119">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
