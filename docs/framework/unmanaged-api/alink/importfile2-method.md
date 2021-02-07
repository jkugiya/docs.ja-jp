---
description: '詳細情報: ImportFile2 メソッド'
title: ImportFile2 メソッド
ms.date: 03/30/2017
api_name:
- IALink.ImportFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile2
helpviewer_keywords:
- ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type:
- apiref
ms.openlocfilehash: 98da8ecf4bfc19e52c5a92e6509f6af49afbdd5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718058"
---
# <a name="importfile2-method"></a><span data-ttu-id="4cdbb-103">ImportFile2 メソッド</span><span class="sxs-lookup"><span data-stu-id="4cdbb-103">ImportFile2 Method</span></span>

<span data-ttu-id="4cdbb-104">アセンブリとバインドされていないモジュールをインポートします。</span><span class="sxs-lookup"><span data-stu-id="4cdbb-104">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="4cdbb-105">このメソッドは [Importfile メソッド](importfile-method.md)に似ていますが、インポートされるファイルがディスク上に存在しない場合でも機能します。</span><span class="sxs-lookup"><span data-stu-id="4cdbb-105">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cdbb-106">構文</span><span class="sxs-lookup"><span data-stu-id="4cdbb-106">Syntax</span></span>  
  
```cpp  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cdbb-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4cdbb-107">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="4cdbb-108">インポートするファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="4cdbb-108">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="4cdbb-109">アセンブリにリンクされているファイルの名前を変更するために使用できる省略可能な出力ファイル名です。</span><span class="sxs-lookup"><span data-stu-id="4cdbb-109">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="4cdbb-110">省略可能なスコープ [IMetaDataAssemblyImport インターフェイス](../metadata/imetadataassemblyimport-interface.md) インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="4cdbb-110">Optional scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="4cdbb-111">TRUE の場合、ImportTypes が使用されます。それ以外の場合は、インポートを手動で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4cdbb-111">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="4cdbb-112">ファイルまたはアセンブリの ID を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="4cdbb-112">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="4cdbb-113">[IMetaDataAssemblyImport インターフェイス](../metadata/imetadataassemblyimport-interface.md)インターフェイスを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="4cdbb-113">Receives the [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="4cdbb-114">ファイルがアセンブリでない場合は NULL です。</span><span class="sxs-lookup"><span data-stu-id="4cdbb-114">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="4cdbb-115">インポートされたファイルまたはスコープの検出されたを受信します。</span><span class="sxs-lookup"><span data-stu-id="4cdbb-115">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4cdbb-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="4cdbb-116">Return Value</span></span>  

 <span data-ttu-id="4cdbb-117">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="4cdbb-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cdbb-118">要件</span><span class="sxs-lookup"><span data-stu-id="4cdbb-118">Requirements</span></span>  

 <span data-ttu-id="4cdbb-119">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="4cdbb-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cdbb-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="4cdbb-120">See also</span></span>

- [<span data-ttu-id="4cdbb-121">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4cdbb-121">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="4cdbb-122">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4cdbb-122">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="4cdbb-123">ALink API</span><span class="sxs-lookup"><span data-stu-id="4cdbb-123">ALink API</span></span>](index.md)
