---
description: '詳細情報: GetALinkMessageDll 関数'
title: GetALinkMessageDll 関数
ms.date: 03/30/2017
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
ms.openlocfilehash: 67a294d1f21f50cee938ddeb14d1f30b4ccf911b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637873"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="9899e-103">GetALinkMessageDll 関数</span><span class="sxs-lookup"><span data-stu-id="9899e-103">GetALinkMessageDll Function</span></span>

<span data-ttu-id="9899e-104">メッセージ DLL を検索して読み込みます。</span><span class="sxs-lookup"><span data-stu-id="9899e-104">Finds and loads the message DLL.</span></span> <span data-ttu-id="9899e-105">メッセージ DLL が見つからないか、または読み込むことができなかった場合は0を返します。</span><span class="sxs-lookup"><span data-stu-id="9899e-105">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="9899e-106">メッセージ DLL は、名前が言語 ID または現在のディレクトリ内のサブディレクトリにある必要があります。</span><span class="sxs-lookup"><span data-stu-id="9899e-106">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9899e-107">構文</span><span class="sxs-lookup"><span data-stu-id="9899e-107">Syntax</span></span>  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="9899e-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="9899e-108">Requirements</span></span>  

 <span data-ttu-id="9899e-109">**ヘッダー:** alink</span><span class="sxs-lookup"><span data-stu-id="9899e-109">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="9899e-110">**ライブラリ**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="9899e-110">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9899e-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="9899e-111">See also</span></span>

- [<span data-ttu-id="9899e-112">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="9899e-112">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
