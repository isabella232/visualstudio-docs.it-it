---
title: Oggetto Graphics tabella | Microsoft Docs
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
- vs.graphics.datavisualizer
- vs.graphics.objecttable
- vs.graphics.bufferviewer
ms.assetid: f48f62d9-16ff-4a2e-8c01-5cbe99513788
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ba3ce8aa0727471ff4385792d85659fa2d208dc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809090"
---
# <a name="graphics-object-table"></a>Tabella oggetti grafici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La Tabella oggetti grafici disponibile in Analisi grafica di Visual Studio consente di individuare gli oggetti Direct3D che supportano un frame specifico del gioco o dell'app.  
  
 Questa è la Tabella oggetti:  
  
 ![Oggetti Direct3D che sono stati creati da un'app.](../debugger/media/gfx-diag-demo-object-table-orientation.png "gfx_diag_demo_object_table_orientation")  
  
## <a name="understanding-the-graphics-object-table"></a>Informazioni sullo strumento Tabella oggetti grafici  
 Con la Tabella oggetti è possibile analizzare gli oggetti Direct3 che supportano il rendering di un frame specifico. È possibile associare con precisione un problema di rendering a un oggetto specifico esaminandone le proprietà e i dati, usando gli altri strumenti di Diagnostica grafica usati in precedenza nella diagnosi è possibile restringere l'elenco di oggetti che potrebbe non corrispondere a quanto previsto. Dopo aver trovato l'oggetto che causa l'errore, è possibile usare una visualizzazione specifica per quel tipo di verifica, ad esempio, è possibile usare l'Editor di immagini per visualizzare le trame o il *Visualizzatore Buffer* per visualizzare il contenuto del buffer.  
  
 La Tabella oggetti supporta le funzioni di copia e incolla in modo che sia possibile usare un altro strumento, ad esempio Microsoft Excel, per esaminarne il contenuto.  
  
### <a name="graphics-object-table-format"></a>Formato della Tabella oggetti grafici  
 Nella Tabella oggetti vengono visualizzati gli oggetti e le risorse Direct3D che supportano il frame associato all'evento selezionato, ad esempio gli oggetti di stato, i buffer, gli shader, le trame e altre risorse. Gli oggetti creati nel frame precedente ma non usati durante il frame acquisito vengono omessi dalla tabella degli oggetti. Gli oggetti eliminati da eventi precedenti durante il frame acquisito vengono omessi negli eventi successivi. Gli oggetti che non vengono impostati per D3D10Device o D3D11DeviceContext vengono visualizzati come testo in grigio. Gli oggetti vengono visualizzati in un formato tabella.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Identificatore**|ID dell'oggetto.|  
|**Name**|Informazioni specifiche dell'applicazione impostate per l'oggetto con la funzione Direct3D `SetPrivateData`, in genere per fornire informazioni di identificazione aggiuntive su un oggetto.|  
|**Type**|Tipo di oggetto.|  
|**Attiva**|Visualizza "*" per un oggetto impostato per D3D10Device o D3D11DeviceContext durante il frame acquisito.<br /><br /> Corrisponde agli oggetti visualizzati come testo in grigio, ma fornisce una voce di colonna che è possibile usare per ordinare la tabella degli oggetti.|  
|**Dimensione**|Dimensione dell'oggetto in byte.|  
|**Format**|Formato dell'oggetto. Ad esempio, il formato di un oggetto trama o il modello di shader di un oggetto shader.|  
|**Larghezza**|Larghezza di un oggetto trama. Non vale per altri tipi di oggetto.|  
|**Altezza**|Altezza di un oggetto trama. Non vale per altri tipi di oggetto.|  
|**profondità**|Profondità di un oggetto trama tridimensionale. Se una trama non è in 3D, il valore sarà 0. Non vale per altri tipi di oggetto.|  
|**MIPS**|Numero di livelli MIP di un oggetto trama. Non vale per altri tipi di oggetto.|  
|**Della dimensione matrice**|Numero di trame in una matrice di trame. L'intervallo è compreso tra 1 e un limite superiore definito dal livello della funzionalità corrente. Per una mappa cubi, questo valore corrisponde a 6 volte il numero delle mappe cubi nella matrice.|  
|**Esempi**|Numero di trame multicampionate per pixel.|  
  
## <a name="graphics-object-viewers"></a>Visualizzatori di oggetti grafici  
 Per visualizzare i dettagli relativi a un oggetto, aprirlo scegliendone il nome nella Tabella oggetti. I dettagli sull'oggetto vengono visualizzati in formati diversi, a seconda del tipo di oggetto. Ad esempio,le trame vengono visualizzate mediante il Visualizzatore trame, mentre lo stato del dispositivo, ad esempio Contesto di dispositivo D3D11, viene visualizzato come un elenco formattato. Versioni diverse di Direct3D usano oggetti differenti e spesso esistono visualizzatori specifici per gli oggetti più importanti di ogni versione.  
  
 Ecco il Visualizzatore trame che mostra il contenuto della fase della pipeline Unione output.  
  
 ![Anteprima della trama con unione output](../debugger/media/gfx-diag-texture-preview.png "gfx_diag_texture_preview")  
  
### <a name="d3d12-command-list"></a>Elenco comandi D3D12  
 In Direct3D 12 un elenco di comandi è un oggetto che registra i comandi in un allocatore di comandi, in modo che sia possibile inviarli alla GPU come una singola richiesta. Gli elenchi di comandi in genere eseguono una serie di comandi di impostazione dello stato, disegno, cancellazione e copia. Sono particolarmente importanti perché rappresentano il metodo consigliato per il rendering in Direct3D 12 e possono essere riutilizzati tra i frame per migliorare le prestazioni. I dettagli sull'elenco di comandi vengono visualizzati in una nuova finestra del documento, con informazioni relative a ogni fase della pipeline presentate in schede separate.  
  
### <a name="d3d12-pipeline-state-object-pso"></a>Oggetto stato pipeline D3D12  
 In Direct3D 12 un oggetti di stato della pipeline rappresenta una parte significativa dello stato della GPU, compresi tutti gli shader attualmente importati e alcuni oggetti di stato a funzione fissa. Una volta creato, un oggetto di stato della pipeline non è modificabile: un'applicazione può modificare la configurazione della pipeline solo mediante il binding di un oggetto di stato della pipeline diverso. I dettagli sull'oggetto di stato della pipeline vengono visualizzati in una nuova finestra del documento, con i dettagli della configurazione della pipeline disposti in ordine gerarchico.  
  
### <a name="d3d12-root-signature"></a>Firma radice D3D12  
 In Direct3D 12, la firma radice definisce tutte le risorse associate a una pipeline grafica o di calcolo e collega gli elenchi di comandi alle risorse richieste dagli shader. In genere in un'app è presente una firma radice per la pipeline grafica e una per la pipeline di calcolo I dettagli sulla firma radice vengono visualizzati in una nuova finestra del documento, disposti in ordine gerarchico.  
  
### <a name="d3d12-resources"></a>Risorse D3D12  
 In Direct3D 12, le risorse sono oggetti polivalenti che forniscono dati alla pipeline di rendering. In Direct3D11, al contrario, vengono definiti molti oggetti specifici per dimensioni e tipi diversi delle risorse. Una risorsa Direct3D 12 può contenere dati di trame, vertici, shader e altro ancora. Possono anche rappresentare destinazioni di rendering, ad esempio il buffer di profondità. I dettagli di una risorsa Direct3D 12 vengono visualizzati in una nuova finestra del documento. Analisi grafica userà il visualizzatore appropriato per il contenuto dell'oggetto risorsa, se è in grado di determinare il tipo. Ad esempio, un oggetto risorsa che contiene dati di trama, come l'oggetto D3D11 Texture2D, viene visualizzato con il Visualizzatore trame.  
  
### <a name="device-context-object"></a>Oggetto contesto del dispositivo  
 In Direct3D 11 e Direct3D 10, il contesto di dispositivo (**contesto di dispositivo D3D11** oppure **dispositivo D3D10**) oggetti sono particolarmente importanti perché contiene le informazioni sullo stato più importanti ed è collegato ad altri oggetti dello stato attualmente impostati. I dettagli del contesto di dispositivo vengono visualizzati in una nuova finestra del documento e ogni categoria di informazioni viene visualizzata nella rispettiva scheda. Il contesto di dispositivo cambia quando viene selezionato un nuovo evento in modo da rispecchiare lo stato corrente del dispositivo.  
  
### <a name="buffer-object"></a>Oggetto buffer  
 I dettagli dell'oggetto buffer (Buffer D3D11 o Buffer D3D10) vengono visualizzati in una nuova finestra del documento che mostra il contenuto del buffer in una tabella e fornisce un'interfaccia per modificare il modo in cui il contenuto del buffer viene visualizzato. Il **buffer dati** tabella supporta la copia e Incolla in modo che è possibile usare un altro strumento, ad esempio Microsoft Excel, per esaminarne il contenuto. Il contenuto del buffer viene interpretato secondo il valore della **formato** casella combinata, che si trova sopra il **buffer dati** tabella. Nella casella è possibile immettere un formato di dati composito costituito dai tipi di dati elencati nella tabella seguente. Ad esempio, con "float int" viene visualizzato un elenco di strutture che contengono un valore a virgola mobile a 32 bit seguito da un valore Signed Integer a 32 bit. I formati dati compositi specificati vengono aggiunti alla casella combinata per un uso successivo.  
  
 È anche possibile attivare o disattivare la **Mostra offset** casella di controllo per nascondere o visualizzare l'offset di ogni elemento nel buffer.  
  
|Tipo|Descrizione|  
|----------|-----------------|  
|**float**|Valore a virgola mobile a 32 bit.|  
|**float2**|Vettore che contiene due valori a virgola mobile a 32 bit.|  
|**float3**|Vettore che contiene tre valori a virgola mobile a 32 bit.|  
|**float4**|Vettore che contiene quattro valori a virgola mobile a 32 bit.|  
|**byte**|Valore Signed Integer a 8 bit.|  
|**2 byte**|Valore Signed Integer a 16 bit.|  
|**a 4 byte**|Valore Signed Integer a 32 bit. Uguale allo **int**.|  
|**8 byte**|Valore Signed Integer a 64 bit. Uguale allo **int64**.|  
|**xbyte**|Valore esadecimale a 8 bit.|  
|**x2byte**|Valore esadecimale a 16 bit.|  
|**x4byte**|Valore esadecimale a 32 bit. Uguale allo **xint**.|  
|**x8byte**|Valore esadecimale a 64 bit. Uguale allo **xint64**.|  
|**ubyte**|Valore Unsigned Integer a 8 bit.|  
|**u2byte**|Valore Unsigned Integer a 16 bit.|  
|**u4byte**|Valore Unsigned Integer a 32 bit. Uguale allo **uint**.|  
|**u8byte**|Valore Unsigned Integer a 64 bit. Uguale allo **uint64**.|  
|**metà**|Valore a virgola mobile a 16 bit.|  
|**half2**|Vettore che contiene due valori a virgola mobile a 16 bit.|  
|**half3**|Vettore che contiene tre valori a virgola mobile a 16 bit.|  
|**half4**|Vettore che contiene quattro valori a virgola mobile a 16 bit.|  
|**double**|Valore a virgola mobile a 64 bit.|  
|**int**|Valore Signed Integer a 32 bit. Uguale allo **4byte**.|  
|**int64**|Valore Signed Integer a 64 bit. Uguale allo **8byte**.|  
|**xint**|Valore esadecimale a 32 bit. Uguale allo **x4byte**.|  
|**xint64**|Valore esadecimale a 64 bit. Uguale allo **x8byte**.|  
|**uint**|Valore Unsigned Integer a 32 bit. Uguale allo **u4byte**.|  
|**uint64**|Valore Unsigned Integer a 64 bit. Uguale allo **u8byte**.|  
|**bool**|Valore booleano (`true` o `false`). Ogni valore booleano è rappresentato da un valore a 32 bit.|  
  
## <a name="see-also"></a>Vedere anche  
 [Diagnostica della grafica (debug grafica DirectX)](../debugger/visual-studio-graphics-diagnostics.md)   
 [Procedura dettagliata: oggetti mancanti a causa dello stato del dispositivo](../debugger/walkthrough-missing-objects-due-to-device-state.md)



