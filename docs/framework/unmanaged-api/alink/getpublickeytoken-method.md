---
description: '詳細情報: GetPublicKeyToken メソッド'
title: GetPublicKeyToken メソッド
ms.date: 03/30/2017
api_name:
- IALink2.GetPublicKeyToken
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetPublicKeyToken
helpviewer_keywords:
- GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type:
- apiref
ms.openlocfilehash: b864c1dc61c7498ccca6aa04ef29b57a30e1a9ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718422"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="61577-103">GetPublicKeyToken メソッド</span><span class="sxs-lookup"><span data-stu-id="61577-103">GetPublicKeyToken Method</span></span>

<span data-ttu-id="61577-104">指定されたキーキーまたはキーコンテナーの公開キートークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="61577-104">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61577-105">構文</span><span class="sxs-lookup"><span data-stu-id="61577-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="61577-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="61577-106">Parameters</span></span>  

 `pszKeyFile`  
 <span data-ttu-id="61577-107">キーのファイル名。</span><span class="sxs-lookup"><span data-stu-id="61577-107">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="61577-108">キーコンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="61577-108">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="61577-109">キートークンを格納するアドレス。</span><span class="sxs-lookup"><span data-stu-id="61577-109">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="61577-110">によって示されるバッファーのサイズ (バイト単位) を指定し `pvPublicKeyToken` ます。</span><span class="sxs-lookup"><span data-stu-id="61577-110">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="61577-111">戻り時には、実際に使用されたバイト数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="61577-111">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61577-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="61577-112">Return Value</span></span>  

 <span data-ttu-id="61577-113">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="61577-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61577-114">要件</span><span class="sxs-lookup"><span data-stu-id="61577-114">Requirements</span></span>  

 <span data-ttu-id="61577-115">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="61577-115">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61577-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="61577-116">See also</span></span>

- [<span data-ttu-id="61577-117">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="61577-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="61577-118">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="61577-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="61577-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="61577-119">ALink API</span></span>](index.md)
