---
title: Configurazioni e piattaforme per i test codificati dell'interfaccia utente
description: Questo articolo contiene le configurazioni e le piattaforme supportate per i test codificati dell'interfaccia utente per Visual Studio Enterprise.
ms.custom: SEO-VS-2020
ms.date: 10/04/2015
ms.topic: reference
helpviewer_keywords:
- coded UI tests
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: b65d5a3f761f0e10eb95fef0122730a72978aa3a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092274"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>Configurazioni e piattaforme supportate per i test codificati dell'interfaccia utente e le registrazioni delle azioni

La tabella seguente riporta le configurazioni e le piattaforme supportate per i test codificati dell'interfaccia utente per Visual Studio Enterprise. Queste configurazioni si applicano anche alle registrazioni delle azioni create tramite [!INCLUDE[MTRlong](../test/includes/mtrlong_md.md)].

> [!NOTE]
> Il processo del test codificato dell'interfaccia utente deve avere gli stessi privilegi dell'applicazione sottoposta a test.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Requisiti**

- Visual Studio Enterprise

## <a name="supported-configurations"></a>Configurazioni supportate

| Configurazione | Supportato |
|-| - |
| Sistemi operativi | [!INCLUDE[win7](../debugger/includes/win7_md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]<br /><br /> [!INCLUDE[win8](../debugger/includes/win8_md.md)]<br /><br /> Windows 10 |
| Supporto a 32 bit / 64 bit | Le applicazioni a 32 bit possono essere testate nel sistema operativo Windows a 32 bit che esegue [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] a 32 bit.<br /><br /> Le applicazioni WOW a 32 bit con Sincronizzazione dell'interfaccia utente possono essere testate nel sistema operativo Windows a 64 bit che esegue [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] a 32 bit.<br /><br /> Le applicazioni Windows Form e WPF a 64 bit prive di Sincronizzazione dell'interfaccia utente possono essere testate nel sistema operativo Windows a 64 bit che esegue [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] a 32 bit. |
| Architettura | x86 e x64 **Nota:** Internet Explorer non è supportato in modalità a 64 bit se non è in esecuzione in [!INCLUDE[win8](../debugger/includes/win8_md.md)] o versioni successive. |
| .NET | .NET 2.0, 3.0, 3.5, 4 e 4.5. **Nota:**  [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] e Visual Studio richiedono entrambi .NET 4. Tuttavia, le applicazioni sviluppate tramite le versioni di .NET elencate sono supportate. |

> [!NOTE]
> *Sincronizzazione dell'interfaccia utente* è una funzionalità in cui la riproduzione viene verificata nella coda messaggi di ogni controllo. Se un controllo non risponde all'evento ricevuto, quest'ultimo viene nuovamente inviato.

## <a name="platform-support"></a>Piattaforme supportate

| Piattaforma | Livello di supporto |
|-| - |
| App di Windows Phone | Sono supportate solo le app Phone basate su WinRT-XAML. |
| App UWP | Sono supportate solo le app UWP basate su XAML. |
| App di Windows universale | Sono supportate solo le app di Windows universale basate su XAML per desktop e telefono. |
| Microsoft Edge | La registrazione dei passaggi dell'azione o l'utilizzo del generatore per la visualizzazione delle proprietà dell'oggetto non è supportata. I test possono essere riprodotti nel browser Edge usando Visual Studio 2015 Update 2 e versioni successive usando l'estensione [coded ui cross browser testing .](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting) |
| Internet Explorer 8<br /><br /> Internet Explorer 9<br /><br /> Internet Explorer 10 **Importante:**  Internet Explorer 10 è supportato solo su desktop. <br /><br /> Internet Explorer 11 **Importante:**  Internet Explorer 11 è supportato solo su desktop. | Completamente supportato.<br /><br /> -   **Supporto per HTML5 in Internet Explorer 9 e Internet Explorer 10:** I test codificati dell'interfaccia utente supportano la registrazione, la riproduzione e la convalida dei controlli HTML5: Audio, Video, ProgressBar e Slider. Per altre informazioni, vedere Uso [di controlli HTML5 nei test codificati dell'interfaccia utente.](../test/using-html5-controls-in-coded-ui-tests.md) **Avviso:**      Un test codificato dell'interfaccia utente creato in Internet Explorer 10 potrebbe non funzionare in Internet Explorer 9 o Internet Explorer 8. Questo perché Internet Explorer 10 include controlli HTML5 come audio, video, ProgressBar e dispositivo di scorrimento. Questi controlli HTML5 non sono riconosciuti da Internet Explorer 9 o da Internet Explorer 8. Analogamente, il test codificato dell'interfaccia utente creato in Internet Explorer 9 potrebbe includere alcuni controlli HTML5 non riconosciuti in Internet Explorer 8.<br />-   **Supporto per il Internet Explorer 10 ortografico: Internet Explorer 10** funzionalità di controllo ortografico per tutte le caselle di testo. In tal modo è possibile scegliere da un elenco di correzioni suggerite. Il test codificato dell'interfaccia utente ignorerà le azioni dell'utente, come ad esempio la selezione di un suggerimento alternativo di ortografia. Solo il testo finale digitato nella casella di testo verrà registrato.<br />     Per il test codificato dell'interfaccia utente che usa il controllo ortografico vengono registrate le azioni seguenti: Aggiungi al dizionario, Copia, Seleziona tutto e Ignora.<br />-   **Supporto per le applicazioni a 64 bit Internet Explorer in esecuzione in Windows 8:** In precedenza, le versioni a 64 bit Internet Explorer non erano supportate per la registrazione e la riproduzione. Con [!INCLUDE[win8](../debugger/includes/win8_md.md)] e [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], i test codificati dell'interfaccia utente sono stati abilitati per le versioni a 64 bit di Internet Explorer. **Avviso:**      Il supporto a 64 bit in Internet Explorer si applica solo quando si esegue [!INCLUDE[win8](../debugger/includes/win8_md.md)] o versioni successive.<br />-   **Supporto per siti aggiunti in Internet Explorer 9:** In Internet Explorer 9 sono stati introdotti siti aggiunti. Con i siti aggiunti è possibile accedere ai siti preferiti direttamente dalla barra delle applicazioni di Windows, senza dover prima aprire Internet Explorer. I test codificati dell'interfaccia utente possono ora generare azioni di intenzione sui siti aggiunti. Per altre informazioni sui siti aggiunti, vedere [Siti aggiunti.](https://support.microsoft.com/hub/4230784/internet-explorer-help)<br />-   **Supporto per Internet Explorer 9 tag semantici:** Internet Explorer 9 ha introdotto i tag semantici seguenti: section, nav, article, aside, hgroup, header, footer, figure, figcaption e mark. I test codificati dell'interfaccia utente ignorano tutti questi tag semantici durante la registrazione. È possibile aggiungere asserzioni a questi tag usando il generatore di test codificati dell'interfaccia utente. È possibile usare il riquadro di navigazione nel generatore di test codificati dell'interfaccia utente per passare a uno di questi elementi e visualizzarne le proprietà.<br />-   **Facile gestione degli spazi vuoti tra le versioni di Internet Explorer:** Esistono differenze nella gestione degli spazi vuoti tra Internet Explorer 8, Internet Explorer 9 e Internet Explorer 10. Il test codificato dell'interfaccia utente gestisce le differenze senza problemi. Un test codificato dell'interfaccia utente creato in Internet Explorer 8 ad esempio, viene quindi riprodotto correttamente in Internet Explorer 9 e in Internet Explorer 10.<br />-   **L'area di notifica Internet Explorer vengono ora registrate con** il set di attributi "Continue on Error": Tutte le azioni nell'area di notifica Internet Explorer ora vengono registrate con l'attributo "Continue on Error" impostato. Se la barra di notifica non viene visualizzata durante la riproduzione, le azioni verranno ignorate e il test codificato dell'interfaccia utente proseguirà con l'azione successiva. |
| Controlli di terze parti WPF e Windows Forms | Completamente supportato.<br /><br /> Per abilitare i controlli di terze parti nelle applicazioni Windows Form e WPF, è necessario aggiungere i riferimenti e il codice. Per altre informazioni, vedere la pagina [Abilitare test codificati dell'interfaccia utente per i controlli](../test/enable-coded-ui-testing-of-your-controls.md). |
| Internet Explorer 6<br /><br /> Internet Explorer 7 | Non supportata. |
| Chrome<br /><br /> Firefox | La registrazione dei passaggi delle azioni non è supportata. I test codificati dell'interfaccia utente possono essere riprodotti nei browser Chrome e Firefox con Visual Studio 2012 Update 4 o versioni successive. Per altre informazioni, fare clic [qui](using-different-web-browsers-with-coded-ui-tests.md) . |
| Opera<br /><br /> Safari | Non supportata. |
| Silverlight | Non supportata.<br /><br /> Per Visual Studo 2013 è tuttavia possibile scaricare il [plug-in del test codificato dell'interfaccia utente Microsoft Visual Studio 2013 per Silverlight](https://marketplace.visualstudio.com/items?itemName=PrachiBoraMSFT.MicrosoftVisualStudio2013CodedUITestPluginforSilve) da Visual Studio Gallery. |
| Flash/Java | Non supportata. |
| Windows Form 2.0 e versioni successive | Completamente supportato. **Nota:** i controlli NetFx sono completamente supportati, ma non tutti i controlli di terze parti sono supportati. |
| WPF 3.5 e versioni successive | Completamente supportato.<br /><br /> **Nota** I controlli NetFx sono completamente supportati, ma non tutti i controlli di terze parti sono supportati. |
| Windows Win32 | Può essere usato ma presenta alcuni problemi noti. Non è ufficialmente supportato. |
| MFC | Parzialmente supportato. Per informazioni dettagliate sulle funzionalità supportate, vedere il [framework UITest](/archive/blogs/vstsqualitytools/uitest-framework-mfc-support-in-vs-2010). |
| SharePoint | Completamente supportato. |
| Applicazioni client di Office | Non supportata. |
| Client Web di Dynamics CRM | Completamente supportato. |
| Client di Dynamics (Ax) 2012 | La registrazione e la riproduzione delle azioni sono parzialmente supportate. Per informazioni dettagliate, vedere il post relativo al [supporto dei test codificati dell'interfaccia utente e delle registrazioni delle azioni in Visual Studio 10 per Microsoft Dynamics](/archive/blogs/dave_froslie/visual-studio-10-coded-ui-action-recordings-support-for-microsoft-dynamics-ax-2012). |
| SAP | Non supportata. |
| Servizi Citrix/terminal | La registrazione delle azioni in un server terminal non è consigliabile. Il registratore non supporta l'esecuzione di più istanze nello stesso momento. |
| PowerBuilder | Parzialmente supportato.<br /><br /> Il supporto di accessibilità di ambito è abilitato per i controlli di PowerBuilder. |

Per altre informazioni sulla creazione di estensioni per supportare altre piattaforme, vedere [Abilitare test codificati dell'interfaccia utente per i controlli](../test/enable-coded-ui-testing-of-your-controls.md) ed [Estendere test codificati dell'interfaccia utente e registrazioni delle azioni](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md).

## <a name="see-also"></a>Vedi anche

- [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)