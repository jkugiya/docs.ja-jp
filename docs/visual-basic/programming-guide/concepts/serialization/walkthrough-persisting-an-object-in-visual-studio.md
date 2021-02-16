---
description: '詳細情報: チュートリアル: Visual Studio でのオブジェクトの永続化 (Visual Basic)'
title: オブジェクトの永続化 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: 4145f84d14eadae6a305a4a1f5860cdcc38450c8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100486863"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a><span data-ttu-id="7b6dd-103">チュートリアル: Visual Studio でのオブジェクトの永続化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b6dd-103">Walkthrough: Persisting an Object in Visual Studio (Visual Basic)</span></span>

<span data-ttu-id="7b6dd-104">オブジェクトのプロパティはデザイン時に既定値に設定できますが、そのオブジェクトが破棄されると、実行時に入力した値はすべて失われます。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-104">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span></span> <span data-ttu-id="7b6dd-105">シリアル化によってインスタンス間でオブジェクトのデータを永続化すると、値を保存しておき、次にそのオブジェクトをインスタンス化するときに、その値を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-105">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b6dd-106">Visual Basic では、`My.Settings` オブジェクトを使用して、名前や数値などの単純なデータを保存できます。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-106">In Visual Basic, to store simple data, such as a name or number, you can use the `My.Settings` object.</span></span> <span data-ttu-id="7b6dd-107">詳細については、「[My.Settings オブジェクト](../../../language-reference/objects/my-settings-object.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-107">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
 <span data-ttu-id="7b6dd-108">このチュートリアルでは、簡単な `Loan` オブジェクトを作成し、そのデータをファイルに永続化します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-108">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="7b6dd-109">その後、オブジェクトを再作成するときに、そのファイルからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-109">You will then retrieve the data from the file when you re-create the object.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7b6dd-110">次のコード例では、ファイルが存在しない場合は新規にファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-110">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="7b6dd-111">アプリケーションでファイルを作成する必要がある場合、そのアプリケーションには、フォルダーに対する `Create` アクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-111">If an application must create a file, that application must `Create` permission for the folder.</span></span> <span data-ttu-id="7b6dd-112">アクセス許可は、アクセス制御リストを使用して設定します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-112">Permissions are set by using access control lists.</span></span> <span data-ttu-id="7b6dd-113">ファイルが既に存在する場合、アプリケーションに必要なのは下位の `Write` アクセス許可だけです。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-113">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="7b6dd-114">可能な場合は、(フォルダーに対して Create アクセス許可を付与するのではなく) 配置時にファイルを作成し、1 つのファイルに対してのみ `Read` アクセス許可を付与する方が安全です。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-114">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="7b6dd-115">また、ルート フォルダーや Program Files フォルダーにデータを書き込むよりも、ユーザー フォルダーに書き込む方が安全です。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-115">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7b6dd-116">この例では、バイナリにデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-116">This example stores data in a binary.</span></span> <span data-ttu-id="7b6dd-117">この形式は、パスワードやクレジット カード情報などの重要情報には使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-117">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b6dd-118">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-118">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7b6dd-119">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-119">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7b6dd-120">詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-120">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-loan-object"></a><span data-ttu-id="7b6dd-121">Loan オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="7b6dd-121">Creating the Loan Object</span></span>  

 <span data-ttu-id="7b6dd-122">まず、`Loan` クラスとそのクラスを使用するテスト アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-122">The first step is to create a `Loan` class and a test application that uses the class.</span></span>  
  
### <a name="to-create-the-loan-class"></a><span data-ttu-id="7b6dd-123">Loan クラスを作成するには</span><span class="sxs-lookup"><span data-stu-id="7b6dd-123">To create the Loan class</span></span>  
  
1. <span data-ttu-id="7b6dd-124">新しいクラス ライブラリ プロジェクトを作成して、"LoanClass" という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-124">Create a new Class Library project and name it "LoanClass".</span></span> <span data-ttu-id="7b6dd-125">詳細については、「[ソリューションとプロジェクトの作成](/visualstudio/ide/creating-solutions-and-projects)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-125">For more information, see [Creating Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).</span></span>  
  
2. <span data-ttu-id="7b6dd-126">**ソリューション エクスプローラー** で、Class1 ファイルのショートカット メニューを開き、 **[名前の変更]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-126">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span></span> <span data-ttu-id="7b6dd-127">ファイルの名前を `Loan` に変更し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-127">Rename the file to `Loan` and press ENTER.</span></span> <span data-ttu-id="7b6dd-128">ファイルの名前を変更すると、クラスの名前も `Loan` に変更されます。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-128">Renaming the file will also rename the class to `Loan`.</span></span>  
  
3. <span data-ttu-id="7b6dd-129">クラスに次のパブリック メンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-129">Add the following public members to the class:</span></span>  
  
    ```vb  
    Public Class Loan  
        Implements System.ComponentModel.INotifyPropertyChanged  
  
        Public Property LoanAmount As Double  
        Public Property InterestRate As Double  
        Public Property Term As Integer  
  
        Private p_Customer As String  
        Public Property Customer As String  
            Get  
                Return p_Customer  
            End Get  
            Set(ByVal value As String)  
                p_Customer = value  
                RaiseEvent PropertyChanged(Me,  
                  New System.ComponentModel.PropertyChangedEventArgs("Customer"))  
            End Set  
        End Property  
  
        Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
          Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
  
        Public Sub New(ByVal loanAmount As Double,  
                       ByVal interestRate As Double,  
                       ByVal term As Integer,  
                       ByVal customer As String)  
  
            Me.LoanAmount = loanAmount  
            Me.InterestRate = interestRate  
            Me.Term = term  
            p_Customer = customer  
        End Sub  
    End Class  
    ```  
  
 <span data-ttu-id="7b6dd-130">また、`Loan` クラスを使用する簡単なアプリケーションも作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-130">You will also have to create a simple application that uses the `Loan` class.</span></span>  
  
### <a name="to-create-a-test-application"></a><span data-ttu-id="7b6dd-131">テスト アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="7b6dd-131">To create a test application</span></span>  
  
1. <span data-ttu-id="7b6dd-132">**[ファイル]** メニューで **[追加]** 、 **[新しいプロジェクト]** の順に選択して、Windows フォーム アプリケーション プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-132">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**,**New Project**.</span></span>  
  
2. <span data-ttu-id="7b6dd-133">**[新しいプロジェクトの追加]** ダイアログ ボックスで、 **[Windows フォーム アプリケーション]** を選択し、プロジェクト名として「`LoanApp`」と入力します。次に、 **[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-133">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="7b6dd-134">**ソリューション エクスプローラー** で LoanApp プロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-134">In **Solution Explorer**, choose the LoanApp project.</span></span>  
  
4. <span data-ttu-id="7b6dd-135">**[プロジェクト]** メニューの **[スタートアップ プロジェクトに設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-135">On the **Project** menu, choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="7b6dd-136">**[プロジェクト]** メニューの **[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-136">On the **Project** menu, choose **Add Reference**.</span></span>  
  
6. <span data-ttu-id="7b6dd-137">**[参照の追加]** ダイアログ ボックスで、 **[プロジェクト]** タブをクリックし、LoanClass プロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-137">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span></span>  
  
7. <span data-ttu-id="7b6dd-138">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-138">Click **OK** to close the dialog box.</span></span>  
  
8. <span data-ttu-id="7b6dd-139">デザイナーで、フォームに <xref:System.Windows.Forms.TextBox> コントロールを 4 つ追加します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-139">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span></span>  
  
9. <span data-ttu-id="7b6dd-140">コード エディターで、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-140">In the Code Editor, add the following code:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. <span data-ttu-id="7b6dd-141">次のコードを使用して、`PropertyChanged` イベントのイベント ハンドラーをフォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-141">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span></span>  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 <span data-ttu-id="7b6dd-142">この時点で、アプリケーションをビルドして実行できます。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-142">At this point, you can build and run the application.</span></span> <span data-ttu-id="7b6dd-143">`Loan` クラスの既定値が、テキスト ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-143">Note that the default values from the `Loan` class appear in the text boxes.</span></span> <span data-ttu-id="7b6dd-144">利率の値を 7.5 から 7.1 に変更し、アプリケーションをいったん閉じてから、再び実行してください。値が既定値の 7.5 に戻ります。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-144">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span></span>  
  
 <span data-ttu-id="7b6dd-145">実際には利率は定期的に変わりますが、アプリケーションを実行するたびに変わるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-145">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="7b6dd-146">アプリケーションを実行するたびにユーザーが利率を更新するのではなく、アプリケーションのインスタンス間で最新の利率を保持できるようにすると便利です。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-146">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="7b6dd-147">次の手順では、Loan クラスにシリアル化を追加して、利率を保持できるようにします。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-147">In the next step, you will do just that by adding serialization to the Loan class.</span></span>  
  
## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="7b6dd-148">シリアル化を使用したオブジェクトの永続化</span><span class="sxs-lookup"><span data-stu-id="7b6dd-148">Using Serialization to Persist the Object</span></span>  

 <span data-ttu-id="7b6dd-149">Loan クラスの値を永続化するには、まず、クラスを `Serializable` 属性でマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-149">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span>  
  
### <a name="to-mark-a-class-as-serializable"></a><span data-ttu-id="7b6dd-150">クラスをシリアル化可能としてマークするには</span><span class="sxs-lookup"><span data-stu-id="7b6dd-150">To mark a class as serializable</span></span>  
  
- <span data-ttu-id="7b6dd-151">Loan クラスのクラス宣言を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-151">Change the class declaration for the Loan class as follows:</span></span>  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 <span data-ttu-id="7b6dd-152">`Serializable` 属性は、クラス内のすべての要素がファイルに永続化できることをコンパイラに示します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-152">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="7b6dd-153">`PropertyChanged` イベントは Windows フォーム オブジェクトで処理されるためシリアル化できません。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-153">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span></span> <span data-ttu-id="7b6dd-154">永続化しないクラス メンバーは、`NonSerialized` 属性でマークできます。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-154">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span></span>  
  
### <a name="to-prevent-a-member-from-being-serialized"></a><span data-ttu-id="7b6dd-155">メンバーをシリアル化の対象から除外するには</span><span class="sxs-lookup"><span data-stu-id="7b6dd-155">To prevent a member from being serialized</span></span>  
  
- <span data-ttu-id="7b6dd-156">`PropertyChanged` イベントの宣言を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-156">Change the declaration for the `PropertyChanged` event as follows:</span></span>  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 <span data-ttu-id="7b6dd-157">次に、LoanApp アプリケーションにシリアル化コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-157">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="7b6dd-158">クラスをシリアル化してファイルに書き込むには、<xref:System.IO> 名前空間と <xref:System.Xml.Serialization> 名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-158">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span></span> <span data-ttu-id="7b6dd-159">必要なクラス ライブラリへの参照を追加すると、完全修飾名の入力が不要になります。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-159">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span></span>  
  
### <a name="to-add-references-to-namespaces"></a><span data-ttu-id="7b6dd-160">名前空間に参照を追加するには</span><span class="sxs-lookup"><span data-stu-id="7b6dd-160">To add references to namespaces</span></span>  
  
- <span data-ttu-id="7b6dd-161">`Form1` クラスの先頭に、次のステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-161">Add the following statements to the top of the `Form1` class:</span></span>  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     <span data-ttu-id="7b6dd-162">この場合は、バイナリ フォーマッタを使用して、バイナリ形式でオブジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-162">In this case, you are using a binary formatter to save the object in a binary format.</span></span>  
  
 <span data-ttu-id="7b6dd-163">次の手順では、オブジェクトの作成時にファイルからオブジェクトを逆シリアル化するコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-163">The next step is to add code to deserialize the object from the file when the object is created.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="7b6dd-164">オブジェクトを逆シリアル化するには</span><span class="sxs-lookup"><span data-stu-id="7b6dd-164">To deserialize an object</span></span>  
  
1. <span data-ttu-id="7b6dd-165">シリアル化されたデータのファイル名を定数としてクラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-165">Add a constant to the class for the serialized data's file name.</span></span>  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2. <span data-ttu-id="7b6dd-166">`Form1_Load` イベント プロシージャのコードを次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-166">Modify the code in the `Form1_Load` event procedure as follows:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        If File.Exists(FileName) Then  
            Dim TestFileStream As Stream = File.OpenRead(FileName)  
            Dim deserializer As New BinaryFormatter  
            TestLoan = CType(deserializer.Deserialize(TestFileStream), LoanClass.Loan)  
            TestFileStream.Close()  
        End If  
  
        AddHandler TestLoan.PropertyChanged, AddressOf Me.CustomerPropertyChanged  
  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
     <span data-ttu-id="7b6dd-167">まず、ファイルが存在することを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-167">Note that you first must check that the file exists.</span></span> <span data-ttu-id="7b6dd-168">ファイルが存在する場合は、バイナリ ファイルを読み取る <xref:System.IO.Stream> クラスと、ファイルを変換する <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-168">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="7b6dd-169">ストリーム型を Loan オブジェクト型に変換する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-169">You also need to convert from the stream type to the Loan object type.</span></span>  
  
 <span data-ttu-id="7b6dd-170">次に、テキスト ボックスに入力されたデータを `Loan` クラスに保存するコードを追加します。その後、クラスをファイルにシリアル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-170">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span></span>  
  
### <a name="to-save-the-data-and-serialize-the-class"></a><span data-ttu-id="7b6dd-171">データを保存してクラスをシリアル化するには</span><span class="sxs-lookup"><span data-stu-id="7b6dd-171">To save the data and serialize the class</span></span>  
  
- <span data-ttu-id="7b6dd-172">`Form1_FormClosing` イベント プロシージャに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-172">Add the following code to the `Form1_FormClosing` event procedure:</span></span>  
  
    ```vb  
    Private Sub Form1_FormClosing() Handles MyBase.FormClosing  
        TestLoan.LoanAmount = CDbl(TextBox1.Text)  
        TestLoan.InterestRate = CDbl(TextBox2.Text)  
        TestLoan.Term = CInt(TextBox3.Text)  
        TestLoan.Customer = TextBox4.Text  
  
        Dim TestFileStream As Stream = File.Create(FileName)  
        Dim serializer As New BinaryFormatter  
        serializer.Serialize(TestFileStream, TestLoan)  
        TestFileStream.Close()  
    End Sub  
    ```  
  
 <span data-ttu-id="7b6dd-173">この時点で、アプリケーションを再度ビルドして実行できます。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-173">At this point, you can again build and run the application.</span></span> <span data-ttu-id="7b6dd-174">最初に既定値がテキスト ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-174">Initially, the default values appear in the text boxes.</span></span> <span data-ttu-id="7b6dd-175">値を変更して、4 番目のテキスト ボックスに名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-175">Try to change the values and enter a name in the fourth text box.</span></span> <span data-ttu-id="7b6dd-176">いったんアプリケーションを閉じて、再び実行します。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-176">Close the application and then run it again.</span></span> <span data-ttu-id="7b6dd-177">これで、新しい値がテキスト ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b6dd-177">Note that the new values now appear in the text boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b6dd-178">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b6dd-178">See also</span></span>

- [<span data-ttu-id="7b6dd-179">シリアル化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b6dd-179">Serialization (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="7b6dd-180">Visual Basic プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="7b6dd-180">Visual Basic Programming Guide</span></span>](../../index.md)
