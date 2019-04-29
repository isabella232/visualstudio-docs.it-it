---
title: 'Procedura: Verificare le impostazioni delle proprietà IIS | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3dd516151f7a3656da1bae195870e8cc29528cfa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846428"
---
# <a name="how-to-verify-iis-property-settings"></a>Procedura: Verificare le impostazioni delle proprietà IIS

È possibile impostare le proprietà di un'applicazione Web utilizzando lo strumento di amministrazione IIS. Per consentire l'esecuzione dell'applicazione, è necessario che tali proprietà siano impostate correttamente, pertanto la verifica di queste impostazioni è spesso un passaggio necessario nel processo di risoluzione dei problemi.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

## <a name="to-check-iis-settings-for-the-web-application"></a>Per controllare le impostazioni IIS dell'applicazione Web

1. Aprire il **strumenti di amministrazione** finestra: Nel **avviare** dal menu **programmi**, quindi fare clic su **strumenti di amministrazione**. Se la voce **Strumenti di amministrazione** non è presente nel menu **Programmi**, cercarla nel **Pannello di controllo**.

   - In Windows 2000 selezionare **Gestione servizi Internet**.

   - In Windows XP selezionare **Internet Information Services**.

   - In Windows Server 2003 fare doppio clic su **Amministrazione server**.

        Verrà visualizzata la finestra **Amministrazione server**. In **Server applicazioni** fare clic su **Gestisci questo server applicazioni**.

        Viene visualizzata la finestra **Server applicazioni**. Aprire il nodo **Gestione Internet Information Services (IIS)** nel riquadro di sinistra.

2. Nella finestra di dialogo fare clic sul nodo del controllo struttura ad albero per il computer. Fare clic sul nodo **Siti Web** e quindi selezionare il nodo dell'applicazione Web. Si tratterà di un nodo di sito Web, quindi di pari livello rispetto al nodo **Sito Web predefinito**, o di un nodo di directory virtuale al di sotto di un nodo di sito Web.

3. Fare clic con il pulsante destro del mouse sull'applicazione Web, quindi scegliere **Proprietà** dal menu di scelta rapida.

4. Verificare le impostazioni di sicurezza dell'applicazione Web:

   1. Nella finestra **Proprietà** dell'applicazione Web fare clic sulla scheda **Sicurezza directory** e scegliere **Modifica**.

   2. Nella finestra di dialogo **Metodi di autenticazione** selezionare **Consenti accesso anonimo** e **Autenticazione Windows integrata**, se queste opzioni non sono già selezionate.

   3. Scegliere **OK** per chiudere la finestra di dialogo **Metodi di autenticazione**.

5. Per un'applicazione ATL Server verificare che il verbo DEBUG sia associato all'estensione ISAPI. Per altre informazioni, vedere [Procedura: Associare il verbo DEBUG con estensione](https://msdn.microsoft.com/library/50d261d3-4bd4-41c0-b44e-3591086f121e).

6. Per un'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], accertarsi che per la cartella virtuale dell'applicazione sia impostato un Nome applicazione in **Gestione Internet Information Services (IIS)**, **Gestione servizi Internet** o **Internet Information Services**.

   1. Nella finestra **Proprietà** dell'applicazione Web scegliere la scheda **Directory**, se l'applicazione è contenuta in una directory virtuale, o **Home directory**, se è contenuta in un sito Web.

   2. Verificare che il nome in **Percorso locale** corrisponda al nome della directory in cui l'applicazione è stata effettivamente distribuita.

   3. In **Impostazioni applicazione** digitare il nome della directory radice che contiene l'applicazione.

   4. Fare clic su **OK** per chiudere la finestra di dialogo **Proprietà**.

7. Per un'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], fare clic sulla scheda **ASP.NET** e verificare che sia specificata la versione corretta di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

8. Fare clic su **OK** per chiudere la finestra di dialogo **Proprietà**.

9. Fare clic su **OK** per chiudere le finestre di dialogo **Gestione Internet Information Services (IIS)**, **Gestione servizi Internet** o **Internet Information Services**.

## <a name="see-also"></a>Vedere anche

- [Risoluzione dei problemi](../debugger/debugging-web-applications-troubleshooting.md)