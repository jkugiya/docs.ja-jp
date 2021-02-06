---
description: '詳細情報: EmitAssembly メソッド'
title: EmitAssembly メソッド
ms.date: 03/30/2017
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
ms.openlocfilehash: aada17d8df6435c5edfe6beb5db5ee13f887f253
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638341"
---
# <a name="emitassembly-method"></a><span data-ttu-id="55da3-103">EmitAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="55da3-103">EmitAssembly Method</span></span>

<span data-ttu-id="55da3-104">アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="55da3-104">Creates the assembly.</span></span> <span data-ttu-id="55da3-105">アセンブリファイルを除く他のすべてのファイルが閉じられた後に、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="55da3-105">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="55da3-106">バインドされていないモジュールを生成する場合は、このメソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="55da3-106">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55da3-107">構文</span><span class="sxs-lookup"><span data-stu-id="55da3-107">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="55da3-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="55da3-108">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="55da3-109">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="55da3-109">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55da3-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="55da3-110">Return Value</span></span>  

 <span data-ttu-id="55da3-111">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="55da3-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55da3-112">要件</span><span class="sxs-lookup"><span data-stu-id="55da3-112">Requirements</span></span>  

 <span data-ttu-id="55da3-113">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="55da3-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55da3-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="55da3-114">See also</span></span>

- [<span data-ttu-id="55da3-115">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="55da3-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="55da3-116">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="55da3-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="55da3-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="55da3-117">ALink API</span></span>](index.md)
