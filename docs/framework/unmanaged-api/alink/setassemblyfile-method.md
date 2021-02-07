---
description: '詳細情報: SetAssemblyFile メソッド'
title: SetAssemblyFile メソッド
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
ms.openlocfilehash: 943e0600b9781aeaf45cc26e39bd8a8b33a783c2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662495"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="73491-103">SetAssemblyFile メソッド</span><span class="sxs-lookup"><span data-stu-id="73491-103">SetAssemblyFile Method</span></span>

<span data-ttu-id="73491-104">ビルドされるアセンブリの名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="73491-104">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="73491-105">非バインドモジュールの生成時には使用しません。</span><span class="sxs-lookup"><span data-stu-id="73491-105">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73491-106">構文</span><span class="sxs-lookup"><span data-stu-id="73491-106">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="73491-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="73491-107">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="73491-108">マニフェストファイルの完全修飾名。</span><span class="sxs-lookup"><span data-stu-id="73491-108">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="73491-109">[IMetaDataEmit インターフェイス](../metadata/imetadataemit-interface.md)インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="73491-109">Pointer to [IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="73491-110">[Assemblyflags 列挙型](../metadata/assemblyflags-enumeration.md)で定義されているフラグ。</span><span class="sxs-lookup"><span data-stu-id="73491-110">Flags as defined in [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="73491-111">結果として得られるアセンブリの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="73491-111">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73491-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="73491-112">Return Value</span></span>  

 <span data-ttu-id="73491-113">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="73491-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73491-114">要件</span><span class="sxs-lookup"><span data-stu-id="73491-114">Requirements</span></span>  

 <span data-ttu-id="73491-115">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="73491-115">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73491-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="73491-116">See also</span></span>

- [<span data-ttu-id="73491-117">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="73491-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="73491-118">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="73491-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="73491-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="73491-119">ALink API</span></span>](index.md)
