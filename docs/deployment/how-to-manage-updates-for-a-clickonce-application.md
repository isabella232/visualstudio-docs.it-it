---
title: Gestire gli aggiornamenti per un'ClickOnce di | Microsoft Docs
description: Informazioni sulle opzioni per verificare automaticamente o a livello di codice la disponibilità di ClickOnce applicazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Update
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, managing applications
- ClickOnce deployment, updates
- updating data, ClickOnce
- application updates
ms.assetid: a3f23f05-e7f1-4620-b23c-2d68f9643684
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 988fc33a7f8d4f2d535a55fac636340c6dfb93ed
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089979"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>Procedura: Gestire gli aggiornamenti per un'applicazione ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le applicazioni possono verificare la disponibilità di aggiornamenti automaticamente o a livello di codice. Gli sviluppatori hanno una grande flessibilità per specificare quando e come vengono eseguiti i controlli degli aggiornamenti, se gli aggiornamenti sono obbligatori e dove l'applicazione deve controllare la disponibilità di aggiornamenti.

 È possibile configurare l'applicazione in modo che controlli automaticamente la disponibilità di aggiornamenti prima dell'avvio dell'applicazione o a intervalli impostati dopo l'avvio dell'applicazione. È anche possibile specificare una versione minima richiesta. in altri caso, viene installato un aggiornamento se la versione dell'utente è inferiore alla versione richiesta.

 È possibile configurare l'applicazione per verificare la disponibilità di aggiornamenti a livello di codice in base a un evento, ad esempio una richiesta utente. La procedura "Per verificare la disponibilità di aggiornamenti a livello di codice" in questo argomento illustra come scrivere codice che usa la classe per verificare la disponibilità di aggiornamenti in <xref:System.Deployment.Application.ApplicationDeployment> base a un evento.

 È anche possibile distribuire l'applicazione da un percorso e aggiornarla da un'altra. Vedere la procedura "Per specificare un percorso di aggiornamento diverso".

 Per altre informazioni, vedere [Scelta di un ClickOnce di aggiornamento.](../deployment/choosing-a-clickonce-update-strategy.md)

 Il comportamento di aggiornamento viene gestito nella  **finestra di** dialogo Aggiornamenti applicazione, disponibile nella pagina Pubblica di Progettazione Project **progettazione.**

### <a name="to-check-for-updates-before-the-application-starts"></a>Per verificare la disponibilità di aggiornamenti prima dell'avvio dell'applicazione

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic **sul pulsante Aggiornamenti** per aprire la finestra di dialogo **Aggiornamenti** applicazione .

4. Nella finestra **di dialogo Aggiornamenti** applicazione assicurarsi che la casella di controllo L'applicazione deve **controllare** la disponibilità di aggiornamenti sia selezionata.

5. Nella sezione **Scegliere quando l'applicazione deve controllare la disponibilità di aggiornamenti** selezionare Prima **dell'avvio dell'applicazione.** In questo modo si garantisce che gli utenti connessi alla rete esercitino sempre l'applicazione con gli aggiornamenti più recenti.

### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Per cercare gli aggiornamenti in background dopo l'avvio dell'applicazione

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic **sul pulsante Aggiornamenti** per aprire la finestra di dialogo **Aggiornamenti** applicazione .

4. Nella finestra **di dialogo Aggiornamenti** applicazione assicurarsi che la casella di controllo **L'applicazione deve controllare la disponibilità di aggiornamenti** sia selezionata.

5. Nella sezione **Scegliere quando l'applicazione deve controllare la disponibilità di aggiornamenti** selezionare Dopo **l'avvio dell'applicazione.** L'applicazione verrà avviata più rapidamente in questo modo e quindi verifica la presenza di aggiornamenti in background e invia una notifica all'utente solo quando è disponibile un aggiornamento. Dopo l'installazione, gli aggiornamenti saranno effettive solo dopo il riavvio dell'applicazione.

6. Nella sezione **Specificare la frequenza** con cui l'applicazione deve verificare la disponibilità di aggiornamenti selezionare Controlla ogni volta che l'applicazione viene eseguita **(impostazione** predefinita) o **Controlla** ogni e immettere un numero e un intervallo di tempo.

### <a name="to-specify-a-minimum-required-version-for-the-application"></a>Per specificare una versione minima richiesta per l'applicazione

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic **sul pulsante Aggiornamenti** per aprire la finestra di dialogo **Aggiornamenti** applicazione .

4. Nella finestra **di dialogo Aggiornamenti** applicazione assicurarsi che la casella di controllo L'applicazione deve **controllare** la disponibilità di aggiornamenti sia selezionata.

5. Selezionare la **casella di controllo Specificare una** versione minima richiesta per l'applicazione e quindi immettere **i** numeri **Principale,** **Secondario,** Build e **Revisione** per l'applicazione.

### <a name="to-specify-a-different-update-location"></a>Per specificare un percorso di aggiornamento diverso

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic **sul pulsante Aggiornamenti** per aprire la finestra di dialogo **Aggiornamenti** applicazione .

4. Nella finestra **di dialogo Aggiornamenti** applicazione assicurarsi che la casella di controllo L'applicazione deve **controllare** la disponibilità di aggiornamenti sia selezionata.

5. Nel campo **Percorso di** aggiornamento immettere il percorso di aggiornamento con un URL completo, usando il formato , o un percorso UNC usando il formato *http://Hostname/ApplicationName* *\\ \Server\ApplicationName* oppure fare clic sul pulsante Sfoglia per cercare il percorso di aggiornamento. 

### <a name="to-check-for-updates-programmatically"></a>Per verificare la disponibilità di aggiornamenti a livello di codice

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic **sul pulsante Aggiornamenti** per aprire la finestra di dialogo **Aggiornamenti** applicazione .

4. Nella finestra **di dialogo Aggiornamenti** applicazione assicurarsi che la casella di controllo L'applicazione deve **controllare** la disponibilità di aggiornamenti sia deselezionata. Facoltativamente, è possibile selezionare questa casella di controllo per verificare la disponibilità di aggiornamenti a livello di codice e consentire al runtime di ClickOnce di controllare automaticamente la disponibilità di aggiornamenti.

5. Nel campo **Percorso di** aggiornamento immettere il percorso di aggiornamento con un URL completo, usando il formato , o un percorso UNC usando il formato *http://Hostname/ApplicationName* *\\ \Server\ApplicationName* oppure fare clic sul pulsante Sfoglia per cercare il percorso di aggiornamento.  Il percorso di aggiornamento è il percorso in cui l'applicazione cerca una versione aggiornata di se stessa.

6. Creare un pulsante, una voce di menu o un'altra voce dell'interfaccia utente in un modulo Windows che gli utenti selezioneranno per verificare la disponibilità di aggiornamenti. Dal gestore eventi di tale elemento, chiamare un metodo per cercare e installare gli aggiornamenti. È possibile trovare un esempio di codice Visual Basic e Visual C# per questo metodo in [Procedura: Controllare](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)gli aggiornamenti dell'applicazione a livello di codice usando l'API ClickOnce distribuzione .

7. Compilare l'applicazione.

## <a name="see-also"></a>Vedi anche
- <xref:System.Deployment.Application.ApplicationDeployment>
- [Finestra di dialogo Aggiornamenti applicazione](/previous-versions/visualstudio/visual-studio-2010/axw1fa38(v=vs.100))
- [Scegliere una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: Pubblicare un'applicazione ClickOnce tramite la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Procedura: Controllare gli aggiornamenti dell'applicazione a livello di codice tramite l'API della distribuzione ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)
