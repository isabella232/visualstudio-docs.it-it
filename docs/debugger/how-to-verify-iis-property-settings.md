---
title: Verificare i valori delle proprietà IIS Impostazioni | Microsoft Docs
description: Informazioni su come verificare le impostazioni delle proprietà IIS impostate per un'applicazione Web usando lo strumento di amministrazione di IIS.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ad9b7d95e6700e7950d92282e86ca86d12d824a18f288acd10a3939b945bfb45
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121453253"
---
# <a name="how-to-verify-iis-property-settings"></a>Procedura: verificare le impostazioni delle proprietà di IIS

È possibile impostare le proprietà di un'applicazione Web utilizzando lo strumento di amministrazione IIS. Per consentire l'esecuzione dell'applicazione, è necessario che tali proprietà siano impostate correttamente, pertanto la verifica di queste impostazioni è spesso un passaggio necessario nel processo di risoluzione dei problemi.

> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

## <a name="to-check-iis-settings-for-the-web-application"></a>Per controllare le impostazioni IIS dell'applicazione Web

1. Aprire la finestra **Strumenti di amministrazione**. Fare clic sul pulsante **Start**, scegliere **Programmi** e quindi **Strumenti di amministrazione**. Se la voce **Strumenti di amministrazione** non è presente nel menu **Programmi**, cercarla nel **Pannello di controllo**.

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

5. Per un'applicazione ATL Server verificare che il verbo DEBUG sia associato all'estensione ISAPI. Per altre informazioni, vedere [Procedura: Associare il verbo DEBUG all'estensione](/previous-versions/ms165022(v=vs.100)).

6. Per un'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], accertarsi che per la cartella virtuale dell'applicazione sia impostato un Nome applicazione in **Gestione Internet Information Services (IIS)**, **Gestione servizi Internet** o **Internet Information Services**.

   1. Nella finestra **Proprietà** dell'applicazione Web scegliere la scheda **Directory**, se l'applicazione è contenuta in una directory virtuale, o **Home directory**, se è contenuta in un sito Web.

   2. Verificare che il nome in **Percorso locale** corrisponda al nome della directory in cui l'applicazione è stata effettivamente distribuita.

   3. In **Impostazioni applicazione** digitare il nome della directory radice che contiene l'applicazione.

   4. Scegliere **OK** per chiudere la finestra di dialogo **Proprietà**.

7. Per un'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], fare clic sulla scheda **ASP.NET** e verificare che sia specificata la versione corretta di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

8. Scegliere **OK** per chiudere la finestra di dialogo **Proprietà**.

9. Fare clic su **OK** per chiudere le finestre di dialogo **Gestione Internet Information Services (IIS)**, **Gestione servizi Internet** o **Internet Information Services**.

## <a name="see-also"></a>Vedi anche

- [Risoluzione dei problemi](../debugger/debugging-web-applications-troubleshooting.md)