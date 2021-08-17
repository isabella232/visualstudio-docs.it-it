---
title: Introduzione alla diagnostica grafica | Microsoft Docs
description: Preparare l'Diagnostica della grafica per la prima volta, quindi acquisire fotogrammi da un'app Direct3D ed esaminarli in Analizzatore grafica.
ms.custom: SEO-VS-2020
ms.date: 06/08/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 88ccd8ea443092e3d22c4266bbecd2a56efb6dd2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074312"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Guida introduttiva a Diagnostica grafica di Visual Studio
In questa sezione ci si prepara al primo utilizzo di Diagnostica della grafica, quindi si acquisisce un frame da un'app Direct3D e lo si esamina in Analizzatore grafica.

## <a name="requirements"></a>Requisiti
 Per usare Diagnostica della grafica in Visual Studio, è necessario usare Visual Studio Enterprise, Visual Studio Professional o Visual Studio Community.  Altre edizioni, tra cui Visual Studio Code, non contengono questa funzionalità.

 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]

### <a name="windows-10-prerequisites"></a>Prerequisiti di Windows 10
 La funzionalità opzionale di Windows *Strumenti di grafica* offre l'infrastruttura di acquisizione e riproduzione richiesta dalla Diagnostica della grafica in Windows 10.

 Per informazioni sull'installazione di Strumenti di grafica, vedere [Installare Strumenti di grafica per Windows 10](#InstallGraphicsTools).

## <a name="install-graphics-tools-for-windows-10"></a><a name="InstallGraphicsTools"></a> Installare Strumenti di grafica per Windows 10
 In Windows 10, l'infrastruttura di diagnostica grafica viene offerta attraverso la funzionalità facoltativa di Windows denominata *Strumenti di grafica*. Questa funzionalità è necessaria per acquisire e riprodurre le informazioni di grafica in Windows 10 indipendentemente dal fatto che l'app acquisita abbia come destinazione una versione precedente di Windows e dalla versione di Direct3D in uso. Si può scegliere di installare la funzionalità di Strumenti di grafica in anticipo; in caso contrario, sarà installata su richiesta al primo avvio di una sessione di Diagnostica grafica da Visual Studio.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Per installare Strumenti di grafica per Windows 10

1. In Cerca digitare **App e funzionalità e** quindi aprire le impostazioni app & **funzionalità.**

2. Sul lato destro delle  impostazioni delle funzionalità & app scegliere Funzionalità facoltative **(in** **App & funzionalità**).

   Vengono **visualizzate le impostazioni funzionalità** facoltative.

3. Nelle impostazioni **funzionalità facoltative** scegliere **Aggiungi una funzionalità**. Viene visualizzato un elenco di funzionalità facoltative che è possibile installare.

4. Selezionare **Strumenti di grafica** nell'elenco di funzionalità e quindi scegliere **Installa**.

   La funzionalità Strumenti di grafica viene inoltre installata automaticamente quando si installa Windows SDK 10.

> [!TIP]
> La funzionalità facoltativa di Windows 10 Strumenti di grafica offre funzionalità leggere di acquisizione e riproduzione, ad esempio il programma di acquisizione da riga di comando **dxcap.exe**, che può essere usato in scenari di supporto, testing e diagnostica nei computer in cui non sono installati gli strumenti di sviluppo. Per altre informazioni, vedere l'argomento [Strumento di acquisizione da riga di comando](command-line-capture-tool.md).

## <a name="using-graphics-diagnostics-for-the-first-time"></a>Primo utilizzo di Diagnostica della grafica
 Ora che si dispone di tutto il necessario, è possibile iniziare a usare Diagnostica della grafica seguendo questa procedura.

### <a name="1---create-a-direct3d-app"></a>1 - Creare un'app Direct3D

Se si ha già un'app Direct3D con cui esplorare Diagnostica della grafica, è ottimo. In caso contrario, usare uno degli elementi seguenti:

