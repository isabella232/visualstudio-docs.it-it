---
title: Configurazioni e piattaforme supportate per i test codificati dell'interfaccia utente e le registrazioni delle azioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests
ms.assetid: 544742b5-4ec1-4d51-b941-72b2f6ff17bc
caps.latest.revision: 108
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 978979cfa7b374c7f1247a0ce582548ef1e87022
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705961"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>Configurazioni e piattaforme supportate per i test codificati dell'interfaccia utente e le registrazioni delle azioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La tabella seguente riporta le configurazioni e le piattaforme supportate per i test codificati dell'interfaccia utente per Visual Studio Enterprise. Queste configurazioni si applicano anche alle registrazioni delle azioni create tramite [!INCLUDE[MTRlong](../includes/mtrlong-md.md)].  
  
> [!NOTE]
> Il processo del test codificato dell'interfaccia utente deve avere gli stessi privilegi dell'applicazione sottoposta a test.  
  
 **Requisiti**  
  
- Visual Studio Enterprise  
  
## <a name="supported-configurations"></a>Configurazioni supportate  
  
|Configurazione|Supportato|  
|-------------------|---------------|  
|Sistemi operativi|[!INCLUDE[win7](../includes/win7-md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)]<br /><br /> [!INCLUDE[win8](../includes/win8-md.md)]<br /><br /> Windows 10|  
|Supporto a 32 bit / 64 bit|Le applicazioni a 32 bit possono essere testate nel sistema operativo Windows a 32 bit che esegue [!INCLUDE[TCMext](../includes/tcmext-md.md)] a 32 bit.<br /><br /> Le applicazioni WOW a 32 bit con Sincronizzazione dell'interfaccia utente possono essere testate nel sistema operativo Windows a 64 bit che esegue [!INCLUDE[TCMext](../includes/tcmext-md.md)] a 32 bit.<br /><br /> Le applicazioni Windows Form e WPF a 64 bit prive di Sincronizzazione dell'interfaccia utente possono essere testate nel sistema operativo Windows a 64 bit che esegue [!INCLUDE[TCMext](../includes/tcmext-md.md)] a 32 bit.|  
|Architettura|x86 e x64 **Nota:**  Internet Explorer non è supportato in modalità a 64 bit se non è in esecuzione in [!INCLUDE[win8](../includes/win8-md.md)] o versioni successive.|  
|.NET|.NET 2.0, 3.0, 3.5, 4 e 4.5. **Nota:**  [!INCLUDE[TCMext](../includes/tcmext-md.md)] e Visual Studio richiedono entrambi .NET 4. Tuttavia, le applicazioni sviluppate tramite le versioni di .NET elencate sono supportate.|  
  
> [!NOTE]
> *Sincronizzazione dell'interfaccia utente* è una funzionalità in cui la riproduzione viene verificata nella coda messaggi di ogni controllo. Se un controllo non risponde all'evento ricevuto, quest'ultimo viene nuovamente inviato.  
  
## <a name="platform-support"></a>Supporto per piattaforme  
  
