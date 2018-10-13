---
title: 'Procedura: eseguire il Debug di codice sorgente di .NET Framework | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c717e1d9eccce48319d8a73dd52d7f13ce36296e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240617"
---
# <a name="how-to-debug-net-framework-source"></a>Procedura: debug del codice sorgente di .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fornisce nuove funzionalità per [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] debug. Per eseguire il debug [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] origine, è necessario avere accesso ai simboli per il codice di debug. È anche necessario attivare l'esecuzione [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] origine.  
  
 È possibile abilitare [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] simboli nel download e l'esecuzione di **opzioni** nella finestra di dialogo. Quando si attiva il download dei simboli, è possibile scegliere di scaricarli immediatamente o attivare solo l'opzione per eseguire il download successivamente. Se non si esegue immediatamente il download, i simboli verranno scaricati la volta successiva che si avvia il debug dell'applicazione. È inoltre possibile scaricarli manualmente dal **moduli** finestra o il **Stack di chiamate** finestra.  
  
### <a name="to-enable-net-framework-source-debugging"></a>Per attivare il debug di origine di .NET Framework   
  
1.  Nel **degli strumenti** menu, fare clic su **opzione**s.  
  
2.  Nel **opzioni** finestra di dialogo, fare clic sul **debug** categoria.  
  
3.  Nel **generali** impostare **abilitare .NET Framework** esecuzione di istruzioni origine.  
  
    1.  Se Just My Code è attivato, viene visualizzata una finestra di dialogo con un avviso indicante che Just My Code è stato disabilitato. Fare clic su **OK**.  
  
    2.  Se il percorso della cache dei simboli non è impostato, viene visualizzata un'altra finestra di dialogo con un avviso indicante che è stato impostato il percorso predefinito della cache dei simboli. Fare clic su **OK**.  
  
4.  Sotto il **Debugging** categoria, fare clic su **simboli**.  
  
5.  Se si desidera modificare il percorso della cache dei simboli:  
  
    1.  Aprire il **debug** nodo nella casella a sinistra.  
  
    2.  Sotto il **Debugging** nodo, fare clic su **simboli**.  
  
    3.  Modificare il percorso in **memorizza nella Cache i simboli dai server dei simboli per questa directory** oppure fare clic su **Sfoglia** per scegliere un percorso.  
  
6.  Se si desidera scaricare immediatamente simboli, fare clic su **carica i simboli utilizzando percorsi indicati sopra**.  
  
     Questo pulsante non è disponibile nella modalità progettazione.  
  
     Se non si sceglie di scaricare ora i simboli, questi ultimi verranno scaricati automaticamente al successivo avvio del debug del programma.  
  
7.  Fare clic su **OK** per chiudere la finestra di dialogo **Opzioni**.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Per caricare simboli di Framework utilizzando la finestra Moduli  
  
1.  Nel **moduli** finestra, pulsante destro del mouse un modulo per il quale non sono stati caricati i simboli. È possibile indicare se i simboli sono caricati o non esaminando il **stato simboli** colonna.  
  
2.  Puntare **Carica simboli da** e fare clic su **server dei simboli Microsoft** per scaricare i simboli dai server dei simboli pubblici Microsoft oppure **percorso dei simboli** caricare da una directory in cui è stata precedentemente memorizzata simboli.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Per caricare simboli di Framework utilizzando la finestra Stack di chiamate  
  
1.  Nel **Stack di chiamate** , il pulsante destro finestra frame per il quale non sono stati caricati i simboli. Il frame verrà disattivato (rappresentato in grigio).  
  
2.  Puntare **Carica simboli da** e fare clic su **server dei simboli Microsoft** oppure **percorso dei simboli**.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)



