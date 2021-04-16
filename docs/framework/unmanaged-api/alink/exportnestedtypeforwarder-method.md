---
description: '詳細情報: ExportNestedTypeForwarder メソッド'
title: ExportNestedTypeForwarder メソッド
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
ms.openlocfilehash: fd791e3fea76338f191fcf924d56720d257d2e8b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638107"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="169a6-103">ExportNestedTypeForwarder メソッド</span><span class="sxs-lookup"><span data-stu-id="169a6-103">ExportNestedTypeForwarder Method</span></span>

<span data-ttu-id="169a6-104">指定されたアセンブリの型テーブルに、入れ子にされた型の型フォワーダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="169a6-104">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="169a6-105">構文</span><span class="sxs-lookup"><span data-stu-id="169a6-105">Syntax</span></span>  
  
```cpp  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="169a6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="169a6-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="169a6-107">エクスポート元のアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="169a6-107">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="169a6-108">型を定義するファイルのファイル トークンまたはアセンブリ ID。</span><span class="sxs-lookup"><span data-stu-id="169a6-108">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="169a6-109">型のトークン。</span><span class="sxs-lookup"><span data-stu-id="169a6-109">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="169a6-110">親の型のトークン。</span><span class="sxs-lookup"><span data-stu-id="169a6-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="169a6-111">エクスポートする完全修飾型名。</span><span class="sxs-lookup"><span data-stu-id="169a6-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="169a6-112">`tdPublic` や `tdNested` などの `ComType` フラグ。</span><span class="sxs-lookup"><span data-stu-id="169a6-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="169a6-113">エクスポート型のトークンを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="169a6-113">Receives token of export type.</span></span> <span data-ttu-id="169a6-114">これは、入れ子にされた型を出力する場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="169a6-114">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="169a6-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="169a6-115">Return Value</span></span>  

 <span data-ttu-id="169a6-116">メソッドが成功した場合は、S_OK が返されます。</span><span class="sxs-lookup"><span data-stu-id="169a6-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="169a6-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="169a6-117">Requirements</span></span>  

 <span data-ttu-id="169a6-118">alink.h を必要とします</span><span class="sxs-lookup"><span data-stu-id="169a6-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="169a6-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="169a6-119">See also</span></span>

- [<span data-ttu-id="169a6-120">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="169a6-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="169a6-121">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="169a6-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="169a6-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="169a6-122">ALink API</span></span>](index.md)
