---
description: '詳細情報: IDebugAutoAttach:: AutoAttach メソッド'
title: IDebugAutoAttach::AutoAttach メソッド
ms.date: 03/30/2017
api_name:
- IDebugAutoAttach.AutoAttach
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type:
- apiref
ms.openlocfilehash: 8abd35b1d94fc074d4dafe424c52c274b1de1541
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800358"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="e054a-103">IDebugAutoAttach::AutoAttach メソッド</span><span class="sxs-lookup"><span data-stu-id="e054a-103">IDebugAutoAttach::AutoAttach Method</span></span>

<span data-ttu-id="e054a-104">サーバーによって呼び出されたデバッガーの自動アタッチを実行します。</span><span class="sxs-lookup"><span data-stu-id="e054a-104">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e054a-105">構文</span><span class="sxs-lookup"><span data-stu-id="e054a-105">Syntax</span></span>  
  
```cpp  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e054a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e054a-106">Parameters</span></span>  

 `guidPort`  
 <span data-ttu-id="e054a-107">から常にに設定 `GUID_NULL` します。</span><span class="sxs-lookup"><span data-stu-id="e054a-107">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="e054a-108">からプロセス ID。通常は関数を使用して取得さ `GetCurrentProcessId` れます。</span><span class="sxs-lookup"><span data-stu-id="e054a-108">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="e054a-109">からプログラムの種類: `AUTOATTACH_PROGRAM_WIN32` 、 `AUTOATTACH_PROGRAM_COMPLUS` 、または `AUTOATTACH_PROGRAM_UNKNOWN` 。</span><span class="sxs-lookup"><span data-stu-id="e054a-109">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="e054a-110">からプログラム ID。</span><span class="sxs-lookup"><span data-stu-id="e054a-110">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="e054a-111">からデバッグ動詞によって渡された文字列。</span><span class="sxs-lookup"><span data-stu-id="e054a-111">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e054a-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="e054a-112">Return Value</span></span>  

 <span data-ttu-id="e054a-113">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="e054a-113">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e054a-114">要件</span><span class="sxs-lookup"><span data-stu-id="e054a-114">Requirements</span></span>  

 <span data-ttu-id="e054a-115">**ヘッダー:** DbgAutoAttach .h</span><span class="sxs-lookup"><span data-stu-id="e054a-115">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e054a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e054a-116">See also</span></span>

- [<span data-ttu-id="e054a-117">IDebugAutoAttach インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e054a-117">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)
