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
ms.openlocfilehash: b81bd810bac142bdec23074e69bbd3840043c8f6
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841396"
---
# <a name="ca3003-review-code-for-file-path-injection-vulnerabilities"></a>CA3003: Esaminare il codice per verificare la presenza di vulnerabilità di tipo file path injection

|||
|-|-|
|TypeName|ReviewCodeForFilePathInjectionVulnerabilities|
|CheckId|CA3003|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Input della richiesta HTTP potenzialmente non attendibili raggiunge il percorso di un'operazione di file.

## <a name="rule-description"></a>Descrizione della regola

Quando si lavora con input non attendibile dalle richieste web, tenere usando input controllata dall'utente quando si specificano i percorsi dei file. Un utente malintenzionato potrebbe essere in grado di leggere un file indesiderato, causando la diffusione di informazioni dei dati sensibili. In alternativa, un utente malintenzionato potrebbe essere in grado di scrivere in un file indesiderato, causando la modifica non autorizzata dei dati sensibili o compromettere la sicurezza del server. È una tecnica comune di attacco [Path Traversal](https://www.owasp.org/index.php/Path_Traversal) per accedere ai file all'esterno della directory desiderata.

Questa regola cerca di trovare input dalle richieste HTTP raggiungere un percorso in un'operazione di file.

> [!NOTE]
> Questa regola non è possibile tenere traccia dei dati tra gli assembly. Ad esempio, se un unico assembly legge l'input della richiesta HTTP e quindi lo si passa a un altro assembly che scrive in un file, questa regola non genera un avviso.

> [!NOTE]
> È previsto un limite configurabile per il livello di profondità questa regola analizza il flusso di dati durante le chiamate di metodo. Visualizzare [configurazione dell'analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) per informazioni su come configurare il limite in un file con estensione EditorConfig.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

- Se possibile, limitare i percorsi di file basati sull'input dell'utente a un elenco di elementi attendibili noto in modo esplicito.  Ad esempio, se l'applicazione deve solo accedere "red.txt", "green.txt" o "blue.txt", consentire solo tali valori.
- Verificare la presenza di nomi di file non attendibili e verificare che il nome sia ben formato.
- Usare nomi di percorso completi quando si specificano i percorsi.
- Evitare costrutti potenzialmente pericolosi come variabili di ambiente path.
- Accettano nomi file lunghi e convalidare nomi lunghi, se l'utente invia i nomi brevi.
- Limitare l'input dell'utente finale per i caratteri validi.
- Rifiutare i nomi in cui superamento della lunghezza MAX_PATH.
- Gestire i nomi di file in modo letterale, senza interpretazione.
- Determinare se il nome file rappresenta un file o un dispositivo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Se si è verificato l'input come descritto nella sezione precedente, è possibile eliminare l'avviso.

## <a name="pseudo-code-examples"></a>Esempi di pseudocodice

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
