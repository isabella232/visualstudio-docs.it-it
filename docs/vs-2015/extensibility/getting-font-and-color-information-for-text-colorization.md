---
title: Recuperare le informazioni di colore per la colorazione del testo e carattere | Microsoft Docs
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
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41fc6ac7ba20bc552ebdfde2cab69dd28867ee7f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741283"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Recuperare le informazioni di colore per la colorazione del testo e del tipo di carattere
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il processo che esegue il rendering o Visualizza colorato testo negli elementi dell'interfaccia utente dipende dal tipo di progetto, la tecnologia e per gli sviluppatori preferenze. Il **Fonts and Colors** pagina delle proprietà vengono archiviate le impostazioni.  
  
 La maggior parte delle implementazioni che visualizzano testo colorato necessario il `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` e associate le interfacce per la presentazione, recuperare e archiviare il testo delle impostazioni di visualizzazione.  
  
> [!NOTE]
>  Quando si personalizza l'editor principale (che supporta il **EditorCategory testo**), è consigliabile usare la tecnologia di colorazione del servizio di linguaggio. Per altre informazioni, vedere [tipo di carattere e colore Panoramica](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Recuperare le informazioni di colore e tipo di carattere predefinito  
 Tutti i **i tipi di carattere e colori** le impostazioni di qualsiasi finestra di visualizzazione di testo devono essere specificate nel **elementi visualizzati** di uno **categoria**. Per altre informazioni, vedere [Fonts and Colors, Environment, Options Dialog Box](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Per colorare, un pacchetto VSPackage deve ottenere corrente **Fonts and Colors** impostazioni. Un pacchetto VSPackage può eseguire questa operazione nei modi seguenti, a seconda delle esigenze:  
  
- Usare il meccanismo di persistenza di carattere e colori per recuperare lo stato corrente o archiviato. Per altre informazioni, vedere [l'accesso a tipi di carattere archiviate e le impostazioni dei colori](../extensibility/accessing-stored-font-and-color-settings.md).  
  
- Usare la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfaccia di un servizio che fornisce dati di carattere e colori per ottenere un'istanza di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, se il pacchetto VSPackage non sia anche il provider di tipi di carattere e colore.  
  
- Implementare l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>.  
  
  Per garantire che i risultati ottenuti eseguendo il polling vengono aggiornate, può essere utile usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaccia per determinare se è necessario un aggiornamento prima di chiamare i metodi di recupero del <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia.  
  
  Dopo aver ottenuto le informazioni di carattere e colori, analizzare il testo da visualizzare per identificare quelli che richiedono la colorazione e quindi visualizzato il testo della finestra utilizzando i tipi di carattere appropriati e i colori.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Uso di tipi di carattere e testo](http://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Utilizzo dei colori](http://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [GDI (interfaccia graphics device)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)

