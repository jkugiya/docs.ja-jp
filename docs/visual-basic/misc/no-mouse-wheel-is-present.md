---
description: 詳細については、「マウスホイールが存在しません」を参照してください。
title: マウスのホイールが存在しません
ms.date: 07/20/2015
f1_keywords:
- vbrMouse_NoWheelIsPresent
ms.assetid: e924ffba-4af1-4247-9a6f-d19a03738f62
ms.openlocfilehash: c712903f41aa9f7c37c0cf1e3ffdc76edfd85b7f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100479102"
---
# <a name="no-mouse-wheel-is-present"></a><span data-ttu-id="60a85-103">マウスのホイールが存在しません</span><span class="sxs-lookup"><span data-stu-id="60a85-103">No mouse wheel is present</span></span>

<span data-ttu-id="60a85-104">`My.Computer.Mouse.WheelScrollLines` プロパティが呼び出されましたが、マウスにスクロール ホイールがありません。</span><span class="sxs-lookup"><span data-stu-id="60a85-104">The `My.Computer.Mouse.WheelScrollLines` property was called, but the mouse has no scroll wheel.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="60a85-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="60a85-105">To correct this error</span></span>  
  
- <span data-ttu-id="60a85-106">`My.Computer.Mouse.WheelExists` プロパティを呼び出す前に `My.Computer.Mouse.WheelScrollLines` プロパティを調べて、マウスにスクロール ホイールがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="60a85-106">Check the `My.Computer.Mouse.WheelExists` property to see if the mouse has a scroll wheel before calling the `My.Computer.Mouse.WheelScrollLines` property.</span></span>  
  
     <span data-ttu-id="60a85-107">- または -</span><span class="sxs-lookup"><span data-stu-id="60a85-107">-or-</span></span>  
  
- <span data-ttu-id="60a85-108">スクロール ホイールのあるマウスをコンピュータにインストールします。</span><span class="sxs-lookup"><span data-stu-id="60a85-108">Install a mouse with a scroll wheel on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60a85-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="60a85-109">See also</span></span>

- [<span data-ttu-id="60a85-110">マイ. My.computer.mouse.wheelscrolllines</span><span class="sxs-lookup"><span data-stu-id="60a85-110">My.Computer.Mouse.WheelScrollLines</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse.WheelScrollLines)
- [<span data-ttu-id="60a85-111">マイ. My.computer.mouse.wheelexists</span><span class="sxs-lookup"><span data-stu-id="60a85-111">My.Computer.Mouse.WheelExists</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse.WheelExists)
- [<span data-ttu-id="60a85-112">.NET での例外の処理とスロー</span><span class="sxs-lookup"><span data-stu-id="60a85-112">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
