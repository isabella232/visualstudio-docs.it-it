---
title: Accesso alle impostazioni dei tipi di carattere e dei colori archiviati | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fbb2f118d903eae2124e705f14c7aa7b51bf9c4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821834"
---
# <a name="accessing-stored-font-and-color-settings"></a>Accesso alle impostazioni di tipi di carattere e colori archiviate
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Integrated Development Environment (IDE) archivia le impostazioni modificate per i tipi di carattere e i colori nel registro di sistema. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>Per accedere a queste impostazioni, è possibile usare l'interfaccia.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Per avviare la persistenza dello stato di tipi di carattere e colori  
 Le informazioni relative al tipo di carattere e ai colori vengono archiviate per categoria nel seguente percorso del registro di sistema: [HKCU\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<CategoryGUID>* ], dove *\<CategoryGUID>* è il GUID della categoria.  
  
 Pertanto, per avviare la persistenza, un pacchetto VSPackage deve:  
  
- Ottenere un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia chiamando `QueryService` il provider di servizi globale.  
  
     `QueryService` deve essere chiamato utilizzando un argomento ID del servizio `SID_SVsFontAndColorStorage` e un argomento ID di interfaccia di `IID_IVsFontAndColorStorage` .  
  
- Usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> metodo per aprire una categoria da salvare in modo permanente usando il GUID e un flag della categoria come argomenti.  
  
  La modalità, specificata dall' `fFlags` argomento, viene costruita dai valori dell' <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> enumerazione. Questa modalità controlla:  

  - Impostazioni a cui è possibile accedere tramite l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia.  

  - Tutte le impostazioni o solo quelle che gli utenti modificano e che possono essere recuperate tramite l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia.  

  - Modalità di propagazione delle modifiche alle impostazioni utente.  

  - Formato dei valori di colore utilizzati.  

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Per utilizzare la persistenza dello stato di tipi di carattere e colori  
 Il salvataggio permanente di tipi di carattere e colori comporta:  
  
- Sincronizzazione delle impostazioni dell'IDE con le impostazioni archiviate nel registro di sistema.  
  
- Propagazione delle informazioni sulla modifica del registro di sistema.  
  
- Impostazione e recupero delle impostazioni archiviate nel registro di sistema.  
  
  La sincronizzazione dell'impostazione di archiviazione con le impostazioni dell'IDE è in gran parte trasparente. L'IDE sottostante scrive automaticamente le impostazioni aggiornate per **gli elementi visualizzati** nelle voci del registro di sistema delle categorie.  
  
  Se più VSPackage condividono una particolare categoria, un pacchetto VSPackage deve richiedere che vengano generati eventi quando vengono usati i metodi dell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia per modificare le impostazioni del registro di sistema archiviate.  
  
  Per impostazione predefinita, la generazione di eventi non è abilitata. Per abilitare la generazione di eventi, è necessario aprire una categoria utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> . In questo modo l'IDE chiamerà il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> metodo appropriato implementato da un pacchetto VSPackage.  
  
> [!NOTE]
> Le modifiche apportate alla pagina delle proprietà **tipo di carattere e colore** generano eventi indipendenti da <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> . È possibile utilizzare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaccia per determinare se è necessario un aggiornamento delle impostazioni del tipo di carattere e dei colori memorizzati nella cache prima di chiamare i metodi della <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> classe.  
  
### <a name="storing-and-retrieving-information"></a>Archiviazione e recupero di informazioni  
 Per ottenere o configurare le informazioni che un utente può modificare per un elemento visualizzato denominato in una categoria aperta, i pacchetti VSPackage chiamano i <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> metodi e.  
  
 Le informazioni sugli attributi del tipo di carattere per una determinata categoria vengono ottenute usando i <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> metodi e.  
  
> [!NOTE]
> L' `fFlags` argomento passato al <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> metodo quando tale categoria è stata aperta definisce il comportamento dei <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> metodi e. Per impostazione predefinita, questi metodi restituiscono solo le informazioni aboutdisplay itemsthat sono state modificate. Tuttavia, se una categoria viene aperta utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> flag, è possibile accedere agli elementi visualizzati sia aggiornati che non modificati mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> .  
  
 Per impostazione predefinita, nel registro di sistema vengono mantenute solo le informazioni relative agli **elementi di visualizzazione** modificate. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>Non è possibile usare l'interfaccia per recuperare tutte le impostazioni per i tipi di carattere e i colori.  
  
> [!NOTE]
> I <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> metodi e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> restituiscono REGDB_E_KEYMISSING (0x80040152L) quando vengono utilizzati per recuperare informazioni sugli **elementi visualizzati**non modificati.  
  
 È possibile ottenere le impostazioni di tutti **gli elementi visualizzati** in una determinata **categoria** utilizzando i metodi dell' `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [Implementazione di categorie ed elementi di visualizzazione personalizzati](../extensibility/implementing-custom-categories-and-display-items.md)
