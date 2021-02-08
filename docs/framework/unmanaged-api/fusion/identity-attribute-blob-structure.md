---
description: '詳細情報: IDENTITY_ATTRIBUTE_BLOB 構造'
title: IDENTITY_ATTRIBUTE_BLOB 構造体
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IDENTITY_ATTRIBUTE_BLOB
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE_BLOB
helpviewer_keywords:
- IDENTITY_ATTRIBUTE_BLOB structure [.NET Framework fusion]
ms.assetid: af14ae5f-d226-47dd-ba90-8fc6e6605d4d
topic_type:
- apiref
ms.openlocfilehash: e89294397287cb5751196b563b1576bb4f1c0f12
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800189"
---
# <a name="identity_attribute_blob-structure"></a><span data-ttu-id="70a22-103">IDENTITY_ATTRIBUTE_BLOB 構造体</span><span class="sxs-lookup"><span data-stu-id="70a22-103">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>

<span data-ttu-id="70a22-104">アセンブリ内の1つの属性に関する情報を格納し、3つので構成され `DWORD` ます。</span><span class="sxs-lookup"><span data-stu-id="70a22-104">Contains information about a single attribute in an assembly, and consists of three `DWORD`s.</span></span> <span data-ttu-id="70a22-105">各 `DWORD` は、 `CurrentIntoBuffer` [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) インターフェイスのメソッドによって生成される文字バッファーへのオフセットです。</span><span class="sxs-lookup"><span data-stu-id="70a22-105">Each `DWORD` is an offset into a character buffer produced by the `CurrentIntoBuffer` method of the [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) interface</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70a22-106">構文</span><span class="sxs-lookup"><span data-stu-id="70a22-106">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE_BLOB {  
    DWORD  ofsNamespace;  
    DWORD  ofsName;  
    DWORD  ofsValue;  
}   IDENTITY_ATTRIBUTE_BLOB;  
```  
  
## <a name="members"></a><span data-ttu-id="70a22-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="70a22-107">Members</span></span>  
  
|<span data-ttu-id="70a22-108">メンバー</span><span class="sxs-lookup"><span data-stu-id="70a22-108">Member</span></span>|<span data-ttu-id="70a22-109">説明</span><span class="sxs-lookup"><span data-stu-id="70a22-109">Description</span></span>|  
|------------|-----------------|  
|`ofsNamespace`|<span data-ttu-id="70a22-110">文字バッファー内の最初のオフセット。</span><span class="sxs-lookup"><span data-stu-id="70a22-110">The first offset into the character buffer.</span></span> <span data-ttu-id="70a22-111">このオフセットの後には、属性の名前空間は含まれませんが、一連の null 文字が続きます。</span><span class="sxs-lookup"><span data-stu-id="70a22-111">This offset is not followed by the attribute's namespace, but by a series of null characters.</span></span> <span data-ttu-id="70a22-112">したがって、これは使用されません。</span><span class="sxs-lookup"><span data-stu-id="70a22-112">Therefore, it is not used.</span></span>|  
|`ofsName`|<span data-ttu-id="70a22-113">文字バッファー内の2番目のオフセット。</span><span class="sxs-lookup"><span data-stu-id="70a22-113">The second offset into the character buffer.</span></span> <span data-ttu-id="70a22-114">この場所は、属性の名前の先頭を示します。</span><span class="sxs-lookup"><span data-stu-id="70a22-114">This location marks the start of the attribute's name.</span></span>|  
|`ofsValue`|<span data-ttu-id="70a22-115">文字バッファーへの3番目のオフセット。</span><span class="sxs-lookup"><span data-stu-id="70a22-115">The third offset into the character buffer.</span></span> <span data-ttu-id="70a22-116">この場所は、属性の値の開始を示します。</span><span class="sxs-lookup"><span data-stu-id="70a22-116">This location marks the start of the attribute's value.</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="70a22-117">サンプル</span><span class="sxs-lookup"><span data-stu-id="70a22-117">Sample</span></span>  

 <span data-ttu-id="70a22-118">次の例は、最終的に構造が設定される基本的な手順を示してい `IDENTITY_ATTRIBUTE_BLOB` ます。</span><span class="sxs-lookup"><span data-stu-id="70a22-118">The following example illustrates several basic steps, which eventually result in a populated `IDENTITY_ATTRIBUTE_BLOB` structure:</span></span>  
  
1. <span data-ttu-id="70a22-119">アセンブリの [IReferenceIdentity](ireferenceidentity-interface.md) を取得します。</span><span class="sxs-lookup"><span data-stu-id="70a22-119">Obtain an [IReferenceIdentity](ireferenceidentity-interface.md) for the assembly.</span></span>  
  
2. <span data-ttu-id="70a22-120">`IReferenceIdentity::EnumAttributes`メソッドを呼び出し、 [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md)を取得します。</span><span class="sxs-lookup"><span data-stu-id="70a22-120">Call the `IReferenceIdentity::EnumAttributes` method, and obtain an [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md).</span></span>  
  
3. <span data-ttu-id="70a22-121">文字バッファーを作成し、それを構造体としてキャストし `IDENTITY_ATTRIBUTE_BLOB` ます。</span><span class="sxs-lookup"><span data-stu-id="70a22-121">Create a character buffer, and cast it as an `IDENTITY_ATTRIBUTE_BLOB` structure.</span></span>  
  
4. <span data-ttu-id="70a22-122">`CurrentIntoBuffer`インターフェイスのメソッドを呼び出し `IEnumIDENTITY_ATTRIBUTE` ます。</span><span class="sxs-lookup"><span data-stu-id="70a22-122">Call the `CurrentIntoBuffer` method of the `IEnumIDENTITY_ATTRIBUTE` interface.</span></span> <span data-ttu-id="70a22-123">このメソッドは、属性 `Namespace` 、 `Name` 、およびを `Value` 文字バッファーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="70a22-123">This method copies the attributes `Namespace`, `Name`, and `Value` into the character buffer.</span></span> <span data-ttu-id="70a22-124">これらの文字列への3つのオフセットは、構造体で使用できるようになり `IDENTITY_ATTRIBUTE_BLOB` ます。</span><span class="sxs-lookup"><span data-stu-id="70a22-124">The three offsets to those strings will become available in the `IDENTITY_ATTRIBUTE_BLOB` structure.</span></span>  
  
```cpp  
// EnumAssemblyAttributes.cpp : main project file.  
  
