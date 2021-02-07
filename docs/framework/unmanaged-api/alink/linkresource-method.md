---
description: '詳細情報: LinkResource メソッド'
title: LinkResource メソッド
ms.date: 03/30/2017
api_name:
- IALink.LinkResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- LinkResource
helpviewer_keywords:
- LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type:
- apiref
ms.openlocfilehash: ff12138433577eccbb313b8e64a329be1358ba70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662547"
---
# <a name="linkresource-method"></a><span data-ttu-id="2cf9c-103">LinkResource メソッド</span><span class="sxs-lookup"><span data-stu-id="2cf9c-103">LinkResource Method</span></span>

<span data-ttu-id="2cf9c-104">リソース内のリンク。</span><span class="sxs-lookup"><span data-stu-id="2cf9c-104">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cf9c-105">構文</span><span class="sxs-lookup"><span data-stu-id="2cf9c-105">Syntax</span></span>  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cf9c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2cf9c-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="2cf9c-107">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="2cf9c-107">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="2cf9c-108">ファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="2cf9c-108">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="2cf9c-109">省略可能な新しいファイル名。</span><span class="sxs-lookup"><span data-stu-id="2cf9c-109">Optional new file name.</span></span> <span data-ttu-id="2cf9c-110">NULL 以外の場合は、 `pszFileName` pszNewLocation にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="2cf9c-110">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="2cf9c-111">リソースの名前。</span><span class="sxs-lookup"><span data-stu-id="2cf9c-111">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2cf9c-112">やなどのアクセシビリティ `mrPublic` フラグ `mrPrivate` 。</span><span class="sxs-lookup"><span data-stu-id="2cf9c-112">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="2cf9c-113">このパラメーターは、 [DefineManifestResource メソッド](../metadata/imetadataassemblyemit-definemanifestresource-method.md)に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="2cf9c-113">This parameter may be passed to [DefineManifestResource Method](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cf9c-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="2cf9c-114">Return Value</span></span>  

 <span data-ttu-id="2cf9c-115">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="2cf9c-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cf9c-116">要件</span><span class="sxs-lookup"><span data-stu-id="2cf9c-116">Requirements</span></span>  

 <span data-ttu-id="2cf9c-117">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="2cf9c-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cf9c-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="2cf9c-118">See also</span></span>

- [<span data-ttu-id="2cf9c-119">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2cf9c-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="2cf9c-120">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2cf9c-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="2cf9c-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="2cf9c-121">ALink API</span></span>](index.md)
