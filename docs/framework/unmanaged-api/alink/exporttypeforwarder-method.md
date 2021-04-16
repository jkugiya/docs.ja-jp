---
description: '詳細情報: ExportTypeForwarder メソッド'
title: ExportTypeForwarder メソッド
ms.date: 03/30/2017
api_name:
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
ms.openlocfilehash: 59fb74c83f6d30dda87d908353795fb218190022
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637990"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="387e2-103">ExportTypeForwarder メソッド</span><span class="sxs-lookup"><span data-stu-id="387e2-103">ExportTypeForwarder Method</span></span>

<span data-ttu-id="387e2-104">指定されたアセンブリの型テーブルに型フォワーダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="387e2-104">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="387e2-105">構文</span><span class="sxs-lookup"><span data-stu-id="387e2-105">Syntax</span></span>  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="387e2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="387e2-106">Parameters</span></span>  

 `tkAssemblyRef`  
 <span data-ttu-id="387e2-107">型フォワーダーが参照するアセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="387e2-107">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="387e2-108">エクスポートする完全修飾型名。</span><span class="sxs-lookup"><span data-stu-id="387e2-108">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="387e2-109">`tdPublic` や `tdNested` などの `ComType` フラグ。</span><span class="sxs-lookup"><span data-stu-id="387e2-109">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="387e2-110">この値は、[DefineExportedType メソッド](../metadata/imetadataassemblyemit-defineexportedtype-method.md)に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="387e2-110">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="387e2-111">エクスポートされた型のトークンを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="387e2-111">Receives the token of the exported type.</span></span> <span data-ttu-id="387e2-112">これは、入れ子にされた型を出力する場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="387e2-112">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="387e2-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="387e2-113">Return Value</span></span>  

 <span data-ttu-id="387e2-114">メソッドが成功した場合は、S_OK が返されます。</span><span class="sxs-lookup"><span data-stu-id="387e2-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="387e2-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="387e2-115">Requirements</span></span>  

 <span data-ttu-id="387e2-116">alink.h を必要とします</span><span class="sxs-lookup"><span data-stu-id="387e2-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="387e2-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="387e2-117">See also</span></span>

- [<span data-ttu-id="387e2-118">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="387e2-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="387e2-119">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="387e2-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="387e2-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="387e2-120">ALink API</span></span>](index.md)
