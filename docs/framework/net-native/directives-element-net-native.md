---
description: '詳細情報: <Directives> 要素 (.NET Native)'
title: <Directives> 要素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 7aa3bf3718f32d55ba8189c65705868c6fb399ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662911"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="3c50f-103">\<Directives> 要素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="3c50f-103">\<Directives> Element (.NET Native)</span></span>

<span data-ttu-id="3c50f-104">.NET Native のすべてのランタイムディレクティブファイルのルート要素。</span><span class="sxs-lookup"><span data-stu-id="3c50f-104">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a><span data-ttu-id="3c50f-105">構文</span><span class="sxs-lookup"><span data-stu-id="3c50f-105">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="3c50f-106">属性</span><span class="sxs-lookup"><span data-stu-id="3c50f-106">Attributes</span></span>  
  
|<span data-ttu-id="3c50f-107">属性</span><span class="sxs-lookup"><span data-stu-id="3c50f-107">Attribute</span></span>|<span data-ttu-id="3c50f-108">説明</span><span class="sxs-lookup"><span data-stu-id="3c50f-108">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="3c50f-109">XML 名前空間。</span><span class="sxs-lookup"><span data-stu-id="3c50f-109">The XML namespace.</span></span> <span data-ttu-id="3c50f-110">値は常に `http://schemas.microsoft.com/netfx/2013/01/metadata` です。</span><span class="sxs-lookup"><span data-stu-id="3c50f-110">Its value is always `http://schemas.microsoft.com/netfx/2013/01/metadata`.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="3c50f-111">子要素</span><span class="sxs-lookup"><span data-stu-id="3c50f-111">Child elements</span></span>  
  
|<span data-ttu-id="3c50f-112">要素</span><span class="sxs-lookup"><span data-stu-id="3c50f-112">Element</span></span>|<span data-ttu-id="3c50f-113">説明</span><span class="sxs-lookup"><span data-stu-id="3c50f-113">Description</span></span>|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="3c50f-114">リフレクションで使用可能なメタデータを持つアプリケーション全体の型と型のメンバーのコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="3c50f-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="3c50f-115">実行時にメタデータを必要とする子型と型のメンバーを持つアセンブリを定義します。</span><span class="sxs-lookup"><span data-stu-id="3c50f-115">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c50f-116">解説</span><span class="sxs-lookup"><span data-stu-id="3c50f-116">Remarks</span></span>  

 <span data-ttu-id="3c50f-117">各ランタイム ディレクティブ ファイルには、`<Directives>` 要素を 1 つのみ含めることができます。</span><span class="sxs-lookup"><span data-stu-id="3c50f-117">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="3c50f-118">要素には、 `<Directives>` 0 個または1個の要素と、0個以上の要素を含めることができ [\<Application>](application-element-net-native.md) [\<Library>](library-element-net-native.md) ます。</span><span class="sxs-lookup"><span data-stu-id="3c50f-118">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c50f-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c50f-119">See also</span></span>

- [<span data-ttu-id="3c50f-120">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="3c50f-120">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="3c50f-121">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="3c50f-121">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
