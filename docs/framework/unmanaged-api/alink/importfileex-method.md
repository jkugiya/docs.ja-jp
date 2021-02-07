---
description: '詳細情報: ImportFileEx メソッド'
title: ImportFileEx メソッド
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx
helpviewer_keywords:
- ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type:
- apiref
ms.openlocfilehash: a8a7e5a142091bf7cc93f50a4ae20c59d800f3ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718019"
---
# <a name="importfileex-method"></a><span data-ttu-id="ebe49-103">ImportFileEx メソッド</span><span class="sxs-lookup"><span data-stu-id="ebe49-103">ImportFileEx Method</span></span>

<span data-ttu-id="ebe49-104">指定したアセンブリまたはバインドされていないモジュールをインポートします。</span><span class="sxs-lookup"><span data-stu-id="ebe49-104">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebe49-105">構文</span><span class="sxs-lookup"><span data-stu-id="ebe49-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebe49-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ebe49-106">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="ebe49-107">インポート元のファイルの完全修飾名。</span><span class="sxs-lookup"><span data-stu-id="ebe49-107">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="ebe49-108">ターゲットファイルの名前 (省略可能)。</span><span class="sxs-lookup"><span data-stu-id="ebe49-108">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="ebe49-109">TRUE の場合、ImportTypes が使用されます。それ以外の場合は、インポートを手動で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebe49-109">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="ebe49-110">[Openscope メソッド](../metadata/imetadatadispenser-openscope-method.md)に渡されるフラグ。</span><span class="sxs-lookup"><span data-stu-id="ebe49-110">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="ebe49-111">インポートされるファイルの ID を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="ebe49-111">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="ebe49-112">アセンブリインポートスコープ [IMetaDataAssemblyImport インターフェイス](../metadata/imetadataassemblyimport-interface.md) インターフェイスを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="ebe49-112">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="ebe49-113">ファイルがアセンブリでない場合、は NULL に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ebe49-113">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="ebe49-114">インポートされたファイルまたはスコープの数を受信します。</span><span class="sxs-lookup"><span data-stu-id="ebe49-114">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ebe49-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="ebe49-115">Return Value</span></span>  

 <span data-ttu-id="ebe49-116">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="ebe49-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebe49-117">要件</span><span class="sxs-lookup"><span data-stu-id="ebe49-117">Requirements</span></span>  

 <span data-ttu-id="ebe49-118">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="ebe49-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebe49-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="ebe49-119">See also</span></span>

- [<span data-ttu-id="ebe49-120">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ebe49-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="ebe49-121">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ebe49-121">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="ebe49-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="ebe49-122">ALink API</span></span>](index.md)
