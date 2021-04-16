---
description: '詳細情報: ExportNestedType メソッド'
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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638145"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="a5ae8-103">ExportNestedType メソッド</span><span class="sxs-lookup"><span data-stu-id="a5ae8-103">ExportNestedType Method</span></span>

<span data-ttu-id="a5ae8-104">入れ子にされた型をエクスポート可能として指定します。</span><span class="sxs-lookup"><span data-stu-id="a5ae8-104">Specifies nested types as exportable.</span></span> <span data-ttu-id="a5ae8-105">入れ子になった型のエクスポートは [ExportType メソッド](exporttype-method.md)でもできますが、このメソッドの方が高速です。</span><span class="sxs-lookup"><span data-stu-id="a5ae8-105">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5ae8-106">構文</span><span class="sxs-lookup"><span data-stu-id="a5ae8-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a5ae8-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a5ae8-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="a5ae8-108">エクスポート元のアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="a5ae8-108">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="a5ae8-109">エクスポート可能にする型を定義するファイルのファイル トークンまたはアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="a5ae8-109">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="a5ae8-110">エクスポート可能にする型の型トークン。</span><span class="sxs-lookup"><span data-stu-id="a5ae8-110">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="a5ae8-111">親の型のトークン。</span><span class="sxs-lookup"><span data-stu-id="a5ae8-111">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="a5ae8-112">エクスポートする完全修飾型名。</span><span class="sxs-lookup"><span data-stu-id="a5ae8-112">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a5ae8-113">`tdPublic` や `tdNested` などの `ComType` フラグ。</span><span class="sxs-lookup"><span data-stu-id="a5ae8-113">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="a5ae8-114">この値は、[DefineExportedType メソッド](../metadata/imetadataassemblyemit-defineexportedtype-method.md)に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="a5ae8-114">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="a5ae8-115">エクスポートされた型のトークンを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a5ae8-115">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5ae8-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="a5ae8-116">Return Value</span></span>  

 <span data-ttu-id="a5ae8-117">メソッドが成功した場合は、S_OK が返されます。</span><span class="sxs-lookup"><span data-stu-id="a5ae8-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5ae8-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="a5ae8-118">Requirements</span></span>  

 <span data-ttu-id="a5ae8-119">alink.h を必要とします</span><span class="sxs-lookup"><span data-stu-id="a5ae8-119">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5ae8-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5ae8-120">See also</span></span>

- [<span data-ttu-id="a5ae8-121">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5ae8-121">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="a5ae8-122">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5ae8-122">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="a5ae8-123">ALink API</span><span class="sxs-lookup"><span data-stu-id="a5ae8-123">ALink API</span></span>](index.md)
