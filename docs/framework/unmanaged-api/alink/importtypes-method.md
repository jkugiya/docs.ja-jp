---
description: '詳細情報: ImportTypes メソッド'
title: ImportTypes メソッド
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
ms.openlocfilehash: 9a30c735ca2c9ad0f945628c3de1eb1bb56efe2c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662625"
---
# <a name="importtypes-method"></a><span data-ttu-id="d3a2d-103">ImportTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="d3a2d-103">ImportTypes Method</span></span>

<span data-ttu-id="d3a2d-104">[Importfile メソッド](importfile-method.md)を使用してインポートされた各スコープからの型のインポートを開始します。</span><span class="sxs-lookup"><span data-stu-id="d3a2d-104">Initiates the importing of types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3a2d-105">構文</span><span class="sxs-lookup"><span data-stu-id="d3a2d-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3a2d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3a2d-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="d3a2d-107">インポート先のアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="d3a2d-107">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d3a2d-108">インポート元のファイルの ID。</span><span class="sxs-lookup"><span data-stu-id="d3a2d-108">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="d3a2d-109">インポートする0から始まるスコープ。</span><span class="sxs-lookup"><span data-stu-id="d3a2d-109">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="d3a2d-110">このスコープ内の型の列挙子ハンドルを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d3a2d-110">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="d3a2d-111">必要に応じて、 [IMetaDataImport インターフェイス](../metadata/imetadataimport-interface.md) インターフェイスを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d3a2d-111">Optionally receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="d3a2d-112">必要に応じて、指定されたスコープ内の型の数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d3a2d-112">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3a2d-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3a2d-113">Return Value</span></span>  

 <span data-ttu-id="d3a2d-114">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="d3a2d-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3a2d-115">要件</span><span class="sxs-lookup"><span data-stu-id="d3a2d-115">Requirements</span></span>  

 <span data-ttu-id="d3a2d-116">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="d3a2d-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3a2d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3a2d-117">See also</span></span>

- [<span data-ttu-id="d3a2d-118">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d3a2d-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d3a2d-119">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d3a2d-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d3a2d-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="d3a2d-120">ALink API</span></span>](index.md)
