---
title: Recuperare le informazioni di colore per la colorazione del testo e carattere | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 49b1fbf18fb0dac23fcc55b7d9765dd4d1a88d32
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499699"
---
# <a name="get-font-and-color-information-for-text-colorization"></a>Ottenere le informazioni di carattere e colori per la colorazione del testo
Il processo che esegue il rendering o Visualizza colorato testo negli elementi dell'interfaccia utente dipende dal tipo di progetto, la tecnologia e per gli sviluppatori preferenze. Il **Fonts and Colors** pagina delle proprietà vengono archiviate le impostazioni.

 La maggior parte delle implementazioni che visualizzano testo colorato necessario il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> e associate le interfacce per la presentazione, recuperare e archiviare il testo delle impostazioni di visualizzazione.

> [!NOTE]
>  Quando si personalizza l'editor principale (che supporta il **EditorCategory testo**), è consigliabile usare la tecnologia di colorazione del servizio di linguaggio. Per altre informazioni, vedere [Panoramica di carattere e colori](../extensibility/font-and-color-overview.md).

## <a name="get-default-font-and-color-information"></a>Ottenere le informazioni di carattere e colori predefinite
 Tutti i **i tipi di carattere e colori** le impostazioni di qualsiasi finestra di visualizzazione di testo devono essere specificate nel **elementi visualizzati** di uno **categoria**. Per altre informazioni, vedere [tipi di carattere e colori, ambiente, finestra di dialogo Opzioni](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).

Per colorare, un pacchetto VSPackage deve ottenere corrente **Fonts and Colors** impostazioni. Un pacchetto VSPackage può ottenere le impostazioni correnti nei modi seguenti, a seconda delle esigenze:

-   Usare il meccanismo di persistenza di carattere e colori per recuperare lo stato corrente o archiviato. Per altre informazioni, vedere [accesso archiviate le impostazioni del tipo di carattere e colore](../extensibility/accessing-stored-font-and-color-settings.md).

-   Usare la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfaccia di un servizio che fornisce i dati di carattere e colori per ottenere un'istanza di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, se il pacchetto VSPackage non sia anche il provider di tipi di carattere e colore.

-   Implementare l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>.

Per garantire che i risultati ottenuti eseguendo il polling vengono aggiornate, può essere utile usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaccia per determinare se è necessario un aggiornamento prima di chiamare i metodi di recupero del <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia.

Dopo aver ottenuto le informazioni di carattere e colori, analizzare il testo da visualizzare per identificare gli elementi che richiedono la colorazione. Visualizzare il testo della finestra utilizzando i tipi di carattere appropriati e i colori.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- [Usare i tipi di carattere e testo](/dotnet/framework/winforms/advanced/using-fonts-and-text)
- [Utilizzare i colori](/cpp/windows/working-with-color-image-editor-for-icons)
- [GDI (interfaccia graphics device)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)