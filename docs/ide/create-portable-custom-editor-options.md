---
title: Uso delle impostazioni di EditorConfig in VisualStudio | Microsoft Docs
ms.custom: 
ms.date: 10/27/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editorconfig [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.openlocfilehash: 39b3228e64257552c8b629e421c9b5aa4f0e0931
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/29/2017
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Creare impostazioni personalizzate e portabili per l'editor con EditorConfig

In Visual Studio le impostazioni dell'editor di testo si applicano a tutti i progetti di un tipo specifico. Quindi, ad esempio, se si modifica un'impostazione dell'editor di testo C#, la modifica viene applicata a *tutti* i progetti C# in Visual Studio. In alcuni casi, tuttavia, potrebbe essere necessario usare convenzioni diverse dalle preferenze personali per l'editor. I file [EditorConfig](http://editorconfig.org/) consentono di usare tali convenzioni descrivendo per l'editor di testo opzioni comuni diverse, ad esempio la dimensione del rientro, a seconda del progetto. Le impostazioni di EditorConfig, contenute in un file con estensione editorconfig che si trova con i file di codice e di progetto, hanno la precedenza sulle impostazioni globali dell'editor di testo di Visual Studio. Ciò significa che è possibile personalizzare ogni codebase in modo che vengano usate le impostazioni dell'editor di testo specifiche del progetto. Per usare questa funzionalità in Visual Studio non è necessario alcun plug-in.

## <a name="coding-consistency"></a>Coerenza del codice

Le impostazioni nei file EditorConfig consentono di mantenere stili e impostazioni di codifica coerenti in una codebase, ad esempio stile di rientro, rientro di tabulazione, caratteri di fine riga, codifica e altro, indipendentemente dall'editor o dall'IDE in uso. Ad esempio, quando si scrive codice in C#, se la codebase ha una convenzione preferita in base alla quale i rientri sono sempre costituiti da cinque spazi, i documenti devono usare la codifica UTF-8 e ogni riga termina sempre con un CR/LF, è possibile configurare un file con estensione editorconfig a tale scopo.

Le convenzioni di codifica usate per i progetti personali possono essere diverse da quelle per i progetti del team. Si potrebbe ad esempio preferire che durante la scrittura di codice il rientro aggiunga un carattere di tabulazione. Il team, tuttavia, potrebbe preferire per il rientro quattro spazi anziché un carattere di tabulazione. I file di EditorConfig risolvono questo problema consentendo di predisporre una configurazione per ogni scenario.

Dato che le impostazioni si trovano all'interno di un file nella codebase, seguono quest'ultima nei suoi spostamenti. Quando il file di codice viene aperto, le impostazioni dell'editor di testo vengono implementate, a condizione che l'editor sia compatibile con EditorConfig. Per altre informazioni sui file di EditorConfig, vedere il sito Web [EditorConfig.org](http://editorconfig.org/).

## <a name="override-editorconfig-settings"></a>Eseguire l'override delle impostazioni di EditorConfig

Quando si aggiunge un file con estensione editorconfig in una cartella della gerarchia di file, le impostazioni vengono applicate a tutti i file applicabili in tale livello e sotto di questo. Per eseguire l'override delle impostazioni di EditorConfig per un determinato progetto o una codebase specifica in modo che usi convenzioni diverse rispetto al file EditorConfig di livello superiore, è sufficiente aggiungere un file con estensione editorconfig al livello radice della directory del repository o del progetto per la codebase. Assicurarsi di inserire nel file la proprietà ```root=true```, in modo che Visual Studio non cerchi nei livelli superiori della struttura di directory altri file con estensione editorconfig. Le impostazioni del nuovo file EditorConfig si applicheranno ai file presenti nello stesso livello e in tutte le sottodirectory.

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
- end\_of_line
- charset
- radice

Le impostazioni dell'editor EditorConfig sono supportate in tutti i linguaggi supportati da Visual Studio, ad eccezione di XML. EditorConfig supporta inoltre le convenzioni di [stile del codice](../ide/editorconfig-code-style-settings-reference.md) e [denominazione](../ide/editorconfig-naming-conventions.md) per C# e Visual Basic.

## <a name="editing-editorconfig-files"></a>Modifica dei file EditorConfig

Visual Studio offre alcune funzionalità di IntelliSense per la modifica dei file con estensione editorconfig. Se si modificano molti file con estensione editorconfig, potrebbe risultare utile l'estensione [EditorConfig Language Service](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig).

Dopo aver modificato il file EditorConfig è necessario ricaricare i file di codice per rendere effettive le nuove impostazioni.

## <a name="adding-and-removing-editorconfig-files"></a>Aggiunta e rimozione dei file EditorConfig

L'aggiunta di un file EditorConfig al progetto o alla codebase non sostituisce gli stili esistenti con quelli nuovi. Se, ad esempio, il file contiene rientri formattati con tabulazioni e si aggiunge un file EditorConfig che imposta un rientro con spazi, i caratteri di rientro non verranno convertiti in spazi. Le nuove righe di codice verranno tuttavia formattate in base al file EditorConfig.

Se il file EditorConfig viene rimosso dal progetto o dalla codebase sarà necessario chiudere e riaprire i file di codice aperti per ripristinare le impostazioni globali dell'editor per le nuove righe di codice.

## <a name="example"></a>Esempio

Di seguito è riportato un esempio che mostra lo stato del rientro di un frammento di codice C# prima e dopo l'aggiunta di un file con estensione editorconfig al progetto. L'impostazione **Tabulazioni** nella finestra di dialogo **Opzioni** per l'editor di testo di Visual Studio è definita in modo che quando si preme **TAB** vengono generati spazi.

![Impostazione della tabulazione dell'editor di testo](../ide/media/vside_editorconfig_tabsetting.png)

Come previsto, premendo **TAB** sulla linea successiva la linea rientra con l'aggiunta di quattro caratteri spazio.

![Il codice prima dell'uso di EditorConfig](../ide/media/vside_editorconfig_before.png)

Verrà aggiunto al progetto un nuovo file con estensione editorconfig e il seguente contenuto. L'impostazione `[*.cs]` indica che questa modifica verrà applicata solo ai file di codice C# all'interno del progetto.

```
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

A questo punto, quando si preme **TAB** si ottengono caratteri di tabulazione anziché spazi.

![TAB aggiunge caratteri di tabulazione](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshooting-editorconfig-settings"></a>Risoluzione dei problemi relativi alle impostazioni EditorConfig

Se è presente un file con estensione editorconfig nella struttura directory in corrispondenza o sopra la posizione del progetto, Visual Studio applica all'editor le impostazioni dell'editor presenti nel file. In questo caso la barra di stato potrebbe visualizzare il seguente messaggio:

   **"Le convenzioni di scrittura codice di questo progetto sostituiscono le preferenze utente per questo tipo di file."**

Ciò significa che se le impostazioni dell'editor in **Strumenti**, **Opzioni**, **Editor di testo**, ad esempio la dimensione e lo stile del rientro, la dimensione delle tabulazioni o le convenzioni di scrittura del codice, sono specificate in un file EditorConfig che si trova sopra o in corrispondenza del livello del progetto nella struttura di directory, le convenzioni presenti nel file EditorConfig hanno la precedenza sulle impostazioni specificate in Opzioni. È possibile controllare questo comportamento attivando o disattivando l'opzione **Segui convenzioni di scrittura codice del progetto** in **Strumenti**, **Opzioni**, **Editor di testo**. Se si deseleziona l'opzione si disattiva il supporto di EditorConfig per Visual Studio.

![Strumenti - Opzioni - Segui convenzioni di scrittura codice del progetto](media/coding_conventions_option.png)

È possibile trovare i file con estensione editorconfig nelle directory padre aprendo un prompt dei comandi ed eseguendo il comando seguente nella directory radice del disco che contiene il progetto:

```
dir .editorconfig /s
```

È possibile controllare l'ambito delle convenzioni EditorConfig impostando la proprietà ```root=true``` nel file con estensione editorconfig presente nella directory radice del repository o nella directory in cui si trova il progetto. Visual Studio cerca un file con estensione editorconfig nella directory del file aperto e in tutte le directory padre. La ricerca viene interrotta se si raggiunge il percorso radice o se viene trovato un file con estensione editorconfig con ```root=true```.

## <a name="see-also"></a>Vedere anche

[.NET code style conventions](../ide/editorconfig-code-style-settings-reference.md) (Convenzioni di stile del codice .NET)  
[Supporting EditorConfig for a language service](../extensibility/supporting-editorconfig.md) (Supporto di EditorConfig per un servizio di linguaggio)  
[EditorConfig.org](http://editorconfig.org/)  
[Writing code in the editor](writing-code-in-the-code-and-text-editor.md) (Scrittura di codice nell'editor)