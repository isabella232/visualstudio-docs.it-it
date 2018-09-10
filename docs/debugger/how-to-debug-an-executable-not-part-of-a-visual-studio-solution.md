---
title: 'Procedura: eseguire il Debug di un file eseguibile che non fa parte di una soluzione di Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce84c4acdc2cf4324c76dbbf7fe0b39ca9715b3c
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279102"
---
# <a name="how-to-debug-an-executable-that-is-not-part-of-a-visual-studio-solution"></a>Procedura: eseguire il Debug di un file eseguibile che non fa parte di una soluzione di Visual Studio
In alcuni casi, è possibile eseguire il debug di un file eseguibile (file .exe) che non fa parte di un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto. ossia di un eseguibile creato all'esterno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o ricevuto da un altro sviluppatore.  
  
In questi casi, normalmente si avvia l'eseguibile all'esterno di Visual Studio e ci si connette al processo in esecuzione utilizzando il debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per altre informazioni, vedere [connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
Per connettersi a un'applicazione è necessario eseguire delle operazioni manuali che richiedono alcuni secondi. A causa di questo minimo ritardo, la connessione non risulterà utile se si tenta di eseguire il debug di un problema verificatosi in fase di avvio. Se inoltre si esegue il debug di un programma che non richiede input da parte dell'utente e che termina rapidamente, il tempo necessario per eseguire la connessione potrebbe non essere disponibile. Se hai [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] e [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] installato, è possibile creare un progetto EXE per tale programma.

> [!NOTE]
>  I progetti EXE non sono supportati da tutti i linguaggi di programmazione.

Quando si esegue il debug di un file eseguibile che non fa parte della soluzione di Visual Studio, le funzionalità di debug disponibili potrebbero risultare limitate, che si collega a un file eseguibile o aggiunga il file eseguibile in un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soluzione.

- Se si dispone del codice sorgente, l'approccio migliore consiste nell'importarlo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e nel creare una build di debug dell'eseguibile in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].
- Se non hai il codice sorgente e se il file eseguibile è stato compilato senza [le informazioni di debug](../debugger/how-to-set-debug-and-release-configurations.md) in un formato compatibile, funzionalità di debug disponibili sono molto limitate. 
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>Per creare un progetto EXE per un eseguibile esistente  
  
1.  Nel **File** menu, fare clic su **Open** e selezionare **progetto**.  
  
2.  Nel **Apri progetto** finestra di dialogo, fare clic sull'elenco a discesa elenco per il **nome File** , quindi selezionare **tutti i file di progetto**.  
  
3.  Individuare il file eseguibile e scegliere **OK**.  

    In questo modo verrà creata una soluzione temporanea contenente l'eseguibile.

5.  Avviare l'eseguibile scegliendo un comando di esecuzione, ad esempio **avviare**, dalle **Debug** menu.    
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>Per importare un eseguibile in una soluzione di Visual Studio  
  
1.  Nel **File** dal menu **Aggiungi progetto**, quindi fare clic su **progetto esistente**.  
  
2.  Nel **Aggiungi progetto esistente** finestra di dialogo, fare clic sull'elenco a discesa elenco per il **nome File** , quindi selezionare **tutti i file di progetto**.  
  
3.  Individuare e selezionare l'eseguibile.  
  
4.  Fare clic su **OK**.  
  
5.  Avviare l'eseguibile scegliendo un comando di esecuzione, ad esempio **avviare**, dalle **Debug** menu.    
  
## <a name="see-also"></a>Vedere anche  
 [Debugger Settings and Preparation](../debugger/debugger-settings-and-preparation.md)  (Impostazioni di debug e preparazione)  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [DBG (file)](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))