#include "stdafx.h"  
  
#include "fusion.h"  
#include "windows.h"  
#include "stdio.h"  
#include "mscoree.h"  
#include "isolation.h"  
  
typedef HRESULT (__stdcall *PFNGETREF)(LPCWSTR pwzFile, REFIID riid, IUnknown **ppUnk);  
typedef HRESULT (__stdcall *PFNGETAUTH)(IIdentityAuthority **ppIIdentityAuthority);  
  
PFNGETREF                   g_pfnGetAssemblyIdentityFromFile = NULL;  
PFNGETAUTH                  g_pfnGetIdentityAuthority = NULL;  
IUnknown                    *g_pUnk = NULL;  
  
bool Init()  
{  
    HRESULT     hr = S_OK;  
    DWORD       dwSize = 0;  
    bool        bRC = false;  
  
    hr = CorBindToRuntimeEx(NULL, L"wks", 0, CLSID_CorRuntimeHost,  
                           IID_ICorRuntimeHost, (void **)&g_pUnk);  
    if(FAILED(hr)) {  
        printf("Error: Failed to initialize CLR runtime! hr = 0x%0x\n",  
                hr);  
        goto Exit;  
    }  
  
    if (SUCCEEDED(hr)) {  
        hr = GetRealProcAddress("GetAssemblyIdentityFromFile",  
                         (VOID **)&g_pfnGetAssemblyIdentityFromFile);  
    }  
  
    if (SUCCEEDED(hr)) {  
        hr = GetRealProcAddress("GetIdentityAuthority",  
                                (VOID **)&g_pfnGetIdentityAuthority);  
    }  
  
    if (!g_pfnGetAssemblyIdentityFromFile ||
        !g_pfnGetIdentityAuthority)  
    {  
        printf("Error: Cannot get required APIs from fusion.dll!\n");  
        goto Exit;  
    }  
  
    bRC = true;  
  
Exit:  
    return bRC;  
}  
  
void Shutdown()  
{  
    if(g_pUnk) {  
        g_pUnk->Release();  
        g_pUnk = NULL;  
    }  
}  
  
