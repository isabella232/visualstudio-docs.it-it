---
title: "Procedura: Verificare la presenza di aggiornamenti dell'applicazione a livello di codice tramite l'API della distribuzione ClickOnce | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27e1f1b923b395121fb5671088d99421a79c45fc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059214"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Procedura: Controllo programmatico degli aggiornamenti delle applicazioni attraverso l'API per la distribuzione ClickOnce
ClickOnce fornisce due modi per aggiornare un'applicazione dopo la distribuzione. Il primo metodo, è possibile configurare la distribuzione ClickOnce per cercare automaticamente gli aggiornamenti a intervalli specifici. Il secondo metodo, è possibile scrivere codice che usa il <xref:System.Deployment.Application.ApplicationDeployment> classe per cercare gli aggiornamenti basati su un evento, ad esempio una richiesta dell'utente.

 Le procedure seguenti mostrano un codice per l'esecuzione di un aggiornamento a livello di codice e viene inoltre descritto come configurare la distribuzione ClickOnce per abilitare i controlli di aggiornamento a livello di codice.

 Per aggiornare un'applicazione ClickOnce a livello di codice, è necessario specificare un percorso per gli aggiornamenti. Ciò è talvolta detta un provider di distribuzione. Per altre informazioni su come impostare questa proprietà, vedere [sceglie una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

> [!NOTE]
>  È anche possibile usare la tecnica descritta di seguito per distribuire l'applicazione da un'unica posizione, ma è un aggiornamento da un'altra. Per altre informazioni, vedere [Procedura: Specificare un percorso alternativo per gli aggiornamenti della distribuzione](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).

### <a name="to-check-for-updates-programmatically"></a>Per cercare gli aggiornamenti a livello di codice

1. Creare una nuova applicazione Windows Forms utilizzando gli strumenti Preferiti della riga di comando o nell'oggetto visivo.

2. Creare pulsanti, voce di menu o altro elemento dell'interfaccia utente si vuole che gli utenti per selezionare questa opzione per verificare la presenza di aggiornamenti. Dal gestore eventi dell'elemento, chiamare il metodo seguente per cercare e installare gli aggiornamenti.

     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]

3. Compilare l'applicazione.

### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Usare Mage.exe per distribuire un'applicazione che verifica la presenza di aggiornamenti a livello di codice

- Seguire le istruzioni per la distribuzione dell'applicazione mediante Mage.exe come descritto in [procedura dettagliata: Distribuire manualmente un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Quando si chiama Mage.exe per generare il manifesto di distribuzione, assicurarsi di usare l'opzione della riga di comando `providerUrl`e per specificare l'URL in cui deve essere controllato per gli aggiornamenti. Se l'applicazione verrà aggiornata dalla [ http://www.adatum.com/MyApp ](http://www.adatum.com/MyApp), ad esempio, la chiamata per generare il manifesto della distribuzione sarà simile al seguente:

    ```cmd
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application
    ```

### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Uso di MageUI.exe per distribuire un'applicazione che verifica la presenza di aggiornamenti a livello di codice

- Seguire le istruzioni per la distribuzione dell'applicazione mediante Mage.exe come descritto in [procedura dettagliata: Distribuire manualmente un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Nel **opzioni di distribuzione** scheda, impostare il **percorso iniziale** campo al manifesto dell'applicazione ClickOnce deve cercare gli aggiornamenti. Nel **opzioni di aggiornamento** scheda, deseleziona le **l'applicazione deve controllare disponibilità di aggiornamenti** casella di controllo.

## <a name="net-framework-security"></a>Sicurezza di .NET Framework
 L'applicazione deve disporre delle autorizzazioni di attendibilità per utilizzare l'aggiornamento a livello di codice.

## <a name="see-also"></a>Vedere anche
- [Procedura: Specificare un percorso alternativo per la distribuzione degli aggiornamenti](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)
- [Scegliere una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)