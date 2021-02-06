---
description: '詳細については、次を参照してください: Assembly属性 Gohere クラス'
title: Assembly属性 Gohere クラス (System.runtime.compilerservices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHere
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHere
helpviewer_keywords:
- AssemblyAttributesGoHere type
- Alink API, AssemblyAttributesGoHere type
ms.assetid: 7b26fcb6-94f4-4f09-933e-b33efe451f4f
topic_type:
- apiref
ms.openlocfilehash: b95ff377f7fa0ffc85136dd69eb4a32121a50dc2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638588"
---
# <a name="assemblyattributesgohere-class"></a><span data-ttu-id="6f214-103">Assembly属性 Gohere クラス</span><span class="sxs-lookup"><span data-stu-id="6f214-103">AssemblyAttributesGoHere Class</span></span>

<span data-ttu-id="6f214-104">ALink でプレースホルダーとして使用し、カスタム属性に関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="6f214-104">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="6f214-105">構文</span><span class="sxs-lookup"><span data-stu-id="6f214-105">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHere
```

## <a name="remarks"></a><span data-ttu-id="6f214-106">解説</span><span class="sxs-lookup"><span data-stu-id="6f214-106">Remarks</span></span>

<span data-ttu-id="6f214-107">この型への参照は、ソースにアセンブリのカスタム属性が含まれている netmodule 内部に埋め込まれていることがあります。</span><span class="sxs-lookup"><span data-stu-id="6f214-107">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="6f214-108">これらの型への参照が含まれる 1 つまたは複数の  netmodule からアセンブリ マニフェストを作成すると、ALink はこれらの参照にアタッチされた情報を使用して、実際のカスタム属性を生成します。</span><span class="sxs-lookup"><span data-stu-id="6f214-108">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="6f214-109">このため、この型がインスタンス化されることはなく、その型への参照はビルド処理の一部としてのみ使用され、最終的なアセンブリでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="6f214-109">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="6f214-110">この型への参照は、セキュリティに関連せず複数の用途を持たないカスタム属性を示します。</span><span class="sxs-lookup"><span data-stu-id="6f214-110">References to this type indicate custom attributes that are not security related and are not multiple-use.</span></span>

<span data-ttu-id="6f214-111">これらの型は、.NET Framework 内で "internal" とマークされ、名前空間に配置され <xref:System.Runtime.CompilerServices> ます。</span><span class="sxs-lookup"><span data-stu-id="6f214-111">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="6f214-112">要件</span><span class="sxs-lookup"><span data-stu-id="6f214-112">Requirements</span></span>

<span data-ttu-id="6f214-113">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="6f214-113">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="6f214-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f214-114">See also</span></span>

- [<span data-ttu-id="6f214-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="6f214-115">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="6f214-116">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="6f214-116">AssemblyAttributesGoHereS</span></span>](assemblyattributesgoheres.md)
- [<span data-ttu-id="6f214-117">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="6f214-117">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
