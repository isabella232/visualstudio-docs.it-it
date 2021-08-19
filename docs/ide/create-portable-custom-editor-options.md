---
title: Impostazioni EditorConfig
description: Informazioni su come aggiungere un file EditorConfig al progetto o alla codebase per applicare stili di codifica coerenti per tutti gli utenti che lavorano nella codebase.
ms.custom: SEO-VS-2020
ms.date: 09/02/2020
ms.topic: how-to
helpviewer_keywords:
- editorconfig [Visual Studio]
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: 6dee0f9dc003e91cdb8d2ba24fc0804d5df5ae54
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109513"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Creare impostazioni personalizzate e portabili per l'editor con EditorConfig

È possibile aggiungere un file EditorConfig al progetto o alla codebase per applicare stili di codifica coerenti per tutti gli utenti che lavorano nella codebase. Le impostazioni di EditorConfig hanno la precedenza sulle impostazioni dell'editor di testo di Visual Studio globali. Ciò significa che è possibile personalizzare ogni codebase in modo che vengano usate le impostazioni dell'editor di testo specifiche del progetto. È comunque possibile impostare preferenze personali per l'editor nella finestra di dialogo **Opzioni** di Visual Studio. Queste impostazioni si applicano ogni volta che si usa una codebase priva di file con estensione *editorconfig* o quando il file con estensione *editorconfig* non esegue l'override di un'impostazione specifica. Un esempio di tale preferenza è lo stile del rientro&mdash;caratteri di tabulazione o spazi.

Le impostazioni di EditorConfig sono supportate da numerosi editor di codice e molti ambienti IDE, tra cui Visual Studio. Si tratta di un componente portatile che viene trasferito con il codice ed è in grado di imporre stili di codice anche all'esterno di Visual Studio.

::: moniker range=">=vs-2019"

Quando si aggiunge un file EditorConfig al progetto in Visual Studio, le nuove righe di codice vengono formattate in base alle impostazioni editorConfig. La formattazione del codice esistente non viene modificata a meno che non venga eseguito uno dei comandi seguenti:

 - [Pulizia del](../ide/code-styles-and-code-cleanup.md) codice (**CTRL** + **K**, **CTRL** E ), che applica le impostazioni degli spazi vuoti, ad esempio lo stile del rientro e le impostazioni di stile del codice selezionate, ad esempio come ordinare + le `using` direttive.
 - **Modifica** > **Avanzate** > **Formatta documento** (o **CTRL** K , CTRL D nel profilo predefinito), che applica solo le impostazioni degli spazi vuoti, ad esempio lo stile +   +  di rientro.

 ::: moniker-end

::: moniker range="=vs-2017"

