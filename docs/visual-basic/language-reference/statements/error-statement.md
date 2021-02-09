---
description: '詳細情報: Error ステートメント'
title: Error ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 6c152e9e4fb4fa3a937042761c7d776b337f4fef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769144"
---
# <a name="error-statement"></a><span data-ttu-id="c81f3-103">Error ステートメント</span><span class="sxs-lookup"><span data-stu-id="c81f3-103">Error Statement</span></span>

<span data-ttu-id="c81f3-104">エラーの発生をシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="c81f3-104">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c81f3-105">構文</span><span class="sxs-lookup"><span data-stu-id="c81f3-105">Syntax</span></span>  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="c81f3-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="c81f3-106">Parts</span></span>  

 `errornumber`  
 <span data-ttu-id="c81f3-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="c81f3-107">Required.</span></span> <span data-ttu-id="c81f3-108">任意の有効なエラー番号を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c81f3-108">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c81f3-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="c81f3-109">Remarks</span></span>  

 <span data-ttu-id="c81f3-110">`Error` ステートメントは下位互換性のためにサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c81f3-110">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="c81f3-111">新しいコードでは、特にオブジェクトを作成する場合に、`Err` オブジェクトの `Raise` メソッドを使用して、実行時エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="c81f3-111">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="c81f3-112">`errornumber` を定義している場合、`Err` オブジェクトのプロパティに次の既定値が代入されると、`Error` ステートメントによって、エラー ハンドラーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c81f3-112">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="c81f3-113">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c81f3-113">Property</span></span>|<span data-ttu-id="c81f3-114">[値]</span><span class="sxs-lookup"><span data-stu-id="c81f3-114">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="c81f3-115">`Error` ステートメントの引数として指定された値。</span><span class="sxs-lookup"><span data-stu-id="c81f3-115">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="c81f3-116">任意の有効なエラー番号を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c81f3-116">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="c81f3-117">現在の Visual Basic プロジェクトの名前。</span><span class="sxs-lookup"><span data-stu-id="c81f3-117">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="c81f3-118">指定した `Number` の `Error` 関数の戻り値に対応する文字列式 (この文字列が存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="c81f3-118">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="c81f3-119">文字列が存在しない場合は、`Description` に長さゼロの文字列 ("") が格納されます。</span><span class="sxs-lookup"><span data-stu-id="c81f3-119">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="c81f3-120">該当する Visual Basic ヘルプ ファイルの完全修飾ドライブ、パス、およびファイル名。</span><span class="sxs-lookup"><span data-stu-id="c81f3-120">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="c81f3-121">`Number` プロパティに対応するエラーについての該当する Visual Basic ヘルプ ファイル コンテキスト ID。</span><span class="sxs-lookup"><span data-stu-id="c81f3-121">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="c81f3-122">ゼロ。</span><span class="sxs-lookup"><span data-stu-id="c81f3-122">Zero.</span></span>|  
  
 <span data-ttu-id="c81f3-123">エラー ハンドラーが存在しない場合、または有効なものがない場合は、`Err` オブジェクトのプロパティからエラーメッセージが作成され、表示されます。</span><span class="sxs-lookup"><span data-stu-id="c81f3-123">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c81f3-124">一部の Visual Basic ホストアプリケーションでは、オブジェクトを作成できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="c81f3-124">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="c81f3-125">ホスト アプリケーションでクラスとオブジェクトを作成できるかどうかを判断するには、そのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c81f3-125">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c81f3-126">例</span><span class="sxs-lookup"><span data-stu-id="c81f3-126">Example</span></span>  

 <span data-ttu-id="c81f3-127">この例では、`Error` ステートメントを使用して、エラー番号 11 を生成しています。</span><span class="sxs-lookup"><span data-stu-id="c81f3-127">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="c81f3-128">必要条件</span><span class="sxs-lookup"><span data-stu-id="c81f3-128">Requirements</span></span>  

 <span data-ttu-id="c81f3-129">**名前空間:** [Microsoft.VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="c81f3-129">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="c81f3-130">**アセンブリ:** Visual Basic ランタイム ライブラリ (Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="c81f3-130">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c81f3-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="c81f3-131">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="c81f3-132">On Error ステートメント</span><span class="sxs-lookup"><span data-stu-id="c81f3-132">On Error Statement</span></span>](on-error-statement.md)
- [<span data-ttu-id="c81f3-133">Resume ステートメント</span><span class="sxs-lookup"><span data-stu-id="c81f3-133">Resume Statement</span></span>](resume-statement.md)
- [<span data-ttu-id="c81f3-134">エラー メッセージ</span><span class="sxs-lookup"><span data-stu-id="c81f3-134">Error Messages</span></span>](../error-messages/index.md)
