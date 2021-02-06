---
description: '詳細情報: EmitAssemblyCustomAttribute メソッド'
title: EmitAssemblyCustomAttribute メソッド
ms.date: 03/30/2017
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssemblyCustomAttribute
helpviewer_keywords:
- EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type:
- apiref
ms.openlocfilehash: c91eb563c14b442a22db8f328287c10e5cc9a63c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638328"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="3b144-103">EmitAssemblyCustomAttribute メソッド</span><span class="sxs-lookup"><span data-stu-id="3b144-103">EmitAssemblyCustomAttribute Method</span></span>

<span data-ttu-id="3b144-104">を呼び出して、アセンブリレベルのカスタム属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="3b144-104">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b144-105">構文</span><span class="sxs-lookup"><span data-stu-id="3b144-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b144-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3b144-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="3b144-107">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="3b144-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="3b144-108">属性をなするファイル。</span><span class="sxs-lookup"><span data-stu-id="3b144-108">File that defiles the attribute.</span></span> <span data-ttu-id="3b144-109">がバインドされ `AssemblyID` ていない .netmodule を示していない場合は、NULL にすることができます。</span><span class="sxs-lookup"><span data-stu-id="3b144-109">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="3b144-110">カスタム属性の型。</span><span class="sxs-lookup"><span data-stu-id="3b144-110">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="3b144-111">カスタム値データ。</span><span class="sxs-lookup"><span data-stu-id="3b144-111">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="3b144-112">カスタム値データの長さ。</span><span class="sxs-lookup"><span data-stu-id="3b144-112">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="3b144-113">カスタム属性がアセンブリ署名に関連付けられている場合は TRUE。</span><span class="sxs-lookup"><span data-stu-id="3b144-113">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="3b144-114">複数の属性を出力する場合は TRUE。</span><span class="sxs-lookup"><span data-stu-id="3b144-114">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b144-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="3b144-115">Return Value</span></span>  

 <span data-ttu-id="3b144-116">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="3b144-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b144-117">要件</span><span class="sxs-lookup"><span data-stu-id="3b144-117">Requirements</span></span>  

 <span data-ttu-id="3b144-118">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="3b144-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b144-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b144-119">See also</span></span>

- [<span data-ttu-id="3b144-120">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3b144-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="3b144-121">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3b144-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="3b144-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="3b144-122">ALink API</span></span>](index.md)
