---
title: 'CA3001: Esaminare il codice per verificare la presenza di vulnerabilità di tipo SQL injection'
ms.date: 04/03/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bd454ffad1efc9d7df84d88630fe71eebc8ca6fc
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238112"
---
# <a name="ca3001-review-code-for-sql-injection-vulnerabilities"></a>CA3001: Esaminare il codice per verificare la presenza di vulnerabilità di tipo SQL injection

|||
|-|-|
|TypeName|ReviewCodeForSqlInjectionsVulnerabilities|
|CheckId|CA3001|
|Category|Microsoft.Security|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un input di richiesta HTTP potenzialmente non attendibile raggiunge il testo di un comando SQL.

## <a name="rule-description"></a>Descrizione della regola

Quando si utilizzano comandi SQL e input non attendibili, tenere presenti gli attacchi SQL injection. Un attacco SQL injection può eseguire comandi SQL dannosi, compromettendo la sicurezza e l'integrità dell'applicazione. Le tecniche tipiche includono l'uso di una virgoletta singola o di un apostrofo per la delimitazione di stringhe letterali, due trattini per un commento e un punto e virgola per la fine di un'istruzione. Per altre informazioni, vedere [SQL injection](/sql/relational-databases/security/sql-injection).

Questa regola tenta di trovare l'input dalle richieste HTTP che raggiungono il testo di un comando SQL.

> [!NOTE]
> Questa regola non è in grado di rilevare i dati tra gli assembly. Se, ad esempio, un assembly legge l'input della richiesta HTTP e lo passa a un altro assembly che esegue il comando SQL, questa regola non genera un avviso.

> [!NOTE]
> Esiste un limite configurabile per il livello di profondità con cui questa regola analizzerà il flusso di dati tra le chiamate al metodo. Per informazioni su come configurare il limite in un file EditorConfig, vedere la pagina relativa alla [configurazione dell'analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Utilizzare comandi SQL con parametri o stored procedure con parametri contenenti l'input non attendibile.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola se si è certi che l'input viene sempre convalidato rispetto a un set di caratteri sicuro noto.

## <a name="pseudo-code-examples"></a>Esempi di pseudo-codice

### <a name="violation"></a>Violazione

```csharp
using System;
using System.Data;
using System.Data.SqlClient;

namespace TestNamespace
{
    public partial class WebForm : System.Web.UI.Page
    {
        public static string ConnectionString { get; set; }

        protected void Page_Load(object sender, EventArgs e)
        {
            string name = Request.Form["product_name"];
            using (SqlConnection connection = new SqlConnection(ConnectionString))
            {
                SqlCommand sqlCommand = new SqlCommand()
                {
                    CommandText = "SELECT ProductId FROM Products WHERE ProductName = '" + name + "'",
                    CommandType = CommandType.Text,
                };

                SqlDataReader reader = sqlCommand.ExecuteReader();
            }
        }
    }
}
```

```vb
Imports System
Imports System.Data
Imports System.Data.SqlClient
Imports System.Linq

Namespace VulnerableWebApp
    Partial Public Class WebForm
        Inherits System.Web.UI.Page

        Public Property ConnectionString As String

        Protected Sub Page_Load(sender As Object, e As EventArgs)
            Dim name As String = Me.Request.Form("product_name")
            Using connection As SqlConnection = New SqlConnection(ConnectionString)
                Dim sqlCommand As SqlCommand = New SqlCommand With {.CommandText = "SELECT ProductId FROM Products WHERE ProductName = '" + name + "'",
                                                                    .CommandType = CommandType.Text}
                Dim reader As SqlDataReader = sqlCommand.ExecuteReader()
            End Using
        End Sub
    End Class
End Namespace
```

### <a name="parameterized-solution"></a>Soluzione con parametri

```csharp
using System;
using System.Data;
using System.Data.SqlClient;

namespace TestNamespace
{
    public partial class WebForm : System.Web.UI.Page
    {
        public static string ConnectionString { get; set; }

        protected void Page_Load(object sender, EventArgs e)
        {
            string name = Request.Form["product_name"];
            using (SqlConnection connection = new SqlConnection(ConnectionString))
            {
                SqlCommand sqlCommand = new SqlCommand()
                {
                    CommandText = "SELECT ProductId FROM Products WHERE ProductName = @productName",
                    CommandType = CommandType.Text,
                };

                sqlCommand.Parameters.Add("@productName", SqlDbType.NVarChar, 128).Value = name;

                SqlDataReader reader = sqlCommand.ExecuteReader();
            }
        }
    }
}
```

```vb
Imports System
Imports System.Data
Imports System.Data.SqlClient
Imports System.Linq

Namespace VulnerableWebApp
    Partial Public Class WebForm
        Inherits System.Web.UI.Page

        Public Property ConnectionString As String

        Protected Sub Page_Load(sender As Object, e As EventArgs)
            Dim name As String = Me.Request.Form("product_name")
            Using connection As SqlConnection = New SqlConnection(ConnectionString)
                Dim sqlCommand As SqlCommand = New SqlCommand With {.CommandText = "SELECT ProductId FROM Products WHERE ProductName = @productName",
                                                                    .CommandType = CommandType.Text}
                sqlCommand.Parameters.Add("@productName", SqlDbType.NVarChar, 128).Value = name
                Dim reader As SqlDataReader = sqlCommand.ExecuteReader()
            End Using
        End Sub
    End Class
End Namespace
```

### <a name="stored-procedure-solution"></a>Soluzione stored procedure

```csharp
using System;
using System.Data;
using System.Data.SqlClient;

namespace TestNamespace
{
    public partial class WebForm : System.Web.UI.Page
    {
        public static string ConnectionString { get; set; }

        protected void Page_Load(object sender, EventArgs e)
        {
            string name = Request.Form["product_name"];
            using (SqlConnection connection = new SqlConnection(ConnectionString))
            {
                SqlCommand sqlCommand = new SqlCommand()
                {
                    CommandText = "sp_GetProductIdFromName",
                    CommandType = CommandType.StoredProcedure,
                };

                sqlCommand.Parameters.Add("@productName", SqlDbType.NVarChar, 128).Value = name;

                SqlDataReader reader = sqlCommand.ExecuteReader();
            }
        }
    }
}
```

```vb
Imports System
Imports System.Data
Imports System.Data.SqlClient
Imports System.Linq

Namespace VulnerableWebApp
    Partial Public Class WebForm
        Inherits System.Web.UI.Page

        Public Property ConnectionString As String

        Protected Sub Page_Load(sender As Object, e As EventArgs)
            Dim name As String = Me.Request.Form("product_name")
            Using connection As SqlConnection = New SqlConnection(ConnectionString)
                Dim sqlCommand As SqlCommand = New SqlCommand With {.CommandText = "sp_GetProductIdFromName",
                                                                    .CommandType = CommandType.StoredProcedure}
                sqlCommand.Parameters.Add("@productName", SqlDbType.NVarChar, 128).Value = name
                Dim reader As SqlDataReader = sqlCommand.ExecuteReader()
            End Using
        End Sub
    End Class
End Namespace
```
