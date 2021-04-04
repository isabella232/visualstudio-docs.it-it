---
title: Aggiornamenti automatici delle app usando l'API di distribuzione ClickOnce
description: Informazioni su come scrivere codice in ClickOnce che usa la classe ApplicationDeployment per verificare la disponibilità di aggiornamenti in base a un evento, ad esempio una richiesta dell'utente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: db82151b7fd4dbe894cecf8fbf5f5b64cb2f5919
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106213940"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Procedura: Controllare gli aggiornamenti dell'applicazione a livello di codice tramite l'API della distribuzione ClickOnce
ClickOnce offre due modi per aggiornare un'applicazione dopo che è stata distribuita. Nel primo metodo, è possibile configurare la distribuzione ClickOnce per verificare automaticamente la disponibilità di aggiornamenti a intervalli specifici. Nel secondo metodo, è possibile scrivere codice che usa la <xref:System.Deployment.Application.ApplicationDeployment> classe per verificare la disponibilità di aggiornamenti in base a un evento, ad esempio una richiesta dell'utente.

 Nelle procedure riportate di seguito viene illustrato il codice per l'esecuzione di un aggiornamento programmatico e viene descritto come configurare la distribuzione ClickOnce per abilitare i controlli di aggiornamento a livello di codice

 Per aggiornare un'applicazione ClickOnce a livello di codice, è necessario specificare un percorso per gli aggiornamenti. Questa operazione viene a volte definita provider di distribuzione. Per ulteriori informazioni sull'impostazione di questa proprietà, vedere [scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

> [!NOTE]
> È anche possibile usare la tecnica descritta di seguito per distribuire l'applicazione da una posizione, ma aggiornarla da un'altra. Per altre informazioni, vedere [procedura: specificare un percorso alternativo per gli aggiornamenti della distribuzione](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).

### <a name="to-check-for-updates-programmatically"></a>Per verificare la disponibilità di aggiornamenti a livello di codice

1. Creare una nuova Windows Forms Application usando la riga di comando o gli strumenti visivi preferiti.

2. Creare qualsiasi pulsante, voce di menu o altro elemento dell'interfaccia utente che si desidera che gli utenti scelgano per verificare la disponibilità di aggiornamenti. Dal gestore eventi di tale elemento, chiamare il metodo seguente per verificare e installare gli aggiornamenti.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs" id="Snippet6":::
    :::code language="cpp" source="../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp" id="Snippet6":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb" id="Snippet6":::

3. Compilare l'applicazione.

### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Usare Mage.exe per distribuire un'applicazione che verifica la disponibilità di aggiornamenti a livello di codice

- Seguire le istruzioni per la distribuzione dell'applicazione usando Mage.exe come illustrato in [procedura dettagliata: distribuire manualmente un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Quando si chiama Mage.exe per generare il manifesto di distribuzione, assicurarsi di usare l'opzione della riga di comando `providerUrl` e di specificare l'URL in cui ClickOnce deve verificare la disponibilità di aggiornamenti. Se l'applicazione verrà aggiornata da `http://www.adatum.com/MyApp` , ad esempio, la chiamata per generare il manifesto di distribuzione potrebbe essere simile alla seguente:

    ```cmd
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application
    ```

### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Uso di MageUI.exe per distribuire un'applicazione che verifica la disponibilità di aggiornamenti a livello di codice

- Seguire le istruzioni per la distribuzione dell'applicazione usando Mage.exe come illustrato in [procedura dettagliata: distribuire manualmente un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Nella scheda **Opzioni di distribuzione** impostare il campo **percorso iniziale** sul manifesto dell'applicazione ClickOnce deve verificare la disponibilità di aggiornamenti. Nella scheda **Opzioni di aggiornamento** deselezionare la casella **di controllo questa applicazione deve verificare la disponibilità di aggiornamenti** .

## <a name="net-framework-security"></a>Sicurezza di .NET Framework
 Per utilizzare l'aggiornamento a livello di codice, l'applicazione deve disporre delle autorizzazioni di attendibilità totale.

## <a name="see-also"></a>Vedi anche
- [Procedura: specificare un percorso alternativo per gli aggiornamenti della distribuzione](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)
- [Scegliere una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)