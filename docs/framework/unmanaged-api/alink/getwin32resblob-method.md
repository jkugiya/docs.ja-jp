---
description: '詳細情報: GetWin32ResBlob メソッド'
title: GetWin32ResBlob メソッド
ms.date: 03/30/2017
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
ms.openlocfilehash: e1140b14bfba56dfac03c443a537d6d2188575b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718266"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="86033-103">GetWin32ResBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="86033-103">GetWin32ResBlob Method</span></span>

<span data-ttu-id="86033-104">Win32 リソース blob を取得します。</span><span class="sxs-lookup"><span data-stu-id="86033-104">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="86033-105">アセンブリオプションを設定した後に、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="86033-105">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86033-106">構文</span><span class="sxs-lookup"><span data-stu-id="86033-106">Syntax</span></span>  
  
```cpp  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="86033-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="86033-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="86033-108">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="86033-108">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="86033-109">Win32 バージョンリソースの構築時に使用されるファイル名を取得するために使用されるファイルトークン</span><span class="sxs-lookup"><span data-stu-id="86033-109">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="86033-110">ファイルが DLL の場合は TRUE、EXE の場合は false。</span><span class="sxs-lookup"><span data-stu-id="86033-110">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="86033-111">リソース blob に挿入するオプションアイコン。</span><span class="sxs-lookup"><span data-stu-id="86033-111">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="86033-112">リソース blob を受信します。</span><span class="sxs-lookup"><span data-stu-id="86033-112">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="86033-113">Blob のサイズを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="86033-113">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86033-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="86033-114">Return Value</span></span>  

 <span data-ttu-id="86033-115">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="86033-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86033-116">要件</span><span class="sxs-lookup"><span data-stu-id="86033-116">Requirements</span></span>  

 <span data-ttu-id="86033-117">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="86033-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86033-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="86033-118">See also</span></span>

- [<span data-ttu-id="86033-119">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="86033-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="86033-120">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="86033-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="86033-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="86033-121">ALink API</span></span>](index.md)
