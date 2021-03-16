---
title: Mgmtclassgen.exe (厳密型クラス ジェネレーター)
description: Mgmtclassgen.exe (厳密型クラス ジェネレーター) について理解します。 このツールを使用すると、WMI クラスに対して、事前バインディングされたマネージド クラスをすばやく生成できます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CIM types
- Management Strongly Typed Class Generator
- WMI class
- Mgmtclassgen.exe
- early-bound managed classes
ms.assetid: 02ce6699-49b5-4a0b-b0d5-1003c491232e
ms.openlocfilehash: 8008644a4c443a2fcd4430c6710f4845f1e4bb30
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259370"
---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a><span data-ttu-id="18d50-104">Mgmtclassgen.exe (厳密型クラス ジェネレーター)</span><span class="sxs-lookup"><span data-stu-id="18d50-104">Mgmtclassgen.exe (Management Strongly Typed Class Generator)</span></span>

<span data-ttu-id="18d50-105">厳密型クラス ジェネレーター (Mgmtclassgen.exe) ツールを使用すると、指定した WMI (Windows Management Instrumentation) クラスに対して、事前バインディングされたマネージド クラスをすばやく生成できます。</span><span class="sxs-lookup"><span data-stu-id="18d50-105">The Management Strongly Typed Class Generator tool enables you to quickly generate an early-bound managed class for a specified Windows Management Instrumentation (WMI) class.</span></span> <span data-ttu-id="18d50-106">生成されたクラスを使用すると、WMI クラスのインスタンスにアクセスするために書く必要のあるコードを簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="18d50-106">The generated class simplifies the code you must write to access an instance of the WMI class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18d50-107">構文</span><span class="sxs-lookup"><span data-stu-id="18d50-107">Syntax</span></span>  
  
```console  
mgmtclassgen
WMIClass [options]
```  
  
|<span data-ttu-id="18d50-108">引数</span><span class="sxs-lookup"><span data-stu-id="18d50-108">Argument</span></span>|<span data-ttu-id="18d50-109">説明</span><span class="sxs-lookup"><span data-stu-id="18d50-109">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="18d50-110">*WMIClass*</span><span class="sxs-lookup"><span data-stu-id="18d50-110">*WMIClass*</span></span>|<span data-ttu-id="18d50-111">事前バインディングしたマネージド クラスを生成する対象の WMI クラスです。</span><span class="sxs-lookup"><span data-stu-id="18d50-111">The Windows Management Instrumentation class for which to generate an early-bound managed class.</span></span>|  
  
