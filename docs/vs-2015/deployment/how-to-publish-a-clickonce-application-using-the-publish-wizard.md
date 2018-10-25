---
title: "Procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- deploying applications [ClickOnce], Publish wizard
- Windows applications, ClickOnce deployments
- publishing, ClickOnce
ms.assetid: 2e4aa67c-4445-4f7b-9e03-9acb95829127
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: f8708658e5daf90e24a0336040ba2b766d5ae975
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862827"
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>Procedura: pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per rendere disponibile un'applicazione ClickOnce agli utenti, è necessario pubblicarla in un una condivisione file, in un percorso, in un server FTP o su un supporto rimovibile. È possibile pubblicare l'applicazione usando la pubblicazione guidata. proprietà aggiuntive relative alla pubblicazione sono disponibili sul **Publish** pagina della **creazione progetti**. Per altre informazioni, vedere [pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md).  
  
 Prima di eseguire la Pubblicazione guidata, impostare correttamente le opzioni di pubblicazione. Ad esempio, se si vuole designare una chiave per firmare l'applicazione ClickOnce, non è così via il **Signing** pagina della **creazione progetti**. Per altre informazioni, vedere [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md).  
  
> [!NOTE]
>  Quando si installa più di una versione di un'applicazione tramite ClickOnce, l'installazione sposta le versioni precedenti dell'applicazione in una cartella denominata Archivio, nel percorso di pubblicazione specificato. L'archiviazione delle versioni precedenti consente di mantenere pulita la directory di installazione.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-publish-to-a-file-share-or-path"></a>Per pubblicare in una condivisione file o in un percorso  
  
1. Nelle **Esplora soluzioni**, selezionare il progetto di applicazione.  
  
2. Nel **compilare** menu, fare clic su **Publish**`Projectname`.  
  
    Verrà visualizzata la Pubblicazione guidata.  
  
3. Nel **in cui si desidera pubblicare l'applicazione?** pagina, immettere un indirizzo del server FTP valido o un percorso valido usando uno dei formati indicati e quindi fare clic su **successivo**.  
  
4. Nel **modo in cui gli utenti installeranno l'applicazione?** pagina, selezionare il percorso in cui accederanno gli utenti per installare l'applicazione:  
  
   -   Se gli utenti eseguiranno l'installazione da un sito Web, fare clic su **da un sito Web** e immettere un URL che corrisponde al percorso di file specificato nel passaggio precedente. Scegliere **Avanti**. In genere questa opzione viene usata quando si specifica un indirizzo FTP come percorso di pubblicazione. Il download diretto da FTP non è supportato, di conseguenza, è necessario specificare un URL.  
  
   -   Se gli utenti installeranno l'applicazione direttamente dalla condivisione file, fare clic su **condivisione file o percorso UNC da un**, quindi fare clic su **successivo**. (Si tratta di pubblicazione di percorsi di c:\deploy\myapp il form o \\\server\myapp.)  
  
   -   Se gli utenti eseguiranno l'installazione da un supporto rimovibile, fare clic su **da CD-ROM o DVD-ROM**, quindi fare clic su **successivo**.  
  
5. Nel **l'applicazione sarà disponibile offline?** pagina, fare clic sull'opzione appropriata:  
  
   - Se si desidera abilitare l'applicazione da eseguire quando l'utente è disconnesso dalla rete, fare clic su **Sì, questa applicazione sarà disponibile online o offline**. Un collegamento sul **avviare** menu verrà creato per l'applicazione.  
  
   - Se si desidera eseguire l'applicazione direttamente dal percorso di pubblicazione, fare clic su **No, questa applicazione è disponibile solo online**. Un collegamento sul **avviare** menu non verrà creato.  
  
     Fare clic su **Avanti** per continuare.  
  
6. Fare clic su **fine** per pubblicare l'applicazione.  
  
    Lo stato di pubblicazione è visualizzato nell'area di notifica dello stato.  
  
### <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>Per pubblicare su CD-ROM o DVD-ROM  
  
1. Nelle **Esplora soluzioni**, fare doppio clic sul progetto di applicazione e fare clic su **proprietà**.  
  
    Viene visualizzata la finestra **Creazione progetti**.  
  
2. Fare clic sul **Publish** pressione di tab per aprire il **Publish** nella pagina il **Progettazione progetti**e fare clic sul **pubblicazione guidata** pulsante.  
  
    Verrà visualizzata la Pubblicazione guidata.  
  
3. Nel **in cui si desidera pubblicare l'applicazione?** pagina, immettere il percorso del file o percorso FTP in cui verrà pubblicata l'applicazione, ad esempio d:\deploy. Quindi fare clic su **successivo** per continuare.  
  
4. Nel **modo in cui gli utenti installeranno l'applicazione?** pagina, fare clic su un **CD-ROM o DVD-ROM**e quindi fare clic su **Avanti**.  
  
   > [!NOTE]
   >  Se si desidera che l'installazione venga eseguita automaticamente quando il CD-ROM viene inserito nell'unità, aprire il **Publish** nella pagina la **creazione progetti** e fare clic sui **opzioni** pulsante, quindi il **Publish Options** procedura guidata, selezionare **per installazioni da CD, avvia automaticamente l'installazione all'inserimento del CD**.  
  
5. Se l'applicazione viene distribuita tramite CD-ROM, sarà necessario pubblicare gli aggiornamenti in un sito Web. Nel **in cui l'applicazione controllerà gli aggiornamenti?** , scegliere un'opzione di aggiornamento pagina:  
  
   - Se l'applicazione controllerà gli aggiornamenti, fare clic su **l'applicazione controllerà gli aggiornamenti dal seguente percorso** e immettere il percorso in cui verranno pubblicati aggiornamenti. Può trattarsi di un percorso di file, un sito Web o un server FTP.  
  
   - Se l'applicazione non controllerà gli aggiornamenti, fare clic su **l'applicazione non controllerà gli aggiornamenti**.  
  
     Fare clic su **Avanti** per continuare.  
  
6. Fare clic su **fine** per pubblicare l'applicazione.  
  
    Lo stato di pubblicazione è visualizzato nell'area di notifica dello stato.  
  
   > [!NOTE]
   >  Al termine della pubblicazione, sarà necessario usare un masterizzatore CD o DVD per copiare i file dal percorso specificato nel passaggio 3 al CD-ROM o DVD-ROM.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Distribuzione di una soluzione Office mediante ClickOnce](http://msdn.microsoft.com/library/feb516b3-5e4d-449a-9fd2-347d08d90252)



