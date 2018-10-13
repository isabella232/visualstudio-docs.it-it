---
title: Generale, Ambiente, finestra di dialogo Opzioni | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.Message.0x800a002e
- VS.ToolsOptionsPages.Environment.General
- VS.Environment.General
helpviewer_keywords:
- MRU lists
- windows, customizing
- MDI, environment options
- speed, environment animation
- File menu
- menus, customizing
- Windows menu customizing
- status bars, displaying
- Visual Studio Start page, setting
- IDE, startup options
- editors, autocompletion
- Options dialog box, General Environment
- General Environment Options dialog box
ms.assetid: 90fc2e6f-572f-4384-96d8-5678299ce58e
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 967036aa0aedef2f789a1352e213079270f70339
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206882"
---
# <a name="general-environment-options-dialog-box"></a>Generale, Ambiente, finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Usare questa pagina per modificare i temi di colori, le impostazioni della barra di stato e le associazioni dell'estensione di file, tra le altre opzioni, per l'ambiente di sviluppo integrato (IDE). Per accedere alla finestra di dialogo **Opzioni**, aprire il menu **Strumenti**, scegliere **Opzioni**, aprire la cartella **Ambiente** e scegliere la pagina **Generale**. Se la pagina non viene visualizzata nell'elenco, selezionare la casella di controllo **Mostra tutte le impostazioni** nella finestra di dialogo **Opzioni**.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, aprire il menu **Strumenti** e quindi scegliere **Importa/Esporta impostazioni**. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="visual-experience"></a>Esperienza visiva  
 **Tema colori**  
 Scegliere il tema colori **Blu**, **Chiaro** o **Scuro** per l'IDE.  
  
 È possibile installare temi predefiniti aggiuntivi e creare temi personalizzati scaricando e installando **Visual Studio 2015 Color Theme Editor** dalla [Visual Studio Gallery](https://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=RootCategory&f%5B0%5D.Value=tools). Dopo avere installato questo strumento, i temi colori aggiuntivi vengono visualizzati nella casella di riepilogo Tema colori.  
  
 Applicare lo stile Tutte Iniziali Maiuscole nella barra dei menu  
 Per impostazione predefinita, in Visual Studio 2015 i menu sono visualizzati con lo stile **Tutte Iniziali Maiuscole**. Deselezionare questa opzione per impostarli su **TUTTO MAIUSCOLE**.  
  
 **Regola automaticamente esperienza visiva in base alle prestazioni del client**  
 Specifica se Visual Studio imposta automaticamente la regolazione dell'esperienza visiva o la regolazione viene impostata in modo esplicito dall'utente. Questa regolazione può modificare la visualizzazione di colori da gradienti a colori uniformi o può limitare l'uso di animazioni nei menu o finestre a comparsa.  
  
 **Abilita esperienza visiva dettagliata del client**  
 Consente l'esperienza visiva completa di Visual Studio, inclusi i gradienti e le animazioni. Deselezionare questa opzione se si usano Connessioni desktop remoto o schede grafiche obsolete, perché le prestazioni di queste funzionalità potrebbero risultare compromesse. Questa opzione è disponibile solo se si deseleziona l'opzione **Regola automaticamente esperienza visiva in base alle prestazioni del client**.  
  
 **Usa accelerazione grafica hardware se disponibile**  
 Usa l'accelerazione grafica hardware, se disponibile, piuttosto che l'accelerazione software.  
  
## <a name="other"></a>Altro  
 **elementi nel menu Finestra**  
 Consente di personalizzare il numero di finestre visualizzate nell'elenco Finestre accessibile dal menu **Finestra**. Digitare un numero compreso tra 1 e 24. Per impostazione predefinita, il numero è 10.  
  
 **elementi negli elenchi degli ultimi file usati**  
 Consente di personalizzare il numero dei file e dei progetti usati più di recente visualizzati nel menu **File**. Digitare un numero compreso tra 1 e 24. Per impostazione predefinita, il numero è 10. Questa funzionalità offre un modo semplice per recuperare progetti e file usati di recente.  
  
 **Mostra barra di stato**  
 Consente di visualizzare la barra di stato. Nella barra di stato, posizionata nella parte inferiore della finestra dell'IDE, sono visualizzate le informazioni sullo stato delle operazioni in corso.  
  
 **Chiudi ha effetto solo sulla finestra degli strumenti attiva**  
 Consente di specificare che quando si fa clic sul pulsante **Chiudi** deve essere chiusa solo la finestra degli strumenti attiva e non tutte le finestre degli strumenti del set ancorato. Questa opzione è selezionata per impostazione predefinita.  
  
 **Nascondi automaticamente ha effetto solo sulla finestra degli strumenti attiva**  
 Consente di specificare che se si fa clic sul pulsante **Nascondi automaticamente** deve essere nascosta automaticamente solo la finestra degli strumenti attiva e non tutte le finestre degli strumenti del set ancorato. Questa opzione è deselezionata per impostazione predefinita.  
  
 **Gestisci associazioni file**  
 Visualizza la finestra di dialogo **Imposta associazioni programmi**, in cui è possibile visualizzare le estensioni dei file per gli elementi in genere associati a Visual Studio e il programma predefinito corrente per l'apertura di ogni tipo di file. Per impostare Visual Studio come applicazione predefinita per i tipi di file non ancora associati a questa applicazione, selezionare l'estensione e quindi scegliere **Salva**.  
  
 Questa opzione può essere utile se sono installate due versioni di Visual Studio nello stesso computer e successivamente viene disinstallata una delle versioni. Dopo aver effettuato la disinstallazione, le icone per i file di Visual Studio non vengono più visualizzate in Esplora file. Inoltre, Windows non rileva più Visual Studio come applicazione predefinita per la modifica di questi file. Questa opzione consente di ripristinare tali associazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Environment Options Dialog Box](../../ide/reference/environment-options-dialog-box.md)  (Ambiente, finestra di dialogo Opzioni)  
 [Personalizzazione del layout delle finestre](../../ide/customizing-window-layouts-in-visual-studio.md)



