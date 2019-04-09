---
title: 'Procedura dettagliata: Acquisizione di informazioni grafiche a livello di codice | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a5adeff9-afaf-4047-b5ce-ef0aefe710eb
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bb12e0691d4e867a73b9c8999d0ad57cebd7ec44
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966943"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Procedura dettagliata: Acquisizione di informazioni grafiche a livello di codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La funzionalità Diagnostica grafica di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] consente di acquisire a livello di codice informazioni grafiche da un'app Direct3D.  
  
 L'acquisizione a livello di codice è utile in scenari quali ad esempio:  
  
-   Iniziare l'acquisizione a livello di codice quando l'app grafica non usa la presentazione della catena di scambio, ad esempio quando esegue il rendering su una trama.  
  
-   Iniziare l'acquisizione a livello di codice quando l'app non esegue il rendering, ad esempio quando usa DirectCompute per eseguire calcoli.  
  
-   Chiamare `CaptureCurrentFrame`quando un problema di rendering è difficile da prevedere e acquisire nei test manuali, ma può essere previsto a livello di codice usando le informazioni sullo stato dell'app in fase di esecuzione.  
  
##  <a name="CaptureDX11_2"></a> Acquisizione a livello di codice in Windows 8.1  
 Questa parte della procedura dettagliata illustra l'acquisizione a livello di codice nelle app che usano l'API DirectX 11.2 su Windows 8.1, che usa il metodo di acquisizione affidabile. Per informazioni sull'acquisizione a livello di codice nelle app che usano versioni precedenti di DirectX in Windows 8.0, vedere [Programmatic capture in Windows 8.0 and earlier](#CaptureDX11_1) più avanti in questa procedura dettagliata.  
  
 Questa sezione illustra l'esecuzione delle attività seguenti:  
  
-   Preparazione dell'app per usare l'acquisizione a livello di codice  
  
-   Ottenere l'interfaccia IDXGraphicsAnalysis  
  
-   Acquisizione di informazioni grafiche  
  
