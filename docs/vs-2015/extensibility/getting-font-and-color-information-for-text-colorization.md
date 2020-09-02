---
title: Recupero delle informazioni sui colori e sui tipi di carattere per la colorazione del testo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8724c31accb26e478c2726dfe791256994fc95ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696850"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Recupero di informazioni su tipi di carattere e colori per la colorazione del testo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il processo che esegue il rendering o la visualizzazione di testo colorato negli elementi dell'interfaccia utente dipende dal tipo di progetto, dalla relativa tecnologia e dalle preferenze per gli sviluppatori. La pagina delle proprietà **tipi di carattere e colori** archivia le impostazioni.  
  
 Per la maggior parte delle implementazioni che visualizzano testo colorato sono necessarie le `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` interfacce e associate per la presentazione, il recupero e l'archiviazione delle impostazioni di visualizzazione del testo.  
  
> [!NOTE]
> Quando si Personalizza l'editor principale (che supporta il **testo EditorCategory**), si consiglia vivamente di utilizzare la tecnologia di colorazione nel servizio di linguaggio. Per ulteriori informazioni, vedere [Cenni preliminari su tipo di carattere e colore](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Recupero delle informazioni predefinite sui tipi di carattere e sui colori  
 Tutte le impostazioni relative ai **tipi di carattere e ai colori** di qualsiasi finestra che Visualizza il testo devono essere specificate negli **elementi visualizzati** di una **categoria**. Per ulteriori informazioni, vedere [tipi di carattere e colori, ambiente, finestra di dialogo Opzioni](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Per colorare, un pacchetto VSPackage deve ottenere le impostazioni correnti relative ai **tipi di carattere e ai colori** . Un pacchetto VSPackage può eseguire questa operazione nei modi seguenti, a seconda delle esigenze:  
  
- Usare il meccanismo di persistenza dei tipi di carattere e dei colori per recuperare lo stato archiviato o corrente. Per ulteriori informazioni, vedere [accesso alle impostazioni dei tipi di carattere e dei colori archiviati](../extensibility/accessing-stored-font-and-color-settings.md).  
  
- Usare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfaccia di un servizio fornendo dati di tipo carattere e colore per ottenere un'istanza di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> , se il pacchetto VSPackage non è anche il provider di tipi di carattere e colori.  
  
- Implementare l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>.  
  
  Per assicurarsi che i risultati ottenuti dal polling siano aggiornati, può essere utile utilizzare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaccia per determinare se è necessario un aggiornamento prima di chiamare i metodi di recupero dell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia.  
  
  Una volta ottenute le informazioni relative al tipo di carattere e al colore, analizzare il testo da visualizzare per identificare gli elementi che richiedono la colorazione e quindi visualizzare il testo nella finestra utilizzando i tipi di carattere e i colori appropriati.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Uso di tipi di carattere e testo](https://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Uso del colore](https://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [GDI (Graphics Device Interface)](https://msdn.microsoft.com/7e1d4540-bb2e-4257-8eee-eee376acba83)
