---
description: '詳細情報: SetAssemblyProps メソッド'
title: SetAssemblyProps メソッド
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyProps
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type:
- apiref
ms.openlocfilehash: 212d8aad22ac1cb231db46f20ff65de2339a21aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662352"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="82f62-103">SetAssemblyProps メソッド</span><span class="sxs-lookup"><span data-stu-id="82f62-103">SetAssemblyProps Method</span></span>

<span data-ttu-id="82f62-104">アセンブリレベルのプロパティを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="82f62-104">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82f62-105">構文</span><span class="sxs-lookup"><span data-stu-id="82f62-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="82f62-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="82f62-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="82f62-107">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="82f62-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="82f62-108">プロパティを定義するファイルです。</span><span class="sxs-lookup"><span data-stu-id="82f62-108">File that defines the property.</span></span> <span data-ttu-id="82f62-109">がバインドされ `AssemblyID` ていない .netmodule を示していない場合は、NULL にすることができます。</span><span class="sxs-lookup"><span data-stu-id="82f62-109">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="82f62-110">変更するオプションを示します。</span><span class="sxs-lookup"><span data-stu-id="82f62-110">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="82f62-111">オプションの新しい値。</span><span class="sxs-lookup"><span data-stu-id="82f62-111">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82f62-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="82f62-112">Return Value</span></span>  

 <span data-ttu-id="82f62-113">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="82f62-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82f62-114">要件</span><span class="sxs-lookup"><span data-stu-id="82f62-114">Requirements</span></span>  

 <span data-ttu-id="82f62-115">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="82f62-115">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82f62-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="82f62-116">See also</span></span>

- [<span data-ttu-id="82f62-117">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82f62-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="82f62-118">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82f62-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="82f62-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="82f62-119">ALink API</span></span>](index.md)
