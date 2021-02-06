---
description: 詳細については、「ExportNestedType メソッド」を参照してください。
title: ExportNestedType メソッド
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedType
helpviewer_keywords:
- ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type:
- apiref
ms.openlocfilehash: 66cf4c3572857a0e7e99efa966cdb0b9ae2be673
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638145"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="cd9b4-103">ExportNestedType メソッド</span><span class="sxs-lookup"><span data-stu-id="cd9b4-103">ExportNestedType Method</span></span>

<span data-ttu-id="cd9b4-104">入れ子にされた型をエクスポート可能として指定します。</span><span class="sxs-lookup"><span data-stu-id="cd9b4-104">Specifies nested types as exportable.</span></span> <span data-ttu-id="cd9b4-105">[Exporttype メソッド](exporttype-method.md)も入れ子になった型をエクスポートできますが、このメソッドの方が高速です。</span><span class="sxs-lookup"><span data-stu-id="cd9b4-105">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd9b4-106">構文</span><span class="sxs-lookup"><span data-stu-id="cd9b4-106">Syntax</span></span>  
  
```cpp  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="cd9b4-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cd9b4-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="cd9b4-108">エクスポート元のアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="cd9b4-108">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="cd9b4-109">エクスポート可能にする型を定義するファイルのトークンまたはアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="cd9b4-109">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="cd9b4-110">エクスポート可能にする型の型トークン。</span><span class="sxs-lookup"><span data-stu-id="cd9b4-110">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="cd9b4-111">親の種類のトークン。</span><span class="sxs-lookup"><span data-stu-id="cd9b4-111">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="cd9b4-112">エクスポートする完全修飾型名。</span><span class="sxs-lookup"><span data-stu-id="cd9b4-112">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="cd9b4-113">`ComType``tdPublic`やなどのフラグ `tdNested` 。</span><span class="sxs-lookup"><span data-stu-id="cd9b4-113">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="cd9b4-114">この値は、この [メソッド](../metadata/imetadataassemblyemit-defineexportedtype-method.md)に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="cd9b4-114">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="cd9b4-115">エクスポートされた型のトークンを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="cd9b4-115">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd9b4-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="cd9b4-116">Return Value</span></span>  

 <span data-ttu-id="cd9b4-117">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="cd9b4-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd9b4-118">要件</span><span class="sxs-lookup"><span data-stu-id="cd9b4-118">Requirements</span></span>  

 <span data-ttu-id="cd9b4-119">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="cd9b4-119">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd9b4-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd9b4-120">See also</span></span>

- [<span data-ttu-id="cd9b4-121">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd9b4-121">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="cd9b4-122">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd9b4-122">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="cd9b4-123">ALink API</span><span class="sxs-lookup"><span data-stu-id="cd9b4-123">ALink API</span></span>](index.md)
