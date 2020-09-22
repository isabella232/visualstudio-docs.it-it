---
title: Progettazione manifesto VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 450d306718906c3b76bf05982594045e7fd215f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839740"
---
# <a name="vsix-manifest-designer"></a>Finestra di progettazione del manifesto VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modifica un file manifesto del pacchetto VSIX, che imposta il comportamento di installazione per un'estensione di Visual Studio.  
  
 La **finestra di progettazione del manifesto VSIX** esegue il mapping allo schema VSIX sottostante. Ogni elemento nello schema può essere impostato utilizzando un controllo corrispondente nella finestra di progettazione. Per altre informazioni sullo schema, vedere [riferimento allo schema di estensione VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
 Per aprire **Progettazione manifesto VSIX**, individuare un file source. Extension. vsixmanifest in **Esplora soluzioni**e aprire il file. Se il file non contiene codice XML valido, la finestra di progettazione del manifesto non verrà aperta.  
  
> [!NOTE]
> Source. Extension. vsixmanifest viene restituito in Extension. vsixmanifest quando il pacchetto viene compilato.  
  
## <a name="uielement-list"></a>Elenco degli elementi di interfaccia  
 La **finestra di progettazione del manifesto VSIX** contiene quattro sezioni che corrispondono a questi elementi di primo livello dello schema:  
  
- Metadati  
  
- Installa destinazioni  
  
- Asset  
  
- Dependencies  
  
  L'area di intestazione contiene i controlli seguenti.  
  
  **Nome prodotto**  
  Descrive il nome dell'estensione.  
  
  **ID prodotto**  
  Specifica le informazioni di identificazione univoche per il pacchetto.  
  
  **Author**  
  Specifica il nome dell'autore dell'estensione.  
  
  **Version**  
  Specifica il numero di versione dell'estensione.  
  
  La scheda **metadati** contiene i controlli seguenti.  
  
  **Descrizione**  
  Fornisce una descrizione di testo dell'estensione da visualizzare in **Gestione estensioni**.  
  
  **Lingua**  
  Specifica la lingua predefinita per il pacchetto, che corrisponde ai dati testuali nel manifesto. L' `Language` attributo segue la convenzione di codice delle impostazioni locali Common Language Runtime (CLR) per gli assembly di risorse, ad esempio en-US, en, fr-fr. Per impostazione predefinita, il valore è neutro; Questo significa che il pacchetto verrà eseguito in qualsiasi versione della lingua di Visual Studio.  
  
  **Licenza**  
  Specifica il file di testo che contiene la licenza utente, se presente.  
  
  **Icona**  
  Specifica il file di grafica (. png,. bmp,. jpeg,. ico) che contiene l'icona da visualizzare in **Gestione estensioni**, se è presente un'icona. L'immagine dell'icona deve essere 32x32 pixel o verrà ridimensionata in tali dimensioni. Se non viene specificata alcuna icona, **Gestione estensioni** usa un'icona predefinita.  
  
  **Anteprima immagine**  
  Specifica il file di grafica (. png,. bmp,. jpeg,. ico) che contiene l'immagine di anteprima da visualizzare in **Gestione estensioni**, se è presente un'immagine di anteprima. L'immagine di anteprima deve essere 200x200 pixel. Se non viene specificata alcuna immagine di anteprima, **Gestione estensioni** usa un'immagine predefinita.  
  
  **Tag**  
  Aggiunge tag di testo da utilizzare per gli hint di ricerca.  
  
  **Note sulla versione**  
  Specifica un file (con estensione txt, RTF) che contiene le note sulla versione. Accetta anche l'URL di un sito Web che visualizza le note sulla versione.  
  
  **Guida Introduzione**  
  Specifica un file (con estensione txt, RTF) che contiene informazioni su come usare l'estensione o il contenuto del pacchetto VSIX. Questa guida viene visualizzata al termine dell'installazione dell'estensione. Accetta anche l'URL di un sito Web che visualizza la guida.  
  
  **Altro URL informazioni**  
  Specifica l'URL di un sito Web che contiene informazioni aggiuntive sul prodotto.  
  
  Nella scheda **destinazioni di installazione** sono inclusi i seguenti controlli.  
  
  **Tipo di installazione**  
  Elenca l' **estensione di Visual Studio** e l' **SDK di estensione** come tipi di installazione di destinazione. Le opzioni variano a seconda del tipo scelto.  
  
  **Estensione di Visual Studio**  
  Elenca gli elementi **installazione** che descrivono come è possibile installare il pacchetto e in quali prodotti Visual Studio è possibile installare questa estensione. Ogni prodotto viene identificato separatamente in base al nome e a una versione o a un intervallo di versioni.  I prodotti possono essere aggiunti all'elenco, modificati ed eliminati. Il nome e la versione di un prodotto corrispondono agli attributi **ID** e **Version** dell'elemento **installazione** associato.  
  
  L' **intervallo di versioni** è [12,0, 14,0] e utilizza la notazione seguente:  
  
- [-versione minima inclusa  
  
- ]: versione massima inclusa  
  
- (-versione minima esclusiva  
  
- ): versione massima esclusiva  
  
- Versione singola: solo la versione specificata  
  
  **SDK di estensione**  
  Specifica un'installazione globale non inclusa nell'ambito di un prodotto e una versione specifici. L' **identificatore della piattaforma di destinazione** è la piattaforma, ad esempio "Windows", di destinazione. La **versione della piattaforma di destinazione** è la versione, ad esempio 8,0, della piattaforma di destinazione. Il nome dell' **SDK** e la **versione** dell'SDK sono rispettivamente il nome e il numero di versione dell'SDK.  
  
  **La casella di controllo VSIX è installata per tutti gli utenti (è richiesta l'elevazione in caso di installazione)**  
  Se questa casella di controllo è selezionata, questa estensione viene installata per tutti gli utenti. in caso contrario, viene installato solo per l'utente corrente.  
  
  **Questo progetto VSIX è installato da Windows Installer casella di** controllo  
  Se questa casella di controllo è selezionata, questa estensione viene installata dal Windows Installer (file con estensione msi); in caso contrario, viene installato come pacchetto VSIX tipico (file VSIX).  
  
  La scheda **Asset** contiene i controlli seguenti.  
  
  **Elenco di asset**  
  Elenca gli elementi asset che descrivono l'estensione o gli elementi di contenuto che questo pacchetto è in superficie. Ogni estensione o elemento di contenuto è elencato separatamente in base all'origine, al tipo e al percorso. Le estensioni e gli elementi di contenuto possono essere aggiunti all'elenco, modificati ed eliminati. Il tipo e il percorso di un'estensione o di un elemento di contenuto corrispondono agli `Type` `Path` attributi e dell' `Asset` elemento associato. Di seguito sono elencati i tipi noti:  
  
- Microsoft. VisualStudio. Package  
  
- Microsoft.VisualStudio.MefComponent  
  
- Microsoft. VisualStudio. ToolboxControl  
  
- Microsoft. VisualStudio. Samples  
  
- Microsoft. VisualStudio. ProjectTemplate  
  
- Microsoft. VisualStudio. ItemTemplate  
  
- Microsoft. VisualStudio. assembly  
  
- Microsoft. ExtensionSDK  
  
  Per aggiungere o modificare un asset, è necessario specificare il tipo di asset, se l'asset è un progetto nella soluzione corrente o un file nel file system e il nome del progetto. È inoltre possibile specificare il nome della cartella in cui eseguire l'incorporamento.  
  
  È anche possibile creare tipi personalizzati e assegnare loro nomi univoci.  
  
  La scheda **dipendenze** contiene i controlli seguenti.  
  
  **Nome, origine e intervallo di versioni**  
  Elenca gli elementi di dipendenza di questo pacchetto, ovvero altri pacchetti da cui dipende questo pacchetto. Se viene specificato un pacchetto di dipendenze, è necessario installarlo prima di installare il pacchetto. in caso contrario, il pacchetto deve installarlo.  
  
  I pacchetti di dipendenze sono specificati dall'identificatore, dal nome, dall'intervallo di versioni, dall'origine e dal modo in cui la dipendenza deve essere risolta. Ogni pacchetto di dipendenze è elencato separatamente in base al nome, alla versione e all'origine. I pacchetti di dipendenze possono essere aggiunti all'elenco, modificati ed eliminati.  
  
  L'identificatore deve corrispondere all' `ID` attributo dei metadati del pacchetto di dipendenze. L'origine può essere un progetto nella soluzione corrente, un'estensione attualmente installata o un file. L'impostazione **How is resolved Dependency** può essere il percorso relativo di un pacchetto annidato o l'URL del percorso di download per la dipendenza. L'ID, la versione e la risoluzione del pacchetto di dipendenze corrispondono agli `Id` attributi, `Version` e `Location` dell' `Dependency` elemento associato.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo schema di estensione VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)
