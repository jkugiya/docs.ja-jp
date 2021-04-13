---
title: BlessIWbemServices 関数 (アンマネージド API リファレンス)
description: BlessIWbemServices 関数では、ユーザー資格情報によって IWbemServices クラスへのアクセスが許可されるかどうかが示されます。
ms.date: 11/06/2017
api_name:
- BlessIWbemServices
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServices
helpviewer_keywords:
- BlessIWbemServices function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 43ef617ee754c9dcd661b31abba6b17434563c22
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708154"
---
# <a name="blessiwbemservices-function"></a><span data-ttu-id="b40d1-103">BlessIWbemServices 関数</span><span class="sxs-lookup"><span data-stu-id="b40d1-103">BlessIWbemServices function</span></span>

<span data-ttu-id="b40d1-104">指定した [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) クラスへのアクセスがユーザーの資格情報によって許可されるかどうかを示されます。</span><span class="sxs-lookup"><span data-stu-id="b40d1-104">Indicates whether the user credentials permit access to the specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) class.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b40d1-105">構文</span><span class="sxs-lookup"><span data-stu-id="b40d1-105">Syntax</span></span>  
  
```cpp
HRESULT BlessIWbemServices (
   [in] IWbemServices* pIWbemServices,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a><span data-ttu-id="b40d1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b40d1-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="b40d1-107">[in] アクセス許可が必要な [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b40d1-107">[in] A pointer to the [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object for which permissions are required.</span></span>

`strUser`\
<span data-ttu-id="b40d1-108">[in] ユーザー名。</span><span class="sxs-lookup"><span data-stu-id="b40d1-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="b40d1-109">[in] `strUser` に関連付けられているパスワード。</span><span class="sxs-lookup"><span data-stu-id="b40d1-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="b40d1-110">[in] ユーザーのドメイン名。</span><span class="sxs-lookup"><span data-stu-id="b40d1-110">[in] The domain name of the user.</span></span> <span data-ttu-id="b40d1-111">詳細については、「[ConnectServerWmi](connectserverwmi.md) 関数」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b40d1-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="b40d1-112">[in] 偽装レベル。</span><span class="sxs-lookup"><span data-stu-id="b40d1-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="b40d1-113">[in] 承認レベル。</span><span class="sxs-lookup"><span data-stu-id="b40d1-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="b40d1-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="b40d1-114">Return value</span></span>

<span data-ttu-id="b40d1-115">この関数によって返される次の値は、*WinError.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="b40d1-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b40d1-116">定数</span><span class="sxs-lookup"><span data-stu-id="b40d1-116">Constant</span></span>  |<span data-ttu-id="b40d1-117">[値]</span><span class="sxs-lookup"><span data-stu-id="b40d1-117">Value</span></span>  |<span data-ttu-id="b40d1-118">説明</span><span class="sxs-lookup"><span data-stu-id="b40d1-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="b40d1-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="b40d1-119">0x80070057</span></span> | <span data-ttu-id="b40d1-120">1 つ以上の引数が無効です。</span><span class="sxs-lookup"><span data-stu-id="b40d1-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="b40d1-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="b40d1-121">0x80004003</span></span> | <span data-ttu-id="b40d1-122">`pIWbemServices` が `null`です。</span><span class="sxs-lookup"><span data-stu-id="b40d1-122">`pIWbemServices` is `null`.</span></span> |
| `E_FAIL` | <span data-ttu-id="b40d1-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="b40d1-123">0x80000008</span></span> | <span data-ttu-id="b40d1-124">特定できないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="b40d1-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="b40d1-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="b40d1-125">0x80000002</span></span> | <span data-ttu-id="b40d1-126">操作を実行するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="b40d1-126">Insufficient memory is available to perform the operation.</span></span> |
| `S_OK` | <span data-ttu-id="b40d1-127">0</span><span class="sxs-lookup"><span data-stu-id="b40d1-127">0</span></span> | <span data-ttu-id="b40d1-128">関数呼び出しは成功しました。</span><span class="sxs-lookup"><span data-stu-id="b40d1-128">The function call was successful.</span></span> |

## <a name="requirements"></a><span data-ttu-id="b40d1-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="b40d1-129">Requirements</span></span>  

 <span data-ttu-id="b40d1-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b40d1-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b40d1-131">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b40d1-131">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b40d1-132">**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b40d1-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b40d1-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="b40d1-133">See also</span></span>

- [<span data-ttu-id="b40d1-134">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="b40d1-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
