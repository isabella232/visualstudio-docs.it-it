---
title: 'CA2100: Controllare la vulnerabilità della sicurezza nelle query SQL'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bbfafb78022e462c1f629019ddb40c711fcd581b
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551467"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: Controllare la vulnerabilità della sicurezza nelle query SQL

|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|Category|Microsoft.Security|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Imposta un metodo di <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> proprietà usando una stringa che viene creata da un argomento di stringa al metodo.

## <a name="rule-description"></a>Descrizione della regola

La regola presuppone che l'argomento stringa contenga l'input dell'utente. Una stringa di comando SQL compilata da un input dell'utente è vulnerabile agli attacchi intrusivi nel codice SQL, In un attacco SQL injection, un utente malintenzionato fornisce un input che modifica la progettazione di una query nel tentativo di danneggiare o accesso non autorizzato al database sottostante. Tecniche tipiche includono l'inserimento di una virgoletta singola o un apostrofo, ovvero il delimitatore di stringa letterale SQL; due trattini, che indica un commento SQL; e un punto e virgola, che indica che un nuovo comando segue. Se l'input dell'utente deve essere parte della query, usare uno dei seguenti, elencate in ordine di efficienza, per ridurre il rischio di attacco.

- Usare una stored procedure.

- Usare una stringa di comando con parametri.

- Convalidare l'input dell'utente per tipo sia il contenuto prima di compilare la stringa di comando.

Quanto segue [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] tipi implementano il <xref:System.Data.IDbCommand.CommandText%2A> proprietà o fornire costruttori che impostare la proprietà con un argomento di tipo stringa.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> e <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> e <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> e <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> e <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

Si noti che questa regola viene violata quando viene utilizzato il metodo ToString di un tipo esplicito o implicito per costruire la stringa di query. Di seguito è riportato un esempio.

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 La regola viene violata perché un utente malintenzionato può sostituire il metodo ToString ().

 Inoltre, la regola viene violata quando ToString viene utilizzato in modo implicito.

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, usare una query con parametri.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola se il testo del comando non contiene alcun input utente.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo, `UnsafeQuery`, che viola la regola e un metodo, `SaferQuery`, che soddisfa la regola con una stringa di comando con parametri.

 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]

## <a name="see-also"></a>Vedere anche
 [Panoramica della sicurezza](/dotnet/framework/data/adonet/security-overview)