---
description: '詳細情報: -errorreport'
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: b6fa10482e6852a819303074b4662f02eb8d1f88
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475943"
---
# <a name="-errorreport"></a><span data-ttu-id="fccfa-103">-errorreport</span><span class="sxs-lookup"><span data-stu-id="fccfa-103">-errorreport</span></span>

<span data-ttu-id="fccfa-104">Visual Basic コンパイラで内部コンパイラ エラーを報告する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="fccfa-104">Specifies how the Visual Basic compiler should report internal compiler errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="fccfa-105">構文</span><span class="sxs-lookup"><span data-stu-id="fccfa-105">Syntax</span></span>

```console
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a><span data-ttu-id="fccfa-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="fccfa-106">Remarks</span></span>

<span data-ttu-id="fccfa-107">このオプションでは、Microsoft の Visual Basic チームに Visual Basic 内部コンパイラ エラー (ICE) を報告する便利な方法が提供されます。</span><span class="sxs-lookup"><span data-stu-id="fccfa-107">This option provides a convenient way to report a Visual Basic internal compiler error (ICE) to the Visual Basic team at Microsoft.</span></span> <span data-ttu-id="fccfa-108">既定では、コンパイラによって Microsoft に情報が送信されることはありません。</span><span class="sxs-lookup"><span data-stu-id="fccfa-108">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="fccfa-109">ただし、このオプションを使用すると、内部コンパイラ エラーが発生した場合に、エラーを Microsoft に報告することができます。</span><span class="sxs-lookup"><span data-stu-id="fccfa-109">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="fccfa-110">その情報は、Microsoft のエンジニアが原因を特定するのに役立ちます。また、Visual Basic の次のリリースの向上に役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="fccfa-110">That information will help Microsoft engineers identify the cause and may help improve the next release of Visual Basic.</span></span>

<span data-ttu-id="fccfa-111">マシンまたはユーザー ポリシーによるアクセス許可によっては、レポートを送信できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="fccfa-111">A user's ability to send reports depends on machine and user policy permissions.</span></span>

<span data-ttu-id="fccfa-112">次の表に、`-errorreport` オプションの結果をまとめています。</span><span class="sxs-lookup"><span data-stu-id="fccfa-112">The following table summarizes the effect of the `-errorreport` option.</span></span>

|<span data-ttu-id="fccfa-113">オプション</span><span class="sxs-lookup"><span data-stu-id="fccfa-113">Option</span></span>|<span data-ttu-id="fccfa-114">動作</span><span class="sxs-lookup"><span data-stu-id="fccfa-114">Behavior</span></span>|
|---|---|
|`prompt`|<span data-ttu-id="fccfa-115">内部コンパイラ エラーが発生すると、コンパイラによって収集された正確なデータを表示するためのダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fccfa-115">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="fccfa-116">エラー レポートに機密情報が含まれているかどうかを確認し、Microsoft に送信するかどうかを決定することができます。</span><span class="sxs-lookup"><span data-stu-id="fccfa-116">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="fccfa-117">送信する場合、マシンとユーザーのポリシー設定でそれが許可されていれば、コンパイラによってデータが Microsoft に送信されます。</span><span class="sxs-lookup"><span data-stu-id="fccfa-117">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|
|`queue`|<span data-ttu-id="fccfa-118">エラー レポートを待ち行列に入れます。</span><span class="sxs-lookup"><span data-stu-id="fccfa-118">Queues the error report.</span></span> <span data-ttu-id="fccfa-119">管理者特権でログインすると、最後にログインした後に発生したすべてのエラーを報告することができます (エラーの報告を 3 日ごとに複数回送信するように求めるメッセージは表示されません)。</span><span class="sxs-lookup"><span data-stu-id="fccfa-119">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="fccfa-120">`-errorreport` オプションが指定されていない場合は、これが既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="fccfa-120">This is the default behavior when the `-errorreport` option is not specified.</span></span>|
|`send`|<span data-ttu-id="fccfa-121">内部コンパイラ エラーが発生した場合、マシンとユーザーのポリシー設定で許可されていれば、コンパイラによってデータが Microsoft に送信されます。</span><span class="sxs-lookup"><span data-stu-id="fccfa-121">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="fccfa-122">オプション `-errorreport:send` では、[Windows エラー報告](/windows/desktop/wer/windows-error-reporting)システム設定でレポートが有効になっている場合、Microsoft にエラー情報を自動的に送信するよう試みられます。</span><span class="sxs-lookup"><span data-stu-id="fccfa-122">The option `-errorreport:send` attempts to automatically send error information to Microsoft if reporting is enabled by the [Windows Error Reporting](/windows/desktop/wer/windows-error-reporting) system settings.</span></span> |
|`none`|<span data-ttu-id="fccfa-123">内部コンパイラ エラーが発生すると、そのエラーは収集されず、Microsoft に送信されません。</span><span class="sxs-lookup"><span data-stu-id="fccfa-123">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|

<span data-ttu-id="fccfa-124">コンパイラによって、エラー発生時にスタックを含むデータが送信されます。これには通常、いくつかのソース コードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="fccfa-124">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="fccfa-125">`-errorreport` を [-bugreport](bugreport.md) オプションと共に使用すると、ソース ファイル全体が送信されます。</span><span class="sxs-lookup"><span data-stu-id="fccfa-125">If `-errorreport` is used with the [-bugreport](bugreport.md) option, then the entire source file is sent.</span></span>

<span data-ttu-id="fccfa-126">Microsoft のエンジニアがエラーをより簡単に再現できるようになるため、このオプションを [-bugreport](bugreport.md) オプションと共に使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fccfa-126">This option is best used with the [-bugreport](bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>

> [!NOTE]
> <span data-ttu-id="fccfa-127">`-errorreport` オプションは、Visual Studio 開発環境からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="fccfa-127">The `-errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="fccfa-128">例</span><span class="sxs-lookup"><span data-stu-id="fccfa-128">Example</span></span>

<span data-ttu-id="fccfa-129">次のコードでは、`T2.vb` のコンパイルが試行されます。コンパイラで内部コンパイラ エラーが発生した場合は、Microsoft にエラー レポートを送信するように求められます。</span><span class="sxs-lookup"><span data-stu-id="fccfa-129">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>

```console
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="fccfa-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="fccfa-130">See also</span></span>

- [<span data-ttu-id="fccfa-131">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="fccfa-131">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="fccfa-132">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="fccfa-132">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="fccfa-133">-bugreport</span><span class="sxs-lookup"><span data-stu-id="fccfa-133">-bugreport</span></span>](bugreport.md)
