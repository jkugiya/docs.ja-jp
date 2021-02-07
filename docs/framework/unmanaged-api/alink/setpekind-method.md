---
description: '詳細情報: SetPEKind メソッド'
title: SetPEKind メソッド
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
ms.openlocfilehash: 4154e9e80b7f88b6951c9aa8da5fc23d340c96dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662300"
---
# <a name="setpekind-method"></a><span data-ttu-id="d9b1c-103">SetPEKind メソッド</span><span class="sxs-lookup"><span data-stu-id="d9b1c-103">SetPEKind Method</span></span>

<span data-ttu-id="d9b1c-104">ポータブル実行可能ファイルの種類 (マシン固有またはコンピューターに依存しない) を決定します。</span><span class="sxs-lookup"><span data-stu-id="d9b1c-104">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9b1c-105">構文</span><span class="sxs-lookup"><span data-stu-id="d9b1c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="d9b1c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d9b1c-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="d9b1c-107">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="d9b1c-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d9b1c-108">PE の種類を設定するファイルのトークン。</span><span class="sxs-lookup"><span data-stu-id="d9b1c-108">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="d9b1c-109">がバインドされ `AssemblyID` ていない .netmodule を示していない場合は、NULL にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d9b1c-109">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="d9b1c-110">[Corpekind 列挙体](../metadata/corpekind-enumeration.md)によって示される PE の種類。</span><span class="sxs-lookup"><span data-stu-id="d9b1c-110">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="d9b1c-111">NT ヘッダーに示されている、対象コンピューターのアーキテクチャ。</span><span class="sxs-lookup"><span data-stu-id="d9b1c-111">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9b1c-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="d9b1c-112">Return Value</span></span>  

 <span data-ttu-id="d9b1c-113">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="d9b1c-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9b1c-114">要件</span><span class="sxs-lookup"><span data-stu-id="d9b1c-114">Requirements</span></span>  

 <span data-ttu-id="d9b1c-115">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="d9b1c-115">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9b1c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9b1c-116">See also</span></span>

- [<span data-ttu-id="d9b1c-117">GetPEKind メソッド</span><span class="sxs-lookup"><span data-stu-id="d9b1c-117">GetPEKind Method</span></span>](../metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="d9b1c-118">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d9b1c-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d9b1c-119">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d9b1c-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d9b1c-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="d9b1c-120">ALink API</span></span>](index.md)
