---
title: Implementazione di categorie personalizzate e elementi visualizzati | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 474d5c66507b56bea609568b6acfe9f5eff75e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839539"
---
# <a name="implementing-custom-categories-and-display-items"></a>Implementazione di categorie ed elementi di visualizzazione personalizzati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un pacchetto VSPackage può fornire il controllo dei tipi di carattere e dei colori del testo al [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Integrated Development Environment (IDE) tramite le categorie personalizzate e gli elementi visualizzati.  
  
 Le categorie personalizzate e gli elementi visualizzati si trovano nella pagina delle proprietà **tipi di carattere e colori** . Per aprire la pagina delle proprietà **tipi di carattere e colori** , scegliere **Opzioni**dal menu **strumenti** . Espandere **ambiente** , quindi fare clic su **tipi di carattere e colori**.  
  
 Quando si usa questo meccanismo, i pacchetti VSPackage devono implementare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfaccia e le interfacce associate.  
  
 In linea di principio, questo meccanismo può essere usato per modificare tutti **gli elementi visualizzati** esistenti e le **categorie** che li contengono. Tuttavia, non deve essere usato per modificare il **testo EditorCategory** o i relativi **elementi visualizzati**. Per ulteriori informazioni, vedere [Cenni preliminari su tipo di carattere e colore](../extensibility/font-and-color-overview.md).  
  
 Per implementare **categorie** personalizzate o **elementi visualizzati**, un pacchetto VSPackage deve:  
  
- Creare o identificare le categorie nel registro di sistema.  
  
   L'implementazione dell'IDE della pagina delle proprietà **tipi di carattere e colori** usa queste informazioni per eseguire una query corretta per il servizio che supporta una determinata categoria.  
  
- Creare o identificare i gruppi (facoltativo) nel registro di sistema.  
  
   Può essere utile definire un gruppo, che rappresenta l'Unione di due o più categorie. Se viene definito un gruppo, l'IDE unisce automaticamente le sottocategorie e distribuisce gli elementi visualizzati all'interno del gruppo.  
  
- Implementare il supporto dell'IDE.  
  
- Gestire le modifiche ai tipi di carattere e ai colori.  
  
  Per informazioni, vedere [accesso alle impostazioni dei tipi di carattere e dei colori archiviati](../extensibility/accessing-stored-font-and-color-settings.md).  
  
## <a name="to-create-or-identify-categories"></a>Per creare o identificare categorie  
  
- Costruire un tipo speciale di voce del registro di sistema Category in [Hklm\software\microsoft. \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ `<Category>` ]  
  
   *\<Category>* nome non localizzato della categoria.  
  
- Popolare il registro di sistema con due valori:  
  
  |Nome|Type|Data|Descrizione|  
  |----------|----------|----------|-----------------|  
  |Category|REG_SZ|GUID|GUID creato per identificare la categoria.|  
  |Pacchetto|REG_SZ|GUID|GUID del servizio VSPackage che supporta la categoria.|  
  
  Il servizio specificato nel registro di sistema deve fornire un'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> per la categoria corrispondente.  
  
## <a name="to-create-or-identify-groups"></a>Per creare o identificare i gruppi  
  
- Costruire un tipo speciale di voce del registro di sistema Category in [Hklm\software\microsoft. \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<group>* ]  
  
   *\<group>* nome non localizzato del gruppo.  
  
- Popolare il registro di sistema con due valori:  
  
  |Nome|Type|Data|Descrizione|  
  |----------|----------|----------|-----------------|  
  |Category|REG_SZ|GUID|GUID creato per identificare il gruppo.|  
  |Pacchetto|REG_SZ|GUID|GUID del servizio che supporta la categoria.|  
  
  Il servizio specificato nel registro di sistema deve fornire un'implementazione di `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` per il gruppo corrispondente.  
  
## <a name="to-implement-ide-support"></a>Per implementare il supporto dell'IDE  
  
- Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A> , che restituisce un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interfaccia o un' `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interfaccia per l'IDE per ogni **categoria** o GUID di gruppo fornito.  
  
- Per ogni **categoria** supportata, un pacchetto VSPackage implementa un'istanza separata dell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interfaccia.  
  
- I metodi implementati tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> devono fornire l'IDE con:  
  
  - Elenchi di **elementi visualizzati** nella **categoria.**  
  
  - Nomi localizzabili per **gli elementi visualizzati**.  
  
  - Visualizza le informazioni per ogni membro di **categoria**.  
  
  > [!NOTE]
  > Ogni **categoria** deve contenere almeno un **elemento visualizzato**.  
  
- L'IDE utilizza l' `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interfaccia per definire un'Unione di diverse categorie.  
  
   La relativa implementazione fornisce l'IDE con:  
  
  - Elenco delle **categorie** che costituiscono un determinato gruppo.  
  
  - Accesso alle istanze di che <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> supportano ogni **categoria** all'interno del gruppo.  
  
  - Nomi dei gruppi localizzabili.  
  
- Aggiornamento dell'IDE:  
  
   L'IDE memorizza nella cache le informazioni sulle impostazioni del **tipo di carattere e del colore** . Quindi, dopo la modifica della configurazione del **tipo di carattere e del colore** dell'IDE, è consigliabile assicurarsi che la cache sia aggiornata.  
  
  L'aggiornamento della cache viene eseguito tramite l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaccia e può essere eseguito a livello globale o solo in elementi selezionati.  
  
## <a name="to-handle-font-and-color-changes"></a>Per gestire le modifiche ai tipi di carattere e ai colori  
 Per supportare correttamente la colorazione del testo visualizzato da un pacchetto VSPackage, il servizio di colorazione che supporta il pacchetto VSPackage deve rispondere alle modifiche avviate dall'utente apportate tramite la pagina delle proprietà **tipi di carattere e colori** . Un pacchetto VSPackage esegue questa operazione per:  
  
- Gestione degli eventi generati dall'IDE implementando l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> interfaccia.  
  
     L'IDE chiama il metodo appropriato che segue le modifiche dell'utente della pagina **tipi di carattere e colori** . Ad esempio, chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> metodo se viene selezionato un nuovo tipo di carattere.  
  
     -oppure-  
  
- Polling dell'IDE per le modifiche.  
  
     Questa operazione può essere eseguita tramite l'interfaccia implementata dal sistema <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> . Sebbene principalmente per il supporto della persistenza, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> metodo può essere utilizzato per ottenere informazioni relative al tipo di carattere e al colore per **gli elementi visualizzati**. Per ulteriori informazioni, vedere [accesso alle impostazioni dei tipi di carattere e dei colori archiviati](../extensibility/accessing-stored-font-and-color-settings.md).  
  
    > [!NOTE]
    > Per assicurarsi che i risultati ottenuti dal polling siano corretti, può essere utile usare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaccia per determinare se sono necessari uno scaricamento della cache e un aggiornamento prima di chiamare i metodi di recupero dell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [Recupero delle informazioni sui colori e sui tipi di carattere per la colorazione del testo](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Accesso alle impostazioni dei tipi di carattere e dei colori archiviati](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Procedura: accedere ai tipi di carattere e alla combinazione di colori predefiniti](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [Panoramica di tipi di carattere e colori](../extensibility/font-and-color-overview.md)
