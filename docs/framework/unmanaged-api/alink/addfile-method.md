---
description: '詳細情報: AddFile メソッド'
title: AddFile メソッド
ms.date: 03/30/2017
api_name:
- IALink.AddFile
- AddFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile
helpviewer_keywords:
- AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type:
- apiref
ms.openlocfilehash: 5e1253587298b2c1559c72dced43ec70dc169090
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638627"
---
# <a name="addfile-method"></a><span data-ttu-id="6cada-103">AddFile メソッド</span><span class="sxs-lookup"><span data-stu-id="6cada-103">AddFile Method</span></span>

<span data-ttu-id="6cada-104">アセンブリにファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="6cada-104">Adds files to the assembly.</span></span> <span data-ttu-id="6cada-105">は、バインドされていないモジュールを作成するためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="6cada-105">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cada-106">構文</span><span class="sxs-lookup"><span data-stu-id="6cada-106">Syntax</span></span>  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cada-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6cada-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="6cada-108">補強するアセンブリの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="6cada-108">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="6cada-109">追加するファイルの完全修飾名。</span><span class="sxs-lookup"><span data-stu-id="6cada-109">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6cada-110">やなどの COM + FileDef フラグ `ffContainsNoMetaData` `ffWriteable` 。</span><span class="sxs-lookup"><span data-stu-id="6cada-110">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="6cada-111">`dwFlags` は、 [メソッド](../metadata/imetadataassemblyemit-definefile-method.md)に渡されます。</span><span class="sxs-lookup"><span data-stu-id="6cada-111">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="6cada-112">必要に応じて、メタデータを出力するために使用される[IMetaDataEmit インターフェイス](../metadata/imetadataemit-interface.md)インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="6cada-112">[IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="6cada-113">追加されたファイルの一意の ID が格納される場所へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6cada-113">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6cada-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="6cada-114">Return Value</span></span>  

 <span data-ttu-id="6cada-115">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="6cada-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cada-116">要件</span><span class="sxs-lookup"><span data-stu-id="6cada-116">Requirements</span></span>  

 <span data-ttu-id="6cada-117">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="6cada-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cada-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="6cada-118">See also</span></span>

- [<span data-ttu-id="6cada-119">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6cada-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="6cada-120">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6cada-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="6cada-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="6cada-121">ALink API</span></span>](index.md)
