---
description: '詳細情報: ImportTypes2 メソッド'
title: ImportTypes2 メソッド
ms.date: 03/30/2017
api_name:
- IALink2.ImportTypes2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes2
helpviewer_keywords:
- ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type:
- apiref
ms.openlocfilehash: ca0d174061608f9b4abf524c43023e867e9a9646
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662612"
---
# <a name="importtypes2-method"></a><span data-ttu-id="4f6f7-103">ImportTypes2 メソッド</span><span class="sxs-lookup"><span data-stu-id="4f6f7-103">ImportTypes2 Method</span></span>

<span data-ttu-id="4f6f7-104">型のインポートを開始します。</span><span class="sxs-lookup"><span data-stu-id="4f6f7-104">Initiates the import of types.</span></span> <span data-ttu-id="4f6f7-105">[Importfile メソッド](importfile-method.md)を使用してインポートされた各スコープから型のインポートを開始するには、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4f6f7-105">Call this method to begin importing types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f6f7-106">構文</span><span class="sxs-lookup"><span data-stu-id="4f6f7-106">Syntax</span></span>  
  
```cpp  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f6f7-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4f6f7-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="4f6f7-108">インポート先のアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="4f6f7-108">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="4f6f7-109">インポート元のファイルの ID。</span><span class="sxs-lookup"><span data-stu-id="4f6f7-109">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="4f6f7-110">インポート元の0から始まるスコープ。</span><span class="sxs-lookup"><span data-stu-id="4f6f7-110">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="4f6f7-111">指定されたスコープ内の型の列挙子ハンドルを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="4f6f7-111">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="4f6f7-112">必要に応じて、 [IMetaDataImport2 インターフェイス](../metadata/imetadataimport2-interface.md) インターフェイスを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="4f6f7-112">Optionally receives [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="4f6f7-113">必要に応じて、指定されたスコープ内の型の数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="4f6f7-113">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f6f7-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="4f6f7-114">Return Value</span></span>  

 <span data-ttu-id="4f6f7-115">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="4f6f7-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f6f7-116">要件</span><span class="sxs-lookup"><span data-stu-id="4f6f7-116">Requirements</span></span>  

 <span data-ttu-id="4f6f7-117">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="4f6f7-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f6f7-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f6f7-118">See also</span></span>

- [<span data-ttu-id="4f6f7-119">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f6f7-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="4f6f7-120">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f6f7-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="4f6f7-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="4f6f7-121">ALink API</span></span>](index.md)
