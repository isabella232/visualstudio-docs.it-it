---
title: Documento di Log della grafica | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.vsglog.error
- vs.graphics.experiment
- vs.graphics.vsglog
ms.assetid: 6ccb1269-d55f-49c4-920d-baedf7de2888
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 097f431446ed2148e2a61c6f85266843fe7ada44
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745174"
---
# <a name="graphics-log-document"></a>Documento log grafica
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il documento di log della grafica è la registrazione degli eventi di grafica che si sono verificati durante l'esecuzione dell'app in una sessione di diagnostica della grafica. Dopo la registrazione, è possibile esaminare il log in Analizzatore grafica di Visual Studio per diagnosticare i problemi di rendering e di prestazioni.  
  
 Ecco l'aspetto di un documento di log della grafica in Analizzatore grafica:  
  
 ![Un log di grafica contenente due frame acquisiti. ](../debugger/media/gfx-diag-demo-graphics-log-orientation.png "gfx_diag_demo_graphics_log_orientation")  
  
## <a name="understanding-graphics-log-documents"></a>Informazioni sui documenti di log della grafica  
 Se si usa Analizzatore grafica per esaminare un documento di log della grafica, è possibile visualizzare gli effetti degli eventi Direct3D che si sono verificati durante l'acquisizione sulla destinazione di rendering. È possibile individuare aree della destinazione di rendering che contengono un output non previsto. Quando si seleziona un pixel nell'area interessata, è possibile usare gli strumenti di Diagnostica grafica per esaminarlo, per analizzare gli shader e gli eventi Direct3D che hanno influito su di esso, gli stack di chiamate dell'applicazione che hanno generato tali eventi e gli oggetti DirectX che supportano tali eventi. È possibile usare queste informazioni per diagnosticare i problemi di rendering nel gioco o nell'app.  
  
 La parte superiore della finestra (**Graphics experiment. vsglog**) consente di visualizzare l'output di destinazione di rendering corrente del frame selezionato e la parte inferiore viene visualizzato un **elenco Frame** che contiene immagini di anteprima del frame acquisiti.  
  
#### <a name="to-inspect-a-frame"></a>Per esaminare un frame  
  
-   Nel **elenco Frame**, selezionare il frame da esaminare. L'output della destinazione di rendering nella parte superiore del documento di log della grafica viene aggiornato per visualizzare il frame selezionato.  
  
#### <a name="to-inspect-a-pixel"></a>Per esaminare un pixel  
  
-   Nella parte superiore del documento di log della grafica, selezionare il pixel desiderato dall'output della destinazione di rendering. Quando viene selezionato un pixel, è possibile usare la **cronologia Pixel grafica** finestra per visualizzare informazioni dettagliate sul pixel selezionato. Per altre informazioni, vedere [cronologia Pixel](../debugger/graphics-pixel-history.md).  
  
## <a name="playback-machine"></a>Computer riproduzione  
 Visualizzata anche nell'angolo superiore destro del **elenco Frame** è la **computer riproduzione**. Computer riproduzione è un computer o un dispositivo usato per riprodurre gli eventi della grafica da un file di log della grafica durante una sessione di diagnostica della grafica successiva. Usando un dispositivo diverso dal computer di sviluppo per riprodurre gli eventi acquisiti, è possibile riprodurre in modo più accurato l'ambiente di esecuzione in cui si verifica il problema. È ad esempio possibile usare un computer con un hardware o driver di grafica diversi rispetto a quelli presenti nel computer di sviluppo o altri tipi di dispositivi, come un tablet Windows RT basato su ARM o un dispositivo Windows Phone.  
  
 Per informazioni su come specificare un computer di riproduzione, vedere [procedura: modificare il computer di riproduzione di diagnostica della grafica](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="graphics-log-summary-information"></a>Informazioni di riepilogo del log di grafica  
 Quando un file di log della grafica è il documento attivo, il **proprietà** finestra vengono visualizzate informazioni sull'ambiente che ha ospitato la sessione di acquisizione di diagnostica della grafica. Sono visualizzate numerose categorie di informazioni.  
  
 **Informazioni Direct3D**  
 Riporta le informazioni relative alle funzionalità di hardware e driver della scheda video usata durante la sessione di acquisizione.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|**Formato High Color 10 bit XR**|**True** se il formato di high color 10 bit XR è supportato; in caso contrario, **False**.|  
|**DirectCompute CS 4.x**|**True** se Compute Shader 4.0 è supportato; in caso contrario, **False**.|  
|**Shader a precisione doppia**|**True** se la scheda video supporta valori a virgola mobile a precisione doppia (64 bit); in caso contrario, **False**.|  
|**Elenco comandi driver**|**True** se il driver supporta gli elenchi comandi; in caso contrario, **False**.|  
|**Creazioni simultanee driver**|**True** se il driver supporta simultanea (asincrona) durante la creazione; in caso contrario, **False**.|  
|**Formati estesi (BGRA e così via)**|**True** se i formati estesi come BGRA sono supportati; in caso contrario, **False**.|  
|**Livello funzionalità hardware massimo**|Visualizza il livello di funzionalità massimo supportato dalla scheda video.|  
  
 **Informazioni di visualizzazione**  
 Visualizza le informazioni relative alla scheda video usata durante la sessione di acquisizione.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|**Descrizione**|Stringa di descrizione della scheda video.|  
|**Memoria visualizzazione**|Quantità di memoria installata nella scheda video grafica.|  
|**Nome del driver**|Nome del driver della scheda video grafica.|  
|**Versione del driver**|Versione del driver della scheda video grafica.|  
|**Name**|Nome della scheda video grafica.|  
  
 **File esperimento**  
 Visualizza le informazioni relative al file esperimento associato alla sessione di acquisizione.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|**Path**|Percorso del file con estensione vsglog. **Nota:** in acquisizione legacy, questa proprietà è inutilizzata.|  
  
 **Informazioni sul modulo**  
 Visualizza il nome e la versione delle DLL (Dynamic Link Library) caricate dall'app durante la sessione di acquisizione.  
  
 **Informazioni di sistema**  
 Visualizza le informazioni relative all'hardware e al sistema operativo che hanno ospitato l'app durante la sessione di acquisizione.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|**Memoria**|Quantità di memoria installata nel computer.|  
|**Architettura del sistema operativo**|L'architettura della CPU di destinazione del sistema operativo.|  
|**Versione del sistema operativo**|Versione del sistema operativo.|  
|**Processore**|Processore installato nel computer.|  
|**Architettura applicazione di destinazione**|L'architettura della CPU di destinazione dell'app. Ciò può essere diverso da quello di **architettura del sistema operativo**.|  
  
 **Applicazione di destinazione**  
 Visualizza le informazioni relative all'app oggetto della sessione di acquisizione.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|**Data/ora dell'ultima modifica**|Data e ora in cui è stata compilata l'app.|  
|**Path**|Percorso dell'app.|  
|**ID processo**|ID processo assegnato all'app.|  
|**Version**|Versione dell'app.|  
  
 **Di Log Vsg**  
 Visualizza le informazioni relative al documento di log della grafica.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|**Creato da**|Nome dell'app che ha creato il documento di log della grafica. Ad esempio, se la sessione di acquisizione è stata avviata da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (acquisizione manuale), il valore di questa proprietà è [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|**Ora di inizio sessione**|Data e ora in cui è stata iniziata la sessione di acquisizione.|  
|**Dimensione**|Dimensione del documento log grafica.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Oggetti mancanti a causa dello sfondo Vertex](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Procedure dettagliate: debug degli errori di rendering dovuti allo sfondo](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)