> [!NOTE]
>  Le implementazioni precedenti di acquisizione a livello di codice si basavano su Remote Tools per [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per fornire funzionalità di acquisizione, Windows 8.1 supporta direttamente l'acquisizione mediante Direct3D 11.2. Di conseguenza, per l'acquisizione a livello di codice in Windows 8.1 non è più necessario installare Remote Tools.  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Preparazione dell'app per usare l'acquisizione a livello di codice  
 Per usare l'acquisizione a livello di codice nell'app, deve includere le intestazioni necessarie. Queste intestazioni fanno parte di Windows 8.1 SDK.  
  
##### <a name="to-include-programmatic-capture-headers"></a>Per includere le intestazioni per l'acquisizione a livello di codice  
  
-   Includere le intestazioni nel file di origine in cui verrà definita l'interfaccia IDXGraphicsAnalysis:  
  
    ```  
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    >  Non includere l'intestazione file vsgcapture.h—which supporta l'acquisizione programmatica in Windows 8.0 e versioni precedenti, per eseguire l'acquisizione a livello di codice nelle app di Windows 8.1. Questa intestazione non è compatibile con DirectX 11.2. Se questo file è incluso dopo l'intestazione d3d11_2.h è inclusa, il compilatore genera un avviso. Se viene inclusa vsgcapture. h prima d3d11_2.h, l'app non verrà avviato.  
  
    > [!NOTE]
    >  Se nel computer è installata la versione di DirectX SDK del giugno 2010 e il percorso di inclusione del progetto contiene `%DXSDK_DIR%includex86`, spostarlo alla fine del percorso di inclusione. Eseguire la stessa operazione per il percorso della libreria.  
  
#### <a name="windows-phone-81"></a>Windows Phone 8.1  
 Perché Windows Phone 8.1 SDK non include l'intestazione dxprogrammablecapture. H, è necessario definire il `IDXGraphicsAnalysis` interfaccia manualmente in modo che è possibile usare il `BeginCapture()` e `EndCapture()` metodi. Includere altre intestazioni come descritto nella sezione precedente.  
  
###### <a name="to-define-the-idxgraphicsanalysis-interface"></a>Per definire l'interfaccia IDXGraphicsAnalysis  
  
- Definire l'interfaccia IDXGraphicsAnalysis nello stesso file in cui sono stati inclusi i file di intestazione.  
  
  ```  
  interface DECLSPEC_UUID("9f251514-9d4d-4902-9d60-18988ab7d4b5") DECLSPEC_NOVTABLE  
  IDXGraphicsAnalysis : public IUnknown  
  {  
      STDMETHOD_(void, BeginCapture)() PURE;  
      STDMETHOD_(void, EndCapture)() PURE;  
  };  
  ```  
  
  Per praticità, si possono eseguire questi passaggi in un nuovo file di intestazione e quindi includerlo nel punto dell'app in cui è necessario.  
  
### <a name="getting-the-idxgraphicsanalysis-interface"></a>Ottenere l'interfaccia IDXGraphicsAnalysis  
 Prima di poter acquisire informazioni grafiche da DirectX 11.2, è necessario ottenere l'interfaccia di debug DXGI.  
  
> [!IMPORTANT]
>  Quando si usa l'acquisizione a livello di codice, è comunque necessario eseguire l'app nella diagnostica della grafica (ALT+F5 in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]) o sotto la [strumento di acquisizione da riga di comando](../debugger/command-line-capture-tool.md).  
  
##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Per ottenere l'interfaccia IDXGraphicsAnalysis  
  
-   Usare il codice seguente per associare l'interfaccia IDXGraphicsAnalysis all'interfaccia di debug DXGI.  
  
    ```  
    IDXGraphicsAnalysis* pGraphicsAnalysis;  
    HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));  
    ```  
  
     Verificare il valore `HRESULT` restituito da `DXGIGetDebugInterface1` per assicurarsi di ottenere un'interfaccia valida prima di usarla:  
  
    ```  
    if (FAILED(getAnalysis))  
    {  
        // Abort program or disable programmatic capture in your app.  
    }  
    ```  
  
    > [!NOTE]
    >  Se si include `DXGIGetDebugInterface1` restituisce `E_NOINTERFACE` (`error: E_NOINTERFACE No such interface supported`), assicurarsi che l'app sia in esecuzione nella diagnostica grafica (ALT+F5 in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]).  
  
### <a name="capturing-graphics-information"></a>Acquisizione di informazioni grafiche  
 Ora che si dispone di un'interfaccia `IDXGraphicsAnalysis` valida, è possibile usare `BeginCapture` e `EndCapture` per acquisire informazioni grafiche.  
  
##### <a name="to-capture-graphics-information"></a>Per acquisire informazioni grafiche  
  
-   Per iniziare ad acquisire informazioni grafiche, usare `BeginCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->BeginCapture();  
    ...  
    ```  
  
     Quando viene chiamato `BeginCapture` , l'acquisizione inizia immediatamente senza aspettare l'inizio del frame successivo. L'acquisizione termina quando viene presentato il frame corrente o quando si chiama `EndCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->EndCapture();  
    ...  
    ```  
  
##  <a name="CaptureDX11_1"></a> Programmatic capture in Windows 8.0 and earlier  
 Questa parte della procedura dettagliata illustra l'acquisizione a livello di codice per Windows 8.0 e versioni precedenti che usano l'API DirectX 11.1, che usa il metodo di acquisizione legacy. Per informazioni sull'acquisizione a livello di codice nelle app che usano DirectX 11.2 in Windows 8.1, vedere [Acquisizione a livello di codice in Windows 8.1](#CaptureDX11_2) in precedenza in questa procedura dettagliata.  
  
 Questa sezione illustra le attività seguenti:  
  
-   Preparazione del computer per usare l'acquisizione a livello di codice  
  
-   Preparazione dell'app per usare l'acquisizione a livello di codice  
  
-   Configurazione del nome e del percorso del file del log di grafica  
  
-   Uso dell'API `CaptureCurrentFrame`  
  
### <a name="preparing-your-computer-to-use-programmatic-capture"></a>Preparazione del computer per usare l'acquisizione a livello di codice  
 L'API di acquisizione a livello di codice usa Remote Tools per [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per rendere disponibili funzionalità di acquisizione. Nel computer in cui verrà eseguita l'app devono essere installati gli strumenti remoti, anche se si usa l'acquisizione a livello di codice nel computer locale. Quando si usa l'acquisizione a livello di codice nel computer locale, non è necessario che[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sia in esecuzione.  
  
 Per usare le API di acquisizione remota in un'app in esecuzione in un computer, è prima di tutto necessario installare Remote Tools per [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nel computer. Versioni diverse degli strumenti remoti supportano piattaforme hardware diverse. Per informazioni su come installare gli strumenti remoti, vedere la pagina di [download di Remote Tools](http://go.microsoft.com/fwlink/p/?LinkId=246691) nel sito Web dei download Microsoft.  
  
 In alternativa, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] installa i componenti necessari per eseguire l'acquisizione remota per app a 32 bit.  
  
> [!NOTE]
>  Poiché la maggior parte delle app desktop Windows, compreso [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], non è supportata in [!INCLUDE[win8](../includes/win8-md.md)] per i dispositivi ARM, usare Remote Tools per [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] insieme all'API di acquisizione a livello di codice rappresenta l'unico modo per acquisire diagnostica grafica nei dispositivi ARM.  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Preparazione dell'app per usare l'acquisizione a livello di codice  
 Per usare gli strumenti di diagnostica grafica, occorre prima di tutto acquisire le informazioni grafiche necessarie. È possibile acquisire le informazioni a livello di codice usando l'API `CaptureCurrentFrame` .  
  
##### <a name="to-prepare-your-app-to-capture-graphics-information-programmatically"></a>Per preparare l'app all'acquisizione di informazioni grafiche a livello di codice  
  
1.  Assicurarsi che l'intestazione `vsgcapture.h` sia inclusa nel codice sorgente dell'app. Può essere inclusa in una sola posizione, ad esempio nel file di codice sorgente in cui si chiamerà l'API di acquisizione a livello di codice o in un file di intestazione precompilato per chiamare l'API da più file di codice sorgente.  
  
2.  Nel codice sorgente dell'app, ogni volta che si vuole acquisire il resto del frame corrente, chiamare `g_pVsgDbg->CaptureCurrentFrame()`. Questo metodo non accetta parametri e non restituisce un valore.  
  
### <a name="configuring-the-name-and-location-of-the-graphics-log-file"></a>Configurazione del nome e del percorso del file del log di grafica  
 Il log di grafica viene creato nel percorso definito dalle macro `DONT_SAVE_VSGLOG_TO_TEMP` e `VSG_DEFAULT_RUN_FILENAME` .  
  
##### <a name="to-configure-the-name-and-location-of-the-graphics-log-file"></a>Per configurare il nome e il percorso del file del log di grafica  
  
- Per evitare che il log di grafica venga scritto nella directory temporanea, prima della riga `#include <vsgcapture.h>` aggiungere quanto segue:  
  
  ```  
  #define DONT_SAVE_VSGLOG_TO_TEMP  
  ```  
  
   È possibile definire questo valore in modo da scrivere il log di grafica in un percorso relativo alla directory di lavoro oppure in un percorso assoluto, se la definizione di `VSG_DEFAULT_RUN_FILENAME` è un percorso assoluto.  
  
