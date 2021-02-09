---
description: '詳細情報: OracleTypes'
title: OracleTypes
ms.date: 03/30/2017
ms.assetid: 18143304-d5c7-4c95-9995-678088d0c142
ms.openlocfilehash: 5444fd8e9eec6172394bdca68ada38cf02e7c2c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672401"
---
# <a name="oracletypes"></a><span data-ttu-id="f8729-103">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="f8729-103">OracleTypes</span></span>

<span data-ttu-id="f8729-104">.NET Framework Data Provider for Oracle には、Oracle データ型で使用されるいくつかの構造体が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f8729-104">The .NET Framework Data Provider for Oracle includes several structures you can use to work with Oracle data types.</span></span> <span data-ttu-id="f8729-105">その中には、<xref:System.Data.OracleClient.OracleNumber> や <xref:System.Data.OracleClient.OracleString> があります。</span><span class="sxs-lookup"><span data-stu-id="f8729-105">These include <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8729-106">これらの構造体に関する詳細な一覧については、「<xref:System.Data.OracleClient>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8729-106">For a complete list of these structures, see <xref:System.Data.OracleClient>.</span></span>  
  
 <span data-ttu-id="f8729-107">C# の例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="f8729-107">The following C# examples:</span></span>  
  
- <span data-ttu-id="f8729-108">Oracle テーブルを作成し、データを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="f8729-108">Create an Oracle table and load it with data.</span></span>  
  
- <span data-ttu-id="f8729-109"><xref:System.Data.OracleClient.OracleDataReader> を使用してデータにアクセスし、いくつかの <xref:System.Data.OracleClient.OracleType> 構造体を使用してデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="f8729-109">Use an <xref:System.Data.OracleClient.OracleDataReader> to access the data, and use several <xref:System.Data.OracleClient.OracleType> structures to display the data.</span></span>  
  
## <a name="creating-an-oracle-table"></a><span data-ttu-id="f8729-110">Oracle テーブルの作成</span><span class="sxs-lookup"><span data-stu-id="f8729-110">Creating an Oracle Table</span></span>  

 <span data-ttu-id="f8729-111">この例では、Oracle テーブルを作成し、データを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="f8729-111">This example creates an Oracle table and loads it with data.</span></span> <span data-ttu-id="f8729-112">次の例を実行する前に、この例を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8729-112">You must run this example before running the next example.</span></span>  
  
```csharp  
public void Setup(string connectionString)  
   {  
   OracleConnection conn = new OracleConnection(connectionString);  
   try  
      {  
      conn.Open();  
      OracleCommand cmd = conn.CreateCommand();  
      cmd.CommandText ="CREATE TABLE OracleTypesTable " +  
        "(MyVarchar2 varchar2(3000),MyNumber number(28,4) " +  
        "PRIMARY KEY ,MyDate date, MyRaw raw(255))";  
      cmd.ExecuteNonQuery();  
      cmd.CommandText ="INSERT INTO OracleTypesTable VALUES " +  
        "( 'test', 2, to_date('2000-01-11 12:54:01','yyyy-mm-dd " +  
        "hh24:mi:ss'), '0001020304' )";  
      cmd.ExecuteNonQuery();  
      }  
   catch(Exception)  
   {  
   }  
   finally  
   {  
      conn.Close();  
   }  
}  
```  
  
## <a name="retrieving-data-from-the-oracle-table"></a><span data-ttu-id="f8729-113">Oracle テーブルからのデータの取得</span><span class="sxs-lookup"><span data-stu-id="f8729-113">Retrieving Data from the Oracle Table</span></span>  

 <span data-ttu-id="f8729-114">この例では、**OracleDataReader** を使用してデータにアクセスし、いくつかの **OracleType** 構造体を使用してデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="f8729-114">This example uses an **OracleDataReader** to access the data, and uses several **OracleType** structures to display the data.</span></span>  
  
```csharp  
public void ReadOracleTypesExample(string connectionString)  
   {  
   OracleConnection myConnection =
      new OracleConnection(connectionString);  
   myConnection.Open();  
   OracleCommand myCommand = myConnection.CreateCommand();  
  
   try  
      {  
      myCommand.CommandText = "SELECT * from OracleTypesTable";  
      OracleDataReader oracledatareader1 = myCommand.ExecuteReader();  
      oracledatareader1.Read();  
  
      //Using the oracle specific getters for each type is faster than  
      //using GetOracleValue.  
  
      //First column, MyVarchar2, is a VARCHAR2 data type in Oracle  
      //Server and maps to OracleString.  
      OracleString oraclestring1 =
        oracledatareader1.GetOracleString(0);  
      Console.WriteLine("OracleString " + oraclestring1.ToString());  
  
      //Second column, MyNumber, is a NUMBER data type in Oracle Server  
      //and maps to OracleNumber.  
      OracleNumber oraclenumber1 =
        oracledatareader1.GetOracleNumber(1);  
      Console.WriteLine("OracleNumber " + oraclenumber1.ToString());  
  
      //Third column, MyDate, is a DATA data type in Oracle Server  
      //and maps to OracleDateTime.  
      OracleDateTime oracledatetime1 =
        oracledatareader1.GetOracleDateTime(2);  
      Console.WriteLine("OracleDateTime " + oracledatetime1.ToString());  
  
      //Fourth column, MyRaw, is a RAW data type in Oracle Server and  
      //maps to OracleBinary.  
      OracleBinary oraclebinary1 =
        oracledatareader1.GetOracleBinary(3);  
      //Calling value on a null OracleBinary throws  
      //OracleNullValueException; therefore, check for a null value.  
      if (oraclebinary1.IsNull==false)  
      {  
         foreach(byte b in oraclebinary1.Value)  
         {  
            Console.WriteLine("byte " + b.ToString());  
         }  
      }  
      oracledatareader1.Close();  
   }  
   catch(Exception e)  
   {  
       Console.WriteLine(e.ToString());  
   }  
   finally  
   {  
       myConnection.Close();  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8729-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8729-115">See also</span></span>

- [<span data-ttu-id="f8729-116">Oracle および ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f8729-116">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="f8729-117">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="f8729-117">ADO.NET Overview</span></span>](ado-net-overview.md)
