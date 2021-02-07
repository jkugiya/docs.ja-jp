---
description: 詳細については、「ImportFile メソッド」を参照してください。
title: ImportFile メソッド
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
ms.openlocfilehash: 82c9c7de7cd739ee205dc3695ea651643d01ea3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718162"
---
# <a name="importfile-method"></a><span data-ttu-id="077b6-103">ImportFile メソッド</span><span class="sxs-lookup"><span data-stu-id="077b6-103">ImportFile Method</span></span>

<span data-ttu-id="077b6-104">アセンブリとバインドされていないモジュールをインポートします。</span><span class="sxs-lookup"><span data-stu-id="077b6-104">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="077b6-105">構文</span><span class="sxs-lookup"><span data-stu-id="077b6-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="077b6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="077b6-106">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="077b6-107">インポートするファイルの完全修飾名。</span><span class="sxs-lookup"><span data-stu-id="077b6-107">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="077b6-108">アセンブリにリンクされているファイルの名前を変更するために使用できる省略可能な出力ファイル名です。</span><span class="sxs-lookup"><span data-stu-id="077b6-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="077b6-109">TRUE の場合、ImportTypes が使用されます。それ以外の場合は、インポートを手動で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="077b6-109">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="077b6-110">一意のファイル ID が格納されるトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="077b6-110">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="077b6-111">ファイルには、アセンブリまたはファイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="077b6-111">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="077b6-112">[IMetaDataAssemblyImport インターフェイス](../metadata/imetadataassemblyimport-interface.md)へのポインターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="077b6-112">Receives pointer to [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="077b6-113">ファイルがアセンブリでない場合は NULL を指定できます。</span><span class="sxs-lookup"><span data-stu-id="077b6-113">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="077b6-114">インポートされたファイルまたはスコープの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="077b6-114">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="077b6-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="077b6-115">Return Value</span></span>  

 <span data-ttu-id="077b6-116">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="077b6-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="077b6-117">要件</span><span class="sxs-lookup"><span data-stu-id="077b6-117">Requirements</span></span>  

 <span data-ttu-id="077b6-118">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="077b6-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="077b6-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="077b6-119">See also</span></span>

- [<span data-ttu-id="077b6-120">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="077b6-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="077b6-121">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="077b6-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="077b6-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="077b6-122">ALink API</span></span>](index.md)
