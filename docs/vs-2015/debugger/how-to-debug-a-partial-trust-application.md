---
title: "Procedura: Eseguire il debug di un'applicazione con attendibilità parziale | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], partial trust applications
- partial trust applications
- security [Visual Studio], partial trust applications
ms.assetid: 9d30ad92-28ce-4b21-91d8-698474cddf64
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8340867406e99fd6c6f84d1dc84d89a395a338fb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60106865"
---
# <a name="how-to-debug-a-partial-trust-application"></a>Procedura: Eseguire il debug di un'applicazione parzialmente attendibile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le informazioni contenute in questo argomento sono valide per applicazioni Windows e console  
  
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md) rende più semplice distribuire le applicazioni parzialmente attendibili che sfruttano [Code Access Security](http://msdn.microsoft.com/library/859af632-c80d-4736-8d6f-1e01b09ce127) per limitare l'accesso alle risorse in un computer.  
  
 Il debug di un'applicazione parzialmente attendibile può essere complesso perché queste applicazioni hanno autorizzazioni di sicurezza diverse e si comportano quindi in modo diverso in base all'area dalla quale viene eseguita l'installazione. Se l'installazione viene eseguita da Internet, un'applicazione parzialmente attendibile disporrà di poche autorizzazioni. Se l'installazione viene eseguita da una rete Intranet locale, avrà un numero di autorizzazioni maggiore. Se l'installazione viene eseguita dal computer locale, avrà autorizzazioni complete. È inoltre possibile configurare aree personalizzate con autorizzazioni personalizzate. Potrebbe essere necessario eseguire il debug di un'applicazione parzialmente attendibile in una o più di queste condizioni. In Visual Studio sono disponibili strumenti che semplificano anche questo tipo di debug.  
  
 Prima di avviare una sessione di debug in Visual Studio, è possibile scegliere un'area dalla quale simulare l'installazione dell'applicazione. Quando si avvia il debug, verranno assegnate automaticamente le autorizzazioni appropriate per un'applicazione parzialmente attendibile installata da tale area. In questo modo è possibile controllare il comportamento che avrà l'applicazione quando verrà scaricata da tale area da un utente.  
  
 Se l'applicazione tenta di eseguire un'operazione per cui non dispone della necessaria autorizzazione, verrà generata un'eccezione. A questo punto sarà possibile scegliere di aggiungere una nuova autorizzazione tramite la funzionalità Informazioni sulle eccezioni, in modo da poter riavviare la sessione di debug con autorizzazioni sufficienti per evitare il problema.  
  
 È possibile controllare successivamente le autorizzazioni aggiunte durante il debug. Se durante il debug è stato necessario assegnare un'ulteriore autorizzazione, probabilmente occorrerà aggiungere una richiesta di consenso dell'utente in tale punto del codice.  
  
> [!NOTE]
>  Per i visualizzatori del debugger sono richiesti maggiori privilegi rispetto a quelli consentiti da un'applicazione parzialmente attendibile. I visualizzatori non vengono caricati in caso di interruzione in codice con attendibilità parziale. Per eseguire il debug tramite un visualizzatore, è necessario eseguire il codice con attendibilità totale.  
  
### <a name="to-choose-a-zone-for-your-partial-trust-application"></a>Per scegliere un'area per l'applicazione parzialmente attendibile  
  
1. Dal **Project** menu, scegliere _NomeProgetto_**proprietà**.  
  
2. Nel *Projectname* pagine delle proprietà, fare clic sui **sicurezza** pagina.  
  
3. Selezionare **abilitare le impostazioni di sicurezza ClickOnce**.  
  
4. Sotto **zona da cui verrà installata l'applicazione**, selezionare la casella di riepilogo di elenco a discesa e selezionare l'area dalla quale si desidera simulare l'installazione dell'applicazione.  
  
     Il **le autorizzazioni richieste dall'applicazione** griglia vengono visualizzate tutte le autorizzazioni disponibili. Le autorizzazioni assegnate all'applicazione sono contrassegnate con un segno di spunta.  
  
5. Se si sceglie l'area è stata **(personalizzata)**, selezionare le impostazioni personalizzate adeguate nella **impostazione** colonna del **autorizzazioni** griglia.  
  
6. Scegliere **OK** per chiudere le pagine delle proprietà.  
  
### <a name="to-add-an-extra-permission-when-a-security-exception-occurs"></a>Per aggiungere un'autorizzazione quando si verifica un'eccezione di sicurezza  
  
1. Il **informazioni sulle eccezioni** verrà visualizzata la finestra di dialogo con messaggio: **SecurityException non gestita.**  
  
2. Nel **informazioni sulle eccezioni** nella finestra di dialogo **azioni**, fare clic su **Aggiungi autorizzazione al progetto**.  
  
3. Il **riavvia Debug** verrà visualizzata la finestra di dialogo.  
  
    - Se si desidera riavviare la sessione di debug con la nuova autorizzazione, fare clic su **Sì**.  
  
    - Se non si desidera riavviare ancora, fare clic su **No**.  
  
### <a name="to-view-extra-permissions-added-while-debugging"></a>Per visualizzare le autorizzazioni aggiunte durante il debug  
  
1. Dal **Project** menu, scegliere _NomeProgetto_**proprietà**.  
  
2. Nel *Projectname* pagine delle proprietà, fare clic sui **sicurezza** pagina.  
  
3. Esaminare i **le autorizzazioni richieste dall'applicazione** griglia. Le autorizzazioni aggiunti sono presenti due icone **inclusi** colonna: il segno di spunta normale, che dispone di autorizzazioni, tutti inclusi e un'icona aggiuntiva a forma di fumetto con una lettera "i".  
  
4. Usare la barra di scorrimento verticale per visualizzare l'intera **le autorizzazioni richieste dall'applicazione** griglia.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)
