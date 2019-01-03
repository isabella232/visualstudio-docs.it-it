---
title: Implementazione di categorie personalizzate e elementi visualizzati | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 178cd43486a9553f70853c9df0e106ac3ece78f1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53908436"
---
# <a name="implement-custom-categories-and-display-items"></a>Implementare le categorie personalizzate e visualizzare gli elementi
Un pacchetto VSPackage può fornire controllo dei tipi di carattere e colori del testo per il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) tramite le categorie personalizzate e di elementi visualizzati.

 Categorie personalizzate e gli elementi di visualizzazione si trovano i **Fonts and Colors** pagina delle proprietà. Per aprire la **i tipi di carattere e colori** pagina delle proprietà, scegliere il **strumenti** dal menu fare clic su **opzioni**. Espandere **ambiente** e quindi fare clic su **Fonts and Colors**.

 Quando si usa questo meccanismo, i pacchetti VSPackage devono implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfaccia e le interfacce associate.

 In teoria, questo meccanismo è utilizzabile per modificare tutte esistenti **elementi visualizzati** e il **categorie** che li contengono. Tuttavia non essere utilizzata per modificare la **testo EditorCategory** o dai relativi **elementi visualizzati**. Per altre informazioni, vedere [Panoramica di carattere e colori](../extensibility/font-and-color-overview.md).

 Per implementare custom **categorie** oppure **elementi visualizzati**, un pacchetto VSPackage deve:

- Creare o identificare le categorie nel Registro di sistema.

   Implementazione dell'IDE del **Fonts and Colors** pagina delle proprietà Usa queste informazioni per eseguire correttamente le query per il servizio che supporta una determinata categoria.

- Creare o identificare i gruppi (facoltativi) nel Registro di sistema.

   Può essere utile definire un gruppo, che rappresenta l'unione di due o più categorie. Se viene definito un gruppo, l'IDE automaticamente unisce le sottocategorie e distribuisce elementi visualizzati all'interno del gruppo.

- Implementazione del supporto IDE.

- Gestire le modifiche di carattere e colori.

  Per informazioni, vedere [accesso archiviate le impostazioni del tipo di carattere e colore](../extensibility/accessing-stored-font-and-color-settings.md).

## <a name="to-create-or-identify-categories"></a>Per creare o identificare le categorie

- Costruire un tipo speciale di voce del Registro di sistema categoria sotto *[HKLM\Software\Microsoft. \Visual Studio\\*\<versione di Visual Studio >*\FontAndColors\\ `<Category>`]*

   *\<Categoria >* è il nome non localizzato della categoria.

- Popolare il Registro di sistema con due valori:

  |nome|Tipo|Dati|Descrizione|
  |----------|----------|----------|-----------------|
  |Category|REG_SZ|GUID|Un GUID creato per identificare la categoria.|
  |Pacchetto|REG_SZ|GUID|Il GUID del servizio di VSPackage che supporta la categoria.|

  Il servizio specificato nel Registro di sistema deve fornire un'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> per la categoria corrispondente.

## <a name="to-create-or-identify-groups"></a>Per creare o identificare i gruppi

- Costruire un tipo speciale di voce del Registro di sistema categoria sotto *[HKLM\Software\Microsoft. \Visual Studio\\*\<versione di Visual Studio >*\FontAndColors\\*  \<gruppo >*]*

   *\<gruppo >* è il nome non localizzato del gruppo.

- Popolare il Registro di sistema con due valori:

  |nome|Tipo|Dati|Descrizione|
  |----------|----------|----------|-----------------|
  |Category|REG_SZ|GUID|Un GUID creato per identificare il gruppo.|
  |Pacchetto|REG_SZ|GUID|Il GUID del servizio che supporta la categoria.|

  Il servizio specificato nel Registro di sistema deve fornire un'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> per il gruppo corrispondente.

## <a name="to-implement-ide-support"></a>Per implementare il supporto dell'IDE

- Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>, che restituisce un <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interfaccia o un <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfaccia per l'IDE per ogni **categoria** o raggruppare i GUID fornito.

- Per ogni **categoria** supportati, un pacchetto VSPackage che implementa un'istanza separata del <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interfaccia.

- I metodi implementati tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> deve fornire l'IDE con:

  -   L'elenco delle **elementi visualizzati** nel **categoria.**

  -   I nomi localizzabili per **elementi visualizzati**.

  -   Visualizzare le informazioni per ogni membro del **categoria**.

  > [!NOTE]
  >  Ogni **categoria** deve contenere almeno uno **elemento visualizzato**.

- L'IDE Usa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfaccia per definire un'unione delle categorie diverse.

   L'implementazione fornisce l'IDE con:

  -   Un elenco del **categorie** che costituiscono un gruppo specificato.

  -   Accedere alle istanze del <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> che supportano ciascuna **categoria** all'interno del gruppo.

  -   Nomi dei gruppi localizzabile.

- Aggiornamento dell'IDE:

   L'IDE memorizza nella cache le informazioni sulle **carattere e colori** impostazioni. Di conseguenza, dopo l'eventuale modifica dell'IDE **carattere e colori** configurazione, è consigliabile verificare che la cache sia aggiornata.

  Aggiornamento della cache viene eseguita tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaccia e può essere eseguiti elementi a livello globale o solo sulla selezionati.

## <a name="to-handle-font-and-color-changes"></a>Per gestire le modifiche di carattere e colori
 Per supportare correttamente la colorazione del testo che consente di visualizzare un pacchetto VSPackage, il servizio di colorazione che supporta il pacchetto VSPackage deve rispondere alle modifiche avviata dall'utente tramite il **Fonts and Colors** pagina delle proprietà. Un pacchetto VSPackage a tale scopo:

-   La gestione degli eventi generati da IDE implementando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> interfaccia.

     L'IDE chiama il metodo appropriato dopo le modifiche apportate dall'utente del **Fonts and Colors** pagina. Ad esempio, chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> metodo se si seleziona un nuovo tipo di carattere.

     -oppure-

-   L'IDE per le modifiche di polling.

     Questa operazione può essere eseguita tramite il sistema implementato <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia. Anche se principalmente per il supporto di persistenza, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> metodo può essere utilizzato per ottenere informazioni di carattere e colori per **elementi visualizzati**. Per altre informazioni, vedere [accesso archiviate le impostazioni del tipo di carattere e colore](../extensibility/accessing-stored-font-and-color-settings.md).

    > [!NOTE]
    >  Per garantire che i risultati ottenuti eseguendo il polling siano corretti, che può essere utile usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaccia per determinare se una cache flush e aggiornamento sono necessari prima di chiamare i metodi di recupero del <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- [Ottenere le informazioni di carattere e colori per la colorazione del testo](../extensibility/getting-font-and-color-information-for-text-colorization.md)
- [Accesso archiviate le impostazioni di carattere e colori](../extensibility/accessing-stored-font-and-color-settings.md)
- [Procedura: Accedere ai tipi di carattere incorporati e combinazione di colori](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)
- [Panoramica di carattere e colori](../extensibility/font-and-color-overview.md)