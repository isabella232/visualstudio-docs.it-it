---
title: 'Procedura dettagliata: Cattura programmatica delle informazioni grafiche | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8fa8d750049d7d74d912e68544c91d5006252068
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722915"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Procedura dettagliata: cattura programmatica delle informazioni grafica
La funzionalità Diagnostica grafica di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consente di acquisire a livello di codice informazioni grafiche da un'app Direct3D.

L'acquisizione a livello di codice è utile in scenari quali ad esempio:

- Iniziare l'acquisizione a livello di codice quando l'app grafica non usa la presentazione della catena di scambio, ad esempio quando esegue il rendering su una trama.

- Iniziare l'acquisizione a livello di codice quando l'app non esegue il rendering, ad esempio quando usa DirectCompute per eseguire calcoli.

- Chiamare `CaptureCurrentFrame`quando un problema di rendering è difficile da prevedere e acquisire nei test manuali, ma può essere previsto a livello di codice usando le informazioni sullo stato dell'app in fase di esecuzione.

## <a name="CaptureDX11_2"></a> Acquisizione a livello di codice in Windows 10
Questa parte della procedura dettagliata illustra l'acquisizione a livello di codice nelle app che usano l'API DirectX 11.2 su Windows 10, che usa il metodo di acquisizione affidabile.

Questa sezione illustra l'esecuzione delle attività seguenti:

- Preparazione dell'app per usare l'acquisizione a livello di codice

- Ottenere l'interfaccia IDXGraphicsAnalysis

- Acquisizione di informazioni grafiche

> [!NOTE]
> Le implementazioni precedenti di acquisizione a livello di codice si basavano su Remote Tools per Visual Studio per [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per fornire funzionalità di acquisizione.

### <a name="preparing-your-app-to-use-programmatic-capture"></a>Preparazione dell'app per usare l'acquisizione a livello di codice
Per usare l'acquisizione a livello di codice nell'app, deve includere le intestazioni necessarie. Queste intestazioni fanno parte di Windows 10 SDK.

##### <a name="to-include-programmatic-capture-headers"></a>Per includere le intestazioni per l'acquisizione a livello di codice

- Includere le intestazioni nel file di origine in cui verrà definita l'interfaccia IDXGraphicsAnalysis:

    ```cpp
    #include <DXGItype.h>
    #include <dxgi1_2.h>
    #include <dxgi1_3.h>
    #include <DXProgrammableCapture.h>
    ```

    > [!IMPORTANT]
    > Non includere il file di intestazione vsgcapture.h, che supporta l'acquisizione a livello di codice in Windows 8.0 e versioni precedenti, per eseguire l'acquisizione a livello di codice nelle app Windows 10. Questa intestazione non è compatibile con DirectX 11.2. Se questo file è incluso dopo l'intestazione d3d11_2.h è inclusa, il compilatore genera un avviso. Se viene inclusa vsgcapture. h prima d3d11_2.h, l'app non verrà avviato.

    > [!NOTE]
    > Se nel computer è installata la versione di DirectX SDK del giugno 2010 e il percorso di inclusione del progetto contiene `%DXSDK_DIR%includex86`, spostarlo alla fine del percorso di inclusione. Eseguire la stessa operazione per il percorso della libreria.

### <a name="getting-the-idxgraphicsanalysis-interface"></a>Ottenere l'interfaccia IDXGraphicsAnalysis
Prima di poter acquisire informazioni grafiche da DirectX 11.2, è necessario ottenere l'interfaccia di debug DXGI.

> [!IMPORTANT]
> Quando si usa l'acquisizione a livello di codice, è comunque necessario eseguire l'app nella diagnostica della grafica (ALT+F5 in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) o sotto la [strumento di acquisizione da riga di comando](command-line-capture-tool.md).

##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Per ottenere l'interfaccia IDXGraphicsAnalysis

- Usare il codice seguente per associare l'interfaccia IDXGraphicsAnalysis all'interfaccia di debug DXGI.

  ```cpp
  IDXGraphicsAnalysis* pGraphicsAnalysis;
  HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));
  ```

  Assicurarsi di controllare la `HRESULT` restituito da [DXGIGetDebugInterface1](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-dxgigetdebuginterface1) per assicurarsi di ottenere un'interfaccia valida prima di usarla:

  ```cpp
  if (FAILED(getAnalysis))
  {
      // Abort program or disable programmatic capture in your app.
  }
  ```

  > [!NOTE]
  > Se si include `DXGIGetDebugInterface1` restituisce `E_NOINTERFACE` (`error: E_NOINTERFACE No such interface supported`), assicurarsi che l'app sia in esecuzione nella diagnostica grafica (ALT+F5 in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).

### <a name="capturing-graphics-information"></a>Acquisizione di informazioni grafiche
Ora che si dispone di un'interfaccia `IDXGraphicsAnalysis` valida, è possibile usare `BeginCapture` e `EndCapture` per acquisire informazioni grafiche.

##### <a name="to-capture-graphics-information"></a>Per acquisire informazioni grafiche

- Per iniziare ad acquisire informazioni grafiche, usare `BeginCapture`:

    ```cpp
    ...
    pGraphicsAnalysis->BeginCapture();
    ...
    ```

    Quando viene chiamato `BeginCapture` , l'acquisizione inizia immediatamente senza aspettare l'inizio del frame successivo. L'acquisizione termina quando viene presentato il frame corrente o quando si chiama `EndCapture`:

    ```cpp
    ...
    pGraphicsAnalysis->EndCapture();
    ...
    ```

- Dopo la chiamata a `EndCapture`, rilasciare l'oggetto graphics.

## <a name="next-steps"></a>Passaggi successivi
In questa procedura dettagliata è stato illustrato come acquisire informazioni grafiche a livello di codice. Come passaggio successivo, prendere in considerare questa opzione:

- Apprendere come analizzare le informazioni grafiche acquisite usando gli strumenti di diagnostica grafica. Visualizzare [Panoramica](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: cattura delle informazioni grafica](walkthrough-capturing-graphics-information.md)
- [Capturing Graphics Information](capturing-graphics-information.md)
- [Strumento di acquisizione da riga di comando](command-line-capture-tool.md)