- Per salvare il log di grafica in un percorso diverso o assegnargli un nome file diverso, prima della riga `#include <vsgcapture.h>` aggiungere quanto segue:  
  
  ```  
  #define VSG_DEFAULT_RUN_FILENAME <filename>  
  ```  
  
   Se non si esegue questo passaggio, il file verrà denominato default.vsglog. Se `DONT_SAVE_VSGLOG_TO_TEMP`non è stato definito, il percorso del file è relativo alla directory temporanea. In caso contrario, è relativo alla directory di lavoro o a un'altra posizione se è stato specificato un nome file assoluto.  
  
  Per la [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] le app, il percorso della directory temporanea è specifico per ogni utente e dell'app e si trova in genere in un percorso, ad esempio C:\users\\*username*\AppData\Local\Packages\\ *nome famiglia pacchetto*\TempState\\. Per le app desktop, il percorso della directory temporanea è specifico per ogni utente e si trova in genere in un percorso, ad esempio C:\Users\\*username*\AppData\Local\Temp.\\.  
  
> [!NOTE]
>  Per scrivere in una posizione specifica è necessario disporre delle autorizzazioni per la scrittura in quella posizione. In caso contrario, si verificherà un errore. Tenere presente che le app [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] hanno più restrizioni rispetto alle app desktop sui percorsi in cui è possibile scrivere dati e che per scrivere in determinati percorsi può essere necessario eseguire operazioni di configurazione aggiuntive.  
  
### <a name="capturing-the-graphics-information"></a>Acquisizione delle informazioni grafiche  
 Dopo aver preparato l'app per l'acquisizione a livello di codice e aver facoltativamente configurato il percorso e il nome del file di log della grafica, compilare l'applicazione ed eseguirla o eseguire il debug per acquisire i dati; non avviare la diagnostica grafica da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] quando si usa l'API di acquisizione a livello di codice. Il log di grafica viene scritto nel percorso specificato. Se si vuole conservare questa versione del log, spostarlo in un altro percorso. In caso contrario, verrà sovrascritto quando si esegue nuovamente l'app.  
  
> [!TIP]
>  Quando si usa l'acquisizione a livello di codice, è comunque possibile acquisire informazioni grafiche manualmente premendo **STAMP**con l'app in stato attivo. Si può usare questa tecnica per acquisire informazioni grafiche aggiuntive, che non vengono acquisite dall'API di acquisizione a livello di codice.  
  
## <a name="next-steps"></a>Passaggi successivi  
 In questa procedura dettagliata è stato illustrato come acquisire informazioni grafiche a livello di codice. Come passaggio successivo, prendere in considerare questa opzione:  
  
-   Apprendere come analizzare le informazioni grafiche acquisite usando gli strumenti di diagnostica grafica. Visualizzare [Panoramica](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Acquisizione di informazioni grafiche](../debugger/walkthrough-capturing-graphics-information.md)   
 [Capturing Graphics Information](../debugger/capturing-graphics-information.md)   
 [Strumento di acquisizione da riga di comando](../debugger/command-line-capture-tool.md)
