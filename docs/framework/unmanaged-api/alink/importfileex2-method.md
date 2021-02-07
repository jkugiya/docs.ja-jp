---
description: '詳細情報: ImportFileEx2 メソッド'
title: ImportFileEx2 メソッド
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx2
helpviewer_keywords:
- ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type:
- apiref
ms.openlocfilehash: 0968318ab7e416e56b71f2f30f2745d538d0ff8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718006"
---
# <a name="importfileex2-method"></a><span data-ttu-id="53827-103">ImportFileEx2 メソッド</span><span class="sxs-lookup"><span data-stu-id="53827-103">ImportFileEx2 Method</span></span>

<span data-ttu-id="53827-104">アセンブリとバインドされていないモジュールをインポートします。</span><span class="sxs-lookup"><span data-stu-id="53827-104">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="53827-105">このメソッドは [Importfile メソッド](importfile-method.md)に似ていますが、インポートされるファイルがディスク上に存在しない場合でも機能します。</span><span class="sxs-lookup"><span data-stu-id="53827-105">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53827-106">構文</span><span class="sxs-lookup"><span data-stu-id="53827-106">Syntax</span></span>  
  
```cpp  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="53827-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="53827-107">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="53827-108">インポートするファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="53827-108">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="53827-109">ターゲットファイルの名前 (省略可能)。</span><span class="sxs-lookup"><span data-stu-id="53827-109">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="53827-110">省略可能なインポートスコープ [IMetaDataAssemblyImport インターフェイス](../metadata/imetadataassemblyimport-interface.md) インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="53827-110">Optional import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="53827-111">TRUE の場合、ImportTypes が使用されます。それ以外の場合は、インポートを手動で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53827-111">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="53827-112">[Openscope メソッド](../metadata/imetadatadispenser-openscope-method.md)に渡されるフラグ。</span><span class="sxs-lookup"><span data-stu-id="53827-112">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="53827-113">アセンブリまたはファイルの一意の ID を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="53827-113">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="53827-114">アセンブリインポートスコープ [IMetaDataAssemblyImport インターフェイス](../metadata/imetadataassemblyimport-interface.md) インターフェイスを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="53827-114">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="53827-115">ファイルがアセンブリでない場合は NULL を指定できます。</span><span class="sxs-lookup"><span data-stu-id="53827-115">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="53827-116">インポートされたファイルまたはスコープの数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="53827-116">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53827-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="53827-117">Return Value</span></span>  

 <span data-ttu-id="53827-118">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="53827-118">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53827-119">要件</span><span class="sxs-lookup"><span data-stu-id="53827-119">Requirements</span></span>  

 <span data-ttu-id="53827-120">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="53827-120">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53827-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="53827-121">See also</span></span>

- [<span data-ttu-id="53827-122">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="53827-122">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="53827-123">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="53827-123">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="53827-124">ALink API</span><span class="sxs-lookup"><span data-stu-id="53827-124">ALink API</span></span>](index.md)
