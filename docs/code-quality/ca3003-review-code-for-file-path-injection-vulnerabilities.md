---
title: 'CA3003: Esaminare il codice per verificare la presenza di vulnerabilità di tipo file path injection'
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
ms.openlocfilehash: c9e43dcdf1e923cb7bc4a98b17fd0be71b7927eb
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237405"
---
# <a name="ca3003-review-code-for-file-path-injection-vulnerabilities"></a>CA3003: Esaminare il codice per verificare la presenza di vulnerabilità di tipo file path injection

|||
|-|-|
|TypeName|ReviewCodeForFilePathInjectionVulnerabilities|
|CheckId|CA3003|
|Category|Microsoft.Security|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un input di richiesta HTTP potenzialmente non attendibile raggiunge il percorso di un'operazione su file.

## <a name="rule-description"></a>Descrizione della regola

Quando si utilizza un input non attendibile da richieste Web, tenere presente l'utilizzo dell'input controllato dall'utente quando si specificano i percorsi dei file. Un utente malintenzionato potrebbe essere in grado di leggere un file imprevisto, causando la divulgazione di dati sensibili. In alternativa, un utente malintenzionato potrebbe essere in grado di scrivere in un file non intenzionale, causando la modifica non autorizzata dei dati sensibili o compromettendo la sicurezza del server. Una tecnica di attacco comune è l' [attraversamento del percorso](https://www.owasp.org/index.php/Path_Traversal) per accedere ai file all'esterno della directory desiderata.

Questa regola tenta di trovare l'input da richieste HTTP che raggiungono un percorso in un'operazione su file.

> [!NOTE]
> Questa regola non è in grado di rilevare i dati tra gli assembly. Se, ad esempio, un assembly legge l'input della richiesta HTTP e lo passa a un altro assembly che scrive in un file, questa regola non genera un avviso.

> [!NOTE]
> Esiste un limite configurabile per il livello di profondità con cui questa regola analizzerà il flusso di dati tra le chiamate al metodo. Per informazioni su come configurare il limite in un file EditorConfig, vedere la pagina relativa alla [configurazione dell'analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

- Se possibile, limitare i percorsi di file in base all'input dell'utente a un elenco sicuro noto in modo esplicito.  Ad esempio, se l'applicazione deve solo accedere a "Red. txt", "Green. txt" o "Blue. txt", consentire solo questi valori.
- Verificare la presenza di nomi file non attendibili e verificare che il nome sia ben formato.
- Usare nomi di percorso completi quando si specificano i percorsi.
- Evitare costrutti potenzialmente pericolosi, ad esempio le variabili di ambiente Path.
- Accettare solo nomi di file lunghi e convalidare il nome lungo se l'utente invia nomi brevi.
- Limitare l'input dell'utente finale a caratteri validi.
- Rifiutare i nomi in cui viene superata la lunghezza di MAX_PATH.
- Gestire i nomi di file letteralmente, senza interpretare.
- Determinare se il nome file rappresenta un file o un dispositivo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Se l'input è stato convalidato come descritto nella sezione precedente, è possibile evitare di visualizzare questo avviso.

## <a name="pseudo-code-examples"></a>Esempi di pseudo-codice

### <a name="violation"></a>Violazione

```csharp
using System;
using System.IO;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string userInput = Request.Params["UserInput"];
        // Assume the following directory structure:
        //   wwwroot\currentWebDirectory\user1.txt
        //   wwwroot\currentWebDirectory\user2.txt
        //   wwwroot\secret\allsecrets.txt
        // There is nothing wrong if the user inputs:
        //   user1.txt
        // However, if the user input is:
        //   ..\secret\allsecrets.txt
        // Then an attacker can now see all the secrets.

        // Avoid this:
        using (File.Open(userInput, FileMode.Open))
        {
            // Read a file with the name supplied by user
            // Input through request's query string and display
            // The content to the webpage.
        }
    }
}
```

```vb
Imports System
Imports System.IO

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim userInput As String = Me.Request.Params("UserInput")
        ' Assume the following directory structure:
        '   wwwroot\currentWebDirectory\user1.txt
        '   wwwroot\currentWebDirectory\user2.txt
        '   wwwroot\secret\allsecrets.txt
        ' There is nothing wrong if the user inputs:
        '   user1.txt
        ' However, if the user input is:
        '   ..\secret\allsecrets.txt
        ' Then an attacker can now see all the secrets.

        ' Avoid this:
        Using File.Open(userInput, FileMode.Open)
            ' Read a file with the name supplied by user
            ' Input through request's query string and display
            ' The content to the webpage.
        End Using
    End Sub
End Class
```
