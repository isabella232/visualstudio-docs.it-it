---
title: Finestra di progettazione manifesto VSIX | Microsoft Docs
description: Informazioni su come Progettazione manifesto VSIX modifica un file manifesto del pacchetto VSIX, che imposta il comportamento di installazione per un'Visual Studio predefinita.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 4fc696d14ca7eb7c9efd3f038ce399cb19f1a926be8bbe515f694b5aa23d4af1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121335238"
---
# <a name="vsix-manifest-designer"></a>Finestra di progettazione del manifesto VSIX
Modifica un file manifesto del pacchetto VSIX, che imposta il comportamento di installazione per un'Visual Studio predefinita.

 Progettazione **manifesto VSIX esegue** il mapping allo schema VSIX sottostante. Ogni elemento dello schema può essere impostato usando un controllo corrispondente nella finestra di progettazione. Per altre informazioni sullo schema, vedere Informazioni [di riferimento sullo schema dell'estensione VSIX 2.0.](../extensibility/vsix-extension-schema-2-0-reference.md)

 Per aprire Progettazione manifesto **VSIX,** individuare un file *source.extension.vsixmanifest* in **Esplora soluzioni** e aprire il file. Se il file non contiene codice XML valido, la finestra di progettazione del manifesto non verrà aperta.

> [!NOTE]
> Il file *source.extension.vsixmanifest* viene restituito *a extension.vsixmanifest* quando viene compilato il pacchetto.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 Progettazione **manifesto VSIX** contiene quattro sezioni che corrispondono a questi elementi di primo livello dello schema:

- Metadati

- Destinazioni di installazione

- Asset

- Dependencies

  L'area di intestazione contiene i controlli seguenti.

  **Nome prodotto** Descrive il nome dell'estensione.

  **ID prodotto** Specifica le informazioni di identificazione univoche per questo pacchetto.

  **Autore** Specifica il nome dell'autore dell'estensione.

  **Versione** Specifica il numero di versione dell'estensione.

  La **scheda Metadati** contiene i controlli seguenti.

  **Descrizione** Fornisce una descrizione testuale dell'estensione da visualizzare in **Gestione estensioni.**

  **Lingua** Specifica la lingua predefinita per il pacchetto, che corrisponde ai dati testuali nel manifesto. L'attributo segue la convenzione del codice delle impostazioni locali CLR (Common Language Runtime) per gli assembly di risorse, ad esempio `Language` en-us, en, fr-fr. Per impostazione predefinita, il valore è neutro, ovvero il pacchetto verrà eseguito in qualsiasi versione del linguaggio di Visual Studio.

  **Licenza** Specifica il file di testo che contiene la licenza utente, se presente.

  **Icona** Specifica il file di grafica (*.png*, *.bmp*, *.jpeg*, *.ico*) che contiene l'icona da visualizzare **in** Gestione estensioni, se è presente un'icona. L'immagine dell'icona deve essere di 32x32 pixel o viene ridimensionata in base a tali dimensioni. Se non viene specificata alcuna icona, **Gestione estensioni usa** un'icona predefinita.

  **Immagine di anteprima** Specifica il file di grafica (*.png*, *.bmp*, *jpeg*, *ico*) che contiene l'immagine di anteprima da visualizzare **in** Gestione estensioni, se è presente un'immagine di anteprima. L'immagine di anteprima deve essere di 200x200 pixel. Se non viene specificata alcuna immagine di anteprima, **Gestione estensioni usa** un'immagine predefinita.

  **Tag** Aggiunge tag di testo da usare per i suggerimenti per la ricerca.

  **Note sulla versione** Specifica un file (*.txt*, *RTF*) che contiene le note sulla versione. Accetta anche l'URL di un sito Web che visualizza le note sulla versione.

  **Attività iniziali guida** Specifica un file (*.txt*, *RTF*) che contiene informazioni su come usare l'estensione o il contenuto nel pacchetto VSIX. Questa guida viene visualizzata al termine dell'installazione dell'estensione. Accetta anche l'URL di un sito Web che visualizza la guida.

  **URL altre informazioni** Specifica l'URL di un sito Web che contiene informazioni aggiuntive sul prodotto.

  La **scheda Destinazioni** di installazione contiene i controlli seguenti.

  **Tipo di installazione** Elenca **Visual Studio sdk di estensione** ed estensione **come** tipi di installazione di destinazione. Le opzioni variano a seconda del tipo scelto.

  **estensione Visual Studio** Elenca gli **elementi InstallationTarget** che descrivono come è possibile installare il pacchetto e in quali Visual Studio prodotti questa estensione può essere installata. Ogni prodotto viene identificato separatamente in base al nome e a una versione o a un intervallo di versioni. I prodotti possono essere aggiunti all'elenco, modificati ed eliminati. Il nome e la versione di un prodotto corrispondono agli **attributi Id** e **Version** dell'elemento **InstallationTarget** associato.

  **L'intervallo** di versioni è [12.0, 14.0] e usa la notazione seguente:

- [ - versione minima inclusiva

- ] - versione massima inclusiva

- ( - versione minima esclusiva

- ) - versione massima esclusiva

- Versione singola # - solo la versione specificata

  **SDK di estensione** Specifica un'installazione globale che non ha come ambito un prodotto e una versione specifici. **Target Platform Identifier (Identificatore** piattaforma di destinazione) è la piattaforma di destinazione, ad esempio "Windows". **Versione piattaforma di** destinazione è la versione, ad esempio 8.0, della piattaforma di destinazione. **Sdk Name** **(Nome SDK) e SDK Version** (Versione SDK) sono rispettivamente il nome e il numero di versione dell'SDK.

  **Questa estensione VSIX viene installata per tutti gli utenti (è necessaria l'elevazione dei privilegi durante l'installazione)** Se si seleziona questa casella di controllo, l'estensione viene installata per tutti gli utenti. in caso contrario, viene installato solo per l'utente corrente.

  **Questo pacchetto VSIX viene installato dal programma di Windows installazione** Se si seleziona questa casella di controllo, l'estensione viene installata dal programma di installazione Windows *(file.msi;* in caso contrario, viene installato come pacchetto VSIX tipico (file *con estensione vsix).*

  La **scheda Asset** contiene i controlli seguenti.

  **Elenco di asset** Elenca gli elementi Asset che descrivono l'estensione o gli elementi di contenuto che il pacchetto visualizza. Ogni estensione o elemento di contenuto è elencato separatamente per origine, tipo e percorso. Le estensioni e gli elementi di contenuto possono essere aggiunti all'elenco, modificati ed eliminati. Il tipo e il percorso di un'estensione o di un elemento di contenuto corrispondono agli `Type` `Path` attributi e dell'elemento `Asset` associato. Di seguito sono elencati i tipi noti:

- Microsoft.visualstudio.package

- Microsoft.VisualStudio.MefComponent

- Microsoft.VisualStudio.ToolboxControl

- Microsoft.VisualStudio.Samples

- Microsoft.VisualStudio.ProjectTemplate

- Microsoft.VisualStudio.ItemTemplate

- Microsoft.VisualStudio.Assembly

- Microsoft.ExtensionSDK

  Per aggiungere o modificare un asset, è necessario specificare il tipo di asset, se l'asset è un progetto nella soluzione corrente o un file nel file system e il nome del progetto. È anche possibile specificare il nome della cartella in cui incorporare.

  È anche possibile creare tipi personalizzati e assegnare loro nomi univoci.

  La **scheda Dipendenze** contiene i controlli seguenti.

  **Nome, origine e intervallo di versioni** Elenca gli elementi Dependency di questo pacchetto, che sono altri pacchetti da cui dipende questo pacchetto. Se viene specificato un pacchetto di dipendenze, è necessario installare il pacchetto prima di installare il pacchetto. In caso contrario, questo pacchetto deve installarlo.

  I pacchetti di dipendenze vengono specificati in base a identificatore, nome, intervallo di versioni, origine e modalità di risoluzione della dipendenza. Ogni pacchetto di dipendenze è elencato separatamente per nome, versione e origine. I pacchetti di dipendenze possono essere aggiunti all'elenco, modificati ed eliminati.

  L'identificatore deve corrispondere `ID` all'attributo dei metadati del pacchetto di dipendenze. L'origine può essere un progetto nella soluzione corrente, un'estensione attualmente installata o un file. **L'impostazione Come viene risolta la** dipendenza può essere il percorso relativo di un pacchetto annidato o l'URL del percorso di download per la dipendenza. L'ID, la versione e la risoluzione del pacchetto di dipendenze corrispondono agli attributi `Id` `Version` , e `Location` dell'elemento `Dependency` associato.

## <a name="see-also"></a>Vedi anche
- [Informazioni di riferimento sullo schema dell'estensione VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)