Quando si aggiunge un file EditorConfig al progetto in Visual Studio, le nuove righe di codice vengono formattate in base alle impostazioni editorConfig. La formattazione del codice esistente non viene modificata a meno che non si formatta il documento (**Modifica** documento in formato avanzato o  >    >   **CTRL** + **K**, **CTRL** + **D** nel profilo predefinito). La formattazione del documento influisce solo sulle impostazioni degli spazi vuoti, ad esempio lo stile del rientro, a meno che non sia stato configurato Formatta documento per [eseguire la pulizia aggiuntiva del codice.](../ide/code-styles-and-code-cleanup.md#apply-code-styles)

 ::: moniker-end

::: moniker range="vs-2017"

È possibile definire le impostazioni di EditorConfig che si desidera applicare con **Formatta documento** nella pagina delle opzioni [**Formattazione**](reference/options-text-editor-csharp-formatting.md#format-document-settings).

::: moniker-end

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [EditorConfig in Visual Studio per Mac](/visualstudio/mac/editorconfig).

## <a name="code-consistency"></a>Coerenza del codice

Le impostazioni nei file EditorConfig consentono di mantenere stili e impostazioni di codifica coerenti in una codebase, ad esempio stile di rientro, rientro di tabulazione, caratteri di fine riga, codifica e altro, indipendentemente dall'editor o dall'IDE in uso. Ad esempio, quando si scrive codice in C#, se la codebase ha una convenzione preferita in base alla quale i rientri sono sempre costituiti da cinque spazi, i documenti devono usare la codifica UTF-8 e ogni riga termina sempre con un CR/LF, è possibile configurare un file con estensione *editorconfig* a tale scopo.

Le convenzioni di codifica usate per i progetti personali possono essere diverse da quelle per i progetti del team. Si potrebbe ad esempio preferire che durante la scrittura di codice il rientro aggiunga un carattere di tabulazione. Il team, tuttavia, potrebbe preferire per il rientro quattro spazi anziché un carattere di tabulazione. I file di EditorConfig risolvono questo problema consentendo di predisporre una configurazione per ogni scenario.

Dato che le impostazioni si trovano all'interno di un file nella codebase, seguono quest'ultima nei suoi spostamenti. Quando il file di codice viene aperto, le impostazioni dell'editor di testo vengono implementate, a condizione che l'editor sia compatibile con EditorConfig. Per altre informazioni sui file di EditorConfig, vedere il sito Web [EditorConfig.org](https://editorconfig.org/).

> [!NOTE]
> Attualmente non è possibile applicare convenzioni impostate in un file EditorConfig in una pipeline CI/CD come errori o avvisi di compilazione. Tutte le deviazioni di stile vengono visualizzate solo nell'editor di Visual Studio e in **Elenco errori**.

## <a name="supported-settings"></a>Impostazioni supportate

L'editor in Visual Studio supporta il set di base delle [proprietà di EditorConfig](https://editorconfig.org/#supported-properties):

- indent_style
- indent_size
- tab_width
- end\_of_line
- charset
- trim\_trailing_whitespace
- insert\_final_newline
- root

Le impostazioni dell'editor EditorConfig sono supportate in tutti i linguaggi supportati da Visual Studio, ad eccezione di XML. EditorConfig supporta inoltre le convenzioni di [stile del codice](/dotnet/fundamentals/code-analysis/code-style-rule-options), incluse le convenzioni di [linguaggio](/dotnet/fundamentals/code-analysis/style-rules/language-rules), [formattazione](/dotnet/fundamentals/code-analysis/style-rules/formatting-rules) e [denominazione](/dotnet/fundamentals/code-analysis/style-rules/naming-rules) per C# e Visual Basic.

## <a name="add-and-remove-editorconfig-files"></a>Aggiungere e rimuovere i file EditorConfig

Quando si aggiunge un file EditorConfig al progetto o alla codebase, le nuove righe di codice scritte vengono formattate in base al file EditorConfig. Tuttavia, l'aggiunta di un file EditorConfig non converte gli stili esistenti in quelli nuovi fino a quando non si formatta il documento o non si esegue [Pulizia codice](../ide/code-styles-and-code-cleanup.md). Se, ad esempio, il file contiene rientri formattati con tabulazioni e si aggiunge un file EditorConfig che imposta rientri con spazi, i caratteri di rientro non vengono convertiti automaticamente in spazi. Quando si formatta il documento **(** Modifica documento in formato avanzato o CTRL K , CTRL D ), le impostazioni degli spazi vuoti nel file EditorConfig vengono  >    >    + applicate alle righe di  + codice esistenti.

Se il file EditorConfig viene rimosso dal progetto o dalla codebase e si vuole che le nuove righe di codice siano formattate in base alle impostazioni globali dell'editor, sarà necessario chiudere e riaprire i file di codice aperti.

### <a name="add-an-editorconfig-file-to-a-project"></a>Aggiungere un file EditorConfig a un progetto

1. Aprire un progetto o una soluzione in Visual Studio. Selezionare il progetto o il nodo della soluzione, a seconda che le impostazioni del file con estensione *editorconfig* siano da applicare a tutti i progetti nella soluzione o soltanto a uno. È anche possibile selezionare una cartella del progetto o della soluzione alla quale aggiungere il file con estensione *editorconfig*.

1. Dalla barra dei menu scegliere **Project**  >  **Aggiungi nuovo elemento** o premere CTRL  + **MAIUSC** + **A.**

   Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo elemento .

1. Nella casella di ricerca cercare **editorconfig**.

   Nei risultati della ricerca verranno visualizzati due modelli di elemento **File editorconfig**.

   ![Modelli di elemento per il file EditorConfig in Visual Studio](media/editorconfig-item-templates.png)

1. Selezionare il modello **File editorconfig (impostazione predefinita)** per aggiungere un file EditorConfig prepopolato con due opzioni principali di EditorConfig per dimensioni e stile del rientro. In alternativa, selezionare il modello **File editorconfig (.NET)** per aggiungere un file EditorConfig prepopolato con i valori predefiniti per le [convenzioni di denominazione, formattazione e stile del codice .NET](/dotnet/fundamentals/code-analysis/code-style-rule-options).

   Un file con estensione *editorconfig* viene visualizzato in Esplora soluzioni e viene aperto nell'editor.

   ![File con estensione editorconfig in Esplora soluzioni e nell'editor](media/editorconfig-dotnet.png)

1. Modificare il file come necessario.

### <a name="other-ways-to-add-an-editorconfig-file"></a>Altri modi per aggiungere un file EditorConfig

Sono disponibili alcuni altri modi per aggiungere un file EditorConfig a un progetto:

- La [funzionalità di inferenza del codice](/visualstudio/intellicode/code-style-inference) di IntelliCode per Visual Studio deduce gli stili del codice dal codice esistente. Viene quindi creato un file EditorConfig non vuoto con le preferenze di stile del codice già definite.

- A partire da Visual Studio 2019, è possibile [generare un file EditorConfig in base alle impostazioni di stile del codice](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files) in **Strumenti** > **Opzioni**.

## <a name="file-hierarchy-and-precedence"></a>Precedenza e gerarchia dei file

Quando si aggiunge un file con estensione *editorconfig* a una cartella nella gerarchia di file, le relative impostazioni si applicano a tutti i file applicabili a tale livello e sotto. È anche possibile eseguire l'override delle impostazioni di EditorConfig per un particolare progetto, codebase o parte di una codebase, in modo da usare convenzioni diverse rispetto ad altre parti della codebase. Questo approccio può essere utile quando si incorpora codice proveniente da altre origini e non si vuole modificarne la convenzioni.

Per eseguire l'override di alcune o di tutte le impostazioni di EditorConfig, aggiungere un file con estensione *editorconfig* a livello della gerarchia di file in cui si vuole applicare l'override delle impostazioni. Le impostazioni del nuovo file EditorConfig vengono applicate ai file presenti allo stesso livello e in tutte le sottodirectory.

![Gerarchia di EditorConfig](../ide/media/vside_editorconfig_hierarchy.png)

Se si vuole eseguire l'override di alcune impostazioni, ma non di tutte, è sufficiente specificare tali impostazioni nel file con estensione *editorconfig*. Viene eseguito l'override solo delle proprietà elencate in modo esplicito nel file di livello inferiore. Le altre impostazioni dei file con estensione *editorconfig* di livello superiore continuano a essere applicate. Per assicurarsi che _nessuna_ impostazione di _nessun_ file con estensione *editorconfig* di livello superiore sia applicata a questa parte della codebase, aggiungere la proprietà ```root=true``` al file con estensione *editorconfig* di livello inferiore:

```ini
# top-most EditorConfig file
root = true
```

I file EditorConfig vengono letti dall'alto verso il basso. Se sono presenti più proprietà con lo stesso nome, la proprietà con tale nome individuata più di recente ha la precedenza.

## <a name="edit-editorconfig-files"></a>Modificare i file EditorConfig

Visual Studio consente di modificare i file con estensione *editorconfig* fornendo elenchi di completamento IntelliSense.

![IntelliSense in un file con estensione editorconfig](media/editorconfig-intellisense-no-extension.png)

Dopo aver modificato il file EditorConfig è necessario ricaricare i file di codice per rendere effettive le nuove impostazioni.

Se si modificano vari file con estensione *editorconfig*, può essere utile usare l'[estensione del servizio di linguaggio EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig). Alcune delle funzionalità di questa estensione sono evidenziazione della sintassi, IntelliSense migliorato, convalida e formattazione di codice.

![IntelliSense con estensione del servizio di linguaggio EditorConfig](media/editorconfig-intellisense.png)

## <a name="example"></a>Esempio

L'esempio seguente illustra lo stato dei rientri di un frammento di codice C# prima e dopo l'aggiunta di un file con estensione *editorconfig* al progetto. L'impostazione **Tabulazioni** nella finestra di dialogo **Opzioni** per l'editor di testo di Visual Studio è definita in modo che quando si preme **TAB** vengono generati spazi.

![Impostazione della tabulazione dell'editor di testo](../ide/media/vside_editorconfig_tabsetting.png)

Come previsto, premendo **TAB** nella riga successiva, viene impostato un rientro con l'aggiunta di altri quattro spazi vuoti.

![Il codice prima dell'uso di EditorConfig](../ide/media/vside_editorconfig_before.png)

Aggiungere al progetto un nuovo file con estensione *editorconfig* e il contenuto seguente. L'impostazione `[*.cs]` indica che questa modifica viene applicata solo ai file di codice C# all'interno del progetto.

```ini
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

A questo punto, quando si preme **TAB,** si ottengono caratteri di tabulazione anziché spazi.

![TAB aggiunge caratteri di tabulazione](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshoot-editorconfig-settings"></a>Risolvere i problemi relativi alle impostazioni di EditorConfig

Se è presente un file con estensione editorconfig nella struttura di directory in corrispondenza o al di sopra della posizione del progetto, Visual Studio applica all'editor le impostazioni dell'editor presenti nel file. In questo caso la barra di stato potrebbe visualizzare il seguente messaggio:

   **"Le convenzioni di scrittura codice di questo progetto sostituiscono le preferenze utente per questo tipo di file."**

Ciò significa che se in un file EditorConfig o sopra il progetto nella struttura di directory le impostazioni dell'editor, ad esempio le dimensioni e lo stile dei rientri, le dimensioni delle tabulazioni o le convenzioni di scrittura del codice, vengono specificate in un file EditorConfig in corrispondenza o al di sopra del progetto nella struttura di directory, le convenzioni nel  >    >   file EditorConfig sostituiscono le impostazioni in **Opzioni**. È possibile controllare questo comportamento attivando o disattivando l'opzione **Segui convenzioni di scrittura codice del progetto** in **Strumenti** > **Opzioni** > **Editor di testo**. Se si deseleziona l'opzione, si disattiva il supporto di EditorConfig per Visual Studio.

![Strumenti - Opzioni - Segui convenzioni di scrittura codice del progetto](media/coding_conventions_option.png)

È possibile trovare qualsiasi file con estensione *editorconfig* nelle directory padre aprendo un prompt dei comandi ed eseguendo il comando seguente dalla radice del disco che contiene il progetto:

```Shell
dir .editorconfig /s
```

È possibile controllare l'ambito delle convenzioni EditorConfig impostando la proprietà ```root=true``` nel file con estensione *editorconfig* presente nella directory radice del repository o nella directory in cui si trova il progetto. Visual Studio cerca un file con estensione *editorconfig* nella directory del file aperto e in tutte le directory padre. La ricerca termina quando si raggiunge il filepath radice o se viene trovato un file con estensione *editorconfig* con ```root=true```.

## <a name="see-also"></a>Vedi anche

- [.NET code style conventions](/dotnet/fundamentals/code-analysis/code-style-rule-options) (Convenzioni di stile del codice .NET)
- [Supporting EditorConfig for a language service](../extensibility/supporting-editorconfig.md) (Supporto di EditorConfig per un servizio di linguaggio)
- [EditorConfig.org](https://editorconfig.org/)
- [Funzionalità dell'editor del codice](writing-code-in-the-code-and-text-editor.md)
- [EditorConfig (Visual Studio per Mac)](/visualstudio/mac/editorconfig)
