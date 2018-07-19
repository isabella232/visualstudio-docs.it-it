---
title: Guida introduttiva a diagnostica della grafica di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 05/26/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 069dd7638296987c195fbae6cc9d858fdd3421ee
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058672"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Guida introduttiva a Diagnostica della grafica di Visual Studio
In questa sezione ci si prepara al primo utilizzo di Diagnostica della grafica, quindi si acquisisce un frame da un'app Direct3D e lo si esamina in Analizzatore grafica.  
  
## <a name="requirements"></a>Requisiti  
 Per usare diagnostica della grafica in Visual Studio, è necessario usare Visual Studio Enterprise, Visual Studio Professional o Visual Studio Community.  Le altre edizioni, tra cui Visual Studio Code, non contengono questa funzionalità.
 
 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]  
  
### <a name="windows-10-prerequisites"></a>Prerequisiti di Windows 10  
 La funzionalità Windows facoltativa *strumenti di grafica* fornisce l'infrastruttura di acquisizione e riproduzione richiesti dalla diagnostica grafica in Windows 10.  
  
 Per informazioni sull'installazione di strumenti di grafica, vedere [installare strumenti di grafica per Windows 10](#InstallGraphicsTools).  
  
##  <a name="InstallGraphicsTools"></a> Installare strumenti di grafica per Windows 10  
 In Windows 10, l'infrastruttura di diagnostica della grafica è fornita da una funzionalità facoltativa di Windows denominato *strumenti di grafica*. Questa funzionalità è necessaria per acquisire e riprodurre le informazioni di grafica in Windows 10 indipendentemente dal fatto che l'app acquisita abbia come destinazione una versione precedente di Windows e dalla versione di Direct3D in uso. Si può scegliere di installare la funzionalità di Strumenti di grafica in anticipo; in caso contrario, sarà installata su richiesta al primo avvio di una sessione di Diagnostica grafica da Visual Studio.  
  
#### <a name="to-install-graphics-tools-for-windows-10"></a>Per installare Strumenti di grafica per Windows 10  
  
1.  Nella ricerca, digitare **App e funzionalità** e quindi aprire il **App e funzionalità** impostazioni.
  
3.  Sul lato destro del **App e funzionalità** finestra di dialogo, scegliere **Gestisci funzionalità facoltative** (sotto **App e funzionalità**).

    Il **Gestisci funzionalità facoltative** viene visualizzata la finestra.
  
4.  Nel **Gestisci funzionalità facoltative** finestra di dialogo, scegliere **aggiungere una funzionalità**. Viene visualizzato un elenco di funzionalità facoltative che è possibile installare.  
  
5.  Selezionare **strumenti di grafica** nell'elenco delle funzionalità, quindi scegliere **installare**.  
  
 La funzionalità Strumenti di grafica viene inoltre installata automaticamente quando si installa Windows SDK 10.  
  
> [!TIP]
>  La funzionalità facoltativa strumenti di grafica di Windows 10 fornisce la funzionalità caricamento leggero di acquisizione e riproduzione, ad esempio il programma di acquisizione da riga di comando **dxcap.exe**, che può essere utilizzato nel supporto, test e scenari di diagnostica in macchine virtuali in cui non sono installati gli strumenti di sviluppo. Per altre informazioni, vedere la [strumento di acquisizione da riga di comando](command-line-capture-tool.md) argomento.  
  
## <a name="using-graphics-diagnostics-for-the-first-time"></a>Primo utilizzo di Diagnostica della grafica  
 Ora che si dispone di tutto il necessario, è possibile iniziare a usare Diagnostica della grafica eseguendo le operazioni descritte nei passaggi seguenti.  
  
### <a name="1---create-a-direct3d-app"></a>1 - Creare un'app Direct3D  
 Se si ha già la propria app Direct3D per esplorare diagnostica della grafica con, benissimo. In caso contrario, usare uno dei seguenti:

- Il **App di DirectX 11 (Windows universale)** oppure **DirectX 12 App (Windows universale)** modelli di progetto per Windows 10.
- [Esempio Direct3D 12 UAP](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) per Windows 10.  
  
 Verificare che sia possibile compilare l'applicazione prima di andare avanti.  
  
### <a name="2---start-a-graphics-diagnostics-session"></a>2 - Avviare una sessione di Diagnostica della grafica  
 A questo punto si è pronti per avviare la prima sessione di diagnostica della grafica. In Visual Studio, nel menu principale, scegliere **eseguire il Debug, grafica, Avvia debug grafica**, oppure premere **ALT+F5**. L'app viene avviata in Diagnostica della grafica e in Visual Studio vengono visualizzate le finestre della sessione di diagnostica.  
  
> [!IMPORTANT]
>  Se si esegue l'app in Windows 10 e non si è ancora installata la funzionalità facoltativa Strumenti di grafica, verrà richiesto di farlo ora. La funzionalità deve essere installata per poter usare Diagnostica della grafica in Windows 10.  
  
### <a name="3---capture-frames"></a>3 - Acquisire frame  
 Non appena l'app si avvia, è possibile iniziare ad acquisire frame.  
  
#### <a name="to-capture-single-frames"></a>Per acquisire singoli frame  
  
-   In Visual Studio, scegliere il **Acquisisci Frame** della finestra di sessione della barra degli strumenti o alla diagnostica della grafica. Oppure, se l'app ha lo stato attivo, premere il **Stamp** sulla tastiera.
  
#### <a name="to-capture-a-sequence-of-frames"></a>Per acquisire una sequenza di frame  
  
-   In Visual Studio, nella finestra della sessione di diagnostica, impostare **frame da acquisire** sul numero di frame da acquisire in sequenza, quindi acquisire la sequenza usando uno dei metodi descritti in precedenza per acquisire singoli frame.  
  
     Per acquisire nuovamente singoli frame, impostare **frame da acquisire** al *1*.  
  
 Al termine dell'acquisizione dei frame sufficiente uscire dall'app o scegliere il **arrestare** pulsante dalla barra degli strumenti grafica o finestra sessione di diagnostica.  
  
### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4 - esaminare i frame acquisiti in Analizzatore grafica  
 A questo punto si è pronti per esaminare i frame acquisiti. Per iniziare ad analizzare un frame, scegliere il numero del frame da esaminare nella finestra della sessione di diagnostica. Verrà aperto il frame nel **analizzatore grafica**, dove è possibile usare gli strumenti di diagnostica della grafica per esaminare come l'app Usa Direct3D per tenere traccia dei problemi di rendering oppure usare il **analisi dei Frame** dello strumento comprendere le prestazioni.  
  
 Se è stato selezionato frame errato nella finestra della sessione di diagnostica oppure si vuole esaminare un frame diverso, è possibile selezionare un altro da Analizzatore grafica. Nel **destinazione rendering** della scheda della finestra del log di grafica, sotto l'immagine di destinazione di rendering, espandere il **elenco Frame** e quindi scegliere un altro frame da esaminare.  
  
 Per altre informazioni su come usare gli strumenti di Analizzatore grafica tra loro, vedere la [esempi](graphics-diagnostics-examples.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Direct3D 12 grafica](/windows/desktop/direct3d12/direct3d-12-graphics)