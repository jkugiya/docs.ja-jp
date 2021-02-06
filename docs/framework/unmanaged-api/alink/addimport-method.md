---
description: '詳細情報: AddImport メソッド'
title: AddImport メソッド
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
ms.openlocfilehash: 9dca26501e66313b0932caf1288db7c909154e1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638601"
---
# <a name="addimport-method"></a><span data-ttu-id="dc700-103">AddImport メソッド</span><span class="sxs-lookup"><span data-stu-id="dc700-103">AddImport Method</span></span>

<span data-ttu-id="dc700-104">アセンブリにインポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="dc700-104">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc700-105">構文</span><span class="sxs-lookup"><span data-stu-id="dc700-105">Syntax</span></span>  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc700-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dc700-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="dc700-107">補強するアセンブリの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="dc700-107">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="dc700-108">インポートするファイルの [Importfile メソッド](importfile-method.md)から取得された一意の ID。</span><span class="sxs-lookup"><span data-stu-id="dc700-108">Unique ID, retrieved from [ImportFile Method](importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="dc700-109">やなどの COM + FileDef フラグ `ffContainsNoMetaData` `ffWriteable` 。</span><span class="sxs-lookup"><span data-stu-id="dc700-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="dc700-110">`dwFlags` は、 [メソッド](../metadata/imetadataassemblyemit-definefile-method.md)に渡されます。</span><span class="sxs-lookup"><span data-stu-id="dc700-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="dc700-111">結果ファイルの ID を受け取るトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dc700-111">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc700-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="dc700-112">Return Value</span></span>  

 <span data-ttu-id="dc700-113">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="dc700-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc700-114">要件</span><span class="sxs-lookup"><span data-stu-id="dc700-114">Requirements</span></span>  

 <span data-ttu-id="dc700-115">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="dc700-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc700-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc700-116">See also</span></span>

- [<span data-ttu-id="dc700-117">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dc700-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="dc700-118">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dc700-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="dc700-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="dc700-119">ALink API</span></span>](index.md)
