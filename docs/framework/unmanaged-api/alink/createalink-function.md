---
description: '詳細情報: CreateALink 関数'
title: CreateALink 関数
ms.date: 03/30/2017
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
ms.openlocfilehash: cf34ae8d38a8339f539c770df8f5dd14e4a3e4b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638367"
---
# <a name="createalink-function"></a><span data-ttu-id="a05ee-103">CreateALink 関数</span><span class="sxs-lookup"><span data-stu-id="a05ee-103">CreateALink Function</span></span>

<span data-ttu-id="a05ee-104">アセンブリリンカーのインスタンスを作成し、指定したインターフェイスへのポインターを設定します。</span><span class="sxs-lookup"><span data-stu-id="a05ee-104">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a05ee-105">構文</span><span class="sxs-lookup"><span data-stu-id="a05ee-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a05ee-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a05ee-106">Parameters</span></span>  
  
|<span data-ttu-id="a05ee-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a05ee-107">Parameter</span></span>|<span data-ttu-id="a05ee-108">説明</span><span class="sxs-lookup"><span data-stu-id="a05ee-108">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="a05ee-109">アセンブリリンカーインターフェイスの1つの物理名。</span><span class="sxs-lookup"><span data-stu-id="a05ee-109">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="a05ee-110">正常に完了した場所には、インターフェイスへのポインターが含まれてい `riid` ます。</span><span class="sxs-lookup"><span data-stu-id="a05ee-110">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a05ee-111">要件</span><span class="sxs-lookup"><span data-stu-id="a05ee-111">Requirements</span></span>  

 <span data-ttu-id="a05ee-112">**ライブラリ**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="a05ee-112">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a05ee-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="a05ee-113">See also</span></span>

- [<span data-ttu-id="a05ee-114">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="a05ee-114">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
