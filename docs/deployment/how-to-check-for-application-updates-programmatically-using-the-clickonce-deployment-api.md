---
title: Aggiornamenti automatici delle app con l'API ClickOnce distribuzione automatica
description: Informazioni su come scrivere codice in ClickOnce che usa la classe ApplicationDeployment per verificare la disponibilità di aggiornamenti in base a un evento, ad esempio una richiesta utente.
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
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: e8440b6d5b3d83138183c368525486d0cad3778be9aee47b4c519b0ac563f461
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121435530"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Procedura: Controllare gli aggiornamenti dell'applicazione a livello di codice tramite l'API della distribuzione ClickOnce
ClickOnce due modi per aggiornare un'applicazione dopo la distribuzione. Nel primo metodo è possibile configurare la distribuzione ClickOnce per controllare automaticamente la disponibilità di aggiornamenti a determinati intervalli. Nel secondo metodo è possibile scrivere codice che usa la classe per verificare la disponibilità di aggiornamenti in base a un evento, ad esempio <xref:System.Deployment.Application.ApplicationDeployment> una richiesta utente.

 Le procedure seguenti illustrano codice per l'esecuzione di un aggiornamento a livello di codice e descrivono anche come configurare la distribuzione ClickOnce per abilitare i controlli degli aggiornamenti a livello di codice.

 Per aggiornare un'applicazione ClickOnce a livello di codice, è necessario specificare un percorso per gli aggiornamenti. Questa operazione viene talvolta definita provider di distribuzione. Per altre informazioni sull'impostazione di questa proprietà, vedere [Scegliere una ClickOnce di aggiornamento.](../deployment/choosing-a-clickonce-update-strategy.md)

> [!NOTE]
> È anche possibile usare la tecnica descritta di seguito per distribuire l'applicazione da un percorso, ma aggiornarla da un'altra. Per altre informazioni, vedere Procedura: Specificare un percorso [alternativo per gli aggiornamenti della distribuzione.](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)

### <a name="to-check-for-updates-programmatically"></a>Per verificare la disponibilità di aggiornamenti a livello di codice

1. Creare una nuova applicazione Windows Forms usando la riga di comando o gli strumenti visivi preferiti.

2. Creare qualsiasi pulsante, voce di menu o altra voce dell'interfaccia utente che gli utenti devono selezionare per verificare la disponibilità di aggiornamenti. Dal gestore eventi di tale elemento, chiamare il metodo seguente per cercare e installare gli aggiornamenti.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs" id="Snippet6":::
    :::code language="cpp" source="../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp" id="Snippet6":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb" id="Snippet6":::

3. Compilare l'applicazione.

### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Usare Mage.exe per distribuire un'applicazione che verifica la disponibilità di aggiornamenti a livello di codice

- Seguire le istruzioni per distribuire l'applicazione usando Mage.exe come illustrato in Procedura [dettagliata:](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)Distribuire manualmente un'ClickOnce applicazione . Quando si Mage.exe per generare il manifesto della distribuzione, assicurarsi di usare l'opzione della riga di comando e di specificare l'URL in cui ClickOnce verificare la disponibilità `providerUrl` di aggiornamenti. Se l'applicazione si aggiornerà da , ad `http://www.adatum.com/MyApp` esempio, la chiamata per generare il manifesto della distribuzione potrebbe essere simile alla seguente:

    ```cmd
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application
    ```

### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Uso MageUI.exe per distribuire un'applicazione che verifica la disponibilità di aggiornamenti a livello di codice

- Seguire le istruzioni per distribuire l'applicazione usando Mage.exe come illustrato in Procedura [dettagliata:](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)Distribuire manualmente un'ClickOnce applicazione . Nella scheda **Opzioni di distribuzione** impostare il campo **Percorso** iniziale sul manifesto dell'applicazione ClickOnce verificare la disponibilità di aggiornamenti. Nella scheda **Opzioni di** aggiornamento deselezionare la casella di controllo Questa applicazione deve controllare la **disponibilità di** aggiornamenti.

## <a name="net-framework-security"></a>Sicurezza di .NET Framework
 L'applicazione deve avere autorizzazioni di attendibilità totale per usare l'aggiornamento a livello di codice.

## <a name="see-also"></a>Vedi anche
- [Procedura: Specificare un percorso alternativo per gli aggiornamenti della distribuzione](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)
- [Scegliere una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)