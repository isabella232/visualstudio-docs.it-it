---
title: "Procedura: verificare la disponibilità di aggiornamenti dell'applicazione a livello di codice utilizzando l'API di distribuzione ClickOnce Documenti Microsoft"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5250e719cce945bdcce90a9d49d2ed8c27555612
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444978"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Procedura: controllare gli aggiornamenti dell'applicazione a livello di codice tramite l'API della distribuzione ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnceClickOnce offre due modi per aggiornare un'applicazione dopo la distribuzione. Nel primo metodo è possibile configurare la distribuzione ClickOnce per verificare automaticamente la disponibilità di aggiornamenti a determinati intervalli. Nel secondo metodo, è possibile scrivere <xref:System.Deployment.Application.ApplicationDeployment> codice che utilizza la classe per verificare la disponibilità di aggiornamenti in base a un evento, ad esempio una richiesta dell'utente.  
  
 Nelle procedure seguenti viene illustrato del codice per l'esecuzione di un aggiornamento a livello di codice e viene inoltre descritto come configurare la distribuzione ClickOnce per abilitare i controlli di aggiornamento a livello di codice.  
  
 Per aggiornare un'applicazione ClickOnce a livello di codice, è necessario specificare un percorso per gli aggiornamenti. Questa operazione viene talvolta definita provider di distribuzione. Per ulteriori informazioni sull'impostazione di questa proprietà, vedere [Scelta di una strategia](../deployment/choosing-a-clickonce-update-strategy.md)di aggiornamento ClickOnce .  
  
> [!NOTE]
> È anche possibile usare la tecnica descritta di seguito per distribuire l'applicazione da una posizione ma aggiornarla da un'altra. Per ulteriori informazioni, vedere [Procedura: specificare un percorso alternativo per gli aggiornamenti della distribuzione](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### <a name="to-check-for-updates-programmatically"></a>Per verificare la disponibilità di aggiornamenti a livello di codiceTo check for updates programmatically  
  
1. Creare una nuova applicazione Windows Form utilizzando gli strumenti visivi o della riga di comando preferiti.  
  
2. Creare qualsiasi pulsante, voce di menu o altro elemento dell'interfaccia utente che si desidera che gli utenti di selezionare per verificare la disponibilità di aggiornamenti. Dal gestore eventi dell'elemento, chiamare il metodo seguente per cercare e installare gli aggiornamenti.  
  
     [!code-cpp[ClickOnceAPI#6](../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp#6)]
     [!code-csharp[ClickOnceAPI#6](../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs#6)]
     [!code-vb[ClickOnceAPI#6](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb#6)]  
  
3. Compilare l'applicazione.Compile your application.  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Utilizzo di Mage.exe per distribuire un'applicazione che verifica la disponibilità di aggiornamenti a livello di codiceUsing Mage.exe to deploy an application that checks for updates programmatically  
  
- Seguire le istruzioni per la distribuzione dell'applicazione utilizzando Mage.exe come illustrato in [Procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Quando si chiama Mage.exe per generare il manifesto di `providerUrl`distribuzione, assicurarsi di utilizzare l'opzione della riga di comando e di specificare l'URL in cui ClickOnce deve verificare la disponibilità di aggiornamenti. Se l'applicazione `http://www.adatum.com/MyApp`verrà aggiornata da , ad esempio, la chiamata per generare il manifesto di distribuzione potrebbe essere simile alla seguente:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Utilizzo di MageUI.exe per distribuire un'applicazione che verifica la disponibilità di aggiornamenti a livello di codiceUsing MageUI.exe to deploy an application that checks for updates programmatically  
  
- Seguire le istruzioni per la distribuzione dell'applicazione utilizzando Mage.exe come illustrato in [Procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Nella scheda **Opzioni di distribuzione** impostare il campo Percorso di **avvio** sul manifesto dell'applicazione ClickOnce deve verificare la disponibilità di aggiornamenti. Nella scheda **Opzioni di aggiornamento** deselezionare la casella di controllo **L'applicazione deve verificare** la disponibilità di aggiornamenti.  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 L'applicazione deve disporre di autorizzazioni di attendibilità totale per utilizzare l'aggiornamento a livello di codice.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: specificare un percorso alternativo per gli aggiornamenti della distribuzioneHow to: Specify an Alternate Location for Deployment Updates](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Scelta di una strategia di aggiornamento ClickOnceChoosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
