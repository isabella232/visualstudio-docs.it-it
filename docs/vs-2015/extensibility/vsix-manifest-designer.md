---
title: Finestra di progettazione del manifesto VSIX | Microsoft Docs
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
ms.openlocfilehash: 308259e7addcf41ae6e15191934a8c37ac3f57b5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954232"
---
# <a name="vsix-manifest-designer"></a>Finestra di progettazione del manifesto VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modifica un file manifesto di pacchetto VSIX, che imposta il comportamento di installazione per un'estensione di Visual Studio.  
  
 Il **progettazione del manifesto VSIX** viene eseguito il mapping allo schema VSIX sottostante. Ogni elemento nello schema può essere impostato tramite un controllo corrispondente nella finestra di progettazione. Per altre informazioni sullo schema, vedere [riferimenti su VSIX Extension Schema 2.0](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
 Per aprire la **progettazione del manifesto VSIX**, individuare un file nella cartella vsixmanifest **Esplora soluzioni**e aprire il file. Se il file non contiene un XML valido, non si aprirà la finestra di progettazione manifesto.  
  
> [!NOTE]
>  Vsixmanifest è output Extension. vsixmanifest quando il pacchetto viene compilato.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 Il **progettazione del manifesto VSIX** contiene quattro sezioni che corrispondono a questi elementi di primo livello dello schema:  
  
- Metadati  
  
- Le destinazioni di installazione  
  
- Asset  
  
- Dipendenze  
  
  L'area di intestazione contiene i controlli seguenti.  
  
  **Nome del prodotto**  
  Descrive il nome dell'estensione.  
  
  **ID prodotto**  
  Specifica le informazioni di identificazione univoco del pacchetto.  
  
  **Autore**  
  Specifica il nome dell'autore dell'estensione.  
  
  **Version**  
  Specifica il numero di versione dell'estensione.  
  
  Il **metadati** scheda contiene i controlli seguenti.  
  
  **Descrizione**  
  Fornisce la descrizione testuale dell'estensione, deve essere visualizzato nella **gestore estensioni del**.  
  
  **Lingua**  
  Specifica la lingua predefinita per il pacchetto, che corrisponde ai dati testuali nel manifesto. Il `Language` attributo segue la convenzione di codice delle impostazioni locali di common language runtime (CLR) per gli assembly di risorse, ad esempio, en-us, en, fr-fr. Per impostazione predefinita, il valore è neutro; Ciò significa che il pacchetto verrà eseguito in qualsiasi versione localizzata di Visual Studio.  
  
  **licenza**  
  Specifica il file di testo che contiene la licenza utente, se presente.  
  
  **Icona**  
  Specifica il file di grafica (. PNG, bmp, JPEG,. ico) che contiene l'icona da visualizzare nella **gestore estensioni del**, se è presente un'icona. L'immagine dell'icona deve essere 32 x 32 pixel o verrà ridimensionato in base a tali dimensioni. Se non viene specificata alcuna icona, **gestore estensioni del** utilizza un'icona predefinita.  
  
  **Immagine di anteprima**  
  Specifica il file di grafica (. PNG, bmp, JPEG,. ico) che contiene l'immagine di anteprima da visualizzare nella **gestore estensioni del**, se è presente un'immagine di anteprima. L'immagine di anteprima deve essere 200x200 pixel. Se viene specificata alcuna immagine di anteprima **gestore estensioni del** Usa un'immagine predefinita.  
  
  **Tag**  
  Aggiunge i tag di testo da utilizzare per i suggerimenti di ricerca.  
  
  **Note sulla versione**  
  Specifica un file (con estensione txt,. RTF) che contiene le note sulla versione. Accetta inoltre l'URL di un sito Web che consente di visualizzare le note sulla versione.  
  
  **Guida introduttiva**  
  Specifica un file (con estensione txt,. RTF) che contiene informazioni su come usare l'estensione o il contenuto nel pacchetto VSIX. Questa guida viene visualizzata quando l'installazione dell'estensione è stata completata. Accetta inoltre l'URL di un sito Web che consente di visualizzare la Guida.  
  
  **Altre informazioni sull'URL**  
  Specifica l'URL di un sito Web che contiene informazioni aggiuntive sul prodotto.  
  
  Il **destinazioni di installazione** scheda contiene i controlli seguenti.  
  
  **Tipo di installazione**  
  Elenca **estensione di Visual Studio** e **SDK di estensione** come tipi di installazione di destinazione. Le opzioni variano a seconda del tipo scelto.  
  
  **Estensione di Visual Studio**  
  Elenca le **la destinazione di installazione** gli elementi che descrivono come il pacchetto può essere installato e in quali prodotti di Visual Studio è possibile installare questa estensione. Ogni prodotto viene identificato separatamente in base a nome e una versione o intervallo.  Prodotti possono essere aggiunto all'elenco, modificare ed eliminati. Il nome e la versione di un prodotto corrispondono per la **Id** e **versione** gli attributi dell'oggetto associato **la destinazione di installazione** elemento.  
  
  **Intervallo di versioni** è [12.0, 14,0] e Usa la notazione seguente:  
  
- [: versione minima inclusiva  
  
- ] – versione massima inclusivo  
  
- (-versione minima esclusiva  
  
- )-versione massima esclusivo  
  
- Versione unica & - solo la versione specificata  
  
  **Extension SDK**  
  Specifica un'installazione globale che non è nell'ambito di un prodotto specifico e una versione. **Identificatore della piattaforma di destinazione** è la piattaforma, ad esempio "Windows", di destinazione. **Versione piattaforma di destinazione** è la versione, ad esempio 8.0, la piattaforma di destinazione. **Nome del SDK** e **SDK versione** sono rispettivamente il nome e il numero di versione del SDK.  
  
  **Questa estensione VSIX è installato per tutti gli utenti (richiede l'elevazione dei privilegi durante l'installazione)** casella di controllo  
  Se questa casella di controllo è selezionata, questa estensione è installata per tutti gli utenti. in caso contrario, viene installato solo per l'utente corrente.  
  
  **Questa estensione VSIX è installato dal programma di installazione di Windows** casella di controllo  
  Se questa casella di controllo è selezionata, questa estensione viene installata dal programma di installazione di Windows (file con estensione msi); in caso contrario, viene installato come un pacchetto VSIX tipico (file con estensione VSIX).  
  
  Il **asset** scheda contiene i controlli seguenti.  
  
  **Elenco degli asset**  
  Elenca gli elementi di Asset che descrivono gli elementi di estensione o il contenuto da questo pacchetto superfici. Ogni estensione o elemento di contenuto è elencato separatamente dall'origine, tipo e percorso. Gli elementi di contenuto e le estensioni possono essere aggiunti all'elenco, modificati ed eliminati. Il tipo e il percorso di un elemento di estensione o il contenuto corrispondente per il `Type` e `Path` gli attributi dell'oggetto associato `Asset` elemento. I seguenti tipi sono noti:  
  
- Microsoft.VisualStudio.Package  
  
- Microsoft.VisualStudio.MefComponent  
  
- Microsoft.VisualStudio.ToolboxControl  
  
- Microsoft.VisualStudio.Samples  
  
- Microsoft.VisualStudio.ProjectTemplate  
  
- Microsoft.VisualStudio.ItemTemplate  
  
- Microsoft.VisualStudio.Assembly  
  
- Microsoft.ExtensionSDK  
  
  Per aggiungere o modificare un asset, è necessario specificare il tipo di risorsa, se l'asset è un progetto nella soluzione corrente o un file nel file system e il nome del progetto. È anche possibile specificare il nome della cartella in cui deve essere incorporato.  
  
  È anche possibile creare tipi personalizzati e assegnare loro nomi univoci.  
  
  Il **dipendenze** scheda contiene i controlli seguenti.  
  
  **Nome di origine e intervallo di versioni**  
  Elenca gli elementi di dipendenza di questo pacchetto, costituiti da altri pacchetti che dipende da questo pacchetto. Se un pacchetto di dipendenze è specificato, deve essere installato prima di questo pacchetto viene installato; in caso contrario, questo pacchetto è necessario installarlo.  
  
  I pacchetti di dipendenza vengono specificati dall'identificatore di nome, intervallo di versioni, origine e come la dipendenza deve essere risolto. Ogni pacchetto di dipendenza è elencato separatamente dal nome, versione e origine. I pacchetti di dipendenza possono essere aggiunto all'elenco, modificati ed eliminati.  
  
  L'identificatore deve corrispondere il `ID` attributo dei metadati del pacchetto di dipendenza. L'origine può essere un progetto nella soluzione corrente, un'estensione attualmente installata o un file. Il **è la modalità di dipendenza viene risolta** impostazione può essere il percorso relativo di un pacchetto annidato o l'URL del percorso di download per la dipendenza. L'ID, la versione e la risoluzione del pacchetto della dipendenza corrispondono per la `Id`, `Version`, e `Location` gli attributi dell'oggetto associato `Dependency` elemento.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti su VSIX Extension Schema 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)
