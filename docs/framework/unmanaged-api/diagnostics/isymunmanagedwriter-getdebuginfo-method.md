---
description: '詳細について: ISymUnmanagedWriter:: GetDebugInfo メソッド'
title: ISymUnmanagedWriter::GetDebugInfo メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.GetDebugInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type:
- apiref
ms.openlocfilehash: 2255cc90c0bfcd36dacdf81703af67d3f47739db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762319"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a><span data-ttu-id="0193a-103">ISymUnmanagedWriter::GetDebugInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="0193a-103">ISymUnmanagedWriter::GetDebugInfo Method</span></span>

<span data-ttu-id="0193a-104">コンパイラがポータブル実行可能 (PE) ファイルヘッダーにデバッグディレクトリエントリを書き込むために必要な情報を返します。</span><span class="sxs-lookup"><span data-stu-id="0193a-104">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span> <span data-ttu-id="0193a-105">シンボルライターは、およびを除くすべてのフィールドを入力し `TimeDateStamp` `PointerToRawData` ます。</span><span class="sxs-lookup"><span data-stu-id="0193a-105">The symbol writer fills out all fields except for `TimeDateStamp` and `PointerToRawData`.</span></span> <span data-ttu-id="0193a-106">(コンパイラは、これらの2つのフィールドを適切に設定する必要があります)。</span><span class="sxs-lookup"><span data-stu-id="0193a-106">(The compiler is responsible for setting these two fields appropriately.)</span></span>  
  
 <span data-ttu-id="0193a-107">コンパイラは、このメソッドを呼び出し、PE ファイルにデータ blob を出力します。次に、 `PointerToRawData` 生成されたデータを指すように IMAGE_DEBUG_DIRECTORY のフィールドを設定し、IMAGE_DEBUG_DIRECTORY を pe ファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="0193a-107">A compiler should call this method, emit the data blob to the PE file, set the `PointerToRawData` field in the IMAGE_DEBUG_DIRECTORY to point to the emitted data, and write the IMAGE_DEBUG_DIRECTORY to the PE file.</span></span> <span data-ttu-id="0193a-108">また、コンパイラは、 `TimeDateStamp` `TimeDateStamp` 生成される PE ファイルのと同じフィールドをに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0193a-108">The compiler should also set the `TimeDateStamp` field to equal the `TimeDateStamp` of the PE file being generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0193a-109">構文</span><span class="sxs-lookup"><span data-stu-id="0193a-109">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0193a-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0193a-110">Parameters</span></span>  

 `pIDD`  
 <span data-ttu-id="0193a-111">[入力、出力]シンボルライターが入力する IMAGE_DEBUG_DIRECTORY へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0193a-111">[in, out] A pointer to an IMAGE_DEBUG_DIRECTORY that the symbol writer will fill out.</span></span>  
  
 `cData`  
 <span data-ttu-id="0193a-112">から `DWORD` デバッグデータのサイズを格納している。</span><span class="sxs-lookup"><span data-stu-id="0193a-112">[in] A `DWORD` that contains the size of the debug data.</span></span>  
  
 `pcData`  
 <span data-ttu-id="0193a-113">入出力 `DWORD` デバッグデータを格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0193a-113">[out] A pointer to a `DWORD` that receives the size of the buffer required to contain the debug data.</span></span>  
  
 `data`  
 <span data-ttu-id="0193a-114">入出力シンボルストアのデバッグデータを保持するのに十分な大きさのバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0193a-114">[out] A pointer to a buffer that is large enough to hold the debug data for the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0193a-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="0193a-115">Return Value</span></span>  

 <span data-ttu-id="0193a-116">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="0193a-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0193a-117">要件</span><span class="sxs-lookup"><span data-stu-id="0193a-117">Requirements</span></span>  

 <span data-ttu-id="0193a-118">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="0193a-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0193a-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="0193a-119">See also</span></span>

- [<span data-ttu-id="0193a-120">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0193a-120">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
