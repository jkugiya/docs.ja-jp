---
description: '詳細情報: 方法:XML ファイルからオブジェクト データを読み込む (Visual Basic)'
title: '方法: XML ファイルからオブジェクト データを読み込む'
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: d281997a0dd96ad6263fe03cea84b3e84005a3ad
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100486824"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="cfcb0-103">方法: XML ファイルからオブジェクト データを読み込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cfcb0-103">How to: Read Object Data from an XML File (Visual Basic)</span></span>

<span data-ttu-id="cfcb0-104">次の例では、<xref:System.Xml.Serialization.XmlSerializer> クラスを使用して、XML ファイルに以前に書き込まれたオブジェクト データを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="cfcb0-104">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfcb0-105">例</span><span class="sxs-lookup"><span data-stu-id="cfcb0-105">Example</span></span>  
  
```vb  
Public Class Book  
    Public Title As String  
End Class  
  
Public Sub ReadXML()  
    Dim reader As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
    Dim file As New System.IO.StreamReader(  
        "c:\temp\SerializationOverview.xml")  
    Dim overview As Book  
    overview = CType(reader.Deserialize(file), Book)  
    Console.WriteLine(overview.Title)  
End Sub  
```  
  
## <a name="compile-the-code"></a><span data-ttu-id="cfcb0-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="cfcb0-106">Compile the code</span></span>  

 <span data-ttu-id="cfcb0-107">ファイル名 "c:\temp\SerializationOverview.xml" を、シリアル化されたデータを含むファイルの名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="cfcb0-107">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="cfcb0-108">データのシリアル化の詳細については、「[方法:XML ファイルにオブジェクト データを書き込む (Visual Basic)](how-to-write-object-data-to-an-xml-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cfcb0-108">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="cfcb0-109">クラスには、パラメーターのないパブリック コンストラクターが必要です。</span><span class="sxs-lookup"><span data-stu-id="cfcb0-109">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="cfcb0-110">パブリック プロパティとパブリック フィールドだけが逆シリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="cfcb0-110">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="cfcb0-111">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="cfcb0-111">Robust Programming</span></span>  

 <span data-ttu-id="cfcb0-112">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cfcb0-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="cfcb0-113">シリアル化されるクラスにパブリックなパラメーターなしのコンストラクターがない場合</span><span class="sxs-lookup"><span data-stu-id="cfcb0-113">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="cfcb0-114">ファイル内のデータが、逆シリアル化されるクラスのデータを表していない場合。</span><span class="sxs-lookup"><span data-stu-id="cfcb0-114">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="cfcb0-115">ファイルが存在しない (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="cfcb0-115">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="cfcb0-116">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="cfcb0-116">.NET Framework Security</span></span>  

 <span data-ttu-id="cfcb0-117">入力を常に検証し、信頼できないソースから決してデータを逆シリアル化しないでください。</span><span class="sxs-lookup"><span data-stu-id="cfcb0-117">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="cfcb0-118">再作成されたオブジェクトは、そのオブジェクトを逆シリアル化したコードと同じアクセス許可を持つローカル コンピューターで実行されます。</span><span class="sxs-lookup"><span data-stu-id="cfcb0-118">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="cfcb0-119">アプリケーションでデータを使用する前に、入力をすべて検証してください。</span><span class="sxs-lookup"><span data-stu-id="cfcb0-119">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfcb0-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="cfcb0-120">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="cfcb0-121">方法: XML ファイルにオブジェクト データを書き込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cfcb0-121">How to: Write Object Data to an XML File (Visual Basic)</span></span>](how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="cfcb0-122">シリアル化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cfcb0-122">Serialization (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="cfcb0-123">Visual Basic プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="cfcb0-123">Visual Basic Programming Guide</span></span>](../../index.md)
