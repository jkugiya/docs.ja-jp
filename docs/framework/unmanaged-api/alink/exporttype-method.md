---
description: '詳細情報: ExportType メソッド'
title: ExportType メソッド
ms.date: 03/30/2017
api_name:
- IALink.ExportType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportType
helpviewer_keywords:
- ExportType method
ms.assetid: 91a7ce63-f5b8-4f16-b2c4-e1d0baa88944
topic_type:
- apiref
ms.openlocfilehash: 6dc047cac3b80e6fe7a6f2cd980061b34bb7f286
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638068"
---
# <a name="exporttype-method"></a><span data-ttu-id="7565b-103">ExportType メソッド</span><span class="sxs-lookup"><span data-stu-id="7565b-103">ExportType Method</span></span>

<span data-ttu-id="7565b-104">型がエクスポート可能であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7565b-104">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7565b-105">構文</span><span class="sxs-lookup"><span data-stu-id="7565b-105">Syntax</span></span>  
  
```cpp  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="7565b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7565b-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="7565b-107">エクスポート元のアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="7565b-107">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="7565b-108">エクスポート可能な型を定義するファイルのファイルトークンまたはアセンブリ ID。</span><span class="sxs-lookup"><span data-stu-id="7565b-108">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="7565b-109">エクスポート可能にする型のトークン。</span><span class="sxs-lookup"><span data-stu-id="7565b-109">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="7565b-110">エクスポート可能にする完全修飾型名。</span><span class="sxs-lookup"><span data-stu-id="7565b-110">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="7565b-111">`ComType``tdPublic`やなどのフラグ `tdNested` 。</span><span class="sxs-lookup"><span data-stu-id="7565b-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="7565b-112">このパラメーターは、この [メソッド](../metadata/imetadataassemblyemit-defineexportedtype-method.md)に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="7565b-112">This parameter may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="7565b-113">エクスポートされた型のトークンを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="7565b-113">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7565b-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="7565b-114">Return Value</span></span>  

 <span data-ttu-id="7565b-115">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="7565b-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7565b-116">要件</span><span class="sxs-lookup"><span data-stu-id="7565b-116">Requirements</span></span>  

 <span data-ttu-id="7565b-117">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="7565b-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7565b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="7565b-118">See also</span></span>

- [<span data-ttu-id="7565b-119">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7565b-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="7565b-120">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7565b-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="7565b-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="7565b-121">ALink API</span></span>](index.md)
