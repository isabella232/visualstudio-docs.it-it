---
title: 'Procedura: verificare le impostazioni delle proprietà IIS | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b6eb30c411b7a863d4ba9522159d6100abb48cb6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884849"
---
# <a name="how-to-verify-iis-property-settings"></a>Procedura: verificare le impostazioni delle proprietà di IIS
È possibile impostare le proprietà di un'applicazione Web utilizzando lo strumento di amministrazione IIS. Per consentire l'esecuzione dell'applicazione, è necessario che tali proprietà siano impostate correttamente, pertanto la verifica di queste impostazioni è spesso un passaggio necessario nel processo di risoluzione dei problemi.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-check-iis-settings-for-the-web-application"></a>Per controllare le impostazioni IIS dell'applicazione Web  
  
1. Aprire il **strumenti di amministrazione** finestra: sulle **avviare** dal menu **programmi**e quindi fare clic su **strumenti di amministrazione**. Se **strumenti di amministrazione** non viene visualizzato nella **programmi** dal menu e quindi cercarlo nel **Pannello di controllo**.  
  
   -   In Windows 2000, selezionare **Gestione servizi Internet**.  
  
   -   In Windows XP, selezionare **Internet Information Services**.  
  
   -   In Windows Server 2003, fare doppio clic su **gestire il proprio Server**.  
  
        Il **gestire il proprio Server** verrà visualizzata la finestra. Sotto **Server applicazioni**, fare clic su **gestire il server applicazioni**.  
  
        Il **Server applicazioni** verrà visualizzata la finestra. Aprire il **Internet Information Services (IIS) Manager** nodo nel riquadro sinistro.  
  
2. Nella finestra di dialogo fare clic sul nodo del controllo albero per il computer. Fare clic sui **siti Web** nodo, quindi selezionare il nodo dell'applicazione Web. Si tratterà di un nodo del sito Web e pertanto di pari livello la **sito Web predefinito** nodo o un nodo di directory virtuale sotto un nodo di sito Web esistente.  
  
3. Fare doppio clic su applicazione Web e nel menu di scelta rapida, fare clic su **proprietà**.  
  
4. Verificare le impostazioni di sicurezza dell'applicazione Web:  
  
   1.  Nell'applicazione Web **delle proprietà** finestra, fare clic sul **protezione Directory** scheda e fare clic su **modifica**.  
  
   2.  Nel **metodi di autenticazione** finestra di dialogo **Abilita accesso anonimo** e **autenticazione Windows integrata** se non sono già selezionate.  
  
   3.  Fare clic su **OK** per chiudere la **metodi di autenticazione** nella finestra di dialogo.  
  
5. Per un'applicazione ATL Server verificare che il verbo DEBUG sia associato all'estensione ISAPI. Per altre informazioni, vedere [procedura: associare verbo DEBUG con estensione](https://msdn.microsoft.com/library/50d261d3-4bd4-41c0-b44e-3591086f121e).  
  
6. Per un [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dell'applicazione, assicurarsi che la cartella virtuale per l'applicazione ha un nome applicazione impostato **Gestione Internet Information Services (IIS)**, **Gestione servizi Internet** o **Internet Information Services**.  
  
   1.  Nell'applicazione Web **delle proprietà** finestra, seleziona la **Directory** scheda, se l'applicazione è in una directory virtuale, o la **Home Directory** scheda, se l'applicazione è in un sito Web.  
  
   2.  Verificare che il nome nel **percorso locale** corrisponde al nome della directory in cui è stata effettivamente distribuita l'applicazione.  
  
   3.  Sotto **le impostazioni dell'applicazione**, digitare il nome della directory radice che contiene l'applicazione.  
  
   4.  Fare clic su **OK** per chiudere la **proprietà** nella finestra di dialogo.  
  
7. Per un [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dell'applicazione, fare clic sui **ASP.NET** scheda e verificare che la versione corretta di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] è specificato.  
  
8. Fare clic su **OK** per chiudere la **proprietà** nella finestra di dialogo.  
  
9. Fare clic su **OK** per chiudere la **Gestione Internet Information Services (IIS)**, **Gestione servizi Internet**, o **Internet Information Services**finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi](../debugger/debugging-web-applications-troubleshooting.md)