---
description: '詳細情報: SetManifestFile メソッド'
title: SetManifestFile メソッド
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
ms.openlocfilehash: fe91c7f2b4e6f58a0a740de84e055ead49adb77d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662326"
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="29cec-103">SetManifestFile メソッド</span><span class="sxs-lookup"><span data-stu-id="29cec-103">SetManifestFile Method</span></span>

<span data-ttu-id="29cec-104">リンカーがアセンブリを作成するときに使用するマニフェストファイルを指定またはリセットできます。</span><span class="sxs-lookup"><span data-stu-id="29cec-104">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29cec-105">構文</span><span class="sxs-lookup"><span data-stu-id="29cec-105">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="29cec-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="29cec-106">Parameters</span></span>  

 `pszFile`  
  
 <span data-ttu-id="29cec-107">コンテンツが Win32 リソース blob に格納されるマニフェストファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="29cec-107">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29cec-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="29cec-108">Return Value</span></span>  

 <span data-ttu-id="29cec-109">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="29cec-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29cec-110">解説</span><span class="sxs-lookup"><span data-stu-id="29cec-110">Remarks</span></span>  

 <span data-ttu-id="29cec-111">Win32ResBlob を要求する前に、これを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="29cec-111">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="29cec-112">パラメーターの値 `pszFile` は、コンテンツが読み取られ、ID が RT_MANIFEST の Win32 リソースに配置されるマニフェストファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="29cec-112">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="29cec-113">NULL のパラメーターを使用して呼び出されると、以前に読み取られたマニフェストはクリアされます。</span><span class="sxs-lookup"><span data-stu-id="29cec-113">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="29cec-114">これにより、1つのリンカーの状態を初期化時間にリセットできます。</span><span class="sxs-lookup"><span data-stu-id="29cec-114">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29cec-115">要件</span><span class="sxs-lookup"><span data-stu-id="29cec-115">Requirements</span></span>  

 <span data-ttu-id="29cec-116">ALink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="29cec-116">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29cec-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="29cec-117">See also</span></span>

- [<span data-ttu-id="29cec-118">IALink3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="29cec-118">IALink3 Interface</span></span>](ialink3-interface.md)
- [<span data-ttu-id="29cec-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="29cec-119">ALink API</span></span>](index.md)
- [<span data-ttu-id="29cec-120">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="29cec-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="29cec-121">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="29cec-121">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
