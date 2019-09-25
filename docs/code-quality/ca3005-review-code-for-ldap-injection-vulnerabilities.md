---
title: 'CA3005: Esaminare il codice per verificare la presenza di vulnerabilità di tipo LDAP injection'
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
ms.openlocfilehash: c0c99d5d0adb145a061693f8a83b1f674e05eed4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237332"
---
# <a name="ca3005-review-code-for-ldap-injection-vulnerabilities"></a>CA3005: Esaminare il codice per verificare la presenza di vulnerabilità di tipo LDAP injection

|||
|-|-|
|TypeName|ReviewCodeForLdapInjectionVulnerabilities|
|CheckId|CA3005|
|Category|Microsoft.Security|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un input di richiesta HTTP potenzialmente non attendibile raggiunge un'istruzione LDAP.

## <a name="rule-description"></a>Descrizione della regola

Quando si lavora con un input non attendibile, tenere presente gli attacchi di inserimento Lightweight Directory Access Protocol (LDAP). Un utente malintenzionato può eseguire potenzialmente istruzioni LDAP dannose nelle directory delle informazioni. Le applicazioni che utilizzano l'input dell'utente per costruire istruzioni LDAP dinamiche per accedere ai servizi directory sono particolarmente vulnerabili.

Questa regola tenta di trovare l'input da richieste HTTP che raggiungono un'istruzione LDAP.

> [!NOTE]
> Questa regola non è in grado di rilevare i dati tra gli assembly. Se, ad esempio, un assembly legge l'input della richiesta HTTP e lo passa a un altro assembly che esegue un'istruzione LDAP, questa regola non genera un avviso.

> [!NOTE]
> Esiste un limite configurabile per il livello di profondità con cui questa regola analizzerà il flusso di dati tra le chiamate al metodo. Per informazioni su come configurare il limite in un file EditorConfig, vedere la pagina relativa alla [configurazione dell'analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per la parte di istruzioni LDAP controllata dall'utente, prendere in considerazione una delle seguenti operazioni:
- Consente solo un elenco sicuro di caratteri non speciali.
- Non consentire il carattere speciale
- Caratteri di escape speciali.

Per ulteriori informazioni, vedere il foglio informativo sulla [prevenzione dell'iniezione LDAP di OWASP](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/LDAP_Injection_Prevention_Cheat_Sheet.md) .

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Se si sa che l'input è stato convalidato o è stato preceduto da un carattere di escape sicuro, è possibile eliminarlo.

## <a name="pseudo-code-examples"></a>Esempi di pseudo-codice

### <a name="violation"></a>Violazione

```csharp
using System;
using System.DirectoryServices;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string userName = Request.Params["user"];
        string filter = "(uid=" + userName + ")";  // searching for the user entry

        // In this example, if we send the * character in the user parameter which will
        // result in the filter variable in the code to be initialized with (uid=*).
        // The resulting LDAP statement will make the server return any object that
        // contains a uid attribute.
        DirectorySearcher searcher = new DirectorySearcher(filter);
        SearchResultCollection results = searcher.FindAll();

        // Iterate through each SearchResult in the SearchResultCollection.
        foreach (SearchResult searchResult in results)
        {
            // ...
        }
    }
}
```

```vb
Imports System
Imports System.DirectoryServices

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(send As Object, e As EventArgs)
        Dim userName As String = Me.Request.Params(""user"")
        Dim filter As String = ""(uid="" + userName + "")""    ' searching for the user entry

        ' In this example, if we send the * character in the user parameter which will
        ' result in the filter variable in the code to be initialized with (uid=*).
        ' The resulting LDAP statement will make the server return any object that
        ' contains a uid attribute.
        Dim searcher As DirectorySearcher = new DirectorySearcher(filter)
        Dim results As SearchResultCollection = searcher.FindAll()

        ' Iterate through each SearchResult in the SearchResultCollection.
        For Each searchResult As SearchResult in results
            ' ...
        Next searchResult
    End Sub
End Class
```
