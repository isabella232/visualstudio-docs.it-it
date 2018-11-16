---
title: 'Procedura: eseguire il Debug di un eseguibile non incluso in una soluzione di Visual Studio | Microsoft Docs'
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
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a7fb9b0a31f078ce197851bccb1f4c85f24408a0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798664"
---
# <a name="how-to-debug-an-executable-not-part-of-a-visual-studio-solution"></a>Procedura: eseguire il debug di un eseguibile non incluso in una soluzione di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Talvolta può essere necessario eseguire il debug di un file eseguibile non incluso in un progetto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ossia di un eseguibile creato all'esterno di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o ricevuto da un altro sviluppatore.  
  
 In questi casi, normalmente si avvia l'eseguibile all'esterno di Visual Studio e ci si connette al processo in esecuzione utilizzando il debugger di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Per altre informazioni, vedere[connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 Per connettersi a un'applicazione è necessario eseguire delle operazioni manuali che richiedono alcuni secondi. A causa di questo minimo ritardo, la connessione non risulterà utile se si tenta di eseguire il debug di un problema verificatosi in fase di avvio. Se inoltre si esegue il debug di un programma che non richiede input da parte dell'utente e che termina rapidamente, il tempo necessario per eseguire la connessione potrebbe non essere disponibile. Se si è installato [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], è possibile creare un progetto EXE per tale programma.  
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>Per creare un progetto EXE per un eseguibile esistente  
  
1.  Nel **File** menu, fare clic su **Open** e selezionare **progetto**.  
  
2.  Nel **Apri progetto** finestra di dialogo, fare clic sull'elenco a discesa elenco per il **nome File** , quindi selezionare **tutti i file di progetto**.  
  
3.  Individuare il file eseguibile e scegliere **OK**.  
  
     In questo modo verrà creata una soluzione temporanea contenente l'eseguibile.  
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>Per importare un eseguibile in una soluzione di Visual Studio  
  
1.  Nel **File** dal menu **Aggiungi progetto**, quindi fare clic su **progetto esistente**.  
  
2.  Nel **Aggiungi progetto esistente** finestra di dialogo, fare clic sull'elenco a discesa elenco per il **nome File** , quindi selezionare **tutti i file di progetto**.  
  
3.  Individuare e selezionare l'eseguibile.  
  
4.  Fare clic su **OK**.  
  
5.  Avviare l'eseguibile scegliendo un comando di esecuzione, ad esempio **avviare**, dalle **Debug** menu.  
  
    > [!NOTE]
    >  I progetti EXE non sono supportati da tutti i linguaggi di programmazione. Se è necessario utilizzare questa funzionalità, installare [!INCLUDE[vcprvc](../includes/vcprvc-md.md)].  
  
     Quando si effettua il debug di un eseguibile senza il codice sorgente, le funzionalità di debug disponibili sono limitate, indipendentemente dal fatto che si stabilisca una connessione a un eseguibile in esecuzione o che si aggiunga l'eseguibile a una soluzione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Se l'eseguibile è stato compilato senza informazioni di debug in un formato compatibile, le funzionalità disponibili risulteranno ulteriormente limitate. Se si dispone del codice sorgente, l'approccio migliore consiste nell'importarlo in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e nel creare una build di debug dell'eseguibile in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Debugger Settings and Preparation](../debugger/debugger-settings-and-preparation.md)  (Impostazioni di debug e preparazione)  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [DBG (file)](http://msdn.microsoft.com/en-us/91e449e9-8b65-4123-960f-2107cd1f1cfd)



