---
description: '詳細情報: EndMerge メソッド'
title: EndMerge メソッド
ms.date: 03/30/2017
api_name:
- IALink.EndMerge
- EndMerge
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EndMerge
helpviewer_keywords:
- EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type:
- apiref
ms.openlocfilehash: aac23d6d87f3fe74c1094bdd4a7f9c9f7f3fa7cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638159"
---
# <a name="endmerge-method"></a><span data-ttu-id="158f0-103">EndMerge メソッド</span><span class="sxs-lookup"><span data-stu-id="158f0-103">EndMerge Method</span></span>

<span data-ttu-id="158f0-104">すべてのカスタム属性が生成スコープにマージされたことを示します。</span><span class="sxs-lookup"><span data-stu-id="158f0-104">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="158f0-105">構文</span><span class="sxs-lookup"><span data-stu-id="158f0-105">Syntax</span></span>  
  
```cpp  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="158f0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="158f0-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="158f0-107">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="158f0-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="158f0-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="158f0-108">Return Value</span></span>  

 <span data-ttu-id="158f0-109">メソッドが成功した場合は、S_OK が返されます。</span><span class="sxs-lookup"><span data-stu-id="158f0-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="158f0-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="158f0-110">Requirements</span></span>  

 <span data-ttu-id="158f0-111">alink.h を必要とします</span><span class="sxs-lookup"><span data-stu-id="158f0-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="158f0-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="158f0-112">See also</span></span>

- [<span data-ttu-id="158f0-113">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="158f0-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="158f0-114">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="158f0-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="158f0-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="158f0-115">ALink API</span></span>](index.md)