void Usage()  
{  
    printf("EnumAssemblyAttributes: A tool to enumerate the identity
            attributes of a given assembly.\n\n");  
    printf("Usage: EnumAssemblyAttributes AssemblyFilePath\n");  
    printf("\n");  
}  
  
int _cdecl wmain(int argc, LPCWSTR argv[])  
{  
    int     iResult = 1;  
    IUnknown                    *pUnk  = NULL;  
    IReferenceIdentity          *pRef  = NULL;  
    HRESULT                     hr     = S_OK;
    IEnumIDENTITY_ATTRIBUTE     *pEnum = NULL;  
    BYTE                        abData[1024];  
    DWORD                       cbAvailable;  
    DWORD                       cbUsed;  
    IDENTITY_ATTRIBUTE_BLOB     *pBlob;  
  
    if(argc != 2) {  
        Usage();  
        goto Exit;  
    }  
  
    if(!Init()) {  
        printf("Failure initializing EnumIdAttr.\n");  
        goto Exit;  
    }  
  
    hr = g_pfnGetAssemblyIdentityFromFile(argv[1],
                            __uuidof(IReferenceIdentity), &pUnk);  
  
    if (FAILED(hr)) {  
        printf("GetAssemblyIdentityFromFile failed with hr = 0x%x",
                hr);  
        goto Exit;  
    }  
  
    hr = pUnk->QueryInterface(__uuidof(IReferenceIdentity),
                              (void**)&pRef);  
    if (FAILED(hr)) {  
        goto Exit;  
    }  
  
    hr = pRef->EnumAttributes(&pEnum);  
    if (FAILED(hr)) {  
        printf("IReferenceIdentity::EnumAttributes failed with hr =
                0x%x", hr);  
        goto Exit;  
    }  
  
    pBlob = (IDENTITY_ATTRIBUTE_BLOB *)(abData);  
    while (1) {  
        cbAvailable = sizeof(abData);  
        hr = pEnum->CurrentIntoBuffer(cbAvailable, abData, &cbUsed);  
        if (FAILED(hr)) {  
            printf("IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer failed
                    with hr = 0x%x", hr);  
            goto Exit;  
        }  
  
        if (! cbUsed) {  
            break;  
        }  
  
        LPWSTR pwzNameSpace = (LPWSTR)(abData + pBlob->ofsNamespace);  
        LPWSTR pwzName      = (LPWSTR)(abData + pBlob->ofsName);  
        LPWSTR pwzValue     = (LPWSTR)(abData + pBlob->ofsValue);  
        printf("%ws: %ws = %ws\n", pwzNameSpace, pwzName, pwzValue);  
  
        hr = pEnum->Skip(1);  
        if (FAILED(hr)) {  
            printf("IEnumIDENTITY_ATTRIBUTE::Skip failed with hr =
                    0x%x", hr);  
            goto Exit;  
        }  
    }  
  
    iResult = 0;  
  
Exit:  
  
    Shutdown();  
  
    if (pUnk) {  
        pUnk->Release();  
    }  
  
    if (pRef) {  
        pRef->Release();  
    }  
  
    if (pEnum) {  
        pEnum->Release();  
    }  
  
    return iResult;  
}  
```  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="70a22-125">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="70a22-125">To run the sample</span></span>  

 <span data-ttu-id="70a22-126">C: \\> EnumAssemblyAttributes.exe C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\System.dll</span><span class="sxs-lookup"><span data-stu-id="70a22-126">C:\\> EnumAssemblyAttributes.exe C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\System.dll</span></span>  
  
### <a name="sample-output"></a><span data-ttu-id="70a22-127">サンプル出力</span><span class="sxs-lookup"><span data-stu-id="70a22-127">Sample output</span></span>  

 <span data-ttu-id="70a22-128">Culture = ニュートラル</span><span class="sxs-lookup"><span data-stu-id="70a22-128">Culture = neutral</span></span>  
  
 <span data-ttu-id="70a22-129">名前 = System</span><span class="sxs-lookup"><span data-stu-id="70a22-129">name = System</span></span>  
  
 <span data-ttu-id="70a22-130">processorArchitecture = MSIL</span><span class="sxs-lookup"><span data-stu-id="70a22-130">processorArchitecture = MSIL</span></span>  
  
 <span data-ttu-id="70a22-131">PublicKeyToken = b77a5c561934e089</span><span class="sxs-lookup"><span data-stu-id="70a22-131">PublicKeyToken = b77a5c561934e089</span></span>  
  
 <span data-ttu-id="70a22-132">Version = 2.0.0.0</span><span class="sxs-lookup"><span data-stu-id="70a22-132">Version = 2.0.0.0</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70a22-133">要件</span><span class="sxs-lookup"><span data-stu-id="70a22-133">Requirements</span></span>  

 <span data-ttu-id="70a22-134">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70a22-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70a22-135">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="70a22-135">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="70a22-136">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70a22-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70a22-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="70a22-137">See also</span></span>

- [<span data-ttu-id="70a22-138">IReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="70a22-138">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
- [<span data-ttu-id="70a22-139">IEnumIDENTITY_ATTRIBUTE インターフェイス</span><span class="sxs-lookup"><span data-stu-id="70a22-139">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)
- [<span data-ttu-id="70a22-140">IDENTITY_ATTRIBUTE 構造体</span><span class="sxs-lookup"><span data-stu-id="70a22-140">IDENTITY_ATTRIBUTE Structure</span></span>](identity-attribute-structure.md)
- [<span data-ttu-id="70a22-141">Fusion 構造体</span><span class="sxs-lookup"><span data-stu-id="70a22-141">Fusion Structures</span></span>](fusion-structures.md)