|<span data-ttu-id="18d50-112">オプション</span><span class="sxs-lookup"><span data-stu-id="18d50-112">Option</span></span>|<span data-ttu-id="18d50-113">説明</span><span class="sxs-lookup"><span data-stu-id="18d50-113">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="18d50-114">**/l**  *language*</span><span class="sxs-lookup"><span data-stu-id="18d50-114">**/l**  *language*</span></span>|<span data-ttu-id="18d50-115">事前バインディングされたマネージド クラスの生成に使用する言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="18d50-115">Specifies the language in which to generate the early-bound managed class.</span></span> <span data-ttu-id="18d50-116">language 引数として **CS** (C#、既定値)、**VB** (Visual Basic)、**MC** (C++)、または **JS** (JScript) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="18d50-116">You can specify **CS** (C#; default), **VB** (Visual Basic),  **MC** (C++), or **JS** (JScript) as the language argument.</span></span>|  
|<span data-ttu-id="18d50-117">**/m**  *machine*</span><span class="sxs-lookup"><span data-stu-id="18d50-117">**/m**  *machine*</span></span>|<span data-ttu-id="18d50-118">WMI クラスが常駐する、接続先のコンピューターを指定します。</span><span class="sxs-lookup"><span data-stu-id="18d50-118">Specifies the computer to connect to, where the WMI class resides.</span></span> <span data-ttu-id="18d50-119">既定値はローカル コンピューターです。</span><span class="sxs-lookup"><span data-stu-id="18d50-119">The default is the local computer.</span></span>|  
|<span data-ttu-id="18d50-120">**/n**  *path*</span><span class="sxs-lookup"><span data-stu-id="18d50-120">**/n**  *path*</span></span>|<span data-ttu-id="18d50-121">WMI クラスが含まれている WMI 名前空間へのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="18d50-121">Specifies the path to the WMI namespace that contains the WMI class.</span></span> <span data-ttu-id="18d50-122">このオプションを指定しない場合、このツールは既定の **Root\cimv2** 名前空間に *WMIClass* のコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="18d50-122">If you do not specify this option, the tool generates code for *WMIClass* in the default **Root\cimv2** namespace.</span></span>|  
|<span data-ttu-id="18d50-123">**/o**  *classnamespace*</span><span class="sxs-lookup"><span data-stu-id="18d50-123">**/o**  *classnamespace*</span></span>|<span data-ttu-id="18d50-124">マネージド コード クラスを生成する先の .NET 名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="18d50-124">Specifies the .NET namespace in which to generate the managed code class.</span></span> <span data-ttu-id="18d50-125">このオプションを指定しない場合、このツールは WMI 名前空間およびスキーマ プリフィックスを使用して名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="18d50-125">If you do not specify this option, the tool generates the namespace using the WMI namespace and the schema prefix.</span></span> <span data-ttu-id="18d50-126">スキーマ プリフィックスはクラス名の一部で、アンダースコア (_) 文字の前に付きます。</span><span class="sxs-lookup"><span data-stu-id="18d50-126">The schema prefix is the part of the class name preceding the underscore character.</span></span> <span data-ttu-id="18d50-127">たとえば、**Root\cimv2** 名前空間内の **Win32_OperatingSystem** クラスの場合、このツールは **ROOT.CIMV2.Win32** にクラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="18d50-127">For example, for the **Win32_OperatingSystem** class in the **Root\cimv2** namespace, the tool would generate the class in **ROOT.CIMV2.Win32**.</span></span>|  
|<span data-ttu-id="18d50-128">**/p**  *filepath*</span><span class="sxs-lookup"><span data-stu-id="18d50-128">**/p**  *filepath*</span></span>|<span data-ttu-id="18d50-129">生成されたコードを保存するファイルへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="18d50-129">Specifies the path to the file in which to save the generated code.</span></span> <span data-ttu-id="18d50-130">このオプションを指定しない場合、このツールは現在のディレクトリにファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="18d50-130">If you do not specify this option, the tool creates the file in the current directory.</span></span> <span data-ttu-id="18d50-131">*WMIClass* 引数を使用して生成したクラスと、そのクラスを保存したファイルには名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="18d50-131">It names the class and file in which it generates the class using the *WMIClass* argument.</span></span> <span data-ttu-id="18d50-132">クラスおよびファイルの名前は、*WMIClass* の名前と同じです。</span><span class="sxs-lookup"><span data-stu-id="18d50-132">The name of the class and the file are the same as the name of the *WMIClass.*</span></span> <span data-ttu-id="18d50-133">*WMIClass* にアンダースコア (_) 文字が含まれている場合は、アンダースコア (_) 文字の後に続く、クラス名の一部が使用されます。</span><span class="sxs-lookup"><span data-stu-id="18d50-133">If *WMIClass* contains an underscore character, the tool uses the part of the class name following the underscore character.</span></span> <span data-ttu-id="18d50-134">たとえば、*WMIClass* 名が **Win32_LogicalDisk** という形式の場合、生成されたクラスおよびファイルには "logicaldisk" という名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="18d50-134">For example, if the *WMIClass* name is in the format **Win32_LogicalDisk**, the generated class and file is named "logicaldisk".</span></span> <span data-ttu-id="18d50-135">ファイルが既に存在している場合は、既存のファイルが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="18d50-135">If a file already exists, the tool overwrites the existing file.</span></span>|  
|<span data-ttu-id="18d50-136">**/pw**  *password*</span><span class="sxs-lookup"><span data-stu-id="18d50-136">**/pw**  *password*</span></span>|<span data-ttu-id="18d50-137">**/m** オプションで指定したコンピューターにログオンするときに使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="18d50-137">Specifies the password to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="18d50-138">**/u**  *user name*</span><span class="sxs-lookup"><span data-stu-id="18d50-138">**/u**  *user name*</span></span>|<span data-ttu-id="18d50-139">**/m** オプションで指定したコンピューターにログオンするときに使用するユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="18d50-139">Specifies the user name to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="18d50-140">**/?**</span><span class="sxs-lookup"><span data-stu-id="18d50-140">**/?**</span></span>|<span data-ttu-id="18d50-141">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="18d50-141">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18d50-142">Remarks</span><span class="sxs-lookup"><span data-stu-id="18d50-142">Remarks</span></span>  

 <span data-ttu-id="18d50-143">Mgmtclassgen.exe は、<xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="18d50-143">Mgmtclassgen.exe uses the <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="18d50-144">したがって、任意のカスタム コード プロバイダーを使用して、C#、Visual Basic、および JScript 以外のマネージド言語でコードを生成できます。</span><span class="sxs-lookup"><span data-stu-id="18d50-144">Therefore, you can use any custom code provider to generate code in managed languages other than C#, Visual Basic, and JScript.</span></span>  
  
 <span data-ttu-id="18d50-145">生成されたクラスは、それらのクラスを生成する目的となったスキーマにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="18d50-145">Note that generated classes are bound to the schema for which they are generated.</span></span> <span data-ttu-id="18d50-146">基になるスキーマが変更された場合に、その変更をこのスキーマに反映するには、クラスを生成し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="18d50-146">If the underlying schema changes, you must regenerate the class if you want it to reflect changes to the schema.</span></span>  
  
 <span data-ttu-id="18d50-147">WMI CIM (Common Information Model) 型の、生成されたクラスのデータ型への割り当てを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="18d50-147">The following table shows how WMI Common Information Model (CIM) types map to data types in a generated class:</span></span>  
  
|<span data-ttu-id="18d50-148">CIM 型</span><span class="sxs-lookup"><span data-stu-id="18d50-148">CIM type</span></span>|<span data-ttu-id="18d50-149">生成したクラスのデータ型</span><span class="sxs-lookup"><span data-stu-id="18d50-149">Data type in the generated class</span></span>|  
|--------------|--------------------------------------|  
|<span data-ttu-id="18d50-150">CIM_SINT8</span><span class="sxs-lookup"><span data-stu-id="18d50-150">CIM_SINT8</span></span>|<span data-ttu-id="18d50-151">**SByte**</span><span class="sxs-lookup"><span data-stu-id="18d50-151">**SByte**</span></span>|  
|<span data-ttu-id="18d50-152">CIM_UINT8</span><span class="sxs-lookup"><span data-stu-id="18d50-152">CIM_UINT8</span></span>|<span data-ttu-id="18d50-153">**Byte**</span><span class="sxs-lookup"><span data-stu-id="18d50-153">**Byte**</span></span>|  
|<span data-ttu-id="18d50-154">CIM_SINT16</span><span class="sxs-lookup"><span data-stu-id="18d50-154">CIM_SINT16</span></span>|<span data-ttu-id="18d50-155">**Int16**</span><span class="sxs-lookup"><span data-stu-id="18d50-155">**Int16**</span></span>|  
|<span data-ttu-id="18d50-156">CIM_UINT16</span><span class="sxs-lookup"><span data-stu-id="18d50-156">CIM_UINT16</span></span>|<span data-ttu-id="18d50-157">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="18d50-157">**UInt16**</span></span>|  
|<span data-ttu-id="18d50-158">CIM_SINT32</span><span class="sxs-lookup"><span data-stu-id="18d50-158">CIM_SINT32</span></span>|<span data-ttu-id="18d50-159">**Int32**</span><span class="sxs-lookup"><span data-stu-id="18d50-159">**Int32**</span></span>|  
|<span data-ttu-id="18d50-160">SIM_UINT32</span><span class="sxs-lookup"><span data-stu-id="18d50-160">SIM_UINT32</span></span>|<span data-ttu-id="18d50-161">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="18d50-161">**UInt32**</span></span>|  
|<span data-ttu-id="18d50-162">CIM_SINT64</span><span class="sxs-lookup"><span data-stu-id="18d50-162">CIM_SINT64</span></span>|<span data-ttu-id="18d50-163">**Int64**</span><span class="sxs-lookup"><span data-stu-id="18d50-163">**Int64**</span></span>|  
|<span data-ttu-id="18d50-164">CIM_UINT64</span><span class="sxs-lookup"><span data-stu-id="18d50-164">CIM_UINT64</span></span>|<span data-ttu-id="18d50-165">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="18d50-165">**UInt64**</span></span>|  
|<span data-ttu-id="18d50-166">CIM_REAL32</span><span class="sxs-lookup"><span data-stu-id="18d50-166">CIM_REAL32</span></span>|<span data-ttu-id="18d50-167">**Single**</span><span class="sxs-lookup"><span data-stu-id="18d50-167">**Single**</span></span>|  
|<span data-ttu-id="18d50-168">CIM_REAL64</span><span class="sxs-lookup"><span data-stu-id="18d50-168">CIM_REAL64</span></span>|<span data-ttu-id="18d50-169">**Double**</span><span class="sxs-lookup"><span data-stu-id="18d50-169">**Double**</span></span>|  
|<span data-ttu-id="18d50-170">CIM_BOOLEAN</span><span class="sxs-lookup"><span data-stu-id="18d50-170">CIM_BOOLEAN</span></span>|<span data-ttu-id="18d50-171">**Boolean**</span><span class="sxs-lookup"><span data-stu-id="18d50-171">**Boolean**</span></span>|  
|<span data-ttu-id="18d50-172">CIM_String</span><span class="sxs-lookup"><span data-stu-id="18d50-172">CIM_String</span></span>|<span data-ttu-id="18d50-173">**String**</span><span class="sxs-lookup"><span data-stu-id="18d50-173">**String**</span></span>|  
|<span data-ttu-id="18d50-174">CIM_DATETIME</span><span class="sxs-lookup"><span data-stu-id="18d50-174">CIM_DATETIME</span></span>|<span data-ttu-id="18d50-175">**DateTime** または **TimeSpan**</span><span class="sxs-lookup"><span data-stu-id="18d50-175">**DateTime** or **TimeSpan**</span></span>|  
|<span data-ttu-id="18d50-176">CIM_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="18d50-176">CIM_REFERENCE</span></span>|<span data-ttu-id="18d50-177">**ManagementPath**</span><span class="sxs-lookup"><span data-stu-id="18d50-177">**ManagementPath**</span></span>|  
|<span data-ttu-id="18d50-178">CIM_CHAR16</span><span class="sxs-lookup"><span data-stu-id="18d50-178">CIM_CHAR16</span></span>|<span data-ttu-id="18d50-179">**Char**</span><span class="sxs-lookup"><span data-stu-id="18d50-179">**Char**</span></span>|  
|<span data-ttu-id="18d50-180">CIM_OBJECT</span><span class="sxs-lookup"><span data-stu-id="18d50-180">CIM_OBJECT</span></span>|<span data-ttu-id="18d50-181">**ManagementBaseObject**</span><span class="sxs-lookup"><span data-stu-id="18d50-181">**ManagementBaseObject**</span></span>|  
|<span data-ttu-id="18d50-182">CIM_IUNKNOWN</span><span class="sxs-lookup"><span data-stu-id="18d50-182">CIM_IUNKNOWN</span></span>|<span data-ttu-id="18d50-183">**オブジェクト**</span><span class="sxs-lookup"><span data-stu-id="18d50-183">**Object**</span></span>|  
|<span data-ttu-id="18d50-184">CIM_ARRAY</span><span class="sxs-lookup"><span data-stu-id="18d50-184">CIM_ARRAY</span></span>|<span data-ttu-id="18d50-185">上記のオブジェクトの配列</span><span class="sxs-lookup"><span data-stu-id="18d50-185">Array of the above mentioned objects</span></span>|  
  
 <span data-ttu-id="18d50-186">WMI クラスを生成する場合は、次の動作に注意してください｡</span><span class="sxs-lookup"><span data-stu-id="18d50-186">Note the following behaviors when you generate a WMI class:</span></span>  
  
- <span data-ttu-id="18d50-187">標準パブリック プロパティまたはメソッドの名前と既存のプロパティまたはメソッドの名前が同じになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="18d50-187">It is possible for a standard public property or method to have the same name as an existing property or method.</span></span> <span data-ttu-id="18d50-188">このような事態が発生した場合、このツールは生成したクラスのプロパティまたはメソッドの名前を変更して、名前付けの競合を回避します。</span><span class="sxs-lookup"><span data-stu-id="18d50-188">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
- <span data-ttu-id="18d50-189">生成したクラスのプロパティまたはメソッドの名前がプログラミング言語のキーワード名と同じになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="18d50-189">It is possible for the name of a property or method in a generated class to be a keyword in the target programming language.</span></span> <span data-ttu-id="18d50-190">このような事態が発生した場合、このツールは生成したクラスのプロパティまたはメソッドの名前を変更して、名前付けの競合を回避します。</span><span class="sxs-lookup"><span data-stu-id="18d50-190">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
- <span data-ttu-id="18d50-191">WMI では、修飾子は、クラス、インスタンス、プロパティ、またはメソッドを説明する情報を含む修飾子となります。</span><span class="sxs-lookup"><span data-stu-id="18d50-191">In WMI, qualifiers are modifiers that contain information to describe a class, instance, property, or method.</span></span> <span data-ttu-id="18d50-192">WMI は、**Read**、**Write**、**Key** などの標準の修飾子を使用して、生成したクラスのプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="18d50-192">WMI uses standard qualifiers such as **Read**, **Write**, and **Key** to describe a property in a generated class.</span></span> <span data-ttu-id="18d50-193">たとえば、**Read** 修飾子で修飾されたプロパティは、生成したクラスではプロパティ **get** アクセサーだけを伴って定義されます。</span><span class="sxs-lookup"><span data-stu-id="18d50-193">For example, a property that is modified with a **Read** qualifier is defined only with a property **get** accessor in the generated class.</span></span> <span data-ttu-id="18d50-194">**Read** 修飾子でマークされたプロパティは読み取り専用であるため、**set** アクセサーは定義されません。</span><span class="sxs-lookup"><span data-stu-id="18d50-194">Because a property marked with the **Read** qualifier is intended to be read-only, a **set** accessor is not defined.</span></span>  
  
- <span data-ttu-id="18d50-195">数値プロパティを **Values** 修飾子および **ValueMaps** 修飾子によって修飾すると、このプロパティには、指定した許容値しか設定できないことを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="18d50-195">A numeric property can be modified by the **Values** and **ValueMaps** qualifiers to indicate that the property can be set only to specified permissible values.</span></span> <span data-ttu-id="18d50-196">列挙体は、このような **Values** および **ValueMaps** を使用して生成され、このプロパティは列挙体に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="18d50-196">An enumeration is generated with these **Values** and **ValueMaps** and the property is mapped to the enumeration.</span></span>  
  
- <span data-ttu-id="18d50-197">WMI では、インスタンスを 1 つだけを持つことのできるクラスを説明するために、シングルトンという用語を使用します。</span><span class="sxs-lookup"><span data-stu-id="18d50-197">The WMI uses the term singleton to describe a class that can have only one instance.</span></span> <span data-ttu-id="18d50-198">したがって、シングルトン クラスのパラメーターなしのコンストラクターは、クラスをそのクラスの唯一のインスタンスに初期化します。</span><span class="sxs-lookup"><span data-stu-id="18d50-198">Therefore, the parameterless constructor for a singleton class will initialize the class to the only instance of the class.</span></span>  
  
- <span data-ttu-id="18d50-199">WMI クラスは、オブジェクトであるプロパティを持つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="18d50-199">A WMI class can have properties that are objects.</span></span> <span data-ttu-id="18d50-200">そのような型の WMI クラスに対して、厳密に型指定されたクラスを生成する場合は、埋め込まれたオブジェクト プロパティの型それぞれに対して厳密に型指定されたクラスを生成することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="18d50-200">When you generate a strongly typed class for this type of WMI class, you should consider generating strongly typed classes for the types of the embedded object properties.</span></span> <span data-ttu-id="18d50-201">これにより、厳密に型指定する方法で、埋め込まれたオブジェクトにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="18d50-201">This will allow you to access the embedded objects in a strongly typed manner.</span></span> <span data-ttu-id="18d50-202">生成されたコードが、埋め込まれたオブジェクトの型を検出できない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="18d50-202">Note that the generated code might not be able to detect the type of the embedded object.</span></span> <span data-ttu-id="18d50-203">このような場合は、生成されたコード内に、その旨をユーザーに通知するコメントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="18d50-203">In this case, a comment will be created in the generated code to notify you of this issue.</span></span> <span data-ttu-id="18d50-204">これに応じて、生成された他のクラスをプロパティの型として指定するように、生成したコードを変更できます。</span><span class="sxs-lookup"><span data-stu-id="18d50-204">You can then modify the generated code to type the property to the other generated class.</span></span>  
  
- <span data-ttu-id="18d50-205">WMI では、CIM_DATETIME データ型のデータ値は、特定の日時または時間間隔を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="18d50-205">In WMI, the data value of the CIM_DATETIME data type can represent either a specific date and time or a time interval.</span></span> <span data-ttu-id="18d50-206">データ値が日時を表す場合、生成されたクラスのデータ型は **DateTime** です。</span><span class="sxs-lookup"><span data-stu-id="18d50-206">If the data value represents a date and time, the data type in the generated class is **DateTime**.</span></span> <span data-ttu-id="18d50-207">データ値が時間間隔を表す場合、生成されたクラスのデータ型は **TimeSpan** です。</span><span class="sxs-lookup"><span data-stu-id="18d50-207">If the data value represents a time interval, the data type in the generated class is **TimeSpan**.</span></span>  
  
 <span data-ttu-id="18d50-208">Visual Studio .NET のサーバー エクスプローラー管理拡張機能を使用して、厳密に型指定されたクラスを生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="18d50-208">You can alternately generate a strongly typed class using the Server Explorer Management Extension in Visual Studio .NET.</span></span>  
  
 <span data-ttu-id="18d50-209">WMI の詳細については、プラットフォーム SDK の「**Windows Management Instrumentation**」のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="18d50-209">For more information about WMI, see the **Windows Management Instrumentation** topic in the Platform SDK documentation.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="18d50-210">使用例</span><span class="sxs-lookup"><span data-stu-id="18d50-210">Examples</span></span>  

 <span data-ttu-id="18d50-211">**Root\cimv2** 名前空間内の **Win32_LogicalDisk** WMI クラスに対してマネージド クラスを C# コードで生成するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="18d50-211">The following command generates a managed class in C# code for the **Win32_LogicalDisk** WMI class in the **Root\cimv2** namespace.</span></span> <span data-ttu-id="18d50-212">このツールは、**ROOT.CIMV2.Win32** 名前空間内の c:\disk.cs にあるソース ファイルにマネージド クラスを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="18d50-212">The tool writes the managed class to the source file at c:\disk.cs in the **ROOT.CIMV2.Win32** namespace.</span></span>  
  
```console  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 <span data-ttu-id="18d50-213">生成したクラスをプログラムによって使用する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="18d50-213">The following code example shows how to use a generated class programmatically.</span></span> <span data-ttu-id="18d50-214">まず、クラスのインスタンスが列挙され、パスが出力されます。</span><span class="sxs-lookup"><span data-stu-id="18d50-214">First, an instance of the class is enumerated and the path is printed.</span></span> <span data-ttu-id="18d50-215">次に、初期化の対象となる生成したクラスのインスタンスが、WMI のインスタンスを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="18d50-215">Next, an instance of the generated class to be initialized is created with an instance of WMI.</span></span> <span data-ttu-id="18d50-216">**Root\cimv2** 名前空間において `Process` は **Win32_Process** に対して生成されたクラスであり、`LogicalDisk` は **Win32_LogicalDisk** に対して生成されたクラスです。</span><span class="sxs-lookup"><span data-stu-id="18d50-216">`Process` is the class generated for **Win32_Process** and `LogicalDisk` is the class generated for **Win32_LogicalDisk** in the **Root\cimv2** namespace.</span></span>  
  
```vb  
Imports System  
Imports System.Management  
Imports ROOT.CIMV2.Win32  
  
Public Class App
   Public Shared Sub Main()
      ' Enumerate instances of the Win32_process.  
      ' Print the Name property of the instance.  
      Dim ps As Process
      For Each ps In  Process.GetInstances()  
         Console.WriteLine(ps.Name)  
      Next ps  
  
      ' Initialize the instance of LogicalDisk with  
      ' the WMI instance pointing to logical drive d:.  
      Dim dskD As New LogicalDisk(New _  
         ManagementPath("win32_LogicalDisk.DeviceId=""d:"""))  
      Console.WriteLine(dskD.Caption)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Management;  
using ROOT.CIMV2.Win32;  
  
public class App  
{  
   public static void Main()  
   {  
      // Enumerate instances of the Win32_process.  
      // Print the Name property of the instance.  
      foreach(Process ps in Process.GetInstances())  
      {  
         Console.WriteLine(ps.Name);  
      }  
  
      // Initialize the instance of LogicalDisk with  
      // the WMI instance pointing to logical drive d:.  
      LogicalDisk dskD = new LogicalDisk(new ManagementPath(  
        "win32_LogicalDisk.DeviceId=\"d:\""));  
      Console.WriteLine(dskD.Caption);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="18d50-217">関連項目</span><span class="sxs-lookup"><span data-stu-id="18d50-217">See also</span></span>

- <xref:System.Management>
- <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>
- <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>
- [<span data-ttu-id="18d50-218">ツール</span><span class="sxs-lookup"><span data-stu-id="18d50-218">Tools</span></span>](index.md)
- [<span data-ttu-id="18d50-219">開発者コマンドライン シェル</span><span class="sxs-lookup"><span data-stu-id="18d50-219">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
