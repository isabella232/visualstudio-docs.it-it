---
title: Acquisire informazioni grafiche a livello di codice
description: Informazioni su come usare Visual Studio Diagnostica della grafica per acquisire informazioni grafiche a livello di codice da un'app Direct3D.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2c251ee95d86431a64f3c5e7c1f103b98fba3abc632de3b0db2f00d0e95a7549
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121239870"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Procedura dettagliata: Acquisizione di informazioni grafiche a livello di codice
La funzionalità Diagnostica grafica di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consente di acquisire a livello di codice informazioni grafiche da un'app Direct3D.

L'acquisizione a livello di codice è utile in scenari quali ad esempio:

- Iniziare l'acquisizione a livello di codice quando l'app grafica non usa la presentazione della catena di scambio, ad esempio quando esegue il rendering su una trama.

- Iniziare l'acquisizione a livello di codice quando l'app non esegue il rendering, ad esempio quando usa DirectCompute per eseguire calcoli.

- Chiamare quando un problema di rendering è difficile da prevedere e acquisire nei test manuali, ma può essere previsto a livello di codice usando le informazioni sullo stato `CaptureCurrentFrame` dell'app in fase di esecuzione.

## <a name="programmatic-capture-in-windows-10"></a><a name="CaptureDX11_2"></a> Acquisizione a livello di codice in Windows 10
Questa parte della procedura dettagliata illustra l'acquisizione a livello di codice nelle app che usano l'API DirectX 11.2 su Windows 10, che usa il metodo di acquisizione affidabile.

Questa sezione illustra l'esecuzione delle attività seguenti:

- Preparazione dell'app per usare l'acquisizione a livello di codice

- Ottenere l'interfaccia IDXGraphicsAnalysis

- Acquisizione di informazioni grafiche

> [!NOTE]
> Le implementazioni precedenti dell'acquisizione a livello di codice si basano Remote Tools per Visual Studio per fornire funzionalità di acquisizione.

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
    > Non includere il file di intestazione vsgcapture.h, che supporta l'acquisizione a livello di codice in Windows 8.0 e versioni precedenti, per eseguire l'acquisizione a livello di codice nelle app Windows 10. Questa intestazione non è compatibile con DirectX 11.2. Se questo file viene incluso dopo l'd3d11_2.h, il compilatore genera un avviso. Se vsgcapture.h è incluso prima di d3d11_2.h, l'app non verrà avviata.

    > [!NOTE]
    > Se nel computer è installata la versione di DirectX SDK del giugno 2010 e il percorso di inclusione del progetto contiene `%DXSDK_DIR%includex86`, spostarlo alla fine del percorso di inclusione. Eseguire la stessa operazione per il percorso della libreria.

### <a name="getting-the-idxgraphicsanalysis-interface"></a>Ottenere l'interfaccia IDXGraphicsAnalysis
Prima di poter acquisire informazioni grafiche da DirectX 11.2, è necessario ottenere l'interfaccia di debug DXGI.

> [!IMPORTANT]
> Quando si usa l'acquisizione a livello di codice, è comunque necessario eseguire l'app nella diagnostica della grafica (ALT+F5 in ) o nello strumento di acquisizione [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] da riga di [comando](command-line-capture-tool.md).

##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Per ottenere l'interfaccia IDXGraphicsAnalysis

- Usare il codice seguente per associare l'interfaccia IDXGraphicsAnalysis all'interfaccia di debug DXGI.

  ```cpp
  IDXGraphicsAnalysis* pGraphicsAnalysis;
  HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));
  ```

  Assicurarsi di controllare `HRESULT` l'oggetto restituito [da DXGIGetDebugInterface1](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-dxgigetdebuginterface1) per assicurarsi di ottenere un'interfaccia valida prima di usarla:

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

- Dopo la chiamata a `EndCapture` , rilasciare l'oggetto grafico.

## <a name="next-steps"></a>Passaggi successivi
In questa procedura dettagliata è stato illustrato come acquisire informazioni grafiche a livello di codice. Come passaggio successivo, prendere in considerare questa opzione:

- Apprendere come analizzare le informazioni grafiche acquisite usando gli strumenti di diagnostica grafica. Vedere [Panoramica.](overview-of-visual-studio-graphics-diagnostics.md)

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: Acquisizione di informazioni grafiche](walkthrough-capturing-graphics-information.md)
- [Acquisizione di informazioni grafiche](capturing-graphics-information.md)
- [Strumento di acquisizione da riga di comando](command-line-capture-tool.md)
