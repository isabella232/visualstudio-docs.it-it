---
title: Creare impostazioni personalizzate e portabili per l'editor con EditorConfig | Microsoft Docs
ms.custom: 
ms.date: 10/27/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editor
ms.assetid: 
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.openlocfilehash: 2c1df6f8e34d2b8e72486dd804ba57f0dcf2406b
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2017
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Creare impostazioni personalizzate e portabili per l'editor con EditorConfig
In Visual Studio le impostazioni dell'editor di testo si applicano a tutti i progetti di un tipo specifico. Quindi, ad esempio, se si modifica un'impostazione dell'editor di testo C#, la modifica viene applicata a *tutti* i progetti C# in Visual Studio. In alcuni casi, tuttavia, potrebbe essere necessario usare convenzioni diverse dalle preferenze personali per l'editor. I file di [EditorConfig](http://editorconfig.org/) consentono di usare tali convenzioni impostando per l'editor di testo opzioni comuni diverse a seconda del progetto. Le impostazioni di EditorConfig, contenute in un file con estensione editorconfig aggiunto alla codebase, sostituiscono le impostazioni globali di Visual Studio per l'editor di testo. Questo significa che è possibile usare codebase su misura con le impostazioni per l'editor di testo preferite. Per usare questa funzionalità in Visual Studio non è necessario alcun plug-in.

## <a name="coding-consistency"></a>Coerenza del codice
Le impostazioni nei file di EditorConfig consentono di mantenere stili di codifica e impostazioni coerenti nell'ambito un linguaggio, ad esempio lo stile dei rientri, l'ampiezza delle tabulazioni, i caratteri di fine riga, la codifica e altro ancora, in una codebase, indipendentemente dall'IDE o dall'editor in uso. Ad esempio, quando si scrive codice in C#, se la codebase ha una convenzione preferita in base alla quale i rientri sono sempre costituiti da cinque spazi, i documenti devono usare la codifica UTF-8 e ogni riga termina sempre con un CR/LF, è possibile configurare un file con estensione editorconfig a tale scopo.

Le convenzioni di codifica usate per i progetti personali possono essere diverse da quelle per i progetti del team. Si potrebbe ad esempio preferire che durante la scrittura di codice la pressione del tasto TAB aggiunga un carattere di tabulazione. Il team, tuttavia, potrebbe preferire per il rientro quattro spazi anziché un carattere di tabulazione. I file di EditorConfig risolvono questo problema consentendo di predisporre una configurazione per ogni scenario.

Dato che le impostazioni si trovano all'interno di un file nella codebase, seguono quest'ultima nei suoi spostamenti. Quando il file di codice viene aperto, le impostazioni dell'editor di testo vengono implementate, a condizione che l'editor sia compatibile con EditorConfig. Per altre informazioni sui file di EditorConfig, vedere il sito Web [EditorConfig.org](http://editorconfig.org/).

## <a name="override-editorconfig-settings"></a>Eseguire l'override delle impostazioni di EditorConfig
Quando si aggiunge un file con estensione editorconfig in una cartella della gerarchia di file, le impostazioni vengono applicate a tutti i file applicabili in tale livello e sotto di questo. Per eseguire l'override delle impostazioni di EditorConfig per un determinato progetto o una codebase specifica in modo che usi convenzioni diverse rispetto al file con estensione editorconfig di livello superiore, è sufficiente aggiungere un file con estensione editorconfig al livello radice della directory del repository o del progetto per la codebase. Assicurarsi di inserire nel file la proprietà ```root=true```, in modo che Visual Studio non cerchi altri file con estensione editorconfig nei livelli superiori della struttura di directory. Le impostazioni del nuovo file con estensione editorconfig si applicheranno al livello in cui si trova e ai file presenti in tutte le sottodirectory.

```
# top-most EditorConfig file
root = true
```

![Gerarchia di EditorConfig](../ide/media/vside_editorconfig_hierarchy.png)

I file con estensione editorconfig vengono letti dall'alto in basso e i file più vicini vengono letti per ultimi. Le convenzioni delle sezioni EditorConfig corrispondenti vengono applicate in ordine di lettura, pertanto le convenzioni nei file più vicini hanno la precedenza.

## <a name="supported-settings"></a>Impostazioni supportate
L'editor in Visual Studio supporta le proprietà seguenti del set di base di [proprietà di EditorConfig](http://editorconfig.org/#supported-properties):  

- indent_style
- indent_size
- tab_width
- end_of_line
- charset
- radice

Supporta anche le [convenzioni di stile del codice .NET](../ide/editorconfig-code-style-settings-reference.md).  

Le impostazioni di EditorConfig sono supportate in tutti i linguaggi supportati da Visual Studio, ad eccezione dell'XML.

## <a name="intellisense"></a>IntelliSense
Visual Studio offre un'implementazione di IntelliSense limitata per la modifica dei file con estensione editorconfig. Se si modificano molti file con estensione editorconfig, potrebbe risultare utile l'estensione [EditorConfig Language Service](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig).

## <a name="example"></a>Esempio
Di seguito è riportato un esempio che mostra lo stato del rientro di un frammento di codice C# prima e dopo l'aggiunta di un file con estensione editorconfig al progetto. L'impostazione **Tabulazioni** nella finestra di dialogo **Opzioni** per l'editor di testo di Visual Studio è definita in modo che quando si preme **TAB** all'interno del codice vengono generati spazi.

![Impostazione della tabulazione dell'editor di testo](../ide/media/vside_editorconfig_tabsetting.png)

Come previsto, premendo **TAB** sulla linea successiva la linea rientra con l'aggiunta di quattro caratteri spazio.

![Il codice prima dell'uso di EditorConfig](../ide/media/vside_editorconfig_before.png)

Verrà aggiunto al progetto un nuovo file con estensione editorconfig e il seguente contenuto. L'impostazione `[*.cs]` indica che questa modifica verrà applicata solo ai file con estensione cs all'interno del progetto.  

![File .editorconfig aggiunto al progetto](../ide/media/vside_editorconfig_addconfig.png)

A questo punto, quando si preme **TAB** si ottengono caratteri di tabulazione anziché spazi.

![TAB aggiunge caratteri di tabulazione](../ide/media/vside_editorconfig_tab.png)

> [!NOTE]
>  L'aggiunta di un file con estensione editorconfig al progetto o alla codebase non sostituisce gli stili esistenti con quelli nuovi, che vengono applicati solo alle linee aggiunte successivamente. Se si rimuove un file con estensione editorconfig dal progetto o dalla codebase, per ripristinare le impostazioni globali come impostazioni dell'editor è necessario ricaricare i file di codice. Eventuali errori nel file con estensione editorconfig vengono segnalati nella finestra Elenco errori in Visual Studio.

## <a name="troubleshooting-editorconfig-settings"></a>Risoluzione dei problemi relativi alle impostazioni EditorConfig
Se è presente un file con estensione editorconfig nella struttura directory in corrispondenza o sopra la posizione del progetto, Visual Studio applica all'editor le impostazioni dell'editor presenti nel file. In questo caso la barra di stato potrebbe visualizzare il seguente messaggio:

**"Le convenzioni di scrittura codice di questo progetto sostituiscono le preferenze utente per questo tipo di file."**

Ciò significa che se le impostazioni dell'editor in **Strumenti**, **Opzioni**, **Editor di testo**, ad esempio la dimensione rientro, la dimensione tabulazione, lo stile rientro (tabulazioni o spazi) o le convenzioni di scrittura codice quali l'uso di `var` sono specificate in un file con estensione editorconfig che si trova sopra o in corrispondenza del livello del progetto nella struttura directory, le convenzioni presenti nel file con estensione editorconfig hanno la precedenza sulle impostazioni specificate in Opzioni. È possibile controllare questo comportamento attivando o disattivando l'opzione **Segui convenzioni di scrittura codice del progetto** in **Strumenti**, **Opzioni**, **Editor di testo**. Se si deseleziona l'opzione si disattiva il supporto di EditorConfig per Visual Studio.

![Strumenti - Opzioni - Segui convenzioni di scrittura codice del progetto](media/coding_conventions_option.png)

È possibile trovare i file con estensione editorconfig nelle directory padre aprendo un prompt dei comandi ed eseguendo il comando seguente nella directory radice del disco che contiene il progetto:

```
dir .editorconfig /s
```

È possibile controllare l'ambito delle convenzioni EditorConfig impostando la proprietà ```root=true``` nel file con estensione editorconfig presente nella directory radice del repository o nella directory in cui si trova il progetto. Visual Studio cerca un file con estensione editorconfig nella directory del file aperto e in tutte le directory padre. La ricerca viene interrotta se si raggiunge il percorso radice o se viene trovato un file con estensione editorconfig con ```root=true```.

## <a name="support-editorconfig-for-your-language-service"></a>Supporto di EditorConfig per il servizio di linguaggio
Nella maggior parte dei casi, quando si implementa un servizio di linguaggio di Visual Studio, non è necessario alcun intervento aggiuntivo per supportare le proprietà universali di EditorConfig. L'editor principale individua e legge automaticamente il file con estensione editorconfig quando gli utenti aprono i file e imposta le opzioni appropriate per buffer di testo e visualizzazione. Tuttavia, alcuni servizi di linguaggio scelgono di usare un'opzione di visualizzazione testo contestuale appropriata anziché usare impostazioni globali per elementi quali tabulazioni e spazi quando un utente modifica o formatta il testo. In questi casi il servizio di linguaggio deve essere aggiornato in modo da supportare i file EditorConfig.

Di seguito sono elencate le modifiche necessarie per aggiornare un servizio di linguaggio per il supporto dei file EditorConfig, sostituendo un'opzione globale _specifica del linguaggio_ con un'opzione _contestuale_:  

### <a name="indent-style"></a>Stile rientro
Sostituire:  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs  
_o_  
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs  

con:  

!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)  
_o_  
!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)  

### <a name="indent-size"></a>Dimensione rientro
Sostituire:  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize  
_o_  
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize  

con:  

textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)  
_o_  
textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)  

### <a name="tab-size"></a>Dimensione tabulazione
Sostituire:  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize  
_o_  
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize  

con:  

textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)  
_o_  
textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)  

## <a name="see-also"></a>Vedere anche
[.NET code style conventions](../ide/editorconfig-code-style-settings-reference.md) (Convenzioni di stile del codice .NET)  
[EditorConfig.org](http://editorconfig.org/)  
[Writing code in the editor](writing-code-in-the-code-and-text-editor.md) (Scrittura di codice nell'editor)