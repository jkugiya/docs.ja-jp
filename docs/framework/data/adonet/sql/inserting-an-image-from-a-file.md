---
description: '詳細情報: ファイルからの画像の挿入'
title: ファイルからの画像の挿入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 35900aa2-5615-4174-8212-ba184c6b82fb
ms.openlocfilehash: 009b652988a6ce5dc532d3af926f865f7fc806e0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663197"
---
# <a name="inserting-an-image-from-a-file"></a><span data-ttu-id="065af-103">ファイルからの画像の挿入</span><span class="sxs-lookup"><span data-stu-id="065af-103">Inserting an Image from a File</span></span>

<span data-ttu-id="065af-104">データ ソースのフィールドの型に応じて、バイナリ データまたは文字データとして、BLOB (バイナリ ラージ オブジェクト) をデータベースに書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="065af-104">You can write a binary large object (BLOB) to a database as either binary or character data, depending on the type of field at your data source.</span></span> <span data-ttu-id="065af-105">BLOB は `text`、`ntext`、および `image` データ型を示す一般的な用語であり、通常ドキュメントとピクチャが含まれています。</span><span class="sxs-lookup"><span data-stu-id="065af-105">BLOB is a generic term that refers to the `text`, `ntext`, and `image` data types, which typically contain documents and pictures.</span></span>  
  
 <span data-ttu-id="065af-106">BLOB 値をデータベースに書き込むには、適切な INSERT または UPDATE ステートメントを実行し、入力パラメーターとして BLOB 値を渡します (「[パラメーターおよびパラメーター データ型の構成](../configuring-parameters-and-parameter-data-types.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="065af-106">To write a BLOB value to your database, issue the appropriate INSERT or UPDATE statement and pass the BLOB value as an input parameter (see [Configuring Parameters and Parameter Data Types](../configuring-parameters-and-parameter-data-types.md)).</span></span> <span data-ttu-id="065af-107">BLOB が、SQL Server の `text` フィールドなどのようにテキストとして格納される場合は、文字列パラメーターとして BLOB を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="065af-107">If your BLOB is stored as text, such as a SQL Server `text` field, you can pass the BLOB as a string parameter.</span></span> <span data-ttu-id="065af-108">BLOB を SQL Server `image` フィールドなどのバイナリ形式で格納する場合は、`byte` 型の配列をバイナリ パラメーターとして渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="065af-108">If the BLOB is stored in binary format, such as a SQL Server `image` field, you can pass an array of type `byte` as a binary parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="065af-109">例</span><span class="sxs-lookup"><span data-stu-id="065af-109">Example</span></span>  

 <span data-ttu-id="065af-110">次のコード例では、Northwind データベースの Employees テーブルに従業員情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="065af-110">The following code example adds employee information to the Employees table in the Northwind database.</span></span> <span data-ttu-id="065af-111">従業員の写真がファイルから読み取られ、テーブルの Photo フィールド (イメージ フィールド) に追加されます。</span><span class="sxs-lookup"><span data-stu-id="065af-111">A photo of the employee is read from a file and added to the Photo field in the table, which is an image field.</span></span>  
  
```vb  
Public Shared Sub AddEmployee( _  
  lastName As String, _  
  firstName As String, _  
  title As String, _  
  hireDate As DateTime, _  
  reportsTo As Integer, _  
  photoFilePath As String, _  
  connectionString As String)  
  
  Dim photo() as Byte = GetPhoto(photoFilePath)  
  
  Using connection As SqlConnection = New SqlConnection( _  
    connectionString)  
  
  Dim command As SqlCommand = New SqlCommand( _  
    "INSERT INTO Employees (LastName, FirstName, Title, " & _  
    "HireDate, ReportsTo, Photo) " & _  
    "Values(@LastName, @FirstName, @Title, " & _  
    "@HireDate, @ReportsTo, @Photo)", connection)
  
  command.Parameters.Add("@LastName",  _  
    SqlDbType.NVarChar, 20).Value = lastName  
  command.Parameters.Add("@FirstName", _  
    SqlDbType.NVarChar, 10).Value = firstName  
  command.Parameters.Add("@Title", _  
    SqlDbType.NVarChar, 30).Value = title  
  command.Parameters.Add("@HireDate", _  
    SqlDbType.DateTime).Value = hireDate  
  command.Parameters.Add("@ReportsTo", _  
    SqlDbType.Int).Value = reportsTo  
  
  command.Parameters.Add("@Photo", _  
    SqlDbType.Image, photo.Length).Value = photo  
  
  connection.Open()  
  command.ExecuteNonQuery()  
  
  End Using  
End Sub  
  
Public Shared Function GetPhoto(filePath As String) As Byte()  
  Dim stream As FileStream = new FileStream( _  
     filePath, FileMode.Open, FileAccess.Read)  
  Dim reader As BinaryReader = new BinaryReader(stream)  
  
  Dim photo() As Byte = reader.ReadBytes(stream.Length)  
  
  reader.Close()  
  stream.Close()  
  
  Return photo  
End Function  
```  
  
```csharp  
public static void AddEmployee(  
  string lastName,
  string firstName,
  string title,
  DateTime hireDate,
  int reportsTo,
  string photoFilePath,
  string connectionString)  
{  
  byte[] photo = GetPhoto(photoFilePath);  
  
  using (SqlConnection connection = new SqlConnection(  
    connectionString))  
  
  SqlCommand command = new SqlCommand(  
    "INSERT INTO Employees (LastName, FirstName, " +  
    "Title, HireDate, ReportsTo, Photo) " +  
    "Values(@LastName, @FirstName, @Title, " +  
    "@HireDate, @ReportsTo, @Photo)", connection);
  
  command.Parameters.Add("@LastName",
     SqlDbType.NVarChar, 20).Value = lastName;  
  command.Parameters.Add("@FirstName",
      SqlDbType.NVarChar, 10).Value = firstName;  
  command.Parameters.Add("@Title",
      SqlDbType.NVarChar, 30).Value = title;  
  command.Parameters.Add("@HireDate",
       SqlDbType.DateTime).Value = hireDate;  
  command.Parameters.Add("@ReportsTo",
      SqlDbType.Int).Value = reportsTo;  
  
  command.Parameters.Add("@Photo",  
      SqlDbType.Image, photo.Length).Value = photo;  
  
  connection.Open();  
  command.ExecuteNonQuery();  
  }  
}  
  
public static byte[] GetPhoto(string filePath)  
{  
  FileStream stream = new FileStream(  
      filePath, FileMode.Open, FileAccess.Read);  
  BinaryReader reader = new BinaryReader(stream);  
  
  byte[] photo = reader.ReadBytes((int)stream.Length);  
  
  reader.Close();  
  stream.Close();  
  
  return photo;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="065af-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="065af-112">See also</span></span>

- [<span data-ttu-id="065af-113">コマンドを使用したデータ変更</span><span class="sxs-lookup"><span data-stu-id="065af-113">Using Commands to Modify Data</span></span>](../using-commands-to-modify-data.md)
- [<span data-ttu-id="065af-114">バイナリ データの取得</span><span class="sxs-lookup"><span data-stu-id="065af-114">Retrieving Binary Data</span></span>](../retrieving-binary-data.md)
- [<span data-ttu-id="065af-115">SQL Server のバイナリ データと大きな値のデータ</span><span class="sxs-lookup"><span data-stu-id="065af-115">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="065af-116">SQL Server データ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="065af-116">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="065af-117">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="065af-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
