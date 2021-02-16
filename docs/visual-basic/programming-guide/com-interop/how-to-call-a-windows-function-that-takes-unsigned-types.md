---
description: '詳細情報: 方法:符号なしの型を使用する Windows の機能を呼び出す (Visual Basic)'
title: '方法: 符号なしの型を使用する Windows の機能を呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- Windows functions [Visual Basic], calling
- unsigned data types [Visual Basic]
- UShort data type [Visual Basic], using
- functions [Visual Basic], calling Windows functions
- ULong data type [Visual Basic], using
- UInteger data type [Visual Basic], using
- data types [Visual Basic], using
- unsigned types [Visual Basic]
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types [Visual Basic], using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
ms.openlocfilehash: 45851e22db88b9d35e5315398fb4cdbc2a7b920c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475644"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="68fee-103">方法: 符号なしの型を使用する Windows の機能を呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68fee-103">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>

<span data-ttu-id="68fee-104">符号なし整数型のメンバーを含むクラス、モジュール、または構造体を使用している場合、これらのメンバーに Visual Basic を使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="68fee-104">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with Visual Basic.</span></span>

## <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="68fee-105">符号なしの型を使用する Windows の関数を呼び出すには</span><span class="sxs-lookup"><span data-stu-id="68fee-105">To call a Windows function that takes an unsigned type</span></span>

1. <span data-ttu-id="68fee-106">[Declare ステートメント](../../language-reference/statements/declare-statement.md)を使用して、どのライブラリに関数が含まれるか、そのライブラリ内での名前、呼び出し元シーケンス、および呼び出す際の文字列の変換方法を Visual Basic に指定します。</span><span class="sxs-lookup"><span data-stu-id="68fee-106">Use a [Declare Statement](../../language-reference/statements/declare-statement.md) to tell Visual Basic which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>

2. <span data-ttu-id="68fee-107">`Declare` ステートメントでは、符号なしの型の各パラメーターで必要に応じて、`UInteger`、`ULong`、`UShort`、または `Byte` を使用します。</span><span class="sxs-lookup"><span data-stu-id="68fee-107">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>

3. <span data-ttu-id="68fee-108">呼び出す Windows 関数のドキュメントを参照して、使用される定数の名前と値を確認します。</span><span class="sxs-lookup"><span data-stu-id="68fee-108">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="68fee-109">これらの多くは、WinUser.h ファイルで定義されています。</span><span class="sxs-lookup"><span data-stu-id="68fee-109">Many of these are defined in the WinUser.h file.</span></span>

4. <span data-ttu-id="68fee-110">必要な定数をコードで宣言します。</span><span class="sxs-lookup"><span data-stu-id="68fee-110">Declare the necessary constants in your code.</span></span> <span data-ttu-id="68fee-111">多くの Windows 定数は、32 ビットの符号なしの値であるため、これらを `As UInteger` で宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68fee-111">Many Windows constants are 32-bit unsigned values, and you should declare these `As UInteger`.</span></span>

5. <span data-ttu-id="68fee-112">通常の方法で関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="68fee-112">Call the function in the normal way.</span></span> <span data-ttu-id="68fee-113">次の例では、符号なし整数引数を受け取る Windows 関数 `MessageBox` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="68fee-113">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>

    ```vb
    Public Class windowsMessage
        Private Declare Auto Function mb Lib "user32.dll" Alias "MessageBox" (
            ByVal hWnd As Integer,
            ByVal lpText As String,
            ByVal lpCaption As String,
            ByVal uType As UInteger) As Integer
        Private Const MB_OK As UInteger = 0
        Private Const MB_ICONEXCLAMATION As UInteger = &H30
        Private Const IDOK As UInteger = 1
        Private Const IDCLOSE As UInteger = 8
        Private Const c As UInteger = MB_OK Or MB_ICONEXCLAMATION
        Public Function messageThroughWindows() As String
            Dim r As Integer = mb(0, "Click OK if you see this!",
                "Windows API call", c)
            Dim s As String = "Windows API MessageBox returned " &
                 CStr(r)& vbCrLf & "(IDOK = " & CStr(IDOK) &
                 ", IDCLOSE = " & CStr(IDCLOSE) & ")"
            Return s
        End Function
    End Class
    ```

     <span data-ttu-id="68fee-114">次のコードを使用して、関数 `messageThroughWindows` をテストできます。</span><span class="sxs-lookup"><span data-stu-id="68fee-114">You can test the function `messageThroughWindows` with the following code.</span></span>

    ```vb
    Public Sub consumeWindowsMessage()
        Dim w As New windowsMessage
        w.messageThroughWindows()
    End Sub
    ```

    > [!CAUTION]
    > <span data-ttu-id="68fee-115">`UInteger`、`ULong`、`UShort`、および `SByte` データ型は、[言語への非依存性、および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md) (CLS) の一部ではないため、CLS 準拠のコードではこれらを使用するコンポーネントを使用できません。</span><span class="sxs-lookup"><span data-stu-id="68fee-115">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="68fee-116">Windows アプリケーション プログラミング インターフェイス (API) などのアンマネージド コードを呼び出すと、コードが潜在的なセキュリティ リスクにさらされます。</span><span class="sxs-lookup"><span data-stu-id="68fee-116">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="68fee-117">Windows API を呼び出すには、アンマネージド コードのアクセス許可が必要です。これは、部分信頼状況での実行に影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="68fee-117">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="68fee-118">詳細については、「<xref:System.Security.Permissions.SecurityPermission>」および「[コード アクセス許可](/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68fee-118">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="68fee-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="68fee-119">See also</span></span>

- [<span data-ttu-id="68fee-120">データの種類</span><span class="sxs-lookup"><span data-stu-id="68fee-120">Data Types</span></span>](../../language-reference/data-types/index.md)
- [<span data-ttu-id="68fee-121">Integer データ型</span><span class="sxs-lookup"><span data-stu-id="68fee-121">Integer Data Type</span></span>](../../language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="68fee-122">UInteger データ型</span><span class="sxs-lookup"><span data-stu-id="68fee-122">UInteger Data Type</span></span>](../../language-reference/data-types/uinteger-data-type.md)
- [<span data-ttu-id="68fee-123">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="68fee-123">Declare Statement</span></span>](../../language-reference/statements/declare-statement.md)
- [<span data-ttu-id="68fee-124">チュートリアル: Windows API の呼び出し</span><span class="sxs-lookup"><span data-stu-id="68fee-124">Walkthrough: Calling Windows APIs</span></span>](walkthrough-calling-windows-apis.md)
