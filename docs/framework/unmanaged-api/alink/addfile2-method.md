---
description: '詳細情報: AddFile2 メソッド'
title: AddFile2 メソッド
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
ms.openlocfilehash: d53527ecf7e8b3a99a11ea99512fbc812125de3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638614"
---
# <a name="addfile2-method"></a><span data-ttu-id="d682b-103">AddFile2 メソッド</span><span class="sxs-lookup"><span data-stu-id="d682b-103">AddFile2 Method</span></span>

<span data-ttu-id="d682b-104">アセンブリにファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="d682b-104">Adds files to the assembly.</span></span> <span data-ttu-id="d682b-105">は、バインドされていないモジュールを作成するためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="d682b-105">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d682b-106">構文</span><span class="sxs-lookup"><span data-stu-id="d682b-106">Syntax</span></span>  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d682b-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d682b-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="d682b-108">ファイルが追加されるアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="d682b-108">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="d682b-109">追加するファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="d682b-109">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d682b-110">COM + `FileDef` フラグ ( `ffContainsNoMetaData` やなど) `ffWriteable` 。</span><span class="sxs-lookup"><span data-stu-id="d682b-110">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="d682b-111">`dwFlags` は、 [メソッド](../metadata/imetadataassemblyemit-definefile-method.md)に渡されます。</span><span class="sxs-lookup"><span data-stu-id="d682b-111">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="d682b-112">[IMetaDataEmit2 インターフェイス](../metadata/imetadataemit2-interface.md)インターフェイスへのインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="d682b-112">Interface to [IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="d682b-113">追加するファイルの ID を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d682b-113">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d682b-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="d682b-114">Return Value</span></span>  

 <span data-ttu-id="d682b-115">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="d682b-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d682b-116">要件</span><span class="sxs-lookup"><span data-stu-id="d682b-116">Requirements</span></span>  

 <span data-ttu-id="d682b-117">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="d682b-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d682b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="d682b-118">See also</span></span>

- [<span data-ttu-id="d682b-119">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d682b-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d682b-120">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d682b-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d682b-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="d682b-121">ALink API</span></span>](index.md)
