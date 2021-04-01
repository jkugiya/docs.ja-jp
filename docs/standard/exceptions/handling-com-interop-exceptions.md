---
description: '詳細情報: COM 相互運用の例外の処理'
title: COM 相互運用の例外の処理
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
ms.openlocfilehash: c7746f84d30dafcaf30c3d89d4319ca3fb2107d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713287"
---
# <a name="handling-com-interop-exceptions"></a><span data-ttu-id="c9760-103">COM 相互運用の例外の処理</span><span class="sxs-lookup"><span data-stu-id="c9760-103">Handling COM Interop Exceptions</span></span>

<span data-ttu-id="c9760-104">マネージド コードとアンマネージド コードは、例外を処理するために一緒に操作できます。</span><span class="sxs-lookup"><span data-stu-id="c9760-104">Managed and unmanaged code can work together to handle exceptions.</span></span> <span data-ttu-id="c9760-105">マネージド コードでメソッドが例外をスローすると、共通言語ランタイムは、HRESULT を COM オブジェクトに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="c9760-105">If a method throws an exception in managed code, the common language runtime can pass an HRESULT to a COM object.</span></span> <span data-ttu-id="c9760-106">アンマネージド コードでメソッドが失敗して、失敗を示す HRESULT を返した場合、ランタイムはマネージド コードでキャッチできる例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="c9760-106">If a method fails in unmanaged code by returning a failure HRESULT, the runtime throws an exception that can be caught by managed code.</span></span>  
  
 <span data-ttu-id="c9760-107">ランタイムは、HRESULT を COM 相互運用からの自動的にマップして、より詳細な例外を取得します。</span><span class="sxs-lookup"><span data-stu-id="c9760-107">The runtime automatically maps the HRESULT from COM interop to more specific exceptions.</span></span> <span data-ttu-id="c9760-108">たとえば、E_ACCESSDENIED は <xref:System.UnauthorizedAccessException> になり、E_OUTOFMEMORY は <xref:System.OutOfMemoryException> になるなどです。</span><span class="sxs-lookup"><span data-stu-id="c9760-108">For example, E_ACCESSDENIED becomes <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY becomes <xref:System.OutOfMemoryException>, and so on.</span></span>  
  
 <span data-ttu-id="c9760-109">HRESULT がカスタムの結果であるか、またはランタイムで不明な場合は、ランタイムがジェネリック <xref:System.Runtime.InteropServices.COMException> をクライアントに渡します。</span><span class="sxs-lookup"><span data-stu-id="c9760-109">If the HRESULT is a custom result or if it is unknown to the runtime, the runtime passes a generic <xref:System.Runtime.InteropServices.COMException> to the client.</span></span> <span data-ttu-id="c9760-110">**COMException** の **ErrorCode** プロパティには、HRESULT 値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c9760-110">The **ErrorCode** property of the **COMException** contains the HRESULT value.</span></span>  
  
## <a name="working-with-ierrorinfo"></a><span data-ttu-id="c9760-111">IErrorInfo の処理</span><span class="sxs-lookup"><span data-stu-id="c9760-111">Working with IErrorInfo</span></span>  

 <span data-ttu-id="c9760-112">エラーが COM からマネージド コードに渡された場合、ランタイムは例外オブジェクトにエラー情報を入れます。</span><span class="sxs-lookup"><span data-stu-id="c9760-112">When an error is passed from COM to managed code, the runtime populates the exception object with error information.</span></span> <span data-ttu-id="c9760-113">IErrorInfo をサポートして HRESULT を返す COM オブジェクトは、この情報をマネージド コードの例外に提供します。</span><span class="sxs-lookup"><span data-stu-id="c9760-113">COM objects that support IErrorInfo and return HRESULTS provide this information to managed code exceptions.</span></span> <span data-ttu-id="c9760-114">たとえば、ランタイムは、COM エラーからの説明を例外の <xref:System.Exception.Message%2A> プロパティにマップします。</span><span class="sxs-lookup"><span data-stu-id="c9760-114">For example, the runtime maps the Description from the COM error to the exception's <xref:System.Exception.Message%2A> property.</span></span> <span data-ttu-id="c9760-115">HRESULT が追加のエラー情報を提供しない場合、ランタイムは例外のプロパティの多くに既定値を指定します。</span><span class="sxs-lookup"><span data-stu-id="c9760-115">If the HRESULT provides no additional error information, the runtime fills many of the exception's properties with default values.</span></span>  
  
 <span data-ttu-id="c9760-116">アンマネージド コードでメソッドが失敗した場合、例外をマネージド コードのセグメントに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="c9760-116">If a method fails in unmanaged code, an exception can be passed to a managed code segment.</span></span> <span data-ttu-id="c9760-117">「[HRESULT と例外](../../framework/interop/how-to-map-hresults-and-exceptions.md)」のトピックには、HRESULT がランタイム例外オブジェクトにマップする方法を示す表が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c9760-117">The topic [HRESULTS and Exceptions](../../framework/interop/how-to-map-hresults-and-exceptions.md) contains a table showing how HRESULTS map to runtime exception objects.</span></span>  

## <a name="see-also"></a><span data-ttu-id="c9760-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9760-118">See also</span></span>

- [<span data-ttu-id="c9760-119">例外</span><span class="sxs-lookup"><span data-stu-id="c9760-119">Exceptions</span></span>](index.md)
