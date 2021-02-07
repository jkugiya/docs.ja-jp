---
description: '詳細情報: SetAssemblyFile2 メソッド'
title: SetAssemblyFile2 メソッド
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
ms.openlocfilehash: 890646b718c211b476d013daf021f8889198c1ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662404"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="6aa1f-103">SetAssemblyFile2 メソッド</span><span class="sxs-lookup"><span data-stu-id="6aa1f-103">SetAssemblyFile2 Method</span></span>

<span data-ttu-id="6aa1f-104">新しいアセンブリのオプションとオプションの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="6aa1f-104">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="6aa1f-105">バインドされていないモジュールを生成する場合は、このメソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="6aa1f-105">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aa1f-106">構文</span><span class="sxs-lookup"><span data-stu-id="6aa1f-106">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6aa1f-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6aa1f-107">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="6aa1f-108">マニフェストファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="6aa1f-108">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="6aa1f-109">このファイルの[IMetaDataEmit2 インターフェイス](../metadata/imetadataemit2-interface.md)インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="6aa1f-109">[IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="6aa1f-110">[Assemblyflags 列挙体](../metadata/assemblyflags-enumeration.md)によって表されるオプション。</span><span class="sxs-lookup"><span data-stu-id="6aa1f-110">Options represented by [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="6aa1f-111">構築されるアセンブリの一意の ID を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="6aa1f-111">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6aa1f-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="6aa1f-112">Return Value</span></span>  

 <span data-ttu-id="6aa1f-113">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="6aa1f-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6aa1f-114">要件</span><span class="sxs-lookup"><span data-stu-id="6aa1f-114">Requirements</span></span>  

 <span data-ttu-id="6aa1f-115">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="6aa1f-115">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aa1f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="6aa1f-116">See also</span></span>

- [<span data-ttu-id="6aa1f-117">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6aa1f-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="6aa1f-118">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6aa1f-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="6aa1f-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="6aa1f-119">ALink API</span></span>](index.md)
