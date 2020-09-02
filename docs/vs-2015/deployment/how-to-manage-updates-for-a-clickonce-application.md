---
title: "Procedura: gestire gli aggiornamenti per un'applicazione ClickOnce | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0754d816104832f92a0be8d754046d1ee18e7a09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697643"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>Procedura: gestire gli aggiornamenti per un'applicazione ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] le applicazioni possono verificare la disponibilità di aggiornamenti automaticamente o a livello di codice. Gli sviluppatori hanno molta flessibilità nell'specificare quando e come vengono eseguiti i controlli di aggiornamento, se gli aggiornamenti sono obbligatori e quando l'applicazione deve verificare la disponibilità di aggiornamenti.  
  
 È possibile configurare l'applicazione per verificare la disponibilità di aggiornamenti automaticamente prima che l'applicazione venga avviata o a intervalli prestabiliti dopo l'avvio dell'applicazione. È inoltre possibile specificare una versione minima richiesta. ovvero viene installato un aggiornamento se la versione dell'utente è inferiore alla versione richiesta.  
  
 È possibile configurare l'applicazione per verificare la disponibilità di aggiornamenti a livello di codice in base a un evento, ad esempio una richiesta dell'utente. La procedura "per verificare la disponibilità di aggiornamenti a livello di codice" in questo argomento illustra come scrivere codice che usa la <xref:System.Deployment.Application.ApplicationDeployment> classe per verificare la disponibilità di aggiornamenti in base a un evento.  
  
 È anche possibile distribuire l'applicazione da un percorso e aggiornarlo da un altro. Vedere la procedura "per specificare un percorso di aggiornamento diverso".  
  
 Per ulteriori informazioni, vedere [scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Il comportamento di aggiornamento viene gestito nella finestra di dialogo **Aggiornamenti applicazione** , disponibile nella pagina **pubblica** di **Progettazione progetti.**  
  
### <a name="to-check-for-updates-before-the-application-starts"></a>Per verificare la disponibilità di aggiornamenti prima dell'avvio dell'applicazione  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2. Fare clic sulla scheda **Pubblica**.  
  
3. Fare clic sul pulsante **aggiornamenti** per aprire la finestra di dialogo **Aggiornamenti applicazione** .  
  
4. Nella finestra di dialogo **Aggiornamenti applicazione** assicurarsi che la casella **di controllo l'applicazione deve verificare la disponibilità di aggiornamenti** sia selezionata.  
  
5. Nella sezione **scegliere quando controllare gli aggiornamenti dell'applicazione** selezionare **prima che l'applicazione venga avviata**. In questo modo si garantisce che gli utenti connessi alla rete eseguano sempre l'applicazione con gli aggiornamenti più recenti.  
  
### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Per cercare gli aggiornamenti in background dopo l'avvio dell'applicazione  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2. Fare clic sulla scheda **Pubblica**.  
  
3. Fare clic sul pulsante **aggiornamenti** per aprire la finestra di dialogo **Aggiornamenti applicazione** .  
  
4. Nella finestra di dialogo **Aggiornamenti applicazione** verificare che sia selezionata la casella **di controllo l'applicazione deve verificare la disponibilità di aggiornamenti** .  
  
5. Nella **sezione scegliere quando controllare gli aggiornamenti dell'applicazione**selezionare **dopo l'avvio dell'applicazione**. L'applicazione verrà avviata più rapidamente in questo modo, quindi verificherà la disponibilità di aggiornamenti in background e invierà una notifica all'utente solo quando è disponibile un aggiornamento. Una volta installato, gli aggiornamenti non saranno effettivi fino al riavvio dell'applicazione.  
  
6. Nella sezione **specificare la frequenza con cui l'applicazione deve verificare la disponibilità di aggiornamenti** selezionare **Controlla ogni volta che viene eseguita l'applicazione** (impostazione predefinita) o **Controlla ogni** e immettere un numero e un intervallo di tempo.  
  
### <a name="to-specify-a-minimum-required-version-for-the-application"></a>Per specificare una versione minima richiesta per l'applicazione  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2. Fare clic sulla scheda **Pubblica**.  
  
3. Fare clic sul pulsante **aggiornamenti** per aprire la finestra di dialogo **Aggiornamenti applicazione** .  
  
4. Nella finestra di dialogo **Aggiornamenti applicazione** assicurarsi che la casella **di controllo l'applicazione deve verificare la disponibilità di aggiornamenti** sia selezionata.  
  
5. Selezionare la **casella di controllo specificare una versione minima richiesta per l'applicazione** , quindi immettere i numeri **principale**, **secondario**, **Build**e **Revisione** per l'applicazione.  
  
### <a name="to-specify-a-different-update-location"></a>Per specificare un percorso di aggiornamento diverso  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2. Fare clic sulla scheda **Pubblica**.  
  
3. Fare clic sul pulsante **aggiornamenti** per aprire la finestra di dialogo **Aggiornamenti applicazione** .  
  
4. Nella finestra di dialogo **Aggiornamenti applicazione** assicurarsi che la casella **di controllo l'applicazione deve verificare la disponibilità di aggiornamenti** sia selezionata.  
  
5. Nel campo **percorso aggiornamento** immettere il percorso di aggiornamento con un URL completo, usando il formato http://Hostname/ApplicationName o un percorso UNC usando il formato \\ \Server\ApplicationName oppure fare clic sul pulsante **Sfoglia** per cercare il percorso di aggiornamento.  
  
### <a name="to-check-for-updates-programmatically"></a>Per verificare la disponibilità di aggiornamenti a livello di codice  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2. Fare clic sulla scheda **Pubblica**.  
  
3. Fare clic sul pulsante **aggiornamenti** per aprire la finestra di dialogo **Aggiornamenti applicazione** .  
  
4. Nella finestra di dialogo **Aggiornamenti applicazione** assicurarsi che la casella **di controllo l'applicazione deve verificare la disponibilità di aggiornamenti** sia deselezionata. Facoltativamente, è possibile selezionare questa casella di controllo per verificare la disponibilità di aggiornamenti a livello di codice e consentire al runtime di ClickOnce di controllare automaticamente la disponibilità di aggiornamenti.  
  
5. Nel campo **percorso aggiornamento** immettere il percorso di aggiornamento con un URL completo, usando il formato http://Hostname/ApplicationName o un percorso UNC usando il formato \\ \Server\ApplicationName oppure fare clic sul pulsante **Sfoglia** per cercare il percorso di aggiornamento. Il percorso di aggiornamento è il punto in cui l'applicazione cercherà una versione aggiornata di se stessa.  
  
6. Consente di creare un pulsante, una voce di menu o un altro elemento dell'interfaccia utente in un Windows Form che gli utenti selezioneranno per verificare la disponibilità di aggiornamenti. Dal gestore eventi di tale elemento, chiamare un metodo per verificare e installare gli aggiornamenti. È possibile trovare un esempio di codice Visual Basic e Visual C# per un metodo di questo tipo in [procedura: verificare la disponibilità di aggiornamenti dell'applicazione a livello di programmazione tramite l'API di distribuzione ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md).  
  
7. Compilare l'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [Finestra di dialogo Aggiornamenti applicazione](https://msdn.microsoft.com/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f)   
 [Scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Procedura: verificare la disponibilità di aggiornamenti dell'applicazione a livello di codice tramite l'API di distribuzione ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)
