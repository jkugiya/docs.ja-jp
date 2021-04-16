---
description: '詳細情報: EnumCustomAttributes メソッド'
title: EnumCustomAttributes メソッド
ms.date: 03/30/2017
api_name:
- EnumCustomAttributes
- IALink.EnumCustomAttributes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method
ms.assetid: 08dff60c-f01b-4050-8865-ea3f95361c9f
topic_type:
- apiref
ms.openlocfilehash: d5b537462745914903f0cdb1e9f4436f2c27a68d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638134"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="5c42c-103">EnumCustomAttributes メソッド</span><span class="sxs-lookup"><span data-stu-id="5c42c-103">EnumCustomAttributes Method</span></span>

<span data-ttu-id="5c42c-104">アセンブリ レベルのカスタム属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="5c42c-104">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c42c-105">構文</span><span class="sxs-lookup"><span data-stu-id="5c42c-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c42c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5c42c-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="5c42c-107">列挙子のハンドル。</span><span class="sxs-lookup"><span data-stu-id="5c42c-107">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="5c42c-108">列挙する属性の型。</span><span class="sxs-lookup"><span data-stu-id="5c42c-108">Type of attributes to be enumerated.</span></span> <span data-ttu-id="5c42c-109">すべての属性に `mdTokenNill` を使用します。</span><span class="sxs-lookup"><span data-stu-id="5c42c-109">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="5c42c-110">カスタム属性トークンを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="5c42c-110">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5c42c-111">`rCustomValues` 配列のサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="5c42c-111">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="5c42c-112">必要に応じて、トークンの値の数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="5c42c-112">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c42c-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="5c42c-113">Return Value</span></span>  

 <span data-ttu-id="5c42c-114">メソッドが成功した場合は、S_OK が返されます。</span><span class="sxs-lookup"><span data-stu-id="5c42c-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c42c-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="5c42c-115">Requirements</span></span>  

 <span data-ttu-id="5c42c-116">alink.h を必要とします</span><span class="sxs-lookup"><span data-stu-id="5c42c-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c42c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c42c-117">See also</span></span>

- [<span data-ttu-id="5c42c-118">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c42c-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5c42c-119">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c42c-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="5c42c-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="5c42c-120">ALink API</span></span>](index.md)
