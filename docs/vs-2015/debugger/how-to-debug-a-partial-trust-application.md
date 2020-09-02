---
title: "Procedura: eseguire il debug di un'applicazione parzialmente attendibile | Microsoft Docs"
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
ms.openlocfilehash: 030fef750cc1e0f0932de32fca1a0ffef56bc8f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704482"
---
# <a name="how-to-debug-a-partial-trust-application"></a>Procedura: eseguire il debug di un'applicazione parzialmente attendibile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le informazioni contenute in questo argomento sono valide per applicazioni Windows e console  
  
 La [protezione e la distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md) semplificano la distribuzione di applicazioni con attendibilità parziale che sfruttano la sicurezza dall'accesso di [codice](https://msdn.microsoft.com/library/859af632-c80d-4736-8d6f-1e01b09ce127) per limitare l'accesso alle risorse in un computer.  
  
 Il debug di un'applicazione parzialmente attendibile può essere complesso perché queste applicazioni hanno autorizzazioni di sicurezza diverse e si comportano quindi in modo diverso in base all'area dalla quale viene eseguita l'installazione. Se l'installazione viene eseguita da Internet, un'applicazione parzialmente attendibile disporrà di poche autorizzazioni. Se l'installazione viene eseguita da una rete Intranet locale, avrà un numero di autorizzazioni maggiore. Se l'installazione viene eseguita dal computer locale, avrà autorizzazioni complete. È inoltre possibile configurare aree personalizzate con autorizzazioni personalizzate. Potrebbe essere necessario eseguire il debug di un'applicazione parzialmente attendibile in una o più di queste condizioni. In Visual Studio sono disponibili strumenti che semplificano anche questo tipo di debug.  
  
 Prima di avviare una sessione di debug in Visual Studio, è possibile scegliere un'area dalla quale simulare l'installazione dell'applicazione. Quando si avvia il debug, verranno assegnate automaticamente le autorizzazioni appropriate per un'applicazione parzialmente attendibile installata da tale area. In questo modo è possibile controllare il comportamento che avrà l'applicazione quando verrà scaricata da tale area da un utente.  
  
 Se l'applicazione tenta di eseguire un'operazione per cui non dispone della necessaria autorizzazione, verrà generata un'eccezione. A questo punto sarà possibile scegliere di aggiungere una nuova autorizzazione tramite la funzionalità Informazioni sulle eccezioni, in modo da poter riavviare la sessione di debug con autorizzazioni sufficienti per evitare il problema.  
  
 È possibile controllare successivamente le autorizzazioni aggiunte durante il debug. Se durante il debug è stato necessario assegnare un'ulteriore autorizzazione, probabilmente occorrerà aggiungere una richiesta di consenso dell'utente in tale punto del codice.  
  
> [!NOTE]
> Per i visualizzatori del debugger sono richiesti maggiori privilegi rispetto a quelli consentiti da un'applicazione parzialmente attendibile. I visualizzatori non vengono caricati in caso di interruzione in codice con attendibilità parziale. Per eseguire il debug tramite un visualizzatore, è necessario eseguire il codice con attendibilità totale.  
  
### <a name="to-choose-a-zone-for-your-partial-trust-application"></a>Per scegliere un'area per l'applicazione parzialmente attendibile  
  
1. Scegliere**proprietà** _NomeProgetto_dal menu **progetto** .  
  
2. Nelle pagine delle proprietà di *NomeProgetto* fare clic sulla pagina **sicurezza** .  
  
3. Selezionare **Abilita impostazioni di sicurezza ClickOnce**.  
  
4. In **area da cui verrà installata l'applicazione**, fare clic sulla casella di riepilogo a discesa e scegliere la zona da cui si desidera simulare l'applicazione da installare.  
  
     Le **autorizzazioni richieste dalla** griglia dell'applicazione visualizzano tutte le autorizzazioni disponibili. Le autorizzazioni assegnate all'applicazione sono contrassegnate con un segno di spunta.  
  
5. Se la zona scelta è **(personalizzata)**, selezionare le impostazioni personalizzate corrette nella colonna **impostazione** della griglia **autorizzazioni** .  
  
6. Scegliere **OK** per chiudere le pagine delle proprietà.  
  
### <a name="to-add-an-extra-permission-when-a-security-exception-occurs"></a>Per aggiungere un'autorizzazione quando si verifica un'eccezione di sicurezza  
  
1. Viene visualizzata la finestra di dialogo informazioni sulle **eccezioni** con il messaggio: **SecurityException non è stato gestito.**  
  
2. Nella finestra di dialogo informazioni sulle **eccezioni** , in **azioni**, fare clic su **Aggiungi autorizzazione al progetto**.  
  
3. Verrà visualizzata la finestra di dialogo **Riavvia debug** .  
  
    - Se si desidera riavviare la sessione di debug con la nuova autorizzazione, fare clic su **Sì**.  
  
    - Se non si vuole ancora riavviare, fare clic su **No**.  
  
### <a name="to-view-extra-permissions-added-while-debugging"></a>Per visualizzare le autorizzazioni aggiunte durante il debug  
  
1. Scegliere**proprietà** _NomeProgetto_dal menu **progetto** .  
  
2. Nelle pagine delle proprietà di *NomeProgetto* fare clic sulla pagina **sicurezza** .  
  
3. Esaminare le **autorizzazioni richieste dalla griglia dell'applicazione** . Eventuali autorizzazioni aggiuntive aggiunte hanno due icone nella colonna **inclusa** : il segno di spunta normale, che include tutte le autorizzazioni incluse, e un'icona aggiuntiva, simile a un fumetto che contiene la lettera "i".  
  
4. Utilizzare la barra di scorrimento verticale per visualizzare le autorizzazioni intere **richieste dalla griglia dell'applicazione** .  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)
