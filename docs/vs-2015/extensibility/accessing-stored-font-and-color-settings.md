---
title: L'accesso a tipo di carattere archiviata e le impostazioni dei colori | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bab850a6943268581035336a923232377e6489f2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843678"
---
# <a name="accessing-stored-font-and-color-settings"></a>L'accesso a tipo di carattere archiviata e le impostazioni dei colori
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ambiente di sviluppo integrato (IDE) archivia le impostazioni modificate per i tipi di carattere e colori nel Registro di sistema. È possibile usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia per accedere a queste impostazioni.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Per avviare la persistenza dello stato dei tipi di carattere e colori  
 Le informazioni di carattere e colori vengono archiviate in base alla categoria nel percorso seguente del Registro di sistema: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<versione di Visual Studio >* \FontAndColors\\  *\<CategoryGUID >*], dove  *\<CategoryGUID >* è il GUID della categoria.  
  
 Pertanto, per avviare la persistenza, un pacchetto VSPackage deve:  
  
-   Ottenere un <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia chiamando `QueryService` sul provider di servizi globale.  
  
     `QueryService` deve essere chiamato utilizzando un argomento di ID di servizio del `SID_SVsFontAndColorStorage` e un argomento di ID di interfaccia di `IID_IVsFontAndColorStorage`.  
  
-   Usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> metodo per aprire una categoria per essere resa persistente usando il GUID della categoria e un flag di modalità come argomenti.  
  
     La modalità, specificata dal `fFlags` argomento, viene costruito dai valori di <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> enumerazione. Questa modalità consente di controllare:  
  
    -   Le impostazioni che è possibile accedere tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia.  
  
    -   Tutte le impostazioni o solo quelle che gli utenti di modificare e sono recuperabili tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia.  
  
    -   Il modo di propagare le modifiche alle impostazioni dell'utente.  
  
    -   Il formato dei valori di colore che vengono usati.  
  
## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Usare la persistenza dello stato dei tipi di carattere e colori  
 Rendere persistenti i tipi di carattere e colori comporta:  
  
- Sincronizzare le impostazioni IDE con impostazioni archiviate nel Registro di sistema.  
  
- La propagazione di informazioni sulla modifica del Registro di sistema.  
  
- L'impostazione e recupero delle impostazioni archiviate nel Registro di sistema.  
  
  La sincronizzazione delle impostazione di archiviazione con le impostazioni IDE è in gran parte trasparente. L'IDE sottostante scrive automaticamente le impostazioni aggiornate per **elementi visualizzati** alle voci del Registro di sistema delle categorie.  
  
  Se più pacchetti VSPackage condividono una determinata categoria, un pacchetto VSPackage richiede che gli eventi vengono generati quando i metodi del <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia vengono utilizzati per modificare le impostazioni del Registro di sistema archiviati.  
  
  Per impostazione predefinita, non è abilitata la generazione di eventi. Per abilitare la generazione di eventi, una categoria deve essere aperto usando <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>. In questo modo, l'IDE chiamare appropriato <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> metodo che implementa un pacchetto VSPackage.  
  
> [!NOTE]
>  Modifica dei dati mediante la **carattere e colori** pagina delle proprietà generano eventi indipendenti di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>. È possibile usare la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> per determinare se un aggiornamento delle impostazioni di carattere e colori memorizzato nella cache è necessaria prima di chiamare i metodi di interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> classe.  
  
### <a name="storing-and-retrieving-information"></a>L'archiviazione e recupero delle informazioni  
 Per ottenere o configurare le informazioni che un utente può modificare per un elemento visualizzato denominato in una categoria aperta, pacchetti VSPackage chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> metodi.  
  
 Informazioni sul tipo di carattere degli attributi per una determinata categoria verrà ottenuta tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> metodi.  
  
> [!NOTE]
>  Il `fFlags` argomento passato per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> metodo quando è stato aperto tale categoria definisce il comportamento del <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> e il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> metodi. Per impostazione predefinita, questi itemsthat aboutdisplay restituiscono solo le informazioni di metodi sono stati modificati. Tuttavia, se una categoria è stata aperta tramite il <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> flag, sia aggiornato ed sono accessibile elementi visualizzati invariati dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.  
  
 Per impostazione predefinita, solo modificata **elementi visualizzati** informazioni vengono mantenute nel Registro di sistema. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia non può essere usata per recuperare tutte le impostazioni per i tipi di carattere e colori.  
  
> [!NOTE]
>  Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> e il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> metodi restituiscono REGDB_E_KEYMISSING, (0x80040152L) quando vengono utilizzati per recuperare informazioni su non modificato **elementi visualizzati**.  
  
 Le impostazioni di tutte le **elementi visualizzati** in un particolare **categoria** può essere ottenuto utilizzando i metodi del `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [Implementazione di categorie ed elementi di visualizzazione personalizzati](../extensibility/implementing-custom-categories-and-display-items.md)

