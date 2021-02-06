---
description: '詳細情報: EmbedResource メソッド'
title: EmbedResource メソッド
ms.date: 03/30/2017
api_name:
- IALink.EmbedResource
- EmbedResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmbedResource
helpviewer_keywords:
- EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type:
- apiref
ms.openlocfilehash: f7896172e7416048352788caf7e092096924b7af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638354"
---
# <a name="embedresource-method"></a><span data-ttu-id="518a5-103">EmbedResource メソッド</span><span class="sxs-lookup"><span data-stu-id="518a5-103">EmbedResource Method</span></span>

<span data-ttu-id="518a5-104">埋め込みリソースを宣言します。</span><span class="sxs-lookup"><span data-stu-id="518a5-104">Declares an embedded resource.</span></span> <span data-ttu-id="518a5-105">このメソッドは、実際にはリソースを埋め込みません。</span><span class="sxs-lookup"><span data-stu-id="518a5-105">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="518a5-106">構文</span><span class="sxs-lookup"><span data-stu-id="518a5-106">Syntax</span></span>  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="518a5-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="518a5-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="518a5-108">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="518a5-108">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="518a5-109">リソースが含まれているファイルのファイルトークンまたはアセンブリ ID。</span><span class="sxs-lookup"><span data-stu-id="518a5-109">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="518a5-110">リソースの名前。</span><span class="sxs-lookup"><span data-stu-id="518a5-110">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="518a5-111">RVA からのリソースのオフセット。</span><span class="sxs-lookup"><span data-stu-id="518a5-111">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="518a5-112">やなどのアクセシビリティ `mrPublic` フラグ `mrPrivate` 。</span><span class="sxs-lookup"><span data-stu-id="518a5-112">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="518a5-113">これらのフラグは、を使用して、この [メソッド](../metadata/imetadataassemblyemit-defineexportedtype-method.md)に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="518a5-113">These flags may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="518a5-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="518a5-114">Return Value</span></span>  

 <span data-ttu-id="518a5-115">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="518a5-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="518a5-116">要件</span><span class="sxs-lookup"><span data-stu-id="518a5-116">Requirements</span></span>  

 <span data-ttu-id="518a5-117">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="518a5-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="518a5-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="518a5-118">See also</span></span>

- [<span data-ttu-id="518a5-119">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="518a5-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="518a5-120">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="518a5-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="518a5-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="518a5-121">ALink API</span></span>](index.md)
