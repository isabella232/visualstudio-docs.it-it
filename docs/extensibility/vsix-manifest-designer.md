---
title: Finestra di progettazione del manifesto VSIX - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30620e0fe91d0e90995d2d2f721950f878c65fdc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697887"
---
# <a name="vsix-manifest-designer"></a>Finestra di progettazione del manifesto VSIX
Modifica un file manifesto del pacchetto VSIX, che imposta il comportamento di installazione per un'estensione di Visual Studio.

 La finestra di **progettazione del manifesto VSIX esegue** il mapping allo schema VSIX sottostante. Ogni elemento nello schema può essere impostato utilizzando un controllo corrispondente nella finestra di progettazione. Per ulteriori informazioni sullo schema, vedere riferimento allo schema di [estensione VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md).

 Per aprire **progettazione manifesto VSIX**, individuare un file *source.extension.vsixmanifest* in **Esplora soluzioni**e aprire il file. Se il file non contiene codice XML valido, la finestra di progettazione del manifesto non verrà aperta.

> [!NOTE]
> Il file *source.extension.vsixmanifest* viene restituito a *extension.vsixmanifest* quando viene compilato il pacchetto.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 **Progettazione manifesto VSIX** contiene quattro sezioni che corrispondono a questi elementi di primo livello dello schema:

- Metadati

- Destinazione di installazione

- Asset

- Dependencies

  L'area dell'intestazione contiene i seguenti controlli.

  **Nome prodotto** Descrive il nome dell'estensione.

  **ID prodotto** Specifica le informazioni di identificazione univoche per il pacchetto.

  **Autore** Specifica il nome dell'autore dell'estensione.

  **Versione** Specifica il numero di versione dell'estensione.

  La scheda **Metadati** contiene i controlli seguenti.

  **Designazione delle merci** Fornisce una descrizione testuale dell'estensione da visualizzare in **Gestione estensioni.**

  **Lingua** Specifica la lingua predefinita per il pacchetto, che corrisponde ai dati testuali nel manifesto. L'attributo `Language` segue la convenzione del codice delle impostazioni locali di Common Language Runtime (CLR) per gli assembly di risorse, ad esempio en-us, en, fr-fr. Per impostazione predefinita, il valore è neutro, il che significa che il pacchetto verrà eseguito in qualsiasi versione in lingua di Visual Studio.By default, the value is neutral, which means the package will run on any language version of Visual Studio.

  **Licenza** Specifica il file di testo che contiene la licenza utente, se presente.

  **Icona** Specifica il file di grafica (*.png*, *.bmp*, *.jpeg*, *.ico*) che contiene l'icona da visualizzare in **Gestione estensioni**, se è presente un'icona. L'immagine dell'icona deve essere 32x32 pixel o viene ridimensionata in base a tali dimensioni. Se non viene specificata alcuna icona, **Extension Manager** utilizza un'icona predefinita.

  **Immagine di anteprima** Specifica il file di grafica (*.png*, *.bmp*, *.jpeg*, *.ico*) che contiene l'immagine di anteprima da visualizzare in **Gestione estensioni**, se è presente un'immagine di anteprima. L'immagine di anteprima deve essere di 200x200 pixel. Se non viene specificata alcuna immagine di anteprima, **Extension Manager** utilizza un'immagine predefinita.

  **Etichette** Aggiunge tag di testo da utilizzare per gli hint di ricerca.

  **Note sulla versione** Specifica un file (*.txt*, *RTF*) contenente le note sulla versione. Accetta anche l'URL di un sito Web che visualizza le note sulla versione.

  **Guida introduttiva** Specifica un file (*.txt*, *.rtf*) che contiene informazioni su come utilizzare l'estensione o il contenuto nel pacchetto VSIX. Questa guida viene visualizzata al termine dell'installazione dell'estensione. Accetta anche l'URL di un sito Web che visualizza la guida.

  **Ulteriori informazioni URL** Specifica l'URL di un sito Web contenente informazioni aggiuntive sul prodotto.

  La scheda **Installa destinazioni** contiene i seguenti controlli.

  **Tipo di installazione** Elenca **Visual Studio Extension** ed Extension **SDK** come tipi di installazione di destinazione. Le opzioni variano a seconda del tipo scelto.

  **Estensione di Visual Studio** Elenca gli elementi **InstallationTarget** che descrivono come è possibile installare il pacchetto e in quali prodotti Visual Studio è possibile installare questa estensione. Ogni prodotto è identificato separatamente per nome e una versione o un intervallo di versioni. I prodotti possono essere aggiunti all'elenco, modificati ed eliminati. Il nome e la versione di un prodotto corrispondono agli attributi **Id** e **Version** dell'elemento **InstallationTarget** associato.

  **L'intervallo** di versioni è [12.0, 14.0] e utilizza la notazione seguente:

- [ - versione minima inclusa

- ] - versione massima inclusa

- ( - versione minima esclusiva

- ) - versione massima esclusiva

- Versione singola - solo la versione specificata

  **SDK estensione** Specifica un'installazione globale senza ambito per un prodotto e una versione specifici. **L'identificatore** della piattaforma di destinazione è la piattaforma, ad esempio "Windows", di destinazione. **Versione piattaforma** di destinazione è la versione, ad esempio 8.0, della piattaforma di destinazione. **Nome SDK** e **Versione SDK** sono rispettivamente il nome e il numero di versione dell'SDK.

  **Questo progetto VSIX viene installato per tutti gli utenti (richiede l'elevazione al lavoro)This VSIX is installed for all users (requires elevation on install)** Se si seleziona questa casella di controllo, l'estensione viene installata per tutti gli utenti; in caso contrario, viene installato solo per l'utente corrente.

  **Questo vSIX viene installato da Windows Installer** Se si seleziona questa casella di controllo, l'estensione viene installata da Windows Installer (file*con estensione msi);* in caso contrario, viene installato come un pacchetto VSIX tipico (file*VSIX).*

  La scheda **Risorse** contiene i seguenti controlli.

  **Elenco delle risorse** Elenca gli elementi Asset che descrivono l'estensione o gli elementi di contenuto emersi dal pacchetto. Ogni estensione o elemento di contenuto è elencato separatamente per origine, tipo e percorso. Le estensioni e gli elementi di contenuto possono essere aggiunti all'elenco, modificati ed eliminati. Il tipo e il percorso di un'estensione o di un elemento di contenuto corrisponde agli attributi `Type` e `Path` dell'elemento associato. `Asset` Di seguito sono elencati i tipi noti:

- Microsoft.visualstudio.package

- Microsoft.VisualStudio.MefComponent

- Microsoft.VisualStudio.ToolboxControl

- Microsoft.VisualStudio.Samples

- Microsoft.VisualStudio.ProjectTemplate

- Microsoft.VisualStudio.ItemTemplate

- Microsoft.VisualStudio.Assembly

- Microsoft.ExtensionSDK (informazioni in base al tallonidi

  Per aggiungere o modificare una risorsa, è necessario specificare il tipo di risorsa, se la risorsa è un progetto nella soluzione corrente o un file nel file system e il nome del progetto. È inoltre possibile specificare il nome della cartella in cui deve essere incorporato.

  È inoltre possibile creare tipi personalizzati e assegnare loro nomi univoci.

  La scheda **Dipendenze** contiene i seguenti controlli.

  **Nome, origine e intervallo di versioniName, Source, and Version Range** Elenca gli elementi Dependency di questo pacchetto, che sono altri pacchetti da cui dipende questo pacchetto. Se viene specificato un pacchetto di dipendenze, deve essere installato prima dell'installazione del pacchetto. in caso contrario, questo pacchetto deve installarlo.

  I pacchetti di dipendenze vengono specificati in base all'identificatore, al nome, all'intervallo di versioni, all'origine e alla modalità di risoluzione della dipendenza. Ogni pacchetto di dipendenze è elencato separatamente per nome, versione e origine. I pacchetti di dipendenze possono essere aggiunti all'elenco, modificati ed eliminati.

  L'identificatore `ID` deve corrispondere all'attributo dei metadati del pacchetto di dipendenze. L'origine può essere un progetto nella soluzione corrente, un'estensione attualmente installata o un file. L'impostazione **Come viene risolta la dipendenza** può essere il percorso relativo di un pacchetto annidato o l'URL del percorso di download per la dipendenza. L'ID, la versione e la risoluzione del `Id` `Version`pacchetto `Location` di dipendenze `Dependency` corrispondono agli attributi , e dell'elemento associato.

## <a name="see-also"></a>Vedere anche
- [Riferimento allo schema di estensione VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)