::: moniker range=">=vs-2019"
Scaricare un esempio da [Direct3D Game Sample](/samples/microsoft/windows-universal-samples/simple3dgamedx/).
::: moniker-end
::: moniker range="vs-2017"
- Modelli **di progetto dell'app DirectX 11 (Universal Windows)** o **DirectX 12 App (Universal Windows)** per Windows 10.
- [Esempio di Direct3D 12 UAP per](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) Windows 10.
::: moniker-end

Assicurarsi di poter compilare ed eseguire l'app prima di procedere. Scegliere **Compila**  >  **soluzione di** compilazione per assicurarsi che sia compilata senza errori. Scegliere quindi **Avvia**  >  **debug senza eseguire debug** (**CTRL+F5**) per assicurarsi che venga eseguito correttamente. A seconda del computer che si sta testando con lo strumento, potrebbe essere necessario modificare la piattaforma e la destinazione di debug per l'esempio. Ad esempio, per testare la piattaforma x64 nel computer host Visual Studio, scegliere  **x64** come piattaforma della soluzione e computer locale come destinazione di debug. 

### <a name="2---start-a-graphics-diagnostics-session"></a>2 - Avviare una sessione di Diagnostica grafica
 A questo punto si è pronti per avviare la prima sessione di diagnostica della grafica. Nel Visual Studio menu principale scegliere **Debug, Grafica,** Avvia debug grafica oppure premere **ALT+F5.** L'app viene avviata in Diagnostica grafica e in Visual Studio vengono visualizzate le finestre della sessione di diagnostica.

> [!IMPORTANT]
> Se si esegue l'app in Windows 10 e non si è ancora installata la funzionalità facoltativa Strumenti di grafica, verrà richiesto di farlo ora. La funzionalità deve essere installata per poter usare Diagnostica della grafica in Windows 10.

### <a name="3---capture-frames"></a>3 - Acquisire frame
 Non appena l'app si avvia, è possibile iniziare ad acquisire frame.

#### <a name="to-capture-single-frames"></a>Per acquisire singoli frame

- In Visual Studio scegliere il pulsante nella barra degli strumenti **Acquisisci frame** nella barra degli strumenti di grafica o nella finestra della sessione di diagnostica. In caso contrario, se l'app ha lo stato attivo, è sufficiente premere il **tasto** Stampa schermo sulla tastiera.

#### <a name="to-capture-a-sequence-of-frames"></a>Per acquisire una sequenza di frame

- In Visual Studio, nella finestra della sessione di diagnostica impostare **Frame da acquisire** sul numero di frame da acquisire in sequenza, quindi acquisire la sequenza usando uno dei metodi descritti in precedenza per acquisire singoli frame.

   Per acquisire nuovamente singoli frame, impostare **Frame da acquisire** su *1*.

  Al termine dell'operazione di acquisizione dei frame, uscire dall'app o scegliere il pulsante **Arresta** nella barra degli strumenti di grafica o nella finestra della sessione di diagnostica.

### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4 - Esaminare i frame acquisiti in Analizzatore grafica
 A questo punto si è pronti per esaminare i frame acquisiti. Per iniziare ad analizzare un frame, scegliere il numero del frame da esaminare nella finestra della sessione di diagnostica. Il frame verrà aperto in **Analizzatore grafica** dove è possibile servirsi degli strumenti di Diagnostica della grafica per esaminare il modo in cui l'app usa Direct3D per individuare i problemi di rendering oppure usare lo strumento **Analisi dei frame** per comprenderne le prestazioni.

 Se è stato selezionato frame errato nella finestra della sessione di diagnostica oppure si vuole esaminare un frame diverso, è possibile selezionare un altro da Analizzatore grafica. Nella scheda **Destinazione rendering** della finestra del log di grafica, sotto l'immagine della destinazione di rendering, espandere l'**Elenco frame** e quindi scegliere un altro frame da esaminare.

 Per altre informazioni su come usare gli strumenti di Analizzatore grafica insieme, vedere [Esempi](graphics-diagnostics-examples.md).

## <a name="see-also"></a>Vedi anche
- [Grafica Direct3D 12](/windows/desktop/direct3d12/direct3d-12-graphics)