|Piattaforma|Livello di supporto|  
|--------------|----------------------|  
|App di Windows Phone|Sono supportate solo le app Phone basate su WinRT-XAML.|  
|App di Windows Store|Sono supportate solo le app Store basate su XAML.|  
|App di Windows universale|Sono supportate solo le app di Windows universale basate su XAML per desktop e telefono.|  
|Microsoft Edge|In Visual Studio 2015 Update 2 e versioni successive mediante l'[estensione di test codificato dell'interfaccia utente tra browser](https://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d)|  
|Internet Explorer 8<br /><br /> Internet Explorer 9<br /><br /> Internet Explorer 10 **Importante:**  Internet Explorer 10 è supportato solo su desktop. <br /><br /> Internet Explorer 11 **Importante:**  Internet Explorer 11 è supportato solo su desktop.|Completamente supportato.<br /><br /> -   **Supporto di HTML5 in Internet Explorer 9 e Internet Explorer 10:** i test codificati dell'interfaccia supportano la registrazione, la riproduzione e la convalida dei controlli HTML5 seguenti: Audio, Video, ProgressBar e Slider. Per altre informazioni, vedere [Uso dei controlli HTML5 nei test codificati dell'interfaccia utente](../test/using-html5-controls-in-coded-ui-tests.md). **Avviso:**      Un test codificato dell'interfaccia utente creato in Internet Explorer 10 potrebbe non funzionare in Internet Explorer 9 o Internet Explorer 8. Questo perché Internet Explorer 10 include controlli HTML5 come audio, video, ProgressBar e dispositivo di scorrimento. Questi controlli HTML5 non sono riconosciuti da Internet Explorer 9 o da Internet Explorer 8. Analogamente, il test codificato dell'interfaccia utente creato in Internet Explorer 9 potrebbe includere alcuni controlli HTML5 non riconosciuti in Internet Explorer 8.<br />-   **Supporto per il controllo ortografico di Internet Explorer 10:** Internet Explorer 10 include funzionalità di controllo ortografico per tutte le caselle di testo. In tal modo è possibile scegliere da un elenco di correzioni suggerite. Il test codificato dell'interfaccia utente ignorerà le azioni dell'utente, come ad esempio la selezione di un suggerimento alternativo di ortografia. Solo il testo finale digitato nella casella di testo verrà registrato.<br />     Per il test codificato dell'interfaccia utente che usa il controllo ortografico, vengono registrate le azioni seguenti: Aggiungi al dizionario, Copia, Seleziona tutto e Ignora.<br />-   **Supporto per Internet Explorer a 64 bit in esecuzione in Windows 8:** in precedenza, le versioni a 64 bit di Internet Explorer non erano supportate per la registrazione e la riproduzione. Con [!INCLUDE[win8](../includes/win8-md.md)] e [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], i test codificati dell'interfaccia utente sono stati abilitati per le versioni a 64 bit di Internet Explorer. **Avviso:**      Il supporto a 64 bit in Internet Explorer si applica solo quando si esegue [!INCLUDE[win8](../includes/win8-md.md)] o versioni successive.<br />-   **Supporto per i siti aggiunti in Internet Explorer 9:** i siti aggiunti sono stati introdotti in Internet Explorer 9. Con i siti aggiunti è possibile accedere ai siti preferiti direttamente dalla barra delle applicazioni di Windows, senza dover prima aprire Internet Explorer. I test codificati dell'interfaccia utente possono ora generare azioni di intenzione sui siti aggiunti. Per altre informazioni sui siti aggiunti, vedere [Siti aggiunti](http://go.microsoft.com/fwlink/?LinkId=220037).<br />-   **Supporto per i tag semantici in Internet Explorer 9:** con Internet Explorer 9 sono stati introdotti i seguenti tag semantici: section, nav, article, aside, hgroup, header, footer, figure, figcaption e mark. I test codificati dell'interfaccia utente ignorano tutti questi tag semantici durante la registrazione. È possibile aggiungere asserzioni a questi tag usando il generatore di test codificati dell'interfaccia utente. È possibile usare il riquadro di navigazione nel generatore di test codificati dell'interfaccia utente per passare a uno di questi elementi e visualizzarne le proprietà.<br />-   **Gestione facilitata degli spazi vuoti tra le versioni di Internet Explorer:** esistono alcune differenze nella gestione degli spazi vuoti in Internet Explorer 8, Internet Explorer 9 e Internet Explorer 10. Il test codificato dell'interfaccia utente gestisce le differenze senza problemi. Un test codificato dell'interfaccia utente creato in Internet Explorer 8 ad esempio, viene quindi riprodotto correttamente in Internet Explorer 9 e in Internet Explorer 10.<br />-   **Area di notifica di Internet Explorer vengono registrate con l'attributo "Continua in caso di errore" impostato:** Tutte le azioni sull'Area di notifica di Internet Explorer vengono registrate con l'attributo "Continua in caso di errore" impostato. Se la barra di notifica non viene visualizzata durante la riproduzione, le azioni verranno ignorate e il test codificato dell'interfaccia utente proseguirà con l'azione successiva.|  
|Controlli di terze parti WPF e Windows Forms|Completamente supportato.<br /><br /> Per abilitare i controlli di terze parti nelle applicazioni Windows Form e WPF, è necessario aggiungere i riferimenti e il codice. Per altre informazioni, vedere la pagina [Abilitare il test codificato dell'interfaccia utente per i controlli](../test/enable-coded-ui-testing-of-your-controls.md).|  
|Internet Explorer 6<br /><br /> Internet Explorer 7|Non supportato.|  
|Chrome<br /><br /> Firefox|La registrazione dei passaggi delle azioni non è supportata. I test codificati dell'interfaccia utente possono essere riprodotti nei browser Chrome e Firefox con Visual Studio 2012 Update 4 o versioni successive. Per altre informazioni, fare clic [qui](https://msdn.microsoft.com/library/jj835758.aspx) .|  
|Opera<br /><br /> Safari|Non supportato.|  
|Silverlight|Non supportato.<br /><br /> Per Visual Studo 2013, tuttavia, è possibile scaricare il [plug-in del test codificato dell'interfaccia utente Microsoft Visual Studio 2013 per Silverlight](https://go.microsoft.com/fwlink/?LinkId=691026) da Visual Studio Gallery.|  
|Flash/Java|Non supportato.|  
|Windows Form 2.0 e versioni successive|Completamente supportato. **Nota:**  I controlli NetFx sono completamente supportati, ma non tutti i controlli di terze parti sono supportati.|  
|WPF 3.5 e versioni successive|Completamente supportato.<br /><br /> **Nota** I controlli NetFx sono completamente supportati, ma non tutti i controlli di terze parti sono supportati.|  
|Windows Win32|Può essere usato ma presenta alcuni problemi noti. Non è ufficialmente supportato.|  
|MFC|Parzialmente supportato. Per informazioni dettagliate sulle funzionalità supportate, vedere il [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkId=206511) .|  
|SharePoint|Completamente supportato.|  
|Applicazioni client di Office|Non supportato.|  
|Client Web di Dynamics CRM|Completamente supportato.|  
|Client di Dynamics (Ax) 2012|La registrazione e la riproduzione delle azioni sono parzialmente supportate. Per altre informazioni, vedere il [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkId=232677) seguente.|  
|SAP|Non supportato.|  
|Servizi Citrix/terminal|La registrazione delle azioni in un server terminal non è consigliabile. Il registratore non supporta l'esecuzione di più istanze nello stesso momento.|  
|PowerBuilder|Parzialmente supportato.<br /><br /> Il supporto di accessibilità di ambito è abilitato per i controlli di PowerBuilder.|  
  
 Per altre informazioni sulla creazione di estensioni per supportare altre piattaforme, vedere [Abilitare il test codificato dell'interfaccia utente per i controlli](../test/enable-coded-ui-testing-of-your-controls.md) ed [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)   
 [Generazione di un test codificato dell'interfaccia utente da una registrazione delle azioni esistente](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497)
